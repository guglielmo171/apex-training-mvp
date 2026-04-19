# APEX Training MVP - Planning Document

## Contesto del Progetto

**APEX Training MVP** è un'applicazione web single-file (HTML + Tailwind + vanilla JS) per la gestione di piani di allenamento per atleti. L'app prevede due ruoli:
- **Coach**: crea piani, assegna agli atleti, monitora progressi, comunica via chat
- **Atleta**: visualizza il proprio piano, esegue gli esercizi, segna i completamenti

## Problema Identificato

### Struttura dati attuale (WORKOUT_TEMPLATES)

La struttura attuale dei piani di allenamento è **concettualmente sbagliata**:

```js
// PROBLEMA: exerciseIds è un array flat applicato a TUTTI i giorni
{ 
  id:1, 
  name:'Upper Body Power',       
  days:'Lun · Mer · Ven',  // Solo stringa descrittiva
  exerciseIds:[1,2,4,5,6,8],  // Stessi esercizi per ogni giorno!
  level:'Advanced'
}
```

**Risultato**: Gli stessi esercizi si ripetono per tutti i giorni del piano, senza distinzione.

### Modello Atleta attuale

```js
// PROBLEMA: informazioni ridondanti e non strutturate
{ 
  id:1, 
  name:'Alex Carter',
  plan:'Upper Body – Day 3',  // Stringa costruita manualmente
  progress:3,    // Numero esercizi fatti
  total:5,       // Totale esercizi
  status:'active'
}
```

**Risultato**: 
- `plan` è una stringa, non un riferimento strutturato
- `progress`/`total` sono contatori piatti, non legati ai giorni

---

## Analisi dei Requisiti

Attraverso sessioni di Q&A con l'utente, abbiamo definito i seguenti requisiti:

### 1. Struttura del Piano (Plan Structure)

- Un piano = **molteplici giorni**, ciascuno con i propri esercizi
- Ogni giorno ha un nome personalizzabile (default: "Day 1", "Day 2"... oppure "Push Day", "Pull Day"...)
- Numero di esercizi **variabile** per ogni giorno
- L'**ordine** degli esercizi determina la sequenza nell'allenamento
- Ogni esercizio in ogni giorno ha **parametri specifici**: series × ripetizioni

### 2. Progressione Giornaliera (Day Progression)

- **Sequenziale**: completare Day 1 prima di accedere a Day 2
- Dopo l'ultimo giorno, il piano si **resetta automaticamente** (nuovo ciclo)
- I parametri (sets×reps) possono variare per ogni esercizio in ogni giorno

### 3. Assegnazione (Assignment Flow)

- L'atleta vede **tutti i giorni** del piano assegnato
- Parte sempre da **Day 1**
- Quando si assegna un nuovo piano, quello vecchio viene **sostituito**
- L'atleta può vedere la cronologia dei giorni completati

---

## Strategia di Progettazione

### Nuova Struttura Dati Proposta

```js
// Nuova struttura con per-day exercises
const WORKOUT_PLANS = [{
  id: 1,
  name: 'Upper Body Power',
  level: 'Advanced',
  badge: 'badge-advanced',
  days: [
    {
      id: 1,
      name: 'Push Day',  // oppure 'Day 1'
      exercises: [
        { exerciseId: 1, sets: 4, reps: 8, rest: '90s' },
        { exerciseId: 2, sets: 3, reps: 10, rest: '60s' }
      ]
    },
    // ... altri giorni
  ]
}];
```

### Nuovo Modello Atleta

```js
// Atleta con riferimento al piano e progresso
{
  id: 1,
  name: 'Alex Carter',
  planId: 1,        // Riferimento al piano assegnato
  currentDayIndex: 0,  // Indice del giorno corrente (0 = Day 1)
  status: 'active'  // 'idle' | 'active' | 'done'
}
```

---

## Flussi da Implementare

### Flusso 1: Struttura Dati
- Ridisegnare `WORKOUT_TEMPLATES` → `WORKOUT_PLANS` con struttura nested (plan → days → exercises)
- Aggiornare modello `ATHLETES` con `planId` e `currentDayIndex`
- Aggiornare tutte le view che mostrano informazioni sul piano

### Flusso 2: Plan Editor
- Creare interfaccia per configurare giorni uno a uno
- Per ogni giorno: aggiungere/rimuovere esercizi, impostare sets×reps
- Supportare nomi personalizzati per i giorni

### Flusso 3: Assegnazione
- Nuova schermata per selezionare piano da assegnare
- Conferma prima di sostituire piano esistente
- Sostituzione completa del vecchio piano

### Flusso 4: Workout Screen (Atleta)
- Mostrare solo gli esercizi del **giorno corrente**
- Sequentialità: completare il giorno per sbloccare il successivo
- Visualizzazione progresso giorno per giorno

### Flusso 5: Completamento Giorno
- Logica di avanzamento al giorno successivo
- Reset del piano dopo l'ultimo giorno
- Feedback visivo all'atleta

---

## Note per il Continuatore

- L'applicazione è un **single-file HTML** in `apex-training-mvp/index.html`
- Usa **Tailwind CDN** per gli stili
- **Lucide Icons** per le icone
- Sistema di routing basato su **hash** (es: `#coach-home`)
- **Dark theme** obbligatorio (#090909 background, #C8FF00 accent)
- Mantenere approccio MVP: un piano per atleta, progressione sequenziale

---

## File Principale

`apex-training-mvp/index.html` (~2500 righe)

Sezioni rilevanti:
- Linee 1138-1171: `ATHLETES`, `WORKOUT_TEMPLATES`
- Linee 1069-1085: `EXERCISES` (dati esercizi, non modificare struttura)
- Varie funzioni `render*` per le view
- Funzione `navigate()` per il routing