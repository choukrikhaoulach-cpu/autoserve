# Top Auto - Assistant conversationnel WhatsApp

Assistant conversationnel intelligent pour le service client d un concessionnaire de vehicules Renault / Dacia.

**Projet de fin d etudes - Licence Informatique, Reseaux et Multimedia (IRM), FST Mohammedia.**

## Fonctionnalites

- Reception et traitement des messages WhatsApp (texte, audio, image)
- Transcription des messages audio via Whisper (Groq)
- Classification d intention et generation de reponses avec Llama 3.3 70B (via Groq)
- Analyse d images (photos de vehicules) via Llama 4 Scout
- Collecte structuree des informations prospects
- Stockage dans Google Sheets utilise comme CRM leger
- Notification automatique d un conseiller humain
- 10 flux conversationnels : essai, RDI, facture, mainlevee, reclamation, SAV, VN, VO, prix, infos vehicules
- Support bilingue francais / arabe
- Suivi de dossier RDI par numero de chassis

## Architecture
Client WhatsApp
|
v
WhatsApp Business Cloud API
|
v
Flask (app1.py)
|
+---> Whisper (audio -> texte)
+---> Llama 3.3 70B via Groq (classification + generation)
+---> Llama 4 Scout via Groq (analyse d images)
+---> Google Sheets API (CRM)
+---> Notification conseiller (WhatsApp)

text

## Stack technique

- **Langage** : Python 3.11+
- **Framework web** : Flask
- **IA** : Groq (Llama 3.3 70B, Llama 4 Scout, Whisper large-v3)
- **Integrations** : WhatsApp Business Cloud API, Google Sheets API
- **Config** : python-dotenv

## Installation

### Prerequis

- Python 3.11+
- Un compte WhatsApp Business (Meta for Developers)
- Une cle API Groq (https://console.groq.com)
- Un Google Sheet + un compte de service Google Cloud

### Etapes

1. Cloner le depot
git clone https://github.com/khaoulachoukri-cpu/top-auto.git
cd top-auto

text

2. Creer un environnement virtuel
python -m venv .venv
.venv\Scripts\activate # Windows
source .venv/bin/activate # macOS / Linux

text

3. Installer les dependances
pip install -r requirements.txt

text

4. Configurer l environnement
copy .env.example .env # Windows
cp .env.example .env # macOS / Linux

text

Puis editer `.env` avec tes vraies valeurs.

5. Lancer le serveur
python app1.py

text

Le serveur ecoute sur `http://localhost:5000`.

## Configuration WhatsApp

1. Creer une app sur https://developers.facebook.com
2. Ajouter le produit "WhatsApp"
3. Recuperer `WHATSAPP_TOKEN` et `WHATSAPP_PHONE_ID`
4. Configurer le webhook avec une URL publique

## Configuration Google Sheets

1. Creer un projet Google Cloud
2. Activer l API Google Sheets
3. Creer un compte de service, telecharger le JSON
4. Copier le JSON complet dans `GOOGLE_CREDS_JSON` (dans `.env`)
5. Partager chaque Google Sheet avec l email du compte de service

## Structure du projet
topauto-bot-main/
├── app1.py # Application principale (Flask + flows conversationnels)
├── config.py # Configuration (chargement .env)
├── prompts.py # Prompts IA
├── prompt_system.txt # Prompt systeme complet
├── requirements.txt # Dependances Python
├── .env.example # Template variables d environnement (sans secrets)
├── .gitignore
└── README.md

text

## Auteur

**Khaoula Choukri**
- LinkedIn : https://www.linkedin.com/in/khaoula-choukri
- GitHub : https://github.com/khaoulachoukri-cpu

## Contexte academique

Projet de fin d etudes realise dans le cadre de la Licence Informatique, Reseaux et Multimedia (IRM) a la Faculte des Sciences et Techniques de Mohammedia (FST), 2025.