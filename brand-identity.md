# APEX Training — Brand Identity

> Il sistema di identità visiva e comunicativa di APEX, estratto dal design language del prototipo MVP.

---

## 1. Il Nome

**APEX** — il punto più alto, il vertice. Scelto per evocare:
- **Performance massima** — il picco a cui l'atleta aspira
- **Precisione** — un vertice è un punto esatto, non un'area vaga
- **Ambizione tecnica** — richiama il vocabolario dell'ingegneria e della scienza dello sport

Il nome è sempre scritto in **MAIUSCOLO**: `APEX`.
Il prodotto completo è **APEX Training**.

---

## 2. Logo

### Simbolo
- Forma: **Quadrato con bordi arrotondati** (border-radius: 16px)
- Sfondo: **Electric Lime** (#C8FF00)
- Icona: **Activity/Heartbeat line** — traccia ECG stilizzata (3 vertici, linea spezzata)
- Glow: `box-shadow: 0 0 30px rgba(200,255,0,0.25)`

### Logotipo
- Font: **Inter** — weight 900 (Black)
- Colore: Bianco (#FFFFFF)
- Spaziatura: `letter-spacing: -1px` (tight)
- Dimensione: 28px nel contesto mobile

### Composizione
Simbolo + Logotipo allineati orizzontalmente con `gap: 11px`.

---

## 3. Palette Colori

### Colori Primari

| Token | Hex | Uso |
|---|---|---|
| **Electric Lime** | `#C8FF00` | CTA, accenti, feedback positivo, progressi |
| **Void Black** | `#090909` | Background principale, schermo |
| **Pure White** | `#FFFFFF` | Testo primario, titoli |

### Scala di Grigi (Surface System)

| Token | Hex | Uso |
|---|---|---|
| `s0` | `#080808` | Sfondo assoluto |
| `s1` | `#0f0f0f` | Layer 1 (sotto le card) |
| `s2` | `#1a1a1a` | Layer 2 (phone shell gradient start) |
| `s3` | `#242424` | Layer 3 (bordi, separatori) |
| `s4` | `#2e2e2e` | Layer 4 (elementi interattivi hover) |
| **Card base** | `#131313` | Background card standard |

### Colori Semantici (Muscle Badge System)

| Gruppo | Colore | Hex |
|---|---|---|
| Chest | Red | `#f87171` |
| Shoulders | Purple | `#c084fc` |
| Triceps | Orange | `#fb923c` |
| Back | Blue | `#60a5fa` |
| Biceps | Teal | `#2dd4bf` |
| Legs | Violet | `#a78bfa` |
| Core | Yellow | `#eab308` |

> Ogni colore semantico viene usato a tre livelli:
> - **Background**: `rgba(color, 0.10)` 
> - **Testo**: colore pieno
> - **Bordo**: `rgba(color, 0.18)`

### Colori di Stato

| Stato | Colore | Applicazione |
|---|---|---|
| Active | `#C8FF00` (lime) | Atleta in sessione |
| Idle | `#fb923c` (orange) | Atleta fermo |
| Done | `rgba(255,255,255,0.4)` | Sessione completata |
| Online | `#22c55e` (green) | Indicatore presenza |

---

## 4. Tipografia

### Font Family
**Inter** — da Google Fonts, con tutte le weight da 300 a 900.

```
font-family: 'Inter', sans-serif;
-webkit-font-smoothing: antialiased;
```

### Scala Tipografica

| Elemento | Size | Weight | Spacing | Uso |
|---|---|---|---|---|
| **Hero Title** | 22px | 800 (ExtraBold) | -0.6px | Nome atleta, titoli principali |
| **Section Title** | 19px | 800 | -0.4px | Nome workout, nome piano |
| **Card Title** | 16px | 800 | -0.3px | Nome esercizio, ruolo login |
| **CTA Text** | 14.5px | 700 (Bold) | 0.01em | Pulsanti azione |
| **Body** | 14px | 600 (SemiBold) | — | Input, contenuto principale |
| **Caption** | 12px–12.5px | 500 (Medium) | — | Meta-info, sottotitoli |
| **Badge/Label** | 10px–10.5px | 600–700 | 0.06–0.12em | Badge, etichette, status |
| **Micro** | 9.5px | 500–600 | 0.1em | Tab bar, label minori |

### Regole Tipografiche
- Titoli: **letter-spacing negativo** (tight) → sensazione premium e moderna
- Label/Badge: **letter-spacing positivo** + `text-transform: uppercase` → gerarchia chiara
- Numeri: `font-variant-numeric: tabular-nums` → allineamento preciso nei contatori
- Mai peso sotto 500 per UI elements — l'app è **bold-first**

---

## 5. Componenti UI

### Card System

```css
/* Card standard */
background: #131313;
border: 1px solid rgba(255,255,255,0.058);
border-radius: 20px;         /* card grande */
border-radius: 18px;         /* card piccola */
```

### Hero Card (con glow lime)

```css
background: linear-gradient(140deg, #181808 0%, #121208 50%, #0e0e08 100%);
border: 1px solid rgba(200,255,0,0.11);
border-radius: 22px;
/* + radial-gradient glow pseudo-elements */
```

### CTA Button

```css
background: #C8FF00;
color: #000;
font-weight: 700;
border-radius: 16px;
padding: 15px 24px;
/* :active → scale(0.96) + #b5e800 */
```

### Input Field

```css
background: rgba(255,255,255,0.05);
border: 1px solid rgba(255,255,255,0.1);
border-radius: 12px;
color: white;
font-size: 14px;
font-weight: 600;
/* :focus → border-color: rgba(200,255,0,0.45) */
```

### Checkbox (Exercise completion)

```css
width: 26px; height: 26px;
border-radius: 50%;
border: 2px solid rgba(255,255,255,0.14);
/* .done → background: #C8FF00, spring animation */
```

### Badge / Pill

```css
border-radius: 20px;
padding: 2px 9px;
font-size: 10px;
font-weight: 600;
/* Usa la tripletta: bg rgba(0.10), text pieno, border rgba(0.18) */
```

---

## 6. Motion & Animation

### Principi di Motion
1. **Feedback immediato** — ogni tap ha una risposta visiva (`scale(0.96)` on `:active`)
2. **Spring physics** — le checkbox usano `cubic-bezier(0.34,1.56,0.64,1)` per un effetto elastico
3. **Smooth transitions** — navigazione con `translateX + opacity` a 280ms
4. **Continuous feedback** — timer con ring animation, countdown SVG in tempo reale

### Specifiche

| Animazione | Durata | Easing | Uso |
|---|---|---|---|
| Screen slide | 280ms | `cubic-bezier(0.4,0,0.2,1)` | Navigazione tra schermate |
| Checkbox spring | 250ms | `cubic-bezier(0.34,1.56,0.64,1)` | Check esercizio |
| Progress ring | 1200ms | `cubic-bezier(0.4,0,0.2,1)` | Aggiornamento SVG ring |
| Button press | 180ms | ease | Feedback CTA |
| Modal entrance | 300ms | Spring bezier | Modal completamento |
| Typing dots | 1400ms | ease-in-out, infinite | Indicatore typing chat |
| Play ring pulse | 2000ms | ease-out, infinite | Pulsazione play video |
| Toast in/out | 300ms / 250ms | Spring / ease-in | Notifiche toast |

---

## 7. Iconografia

### Libreria
**Lucide Icons** — set open-source, lineare, coerente.

### Icone Core

| Contesto | Icona | Significato |
|---|---|---|
| Atleta | `dumbbell` | Ruolo atleta |
| Coach | `users` | Ruolo coach, gestione |
| Dashboard | `layout-dashboard` | Pannello di controllo |
| Workout | `play` | Avvio sessione |
| Timer | `clock` | Durata, tempo |
| Calorie | `flame` | Energia / intensità |
| Navigazione | `chevron-right`, `chevron-left`, `arrow-left` | Direzione, flusso |
| Chat | `message-circle` | Comunicazione |
| Logout | `log-out` | Uscita |

### Stile Icone
- Dimensione standard: `width: 18-20px`
- Colore default: `rgba(255,255,255,0.3)` — mai troppo invadenti
- Colore attivo: `#C8FF00` (lime)
- Stroke-based, mai filled

---

## 8. Effetti e Atmosfera

### Glow System
APEX usa **radial gradient glow** per creare profondità e direzionalità:

```css
/* Background page — sottile, bilanciato */
radial-gradient(ellipse at 15% 50%, rgba(200,255,0,0.025) 0%, transparent 55%),
radial-gradient(ellipse at 85% 20%, rgba(59,130,246,0.025) 0%, transparent 55%);

/* Hero card — lime glow in alto a destra + basso a sinistra */
radial-gradient(circle, rgba(200,255,0,0.07) 0%, transparent 70%);

/* Logo — box-shadow glow */
box-shadow: 0 0 30px rgba(200,255,0,0.25);
```

### Backdrop Blur
La tab bar e gli overlays usano `backdrop-filter: blur(24px)` per profondità.

### Border Light
Bordi sottilissimi (`rgba(255,255,255,0.05-0.07)`) creano separazione senza peso visivo.

---

## 9. Tone of Voice

### Personalità
- **Diretto**: frasi corte, verbi d'azione ("Start Workout", "Set Done", "Back to Workout")
- **Tecnico ma accessibile**: usa termini fitness reali (sets, reps, rest) senza gergo inutile
- **Incoraggiante senza essere sdolcinato**: "Session in progress", non "You're doing great!!!"
- **Bilingue naturale**: l'interfaccia mescola italiano ed inglese dove il gergo fitness lo richiede ("Accedi come Atleta", ma "Start Workout")

### Pattern Copywriting

| Tipo | Esempio | Stile |
|---|---|---|
| CTA primaria | "Start Workout" | Verbo + sostantivo, breve |
| Status | "Session in progress" | Stato oggettivo |
| Label | "STREAK", "VOLUME" | Uppercase, tracking positivo |
| Greeting | "Good morning, Alex 👋" | Caldo, con nome ed emoji |
| Meta info | "Week 2 · Day 3" | Separatore `·`, conciso |
| Empty state | "DEMO MODE · NO REAL DATA" | Uppercase, informativo |

---

## 10. Design Principles (Riassunto Visivo)

| Principio | Manifestazione |
|---|---|
| **Dark-first** | #090909 ovunque, mai sfondi chiari |
| **Lime as signal** | Il lime (#C8FF00) appare solo dove c'è azione, progresso, o focus |
| **Dense but clear** | Molto contenuto per schermata, ma gerarchia tipografica forte |
| **Tactile feedback** | Ogni interazione ha una risposta fisica (scale, spring, glow) |
| **Contained premium** | iPhone shell, rounded corners generosi, ombre deep |
| **Data over decoration** | Numeri grandi, progress ring, badge informativi — zero illustrazioni decorative |
