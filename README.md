# Workshop Datenmodelle (SQLite · MongoDB · Neo4j · TinyFlux)

Dieses Repository ist für **GitHub Codespaces** vorbereitet. Studierende forken den Kurs, öffnen den Fork in Codespaces und arbeiten direkt in den Jupyter-Notebooks.

---

## 🚀 Quickstart (Codespaces)

1. **Repo forken** (oben rechts „Fork“).
2. Im Fork: **Code → Open with Codespaces**.
3. Warten, bis die Umgebung steht (installiert automatisch `requirements.txt`).
4. **Optional (für Cloud-Dienste):** `.env.sample` nach `.env` kopieren und Variablen setzen:
   - **MongoDB (Atlas)**  
     `MONGO_URI` und `MONGO_DB` (im Kurs: `MONGO_DB=workshop_mongo`)
   - **Neo4j (Aura)**  
     `NEO4J_USER` und `NEO4J_PASSWORD`  
     *(falls in eurem Notebook eine URI genutzt wird, zusätzlich `NEO4J_URI` setzen)*
5. Notebooks öffnen und der Reihenfolge folgen:
   - `01_sqlite.ipynb`
   - `02_mongodb.ipynb`
   - `03_neo4j.ipynb`
   - `04_tinyflux.ipynb` *(oder `_simple_example`)*

> **Hinweis zu `.env`:** Python liest `.env` **nicht automatisch**.  
> Falls euer Notebook noch **nicht** `python-dotenv` lädt, fügt am Anfang hinzu:
> ```python
> from dotenv import load_dotenv
> load_dotenv()
> ```
> Danach stehen die Variablen via `os.environ.get("...")` bereit.

---

## 📁 Datenlayout

Die Notebooks erwarten folgende Ordnerstruktur (relativ zum Repo-Root):

```
data/
  relational/
    users.csv
    posts.csv
    likes.csv
    comments.csv
    follows.csv
  timeseries/
```

- **SQLite** & **TinyFlux** sind dateibasiert (keine Server-Konfiguration nötig).
- **MongoDB** & **Neo4j**: Am einfachsten mit **Atlas** bzw. **Aura Free** (kostenfrei, keine lokalen Ports).

---

## 🔌 Umgebungsvariablen (Kompatibel mit deinen Notebooks)

**02_mongodb.ipynb**
```python
# MongoDB-Verbindung (Umgebungsvariable MONGO_URI respektieren)
MONGO_URI = os.environ.get('MONGO_URI', 'mongodb://localhost:27017')
DB_NAME = os.environ.get('MONGO_DB', 'workshop_mongo')
```
→ Setze in `.env` z. B.:
```
MONGO_URI=mongodb+srv://<user>:<pass>@<cluster>.mongodb.net/?retryWrites=true&w=majority
MONGO_DB=workshop_mongo
```

**03_neo4j.ipynb**
```python
NEO4J_USER = os.environ.get('NEO4J_USER', 'neo4j')
NEO4J_PASSWORD = os.environ.get('NEO4J_PASSWORD', 'test1234')  # lokal anpassen
# Optional, falls im Notebook genutzt:
# NEO4J_URI = os.environ.get('NEO4J_URI', 'bolt://localhost:7687')
```
→ Setze in `.env` z. B.:
```
NEO4J_USER=neo4j
NEO4J_PASSWORD=<password>
# NEO4J_URI=neo4j+s://<id>.databases.neo4j.io
```

---

## ❓ Häufige Fragen

- **Brauche ich Docker?**  
  **Nein.** Codespaces + dieses Repo reichen. Docker ist nur nötig, wenn ihr **ohne Cloud** arbeiten wollt.

- **Wie komme ich an Atlas/Aura?**  
  - MongoDB Atlas: Free Tier anlegen → Connection string (`MONGO_URI`) kopieren.  
  - Neo4j Aura Free: DB anlegen → User/Pass + `NEO4J_URI` notieren.

- **.env wird nicht gelesen?**  
  Sicherstellen, dass am Notebook-Anfang `load_dotenv()` aufgerufen wird (siehe Quickstart).

Viel Erfolg und viel Spaß!
