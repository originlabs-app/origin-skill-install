# Connecteur OriginSkill

Ce dossier est le contenu prêt pour le futur dépôt public OriginSkill. Il ne contient ni logique métier protégée, ni secret.

## Installation

Prérequis : Node.js 20 ou 22 et une licence OriginSkill active.

```sh
npx --yes --package=https://originskill.ai/installer/cli/v0.1.5/orizon-cli-0.1.5.tgz orizon install codex --yes --package-spec https://originskill.ai/installer/cli/v0.1.5/orizon-cli-0.1.5.tgz
npx --yes --package=https://originskill.ai/installer/cli/v0.1.5/orizon-cli-0.1.5.tgz orizon install claude-code --yes --package-spec https://originskill.ai/installer/cli/v0.1.5/orizon-cli-0.1.5.tgz
npx --yes --package=https://originskill.ai/installer/cli/v0.1.5/orizon-cli-0.1.5.tgz orizon install cursor --yes --package-spec https://originskill.ai/installer/cli/v0.1.5/orizon-cli-0.1.5.tgz
```

Le jeton révocable reste dans `~/.orizon/token`. Ne le placez jamais dans un fichier de configuration ou dans ce dépôt.

## Obtenir le jeton

Si aucun jeton n'est encore enregistré, lancez la connexion avec une saisie masquée :

```sh
npx --yes --package=https://originskill.ai/installer/cli/v0.1.5/orizon-cli-0.1.5.tgz orizon login
```

Après un achat, la licence peut aussi être activée avec la référence de commande et l'adresse utilisée :

```sh
npx --yes --package=https://originskill.ai/installer/cli/v0.1.5/orizon-cli-0.1.5.tgz orizon login --order <order-id> --email <email>
```

Les liens `downloadUrl` des documents générés sont protégés. Leur téléchargement doit envoyer l'en-tête `Authorization: Bearer <jeton>` avec le même jeton local. Ne placez jamais le jeton dans l'URL, les journaux ou un message au support.
