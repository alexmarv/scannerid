# Scanner ID

Una **Progressive Web Application (PWA)** leggera, veloce e orientata alla privacy, progettata specificamente per l'acquisizione ottimizzata e la combinazione di documenti d'identità plastificati (CIE e Tessera Sanitaria) direttamente da smartphone.

Sviluppata per risolvere i problemi comuni legati alla scansione nativa di iOS (eccessivo sbiancamento del testo, artefatti sui volti e output in PDF non sempre accettati dai portali di attivazione).

---

## 🎯 Caratteristiche Principali

* **Zero-Server (100% Privacy-First):** L'elaborazione delle immagini avviene interamente nella RAM del dispositivo tramite l'API JavaScript `Canvas` e `Blob`. Nessuna immagine viene mai inviata a server esterni o memorizzata nella cache di rete.
* **Sfruttamento Ottico Nativo:** Sfrutta l'API HTML5 `capture="environment"`. Non utilizza flussi video WebRTC generici, ma invoca l'app Fotocamera nativa dell'iPhone/Android, consentendo l'uso dello zoom hardware, della griglia di allineamento e del blocco dell'esposizione.
* **Nomenclatura Standardizzata Automatica:** Pulisce e normalizza il testo inserito (es. trasforma "Rossi Mario" in `ROSSI_MARIO`), generando nomi file coerenti con i requisiti dei sistemi informatici aziendali e della PA (es. `COGNOME_CIE_FRONT.jpg`).
* **Download Unificato (Fronte + Retro):** Unisce asincronamente le due acquisizioni separate in un unico file JPEG (`_FRONTE_RETRO.jpg`) perfettamente allineato, aggirando il blocco dei download multipli di iOS e dimezzando i passaggi di salvataggio.
* **Burocrazia-Proof:** Ridimensiona il lato lungo a 1920px e applica una compressione ottimizzata all'80%. I file finali mantengono una leggibilità millimetrica ma pesano sempre meno di 1.5 MB, garantendo l'approvazione su qualsiasi portale web.
* **PWA & Offline Ready:** Grazie al Service Worker integrato, l'applicazione può essere installata sulla Home dell'iPhone e funziona al 100% anche in totale assenza di connessione internet.

---

## 🛠️ Architettura Tecnica

Il progetto è volutamente minimale e non richiede moduli di backend Node.js, PHP o Python. Il flusso logico è il seguente:

    [Fotocamera Standard iOS/Android]
                   │
                   ▼
       [HTML5 Input Capture File]
                   │
                   ▼
         [JS Canvas Processing] ───► Ridimensionamento (Max 1920px) & Compressione (JPEG)
                   │
                   ▼
         [Client-Side Blob URL] ───► Generazione File Unificato (Fronte + Retro)
                   │
                   ▼
      [Download Locale in Sandbox] (Zero traccia sul web)

---

## 🚀 Come Installarlo su iOS

1. Apri il link del repository su Safari dal tuo iPhone.
2. Tocca l'icona di **Condivisione** (il quadrato con la freccia verso l'alto).
3. Seleziona **Aggiungi alla schermata Home**.
4. Apri l'app direttamente dalla tua Home per utilizzarla a tutto schermo e offline.

---

## 📝 Licenza

Questo progetto è distribuito sotto licenza MIT. Libero di essere modificato, integrato o clonato per flussi di lavoro amministrativi locali.
