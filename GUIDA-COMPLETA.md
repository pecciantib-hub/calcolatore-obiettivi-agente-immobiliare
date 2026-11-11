# Guida completa: formule e logica del calcolatore

Questa guida descrive il comportamento implementato in [`index.html`](./index.html). Tutti gli importi sono in euro; i tassi percentuali inseriti nell’interfaccia sono convertiti in fattori dividendo per 100. I valori decimali intermedi non vengono arrotondati nei calcoli; l’arrotondamento è solo di visualizzazione.

## 1. Variabili principali

| Simbolo | Significato |
|---|---|
| `T` | Guadagno lordo mensile desiderato (`target`) |
| `p` | Piano provvigionale espresso come numero decimale (`piano / 100`) |
| `vm` | Provvigione media di una vendita |
| `lm` | Provvigione media di una locazione |
| `gI` | Incarichi mensili da acquisire e vendere |
| `gV` | Vendite mensili concluse |
| `gL` | Locazioni mensili concluse |
| `c9…c13` | Tassi di conversione del ramo vendite |
| `c_na_rent…c_it_rent` | Tassi di conversione del ramo affitti |

Il checkbox sulle locazioni è mantenuto nell’interfaccia, ma la logica corrente non lo usa per azzerare o nascondere le locazioni: `gL` e i relativi calcoli restano attivi.

## 2. Compenso mensile stimato (sezioni vendite e affitti)

La quota agente è fissa al 50%; i meriti sono fissi al 120% per l’acquisizione e all’80% per la vendita. Il compenso unitario stimato è:

- **Per incarico acquisito**: `cI = (vm / 2) × 1,20 × p`
- **Per vendita conclusa**: `cV = (vm / 2) × 0,80 × p`
- **Per locazione conclusa**: `cL = lm × p`

Il contributo mensile di ogni attività e il totale sono:

- `kI = gI × cI`
- `kV = gV × cV`
- `kL = gL × cL`
- **Guadagno mensile stimato**: `tot = kI + kV + kL`
- **Scostamento dal target**: `diff = tot − T`
- **Percentuale del target raggiunta**: `tot / T × 100` (se `T > 0`)

Il checkbox locazioni non cambia `kL` né `tot`.

## 3. Fatturato e produzione (sezione 3.1)

Con un piano maggiore di zero:

- **Guadagno lordo annuale obiettivo**: `T × 12`
- **Fatturato annuo necessario**: `fat = (T / p) × 12`
- **Produzione necessaria**: `fat × 1,12`

Se il piano è zero, il calcolatore imposta il fatturato necessario a zero per evitare una divisione per zero. La produzione è il fatturato maggiorato del 12%.

## 4. Funnel vendite

I volumi richiesti a monte sono calcolati risalendo dai volumi mensili inseriti. Ogni divisione usa il tasso espresso come frazione:

### Per gli incarichi da acquisire (`gI`)

- Incarichi da prendere: `oI = gI / (c13 / 100)`
- Acquisizioni necessarie: `qI = oI / (c10 / 100)`
- Notizie necessarie: `nI = qI / (c9 / 100)`

Qui `c13` è il tasso incarichi → transazioni, `c10` acquisizioni → incarichi e `c9` notizie → acquisizioni.

### Per le vendite concluse (`gV`)

- Proposte necessarie: `oV = gV / (c12 / 100)`
- Visite necessarie: `qV = oV / (c11 / 100)`

`c12` è il tasso proposte → vendite e `c11` visite → proposte.

## 5. Funnel affitti

Il ramo affitti usa tassi separati e configurabili. Risalendo dalle locazioni desiderate:

- Incarichi di affitto necessari: `oL = gL / (c_it_rent / 100)`
- Acquisizioni affitto necessarie: `qL = oL / (c_ai_rent / 100)`
- Notizie affitto necessarie: `nL = qL / (c_na_rent / 100)`
- Proposte affitto necessarie: `oV_rent = gL / (c_pt_rent / 100)`
- Visite affitto necessarie: `qV_rent = oV_rent / (c_vp_rent / 100)`

I primi tre risultati costituiscono il percorso **notizie → acquisizioni → incarichi → transazioni**. Visite e proposte sono stimate con il percorso separato **visite → proposte → transazioni**. I due percorsi partono entrambi dal volume di locazioni desiderato; non si moltiplicano l’uno con l’altro.

Con i valori iniziali (`gL = 1`, `c_it_rent = 100%`, `c_ai_rent = 60%`, `c_na_rent = 100%`, `c_pt_rent = 59%`, `c_vp_rent = 21%`), il calcolatore mostra circa 1 incarico, 1,7 acquisizioni e 1,7 notizie, oltre a 1,7 proposte e 8,1 visite.

Se un tasso è zero o negativo, la relativa divisione viene protetta e il fabbisogno interessato vale zero. Gli input del modulo hanno minimo 1%.

## 6. Riepilogo annuale (sezione 3.2)

- Transazioni lato vendite: `(gI + gV) × 12`
- Locazioni concluse: `gL × 12`
- Incarichi vendite: `oI × 12`; incarichi affitti: `oL × 12`
- Valori mensili degli incarichi: `oI` e `oL`
- Rapporto incarichi/transazioni vendite: `1 su (100 / c13)` (se `c13 > 0`)

