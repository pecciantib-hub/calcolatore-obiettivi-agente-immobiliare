# Guida completa al calcolatore

Questa guida spiega in modo pratico come vengono ottenute le stime mostrate dal calcolatore. Le formule sono scritte come operazioni matematiche e descritte a parole, senza riferimenti alle variabili o al codice della pagina.

Gli importi intermedi mantengono i decimali; i risultati visualizzati sono arrotondati. I tassi di conversione si inseriscono come percentuali: per esempio, il 60% significa che, su 100 persone o attività, circa 60 passano alla fase successiva.

## 1. Dati da inserire

- **Guadagno mensile desiderato**: il compenso lordo mensile che si vuole raggiungere.
- **Piano provvigionale**: la percentuale applicata al fatturato per stimare il guadagno.
- **Provvigione media di una vendita** e **provvigione media di una locazione**: i valori medi usati per stimare quanto produce ciascuna attività.
- **Obiettivi mensili**: incarichi da acquisire e vendere, vendite concluse e locazioni concluse.
- **Tassi di conversione**: ogni riga mostra due percentuali, nell’ordine **Vendite | Affitti**.

La quota agente è fissa al 50%. Anche i meriti sono fissi: 120% per l’acquisizione e 80% per la vendita. Il checkbox “Ti occupi anche di locazioni?” non esclude le locazioni dai calcoli: il numero inserito continua a essere conteggiato.

## 2. Come si stima il guadagno mensile

### Incarichi acquisiti e vendite

Per un incarico acquisito, il calcolatore prende metà della provvigione media di vendita, applica il merito acquisitore del 120% e poi il piano provvigionale.

**Esempio:** con una provvigione media di vendita di 10.000 € e un piano del 20%:

1. Metà di 10.000 € è 5.000 €.
2. Il 120% di 5.000 € è 6.000 €.
3. Il 20% di 6.000 € è **1.200 € per incarico acquisito**.

Per una vendita conclusa si usa lo stesso procedimento, ma con il merito venditore dell’80%.

**Esempio:** metà di 10.000 € è 5.000 €; l’80% di 5.000 € è 4.000 €; il 20% di 4.000 € è **800 € per vendita conclusa**.

### Locazioni

Per ogni locazione conclusa, il guadagno stimato è la provvigione media di una locazione moltiplicata per il piano provvigionale.

**Esempio:** con una provvigione media di 1.300 € e un piano del 20%, il compenso stimato è **260 € per locazione**.

### Totale del mese

Il calcolatore moltiplica il compenso unitario di ogni attività per il relativo obiettivo mensile e poi somma i risultati:

**Guadagno mensile stimato = compensi dagli incarichi acquisiti + compensi dalle vendite concluse + compensi dalle locazioni.**

La differenza rispetto al target è il guadagno stimato meno il guadagno mensile desiderato. Un risultato positivo indica che l’obiettivo è superato; uno negativo indica quanto manca.

## 3. Fatturato e produzione necessari (sezione 3.1)

Il guadagno desiderato viene annualizzato moltiplicandolo per 12.

**Esempio:** un target mensile di 3.453 € corrisponde a un target lordo annuale di circa **41.436 €**.

Per stimare il fatturato necessario, il guadagno mensile desiderato viene diviso per la percentuale del piano e il risultato viene moltiplicato per 12:

**Fatturato annuo necessario = (guadagno mensile desiderato ÷ percentuale del piano) × 12.**

La percentuale va letta come frazione: per esempio, un piano del 20% equivale a 0,20.

**Esempio:** 3.453 € diviso 0,20, poi moltiplicato per 12, dà circa **207.180 € di fatturato annuo**.

La produzione necessaria è stimata aggiungendo il 12% al fatturato:

**Produzione necessaria = fatturato annuo × 1,12.**

Nell’esempio, 207.180 € × 1,12 dà circa **232.042 €**.

Se il piano provvigionale è zero, il calcolatore mostra zero per il fatturato necessario, così da evitare una divisione per zero.

## 4. Come leggere i funnel delle vendite

Il funnel parte dagli obiettivi inseriti e risale alle attività necessarie nelle fasi precedenti. Per stimare quante attività servono, il numero desiderato nella fase successiva viene diviso per il relativo tasso di conversione.

### Incarichi da acquisire

Il calcolo parte dal numero mensile di incarichi da prendere e vendere:

1. **Incarichi da prendere:** obiettivo mensile di incarichi diviso per il tasso “Incarichi → transazioni”.
2. **Acquisizioni necessarie:** incarichi da prendere diviso per il tasso “Acquisizioni → incarichi”.
3. **Notizie da trovare:** acquisizioni necessarie divise per il tasso “Notizie → acquisizioni”.

