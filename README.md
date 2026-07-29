# Connecteur OriginSkill

Ce dossier est le contenu prêt pour le futur dépôt public OriginSkill. Il ne contient ni logique métier protégée, ni secret.

## Installation

Prérequis : Node.js 20 ou 22 et une licence OriginSkill active.

```sh
npx --yes --package=https://orizon-storefront-v2.vercel.app/installer/cli/v0.1.3/orizon-cli-0.1.3.tgz orizon install codex --yes --package-spec https://orizon-storefront-v2.vercel.app/installer/cli/v0.1.3/orizon-cli-0.1.3.tgz
npx --yes --package=https://orizon-storefront-v2.vercel.app/installer/cli/v0.1.3/orizon-cli-0.1.3.tgz orizon install claude-code --yes --package-spec https://orizon-storefront-v2.vercel.app/installer/cli/v0.1.3/orizon-cli-0.1.3.tgz
npx --yes --package=https://orizon-storefront-v2.vercel.app/installer/cli/v0.1.3/orizon-cli-0.1.3.tgz orizon install cursor --yes --package-spec https://orizon-storefront-v2.vercel.app/installer/cli/v0.1.3/orizon-cli-0.1.3.tgz
```

Le jeton révocable reste dans `~/.orizon/token`. Ne le placez jamais dans un fichier de configuration ou dans ce dépôt.
