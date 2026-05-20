# ReDsume CI Scheduler

Repo public servant de **déclencheur CI** pour la suite de tests BDD ReDsume.

## Pourquoi ce repo ?

GitHub Actions est **illimité pour les repos publics**.  
Le repo principal (code source) reste **privé** — ce repo se contente de :

1. Déclencher les tests selon le planning cron
2. Checkout le repo privé via un PAT sécurisé
3. Lancer Cypress V1 + Playwright V2 en parallèle
4. Logger chaque run dans `run-history.log`

Le code source de ReDsume n'est **jamais exposé** publiquement.

## Planning (11 runs/semaine)

| Jour      | Heures        |
|-----------|---------------|
| Lundi     | 08h00, 14h00  |
| Mardi     | 09h00, 15h00  |
| Mercredi  | 10h00, 16h00  |
| Jeudi     | 09h00, 13h00, 17h00 |
| Vendredi  | 09h00, 14h00  |

## Secrets à configurer

Dans **Settings → Secrets → Actions** de ce repo :

| Secret | Valeur |
|--------|--------|
| `PRIVATE_REPO` | `youssefkitabrhi/PFE` |
| `PRIVATE_REPO_TOKEN` | PAT GitHub avec scope `repo` |
| `CYPRESS_BASE_URL` | URL de l'app V1 |
| `PLAYWRIGHT_BASE_URL` | URL de l'app V2 |
| `TEST_USER_EMAIL` | Email du compte test |
| `TEST_USER_FULLNAME` | Nom complet du compte test |
| `CYPRESS_USER_LOGIN` | Login Azure AD B2C |
| `CYPRESS_USER_PASSWORD` | Mot de passe Azure AD B2C |

## Créer le PAT

1. GitHub → Settings → Developer settings → Personal access tokens → Fine-grained tokens
2. Repository access : **Only select repositories** → choisir le repo privé
3. Permissions : **Contents = Read**, **Actions = Read**
4. Copier le token → ajouter comme secret `PRIVATE_REPO_TOKEN`