**Esempio:** se servono 2 transazioni e il 51% degli incarichi porta a una transazione, servono 2 ÷ 0,51, cioè circa **3,9 incarichi**. Con un tasso acquisizioni-incarichi del 37%, servono circa 3,9 ÷ 0,37 = **10,6 acquisizioni**. Con un tasso notizie-acquisizioni del 40%, servono circa 10,6 ÷ 0,40 = **26,5 notizie**.

### Vendite concluse

1. **Proposte da ritirare:** vendite desiderate divise per il tasso “Proposte → transazioni”.
2. **Visite da fare:** proposte necessarie divise per il tasso “Visite → proposte”.

Il calcolatore mostra valori frazionari perché si tratta di medie statistiche: nella pratica, il numero di attività sarà naturalmente intero.

## 5. Come leggere il funnel degli affitti

Gli affitti usano percentuali proprie, indipendenti dai tassi delle vendite. Per arrivare al numero di locazioni desiderato, il calcolatore stima due percorsi che partono entrambi dal risultato finale.

### Percorso acquisizione degli incarichi

1. **Incarichi di affitto:** locazioni desiderate divise per il tasso “Incarichi → transazioni”.
2. **Acquisizioni affitto:** incarichi necessari divisi per il tasso “Acquisizioni → incarichi”.
3. **Notizie affitto:** acquisizioni necessarie divise per il tasso “Notizie → acquisizioni”.

### Percorso visite e proposte

1. **Proposte affitto:** locazioni desiderate divise per il tasso “Proposte → transazioni”.
2. **Visite affitto:** proposte necessarie divise per il tasso “Visite → proposte”.

I percorsi sono separati: visite e proposte non si moltiplicano per incarichi, acquisizioni o notizie.

Con i valori iniziali e l’obiettivo di una locazione al mese:

- tasso incarichi-transazioni 100%: serve **1 incarico**;
- tasso acquisizioni-incarichi 60%: servono circa **1,7 acquisizioni**;
- tasso notizie-acquisizioni 100%: servono circa **1,7 notizie**;
- tasso proposte-transazioni 59%: servono circa **1,7 proposte**;
- tasso visite-proposte 21%: servono circa **8,1 visite**.

Se un tasso non è valorizzato o è inferiore a 1%, il fabbisogno che dipende da quel tasso viene protetto e mostrato come zero. Gli input consentono tassi da 1% a 100%.

## 6. Riepilogo annuale (sezione 3.2)

I volumi mensili vengono moltiplicati per 12 per ottenere i totali annuali. Per le vendite, il totale delle transazioni annuali è la somma degli incarichi da acquisire e delle vendite da concludere, moltiplicata per 12. Per le locazioni, il numero mensile di locazioni concluse viene moltiplicato per 12.

Anche gli incarichi necessari vengono annualizzati moltiplicandoli per 12. La tabella mostra sia il totale annuo sia la quantità mensile corrispondente.

Il rapporto “Su quanti incarichi chiudi 1 transazione?” deriva dal tasso incarichi-transazioni. Per esempio, con un tasso del 51%, si calcola 100 ÷ 51: il risultato è circa **1 transazione ogni 2 incarichi**.

La produzione annuale viene ripartita tra vendite e affitti in proporzione al loro contributo al guadagno mensile:

1. Si calcola quale percentuale del guadagno mensile totale arriva dalle vendite e quale dagli affitti.
2. Si applicano le stesse percentuali al fatturato annuo necessario.
3. A ciascuna quota si aggiunge il 12% per ottenere la produzione da indicare.

Se il guadagno mensile totale è zero, le quote di produzione vengono mostrate come zero. Il “Parametratore mensile/annuale” (24/2 incarichi, 19/1,58 vendite e 7/0,58 locazioni) è un riferimento informativo fisso: non cambia al variare dei campi.

## 7. Calcolatore provvigionale (Parte 5)

Questa sezione calcola una stima distinta dal guadagno mensile ottenuto dagli obiettivi. Il badge confronta il lordo stimato della Parte 5 con il target mensile moltiplicato per 12.

### Agente Onboard

Il totale stimato somma:

- 800 € per lo Step 1 selezionato;
- 900 € per lo Step 2 selezionato;
- 1.000 € per lo Step 3 selezionato;
- 200 € per il primo incarico di vendita extra e 100 € per ogni ulteriore incarico;
- 50 € per ciascun incarico di affitto extra;
- 250 € per ciascuna transazione di vendita extra.

**Esempio:** Step 1 e Step 2, due incarichi vendita extra e una transazione extra danno 800 + 900 + 200 + 100 + 250 = **2.250 €**.

