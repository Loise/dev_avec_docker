# TP Noté : Orchestration, Résilience et Industrialisation Docker

**Niveau :** Master 2
**Durée estimée :** 3h - 4h
**Contexte :** Architecture Microservices, Docker Compose, Python FastAPI, Nginx, Redis, Postgres.

---

## 1. Contexte et Objectifs

Vous récupérez le "Proof of Concept" (POC) d'une application existante. Cette stack a été développée rapidement : elle est instable, tourne en `root` et ne gère pas la résilience.

L'équipe précédente a déjà mis en place un début de persistance avec un script `migration-v001.sql` qui initialise une table métier spécifique.

**Votre mission :** Transformer ce POC en une stack de production **résiliente**, **sécurisée** et capable de supporter la nouvelle fonctionnalité "Dashboard Étudiant".

### L'Architecture Cible

L'application finale devra respecter l'architecture 3-tiers suivante :

1. **Frontend** : Un serveur Nginx servant une SPA statique (fichier fourni).
2. **Backend** : Une API Python FastAPI existante (à adapter).
3. **Data Layer** :
   * **Postgres** : Doit contenir les données existantes + la nouvelle table `students`.
   * **Redis** : Pour le comptage de vues en temps réel.

---

## 2. Ressources Fournies

Voici l'arborescence de départ que vous devez constituer :

```text
/project-root
├── docker-compose.yml    (Base fournie)
├── python.Dockerfile     (Base fournie)
├── requirements.txt      (Dépendances Python)
├── sqlfiles/
│   └── migration-v001.sql (Fichier existant fourni par l'équipe précédente)
├── app/
│   └── main.py           (Anciennement postgres-test.py)
└── frontend/
    └── index.html        (Contrat d'interface fourni ci-dessous)