# ⚔️ NSI JEDI ACADEMY — Training System

> **Plateforme d'entraînement aux Évaluations Communes de spécialité NSI (Première)**  
> Interface holographique Star Wars · Exécution Python live · Barème EC officiel

---

## 🎯 Présentation

**NSI Jedi Academy** est une application web autonome (fichier HTML unique, zéro dépendance serveur) conçue pour s'entraîner aux QCM des évaluations communes de NSI en classe de Première générale.

L'élève charge un **fichier de sujet au format JSON**, et la plateforme génère une session d'entraînement interactive avec correction immédiate, explications détaillées, exécution Python en direct et scoring barémé sur 20.

---

## ✨ Fonctionnalités

| Fonctionnalité | Description |
|---|---|
| 📡 **Exécution Python live** | Éditeur Python intégré via PyScript — le code s'exécute directement dans le navigateur |
| ⚡ **Barème EC officiel** | +3 / −1 / 0 avec calcul automatique de la note sur 20 |
| 🛡️ **Mode Examen** | Les corrections sont masquées jusqu'à la fin de la session |
| 💾 **Sauvegarde auto** | La progression est persistée dans le `localStorage` — reprise possible après fermeture |
| ⌨️ **Raccourcis clavier** | Touches `A B C D` pour sélectionner + `Entrée` pour valider + `→` pour passer |
| 🔴 **Mode Révision** | Repassez uniquement les questions ratées |
| ⏱️ **Chronomètre** | Chrono activable pour simuler les conditions d'examen |
| 📊 **Résultats détaillés** | Score global, analyse par thème, détail question par question |

---

## 🗂️ Format du fichier de sujet (JSON)

La plateforme charge des sujets au format JSON structuré. Exemple de structure minimale :

```json
{
  "meta": {
    "id": "G1SNSIN03327",
    "titre": "Évaluation Commune — Spécialité NSI",
    "classe": "Première",
    "voie": "Générale",
    "duree_minutes": 120,
    "nb_questions": 42,
    "nb_themes": 7,
    "bareme": {
      "bonne_reponse": 3,
      "mauvaise_reponse": -1,
      "sans_reponse": 0,
      "diviseur_final": 6.3,
      "arrondi": "superieur"
    }
  },
  "themes": [
    {
      "id": "A",
      "titre": "Types de base",
      "description": "Représentation des entiers, flottants, encodage des caractères.",
      "questions": [
        {
          "id": "A1",
          "difficulte": 1,
          "enonce": "Quelle est l'écriture décimale de `0001 0101` en binaire non signé ?",
          "code": null,
          "type_code": null,
          "propositions": { "A": "21", "B": "15", "C": "111", "D": "420" },
          "reponse": "A",
          "explication": "2⁰ + 2² + 2⁴ = 1 + 4 + 16 = **21**.",
          "notion_cle": "Conversion binaire → décimal",
          "astuce": "Numérotez les bits de droite à gauche en partant de 0."
        }
      ]
    }
  ]
}
```

### Champs d'une question

| Champ | Type | Description |
|---|---|---|
| `id` | `string` | Identifiant unique (ex. `A1`, `B3`) |
| `difficulte` | `1 \| 2 \| 3` | Niveau de difficulté |
| `enonce` | `string` | Texte de la question (Markdown supporté) |
| `code` | `string \| null` | Snippet Python affiché / exécutable |
| `type_code` | `"display" \| "editor" \| null` | Mode d'affichage du code |
| `propositions` | `{A, B, C, D}` | Quatre propositions de réponse |
| `reponse` | `"A" \| "B" \| "C" \| "D"` | Bonne réponse |
| `explication` | `string` | Correction holistique (Markdown) |
| `notion_cle` | `string` | Concept central associé |
| `astuce` | `string` | Conseil méthodologique |

---

## 🚀 Utilisation

1. **Télécharger** le fichier `nsi_jedi_academy.html`
2. **L'ouvrir dans un navigateur** (Chrome ou Firefox recommandés)
3. **Charger un fichier de sujet** `.json` via le bouton ou en glisser-déposer
4. La session démarre automatiquement — bonne mission, Padawan 🌌

> ⚠️ L'exécution Python live nécessite une connexion Internet (chargement de PyScript via CDN).

---

## 🗃️ Thèmes couverts (exemple — sujet `G1SNSIN03327`)

- **A** — Types de base (binaire, hexadécimal, flottants, encodage)
- **B** — Représentation des données (tableaux, dictionnaires, p-uplets)
- **C** — Traitement des données en table (CSV, tris, recherche)
- **D** — Interactions Web (HTML, HTTP, formulaires)
- **E** — Algorithmique (tri, dichotomie, complexité)
- **F** — Langages et programmation (Python, fonctions, récursivité)
- **G** — Systèmes d'exploitation et réseaux (commandes, protocoles)

---

## 🏗️ Architecture technique

```
nsi_jedi_academy.html   ← Application complète (HTML + CSS + JS, fichier unique)
sujet_*.json            ← Fichiers de sujets (un par évaluation)
```

**Stack :**
- HTML5 / CSS3 / JavaScript ES6+ (vanilla, aucun framework)
- [PyScript](https://pyscript.net/) `2024.11.1` — exécution Python côté navigateur
- Google Fonts : Orbitron · Exo 2 · Share Tech Mono
- Stockage : `localStorage` (persistance côté client uniquement)

---

## 🎨 Design

Interface inspirée de l'esthétique **holographique Star Wars** :
- Palette : `#020408` (void) · `#00d4ff` (cyan holo) · `#39ff6e` (saber green) · `#ffb700` (amber)
- Fond étoilé animé, effets de scan CRT, lueurs néon
- Responsive desktop/tablette

---

## 📄 Licence

Projet pédagogique libre — usage en classe et auto-formation.  
Lycée Antoine Watteau · Valenciennes · Spécialité NSI

---

*May the Force be with your algorithms. ⚔️*