### Agente Junior / Analyst

Per ogni categoria, il primo elemento ha un compenso, il secondo può averne uno diverso e ogni elemento successivo usa la tariffa indicata:

| Categoria | Primo | Secondo | Ogni successivo |
|---|---:|---:|---:|
| Incarichi vendita | 100 € | 150 € | 200 € |
| Incarichi affitto | 50 € | 100 € | 150 € |
| Vendite concluse | 250 € | 400 € | 500 € |
| Affitti conclusi | 100 € | 150 € | 200 € |

Si sommano prima i compensi di tutte le categorie. Il calcolatore assume poi un fisso annuo garantito di 12.000 €. Solo la parte del variabile che supera 12.000 € viene moltiplicata per l’aliquota selezionata:

- contratto di lavoro: 12%;
- Partita IVA: 20%.

**Esempio:** se il variabile totale è 15.000 €, l’eccedenza è 3.000 €. Con contratto di lavoro si aggiunge il 12% di 3.000 €, cioè 360 €, al fisso annuo di 12.000 €: totale stimato **12.360 €**.

### Agente oltre 60.000 €

Il livello provvigionale dipende dal fatturato annuo stimato nella sezione 3.1. Si applica la riga della tabella relativa alla soglia più alta che non supera il fatturato raggiunto. Il fisso indicato è mensile; le percentuali si applicano al fatturato annuo.

| Fatturato annuo da | Fisso mensile | Senza patentino: fisso + provvigioni | Senza patentino: solo provvigioni | Con patentino: fisso + provvigioni | Con patentino: solo provvigioni |
|---:|---:|---:|---:|---:|---:|
| 60.000 € | 1.000 € | 4% | 20% | 7% | 23% |
| 90.000 € | 1.100 € | 7% | 22% | 10% | 25% |
| 120.000 € | 1.300 € | 9% | 24% | 13% | 28% |
| 150.000 € | 1.500 € | 11% | 26% | 17% | 32% |
| 180.000 € | 1.800 € | 13% | 28% | 21% | 35% |
| 210.000 € | 2.000 € | 13% | 28% | 23% | 38% |
| 240.000 € | 2.400 € | 13% | 28% | 25% | 40% |
| 280.000 € | 0 € | 13% | 28% | 45% | 45% |

Il calcolo parte dalla prima riga anche se il fatturato è inferiore a 60.000 €. A partire da 280.000 €, se è selezionato il patentino, viene applicata la formula “Solo Provvigioni”. Senza patentino, il livello visualizzato non supera il Livello 5 e il fisso non supera 1.800 € al mese.

Il lordo stimato si ottiene così:

**provvigioni sul fatturato + fisso mensile moltiplicato per 12 + eventuali compensi di guida.**

I bonus selezionabili aggiungono 3 e/o 5 punti percentuali alla percentuale provvigionale. Nel modello attuale questi punti aggiuntivi si applicano all’intero fatturato stimato quando le caselle sono selezionate; non vengono verificati separatamente il superamento trimestrale o quello del budget annuo.

### Compensi per ruoli di guida

- **Tutor:** 150 € per ogni step superato dagli Onboard, più 400 € per ogni transazione chiusa dagli Onboard.
- **Sales Manager:** 100 € al mese per ogni persona coordinata, moltiplicati per 12, più il 2% del fatturato annuo del team.
- **Vice Responsabile:** fisso annuo pari a 100 € al mese senza patentino oppure 200 € al mese con patentino, moltiplicati per 12; si aggiungono i compensi Tutor.
- **Responsabile:** fisso annuo pari a 400 € al mese senza patentino oppure 800 € al mese con patentino, moltiplicati per 12. Si aggiunge il 2,5% del fatturato dell’agenzia senza patentino oppure il 5% con patentino. Se si seleziona il raggiungimento dell’obiettivo dell’agenzia, si aggiunge un ulteriore 1%.

Per il Tutor, i 400 € a transazione sono un valore fisso stimato dal calcolatore, non il ricalcolo del 10% sul valore effettivo della transazione.

## 8. Come interpretare i risultati

- Le cifre sono stime basate sui dati inseriti, non una garanzia di reddito né una busta paga.
- I funnel possono mostrare quantità frazionarie perché i tassi rappresentano medie: nella pratica, le attività si svolgono in numeri interi.
- Per confrontare i risultati con il questionario aziendale, assicurati che target, piano, provvigioni medie e tassi abbiano le stesse definizioni usate dall’azienda.
- La Parte 5 applica le regole e le ipotesi descritte in questa guida; condizioni contrattuali particolari non presenti tra i campi non vengono considerate.
