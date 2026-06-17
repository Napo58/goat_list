# Ultimate Tennis Statistics GOAT List Scraper 🎾

Questo repository contiene un Jupyter Notebook (`goat_list.ipynb`) progettato per automatizzare l'estrazione e il salvataggio dei dati relativi alla classifica **GOAT (Greatest of All Time)** dal sito [Ultimate Tennis Statistics](https://www.ultimatetennisstatistics.com/goatList).

Lo script utilizza **Selenium WebDriver** per interagire dinamicamente con l'interfaccia web, sbloccare metriche nascoste e gestire l'impaginazione completa dei record.

---

## 📌 Funzionalità Principali

* **Automazione dell'Interfaccia (UI Interaction):** Il codice individua la barra degli strumenti superiore (`actionBar`) e apre programmaticamente il menu a discesa per la selezione delle colonne.
* **Estrazione Dati Massiva:** Attraverso l'esecuzione di script JavaScript, seleziona automaticamente tutte le caselle di controllo (checkbox) disponibili nel pannello, forzando la visualizzazione di parametri prestazionali e storici aggiuntivi che altrimenti rimarrebbero nascosti.
* **Gestione Completa della Paginazione:** Implementa un ciclo continuo che naviga in modo asincrono attraverso tutte le pagine della tabella, monitorando lo stato del pulsante "Successivo" (`>`) fino all'esaurimento dei record.
* **Esportazione in DataFrame:** Raccoglie i dati riga per riga e li organizza all'interno di un DataFrame di Pandas, pronto per essere convertito in formato CSV o Excel per successive analisi statistiche o di Machine Learning.

---

## 🛠️ Requisiti e Dipendenze

Per eseguire questo notebook, è necessario avere installato Python (o un ambiente Jupyter) insieme alle seguenti librerie. 

Puoi installarle direttamente eseguendo la cella iniziale del notebook o tramite terminale:

```bash
pip install requests beautifulsoup4 pandas openpyxl lxml selenium

```

### Requisiti di Sistema Aggiuntivi:

* **Google Chrome** installato sul computer.
* Il driver di Selenium integrato utilizzerà il browser Chrome per emulare l'utente e scorrere le pagine del portale.

---

## 📂 Flusso di Esecuzione dello Script

1. **Inizializzazione:** Viene avviata un'istanza del browser Chrome automatizzato tramite Selenium.
2. **Caricamento Pagina & Attesa:** Il software naviga sulla pagina della lista GOAT e sfrutta le funzionalità di `WebDriverWait` per attendere che gli elementi della tabella (`#goatListTable`) siano completamente caricati prima di procedere, evitando errori dovuti al caricamento asincrono.
3. **Espansione Colonne:** Il bot simula i clic sul selettore di colonne, scorre tutte le etichette (`<label>`) e attiva i flag non ancora selezionati.
4. **Scraping Iterativo:** Inizia il ciclo di lettura dei dati estratti dai tag `<td>` e `<th>` per salvare l'intestazione e i valori dei tennisti pagina dopo pagina.
5. **Chiusura Sicura:** Al completamento di tutte le pagine disponibili, la sessione del browser viene chiusa in sicurezza all'interno di un blocco `finally`, prevenendo lo spreco di risorse di sistema.

---

## 📊 Output Generato

Al termine dell'elaborazione, lo script stampa a schermo un'anteprima dei primi 3 tennisti in classifica e restituisce un DataFrame strutturato contenente:

* Il numero totale di giocatori estratti.
* Il numero complessivo di pagine elaborate.
* Tutte le metriche aggiuntive abilitate nel pannello di controllo del portale.

```

```
