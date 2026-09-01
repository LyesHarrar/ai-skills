# 🧠 AI Skills Collection (PM & Product Building)

Une collection de directives méthodologiques (`skill.md`) conçues pour guider les agents et LLMs (Cursor, Claude, Windsurf) dans les tâches de Product Management, d'extraction de connaissances et de conception de systèmes.

---

## 📂 Organisation du Dépôt

- **`/knowledge`** : Directives pour distiller, synthétiser et structurer des contenus bruts (transcripts de vidéos, talks, podcasts, notes).
  - [`tech-transcript-distiller.md`](./knowledge/tech-transcript-distiller.md) : Extraction structurée et actionnable de transcripts tech/produit.

- **`/noe-skills/official-skills`** : Grilles d'évaluation et templates méthodologiques standards du bootcamp Noé (Discovery, Product Strategy, Delivery).
  - [`interview-script-builder.md`](./noe-skills/official-skills/interview-script-builder.md) : Construit un guide d'entretien de discovery (warm-up, comportements passés, exploration du problème, branches, wrap-up) à partir d'une décision et d'objectifs d'apprentissage.
  - [`interview-script-review.md`](./noe-skills/official-skills/interview-script-review.md) : Audite et réécrit un guide d'entretien existant (questions biaisées, hypothétiques, doubles) en version optimisée.
  - [`user-research.md`](./noe-skills/official-skills/user-research.md) : Planifie et synthétise la recherche utilisateur (interviews, sondages, tests d'usabilité, mining de feedback).
  - [`macro-solution-brainstorm.md`](./noe-skills/official-skills/macro-solution-brainstorm.md) : Transforme une liste de problèmes en solutions macro via une session divergence/convergence structurée.
  - [`prd-writer.md`](./noe-skills/official-skills/prd-writer.md) : Rédige un PRD/spec produit orienté décision (problème, métriques, exigences vérifiables, edge cases).
  - [`jira-story-writer.md`](./noe-skills/official-skills/jira-story-writer.md) : Découpe un PRD en epic et user stories INVEST prêtes pour import Jira.
- **`/noe-skills/custom-skills`** : Skills et frameworks sur mesure créés et affinés au fil des cas pratiques et projets Noé.

---

## 🚀 Utilisation

1. Copie le contenu du skill souhaité dans ton dossier `.cursor/rules/`, dans les instructions système de ton agent ou colle-le en référence dans ton prompt.
2. Fournis uniquement la donnée brute en entrée (ex. : transcript, retours utilisateurs, brief).