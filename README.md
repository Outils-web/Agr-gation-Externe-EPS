# AgrégEPS — Centre de Préparation
### Agrégation Externe EPS · Session 2026

Application web locale tout-en-un pour préparer les épreuves d'admissibilité de l'Agrégation externe EPS. Fichier HTML unique, aucune installation requise.

---

## Accès

L'application est protégée par un mot de passe. Le mot de passe **n'est pas stocké en clair** dans le code source — seule son empreinte cryptographique (SHA-256) est présente. Il vous a été communiqué séparément.

---

## Fonctionnalités

### 🏠 Tableau de bord
- Statistiques globales (documents, devoirs, corrections, moyenne)
- Points clés E1 et E2 issus du rapport de jury 2025 (bandeau N4→N5)
- Programmes officiels 2026 E1 et E2
- Actions rapides et dernières corrections

### 📚 Bibliothèque
- Import de documents par glisser-déposer ou clic (PDF, Word, PowerPoint, Excel, TXT)
- Catégorisation : Écrit 1 / Écrit 2 / Jury / Programme / Méthodo / Autre
- Extraction automatique du texte des fichiers `.docx` (via mammoth.js)
- Filtrage par catégorie, suppression, aperçu du texte extrait

### 📝 Écrit 1 — Civilisations (EPS, école et société de 1918 à nos jours)
- Dépôt de devoirs par glisser-déposer ou saisie directe
- Sujet + copie associés
- Accès rapide à la correction IA

### 📄 Écrit 2 — Développement de la Personne
- Même interface que l'Écrit 1
- Prompts IA adaptés à la méthodologie E2 (Blocs A/B, mot pivot)

### 🤖 Correction IA
- Analyse de copies via l'API Anthropic (`claude-sonnet-4-20250514`)
- Retour structuré : note /20, niveau N1→N5, points forts, axes d'amélioration
- Analyse par critère (citation, connaissances, structure, discussion, illustrations, forme)
- Conseil prioritaire + extrait à retravailler + reformulation proposée
- Historique complet des corrections avec vue détaillée

### ✨ Reformulation
- 3 propositions de reformulation stylisées par l'IA
- Style historiographique (E1) ou scientifique/didactique (E2)
- Copie en un clic

### 📖 Guide Méthodologique E1
Basé sur le rapport de jury 2025 :
- Guide étape par étape (4 étapes : analyser → décoder → introduire → développer/conclure)
- Structure d'un argument (4 temps)
- Gestion du temps sur 4h
- Règles d'or du rapport de jury
- Bandeau de correction N1→N5 avec critères détaillés
- 4 acteurs du programme (Baquet, Davisse, Parlebas, Popard) avec œuvres et idées clés
- 8 erreurs à éviter

### 📗 Guide Méthodologique E2
Basé sur la méthodologie A3 ENS Rennes (Groupe Entraide & PArtage, 2026) et le rapport de jury 2025 :
- Guide complet : analyser le sujet → intro (5 étapes) → développement → conclusion
- Décliner le mot pivot (5 qualifications : positive / partielle / absente / inversée / conditionnelle)
- Contenu d'une sous-partie (7 éléments obligatoires)
- Méthode des 9 cases (tableau 3×2)
- 5 pièges à éviter
- Bandeau de correction N1→N5
- Références théoriques par domaine (Engagement / Corps / Apprentissage / Sociologie / Santé-Environnement)

### 💬 Pré-phrases Agrégatives
Base de gabarits à copier en un clic, adaptés à chaque épreuve :

**Écrit 1 (5 catégories) :** Accroche & mise en contexte · Analyse de la citation · Discussion & confrontation · Problématique & transitions · Conclusion

**Écrit 2 (7 catégories) :** Accroche · Définition des blocs · Décliner le mot pivot · Annonce de parties · Introduction d'une théorie · Illustration en EPS · Conclusion & ouverture

Les termes en `[MAJUSCULES]` sont à remplacer par vos propres éléments.

### 📊 Statistiques
- Moyenne générale, E1 et E2
- Graphique d'évolution des notes
- Distribution par niveau (N1→N5)
- Tableau complet de toutes les corrections

### ⚙️ Paramètres
- Prénom personnalisable (affiché dans la sidebar)
- Clé API Anthropic (uniquement pour usage hors Claude.ai)
- Export / Import des données en JSON
- Réinitialisation complète

---

## Base de connaissances intégrée

Les guides méthodologiques et les prompts de correction IA sont nourris par :

| Source | Usage |
|---|---|
| Groupe Entraide & PArtage — A3 ENS Rennes (jan. 2026) | Méthodologie E2, méthode des 9 cases, mot pivot |
| Rapport de jury session 2025 | Bandeau N1→N5 E1 et E2, règles d'or, pièges |
| Programme officiel session 2026 | Items E1 et E2 (dont nouvel item E1 : *Valeurs, transmission, incorporation*) |

---

## Architecture technique

| Élément | Détail |
|---|---|
| Format | Fichier HTML unique (`agregeps.html`) |
| Style | CSS variables, dark theme, Tailwind CDN (usage local) |
| Typographie | Playfair Display + Lora (Google Fonts) |
| Lecture .docx | mammoth.js (cdnjs.cloudflare.com) |
| IA | API Anthropic — `claude-sonnet-4-20250514` |
| Stockage | `window.storage` (Claude.ai) avec fallback `localStorage` |
| Sécurité | SHA-256 via Web Crypto API (mot de passe jamais stocké en clair) |
| Dépendances réseau | Google Fonts · Tailwind CDN · cdnjs · api.anthropic.com |

> **Note sur le message Tailwind :** le message `cdn.tailwindcss.com should not be used in production` est un avertissement inoffensif destiné aux développeurs de sites à fort trafic. Il n'apparaît que dans la console développeur (F12) et n'a aucun impact sur le fonctionnement de l'application.

---

## Utilisation

1. Ouvrir `agregeps.html` dans un navigateur (ou via Claude.ai)
2. Saisir le mot de passe
3. Commencer par enrichir la **Bibliothèque** avec vos documents de référence
4. Déposer vos devoirs dans **Écrit 1** ou **Écrit 2**
5. Lancer une **Correction IA** depuis la fiche devoir ou directement
6. Consulter les **Guides Méthodo** et les **Pré-phrases** avant de rédiger

---

## Données et confidentialité

- Toutes les données (documents, devoirs, corrections) sont stockées **localement** dans votre navigateur
- Aucune donnée n'est envoyée à un serveur tiers, à l'exception des appels à l'API Anthropic pour les corrections et reformulations
- L'export JSON vous permet de sauvegarder et transférer vos données

---

*AgrégEPS — Préparation Agrégation Externe EPS · Session 2026*
