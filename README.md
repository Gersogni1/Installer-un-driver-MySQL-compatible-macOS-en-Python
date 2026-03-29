
### 1️⃣ Installer un driver MySQL compatible macOS

Sur macOS, tu as 2 options principales :

## Option A : Utiliser PyMySQL (100% Python, pas besoin de compiler)

C’est plus simple que mysqlclient sur Mac, surtout sans Homebrew.

Étapes :
1.  Active ton venv :

``` bash
source venv/bin/activate
```

2.  Installe PyMySQL :

``` bash
pip install pymysql
```
3.  Dans ta config pour SQLAlchemy pour utiliser PyMySQL :

``` bash
class Config:
    SQLALCHEMY_DATABASE_URI = "mysql+pymysql://root:password@localhost/python_db"
    SQLALCHEMY_TRACK_MODIFICATIONS = False
```
✅ mysql+pymysql → indique à SQLAlchemy d’utiliser PyMySQL au lieu de MySQLdb

## Option B : Installer mysqlclient (plus rapide en production mais compilation requise)

1.  Installer Homebrew (si tu veux MySQL officiel compilé) :

``` bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

2.  Installer MySQL et pkg-config :

``` bash
brew install mysql pkg-config
```
3.  Installer mysqlclient dans le venv :

``` bash
pip install mysqlclient
```
4.  Garde ta config actuelle :

``` bash
SQLALCHEMY_DATABASE_URI = "mysql://root:password@localhost/python_db"
```

⚠️ Cette méthode est plus complexe sur macOS sans Homebrew, donc PyMySQL est recommandé pour commencer.

### 2️⃣ Créer la base MySQL

Avant de lancer ton app, connecte-toi à MySQL :

``` bash
mysql -u root -p
```
Puis crée la base :

``` bash
CREATE DATABASE python_db;
```

###  3️⃣ Relancer ton projet

Avec PyMySQL (option la plus simple) :

``` bash
source venv/bin/activate
python3 app.py
```

Tu devrais voir :

``` bash
* Running on http://127.0.0.1:5000/
```
------------------------------------------------------------------------

## 👤 Auteur

Gersogni BASHIYA
gersogniyampanya@gmail.com