La produzione viene ripartita in base al contributo di ciascuna linea al guadagno mensile:

- Quota vendite: `fatV = fat × (kI + kV) / tot`
- Quota affitti: `fatA = fat × kL / tot`
- Produzione vendite mostrata: `fatV × 1,12`
- Produzione affitti mostrata: `fatA × 1,12`

Se `tot` è zero, entrambe le quote sono impostate a zero. La tabella “Parametratore mensile/annuale” (24/2 incarichi, 19/1,58 vendite, 7/0,58 locazioni) è informativa e non dipende dagli input.

## 7. Calcolatore provvigionale (Parte 5)

La Parte 5 è una stima distinta dal totale mensile `tot`. Il badge confronta il lordo stimato della Parte 5 con `T × 12`.

### Agente Onboard

Il lordo stimato è la somma di:

- step selezionati: 800 €, 900 € e 1.000 €;
- incarichi vendita extra: 200 € per il primo e 100 € per ciascuno dei successivi;
- incarichi affitto extra: 50 € ciascuno;
- transazioni vendita extra: 250 € ciascuna.

### Agente Junior / Analyst

Il variabile è composto sommando, per ciascuna categoria, il compenso del primo elemento, del secondo se presente e dei successivi:

| Categoria | Primo | Secondo | Successivi |
|---|---:|---:|---:|
| Incarichi vendita | 100 € | 150 € | 200 € ciascuno |
| Incarichi affitto | 50 € | 100 € | 150 € ciascuno |
| Vendite concluse | 250 € | 400 € | 500 € ciascuna |
| Affitti conclusi | 100 € | 150 € | 200 € ciascuno |

Indicando con `V` il variabile totale e con `r` l’aliquota selezionata:

- contratto di lavoro: `r = 12%`;
- Partita IVA: `r = 20%`;
- lordo stimato implementato: `12.000 + max(0, V − 12.000) × r`.

### Agente oltre 60.000 €

Il livello è scelto in base al fatturato annuo `fat` della sezione 3.1. Le colonne delle provvigioni sono percentuali; “fisso” è mensile. La formula “Solo Provvigioni” seleziona la colonna dedicata.

| Fatturato minimo | Fisso mensile | Senza patentino: fisso + provvigioni | Senza patentino: solo provvigioni | Con patentino: fisso + provvigioni | Con patentino: solo provvigioni |
|---:|---:|---:|---:|---:|---:|
| 60.000 € | 1.000 € | 4% | 20% | 7% | 23% |
| 90.000 € | 1.100 € | 7% | 22% | 10% | 25% |
| 120.000 € | 1.300 € | 9% | 24% | 13% | 28% |
| 150.000 € | 1.500 € | 11% | 26% | 17% | 32% |
| 180.000 € | 1.800 € | 13% | 28% | 21% | 35% |
| 210.000 € | 2.000 € | 13% | 28% | 23% | 38% |
| 240.000 € | 2.400 € | 13% | 28% | 25% | 40% |
| 280.000 € | 0 € | 13% | 28% | 45% | 45% |

Il calcolo seleziona la soglia più alta non superiore a `fat`; sotto 60.000 € usa comunque la prima riga della matrice. A 280.000 € o oltre, con patentino, forza “Solo Provvigioni”. Senza patentino, il livello visualizzato e il fisso sono limitati al livello 5 e al fisso mensile di 1.800 €; la percentuale è quella della matrice selezionata.

I bonus selezionabili aggiungono 3 e/o 5 punti percentuali alla percentuale provvigionale base. Nel calcolo attuale si applicano entrambi direttamente a `fat`, se selezionati.

Compensi di guida aggiunti al lordo:

- **Tutor**: `150 € × step superati + 400 € × transazioni degli onboard`.
- **Sales Manager**: `100 € × persone coordinate × 12 + 2% × fatturato annuo team`.
- **Vice Responsabile**: fisso annuo di `100 € × 12` senza patentino o `200 € × 12` con patentino, più la stima Tutor.
- **Responsabile**: fisso annuo di `400 € × 12` senza patentino o `800 € × 12` con patentino, più 2,5% o 5% del fatturato agenzia; se selezionato, si aggiunge un ulteriore 1%.

Formula complessiva per questo profilo:

`lordo = fat × (percentuale base + bonus) / 100 + fisso mensile × 12 + compensi di guida`

Per il Tutor, i 400 € per transazione sono la stima fissa implementata dall’interfaccia, non una percentuale ricalcolata sul valore della transazione.

## 8. Interpretazione e limiti

- I risultati sono stime matematiche, non una garanzia di reddito né una busta paga.
- Gli input dei tassi descrivono conversioni medie; il funnel può quindi produrre valori frazionari di attività.
- Per confrontare i risultati con il questionario aziendale, verificare che target, piano, provvigioni medie e tassi inseriti corrispondano alle definizioni usate dall’azienda.
- Le formule della Parte 5 sono quelle attualmente implementate nel codice e potrebbero non coprire condizioni contrattuali o eccezioni non rappresentate nei campi.
