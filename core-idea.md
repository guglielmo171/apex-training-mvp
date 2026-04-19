# APEX Training — Core Brand Idea

> Il documento fondativo che definisce *cosa* è APEX, *perché* esiste e *per chi* è stato creato.

---

## 1. Essenza del Brand

**APEX** non è un'app di fitness generica. È un **sistema operativo per il rapporto Coach–Atleta**, progettato per digitalizzare e potenziare la relazione professionale tra preparatore e atleta attraverso tecnologia premium, dati strutturati e comunicazione in tempo reale.

### Tagline

> **Digitize your training experience.**

### One-liner

*APEX trasforma il coaching sportivo da fogli Excel e messaggi WhatsApp in un'esperienza digitale fluida, misurabile e professionale.*

---

## 2. Missione

Dare a ogni Coach gli strumenti digitali per gestire i propri atleti con la stessa precisione con cui un software engineer gestisce il proprio codebase: **versionato, tracciato, iterabile**.

Dare a ogni Atleta la chiarezza totale su *cosa fare*, *come farlo* e *quanto manca* — eliminando l'ambiguità dall'allenamento.

---

## 3. Visione

Un ecosistema dove il coaching sportivo diventa **scalabile senza perdere personalizzazione**. Dove un Coach può seguire 50 atleti con la stessa qualità con cui ne segue 5 — perché il sistema si occupa dell'operatività, lasciando al coach il pensiero strategico.

---

## 4. Problema che Risolviamo

| Problema attuale | Soluzione APEX |
|---|---|
| Piani scritti su PDF/Google Sheets non interattivi | Piani strutturati multi-giorno con progressione automatica |
| L'atleta non sa a che punto è | Progress tracking in tempo reale per giorno, esercizio, set |
| Il coach non ha visibilità su chi ha fatto cosa | Dashboard coach con stato di ogni atleta (active/idle/done) |
| Comunicazione frammentata su WhatsApp/Telegram | Chat integrata con note contestuali sull'allenamento |
| Parametri di allenamento persi o dimenticati | Sets × Reps × Rest definiti per ogni esercizio in ogni giorno |
| L'atleta si allena "a sensazione" | Timer guidato per set e recupero con feedback visivo |

---

## 5. Archetipi Utente

### 🏋️ L'Atleta

- **Chi è**: Persona seria riguardo ai propri obiettivi fisici, che investe in un coach professionista
- **Cosa vuole**: Chiarezza assoluta. Aprire l'app, sapere cosa fare oggi, eseguire, tracciare, finire
- **Pain point**: "Il mio coach mi manda una scheda su WhatsApp e poi non so mai se sto facendo bene"
- **Momento wow**: Aprire l'app e vedere il piano del giorno con timer integrato, senza dover chiedere nulla

### 📋 Il Coach

- **Chi è**: Personal trainer / preparatore atletico che gestisce più atleti contemporaneamente
- **Cosa vuole**: Controllo e scalabilità. Creare un piano una volta, assegnarlo, monitorare senza micromanagement
- **Pain point**: "Passo più tempo a mandare messaggi e aggiornare fogli che a pensare agli allenamenti"
- **Momento wow**: Vedere a colpo d'occhio lo stato di tutti i suoi atleti, chi è attivo, chi ha finito, chi è fermo

---

## 6. Principi di Prodotto

### ① Sequenzialità come disciplina
L'allenamento non è casuale. Day 1 → Day 2 → Day 3 → Reset. La struttura **sequenziale** dei piani riflette la filosofia: la progressione richiede ordine.

### ② Zero ambiguità
Ogni schermata risponde a una sola domanda. La Home dice *"cosa faccio oggi?"*. Il Workout dice *"quali esercizi, in che ordine?"*. Il Timer dice *"quante serie mancano, quanto riposo?"*.

### ③ Coach-first design
Il Coach non è un utente secondario. È il **creatore del valore**. L'architettura del prodotto parte dalla sua capacità di creare, assegnare e monitorare piani. L'atleta è il consumatore di quel valore.

### ④ Mobile-native, performance-grade
L'interfaccia è pensata per essere usata **in palestra, con le mani sudate, tra un set e l'altro**. Tap target grandi, feedback tattile, informazioni dense ma leggibili.

### ⑤ Dati strutturati > Testo libero
Un piano non è una nota di testo. È una struttura: `Plan → Days[] → Exercises[] → { sets, reps, rest }`. Questa architettura permette progressione automatica, analytics e scalabilità.

---

## 7. Posizionamento Strategico

```
             Alta Personalizzazione
                     ▲
                     │
                     │    ★ APEX Training
                     │    (scalabile + personale)
                     │
   Scalabile ◄───────┼────────► Non Scalabile
                     │
        App Fitness  │     Coaching 1:1
        Generiche    │     (di persona)
        (MyFitnessPal│     
         Fitbod)     │
                     │
                     ▼
             Bassa Personalizzazione
```

**APEX occupa il quadrante "Scalabile + Personalizzato"** — un coach può gestire molti atleti mantenendo piani individuali e comunicazione dedicata.

---

## 8. Metriche di Successo (North Star)

| Metrica | Descrizione |
|---|---|
| **Sessioni completate / settimana** | L'atleta sta effettivamente usando il piano? |
| **Atleti attivi per coach** | Il coach sta scalando grazie al tool? |
| **Time-to-first-workout** | Quanto velocemente un nuovo atleta inizia il primo allenamento? |
| **Streak medio** | L'app genera abitudine e consistenza? |
| **Messaggi coach / settimana** | La comunicazione avviene nell'app o torna su WhatsApp? |

---

## 9. Mantra Interno

> **"Structure breeds performance."**

La struttura non è burocrazia. La struttura è ciò che trasforma l'intenzione in risultato — tanto nel codice quanto nell'allenamento.
