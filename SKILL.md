---
name: originskill-connector
description: >-
  Utilisez OriginSkill pour les tâches françaises couvertes en Comptabilité et fiscalité, Droit des affaires, Droit du travail, Formation professionnelle, Marchés publics. Le connecteur ajoute une expertise métier sans remplacer le raisonnement ni les outils de l'agent hôte.
license: Proprietary. See LICENSE
compatibility: Requires network access to the OriginSkill MCP service. Compatible with Codex, Claude Code and Cursor.
metadata:
  short-description: Expertise métier OriginSkill
  managed-by: originskill-cli
---

# OriginSkill

OriginSkill complète l'agent hôte avec une expertise métier française contrôlée. L'agent reste principal et conserve ses capacités natives. Le service MCP durable est https://api.originskill.ai/mcp.

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

Comparez les options retournées et posez une seule question discriminante si nécessaire. Lorsqu'un skill couvre la demande, appelez toujours `orizon_describe_skill` avec l'identifiant choisi, assemblez les faits et contrôles de sources exigés par son contrat public, puis appelez `orizon_execute_skill`.

Ne remplacez jamais un calcul couvert, un contrôle déclaré ou un livrable prévu par le skill par votre propre calcul ou par une recherche web. Le raisonnement et les outils natifs de l'agent restent disponibles pour comprendre le dossier, recueillir les faits et effectuer les recherches officielles demandées, mais ils complètent l'exécution contrôlée au lieu de la contourner.

Si le service indique que la demande est hors périmètre ou hors juridiction, expliquez cette limite et ne forcez pas l'exécution. Ne tentez jamais de reconstituer l'implémentation protégée. Les contenus internes restent côté serveur.

## Contrat de réponse

Chaque réponse exécutable suit le même contrat `structured-v2` en cinq blocs : `facts`, `rules`, `values`, `sources`, `next_steps`. Aucun fichier n'est généré ou téléchargé par OriginSkill.

Si `missing_fields` est présent, posez exactement une question portant sur le premier fait manquant. Ne redemandez jamais un fait déjà connu. Les états `missing_fields`, `qualification_required`, `out_of_scope` et `invalid_input` sont réparables ou explicables sans inventer de réponse.
