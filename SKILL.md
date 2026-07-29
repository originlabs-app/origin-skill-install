---
name: origin-office-connector
description: >-
  Utilisez OriginSkill pour les tâches françaises couvertes en Comptabilité et fiscalité, Droit des affaires, Droit du travail, Formation professionnelle, Marchés publics. Le connecteur ajoute une expertise métier sans remplacer le raisonnement ni les outils de l'agent hôte.
license: Proprietary. See LICENSE
compatibility: Requires network access to the OriginSkill MCP service. Compatible with Codex, Claude Code and Cursor.
metadata:
  short-description: Expertise métier OriginSkill
  managed-by: origin-office-cli
---

# OriginSkill

OriginSkill complète l'agent hôte avec une expertise métier française contrôlée. L'agent reste principal et conserve ses capacités natives.

Appelez l'outil technique `orizon_start` lorsqu'une demande explicite ou une nouvelle tâche métier entre dans le périmètre ci-dessous. Pour un suivi étroit dans la même conversation, réutilisez le contexte déjà acquis.

## Périmètre public

- Affectation du résultat et dividendes (France)
- Assemblée générale annuelle (SA non cotée, France)
- Assemblée générale annuelle (SARL ou EURL, France)
- Assemblée générale annuelle (SAS ou SASU, France)
- Assemblée générale annuelle (SCI, France)
- Bilan pédagogique et financier (France)
- Candidature DUME, DC1 et DC2 (France)
- Contrat de travail (côté employeur, France)
- Déclaration de TVA CA3 (France)
- Dépôt des comptes annuels (France)
- Facturation électronique (réforme française 2026)
- Facture conforme (France)
- Financement OPCO (France)
- Liasse fiscale 2033 (France)
- Mémoire technique de marché public (France)
- Préparation à l’audit Qualiopi (France)
- Réponse complète à un appel d’offres public (France)
- Rupture conventionnelle (côté employeur, France)
- Rupture de période d’essai (côté employeur, France)

Comparez les options retournées, posez une seule question discriminante si nécessaire, puis utilisez l'identifiant technique retourné par le service. Ne tentez jamais de reconstituer l'implémentation protégée. Les contenus internes restent côté serveur.
