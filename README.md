# MobaXterm to SecureCRT Session Converter

![Version](https://img.shields.io/badge/version-v1.0.0-blue.svg)
![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)

A lightweight and efficient Python utility designed to migrate SSH sessions from **MobaXterm** to **VanDyke SecureCRT**.

This script parses the MobaXterm export file, preserves the folder structure, filters out non-SSH sessions (like RDP or VNC), and allows for custom username rules based on session keywords.

---

## 🇬🇧 English Documentation

### Features
*   **Folder Structure Preservation**: Keeps your MobaXterm folder hierarchy (`SubRep`) intact in SecureCRT.
*   **SSH Only**: Automatically filters and converts only SSH sessions (ignores RDP/VNC/etc).
*   **Custom Username Mapping**: Define specific usernames based on keywords found in the session data directly inside the script.
*   **CSV Output**: Generates a clean CSV file ready for SecureCRT's Import tool.

### Prerequisites
*   Python 3.x installed on your system.

### Configuration
To map specific keywords to custom usernames (e.g., forcing a specific user for certification environments), simply edit the `USER_RULES` dictionary at the top of the `moba_converter.py` script:

```python
# --- USERNAME MAPPING RULES ---
USER_RULES = {
    "[Moba_User1]": "username1",
    "[Moba_User2]": "username2",
}
```
*   **Key**: The text string to search for in the MobaXterm session line.
*   **Value**: The username to assign if the text is found.

If no match is found, the script will use the **Default Username** you provide at runtime.

### How to Use

1.  **Export** your sessions from MobaXterm (Right-click on `User sessions` -> `Export session to file`).
2.  Save the exported file as **`MobaXterm Sessions.mxtsessions`** in the same directory as the script.
3.  Run the script:
    ```bash
    python3 moba_converter.py
    ```
4.  Enter a **Default Username** when prompted.

### Importing into SecureCRT

Once the `sessions_converted.csv` file is generated:

1.  Open **SecureCRT**.
2.  Go to **File** > **Import...**.
3.  Select **"Text file (.csv, .txt, ...)"** as the source.
4.  Select the generated `sessions_converted.csv` file.
5.  **IMPORTANT:** When asked to map the fields, ensure the order is exactly as follows:
    1.  **Hostname**
    2.  **Protocol**
    3.  **Username**
    4.  **Folder**
    5.  **Session Name**

---

## 🇮🇹 Documentazione in Italiano

### Funzionalità
*   **Mantenimento Struttura Cartelle**: Mantiene la gerarchia delle cartelle (`SubRep`) di MobaXterm all'interno di SecureCRT.
*   **Solo SSH**: Filtra e converte automaticamente solo le sessioni SSH (ignora RDP, VNC, ecc.).
*   **Mappatura Personalizzata Utenti**: Definisci username specifici in base a parole chiave trovate nei dati della sessione modificando direttamente lo script.
*   **Output CSV**: Genera un file CSV pulito pronto per lo strumento di importazione di SecureCRT.

### Prerequisiti
*   Python 3.x installato nel sistema.

### Configurazione
Per mappare parole chiave a specifici username (es. forzare un utente specifico per ambienti di certificazione), modifica il dizionario `USER_RULES` all'inizio dello script `moba_converter.py`:

```python
# --- USERNAME MAPPING RULES ---
USER_RULES = {
    "[Moba_User1]": "username1",
    "[Moba_User2]": "username2",
}
```
*   **Chiave**: Il testo da cercare nella riga della sessione MobaXterm.
*   **Valore**: L'username da assegnare se il testo viene trovato.

Se non viene trovata alcuna corrispondenza, lo script userà l'**Username di Default** fornito durante l'esecuzione.

### Guida all'Uso

1.  **Esporta** le tue sessioni da MobaXterm (Tasto destro su `User sessions` -> `Export session to file`).
2.  Salva il file rinominandolo come **`MobaXterm Sessions.mxtsessions`** nella stessa cartella dello script.
3.  Esegui lo script:
    ```bash
    python3 moba_converter.py
    ```
4.  Inserisci un **Username di Default** quando richiesto.

### Importazione in SecureCRT

Una volta generato il file `sessions_converted.csv`:

1.  Apri **SecureCRT**.
2.  Vai su **File** > **Import...** (Importa).
3.  Seleziona **"Text file (.csv, .txt, ...)"** come sorgente.
4.  Seleziona il file `sessions_converted.csv` appena generato.
5.  **IMPORTANTE:** Quando richiesto di mappare i campi, assicurati che l'ordine sia esattamente il seguente:
    1.  **Hostname**
    2.  **Protocol**
    3.  **Username**
    4.  **Folder**
    5.  **Session Name**

---

## License & Credits

**Author:** Massimo "RedFoxy Darrest" Cicciò  
**Website:** [https://redfoxy.eu](https://redfoxy.eu)  
**GitHub:** [https://github.com/RedFoxy](https://github.com/RedFoxy)

This work is licensed under the **Creative Commons Attribution-NonCommercial 4.0 International License (CC BY-NC 4.0)**.

You are free to:
*   **Share** — copy and redistribute the material in any medium or format.
*   **Adapt** — remix, transform, and build upon the material.

Under the following terms:
*   **Attribution** — You must give appropriate credit to the original author, provide a link to the license, and indicate if changes were made.
*   **NonCommercial** — You may not use the material for commercial purposes.

To view a copy of this license, visit http://creativecommons.org/licenses/by-nc/4.0/
