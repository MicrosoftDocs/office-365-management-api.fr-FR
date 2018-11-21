---
ms.TocTitle: Office 365 Management Activity API frequently asked questions
title: API Activité de gestion Office 365- Questions fréquemment posées
description: Questions fréquemment posées sur l’utilisation de l’API Activité de gestion Office 365
ms.ContentId: ''
ms.topic: reference (API)
ms.date: 09/21/2018
ms.openlocfilehash: 612aac60ab421d79a1c866a4a79157ee255d167d
ms.sourcegitcommit: 525c0d0e78cc44ea8cb6a4bdce1858cb4ef91d57
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2018
ms.locfileid: "25834824"
---
# <a name="office-365-management-activity-api-frequently-asked-questions"></a>API Activité de gestion Office 365- Questions fréquemment posées

#### <a name="what-events-are-audited-for-a-specific-office-365-service"></a>Quels événements sont audités pour un service Office 365 spécifique ?

La documentation du schéma de l’API Activité de gestion Office 365 comprend la liste complète des événements. Pour plus d’informations, reportez-vous à [Schéma de l’API Activité de gestion Office 365](office-365-management-activity-api-schema.md).

#### <a name="how-do-i-onboard-to-the-management-activity-api"></a>Comment intégrer à l’API Activité de gestion ?

Pour commencer à utiliser l’API Activité de gestion Office 365, reportez-vous à [Prise en main des API de gestion Office 365](get-started-with-office-365-management-apis.md).
 
#### <a name="what-is-the-throttling-limit-for-the--management-activity-api"></a>Quel est le seuil de limitation pour l’API Activité de gestion ?

Le seuil de limitation actuel est 60 K demandes/minute par ID de serveur de publication. 

#### <a name="we-want-to-programmatically-capture-all-events-in-all-workloads-what-is-the-most-reliable-way-to-do-this"></a>Nous souhaitons capturer par programme tous les événements dans toutes les charges de travail. Quelle est la façon la plus fiable pour le faire ?

Vous pouvez utiliser l’API Activité de gestion d’Office 365. Par ailleurs, nous vous conseillons d’utiliser le **modèle pull** en raison des problèmes avec l’utilisation des webhooks. Pour plus d’informations, reportez-vous à la section « Utilisation des webhooks » dans la rubrique relative à la [résolution des problèmes de l’API Activité de gestion d’Office 365](troubleshooting-the-office-365-management-activity-api.md#using-webhooks).

#### <a name="is-it-true-that-mailbox-auditing-in-exchange-online-can-only-be-enabled-by-using-powershell"></a>Est-il vrai que l’audit de boîte aux lettres dans Exchange Online peut uniquement être activé à l’aide de PowerShell ?

Oui. Toutefois, nous étudions une solution pour activer l’audit de boîte aux lettres par défaut pour toutes les boîtes aux lettres dans une organisation Office 365. Pour plus d’informations, reportez-vous à la rubrique relative au message « L’audit de boîte aux lettres Exchange sera activé par défaut » dans le [blog sur la sécurité, confidentialité et conformité de Microsoft](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Exchange-Mailbox-Auditing-will-be-enabled-by-default/ba-p/215171).

#### <a name="are-there-any-differences-in-the-records-that-are-fetched-by-the-management-activity-api-versus-the-records-that-are-returned-by-using-the-audit-log-search-tool-in-the-office-365-security--compliance-center"></a>Existe-t-il des différences entre les enregistrements récupérés par l’API Activité de gestion et les enregistrements renvoyés à l’aide de l’outil de recherche de journal d’audit dans le Centre de sécurité et conformité Office 365 ?

Les données renvoyées par les deux méthodes sont identiques. Aucun filtre n’est utilisé. La seule différence est qu’avec l’API, vous pouvez obtenir en une fois les données des 7 derniers jours. Lors de la recherche du journal d’audit dans le Centre de sécurité et conformité (ou à l’aide de la cmdlet [Search-UnifiedAuditLog](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog) correspondante dans Exchange Online), vous pouvez obtenir les données des 90 derniers jours. 
 
#### <a name="arent-webhook-notifications-more-immediate-after-all-arent-they-event-driven"></a>Les notifications webhook ne sont-elles pas plus immédiates ? Après tout, ne sont-elles pas fondées sur les événements ?

Non. Les notifications webhook ne sont pas fondées sur les événements au sens où l’événement déclencherait la notification. Le contenu blob doit toujours être créé et la création du contenu blob déclenche l’envoi de la notification. Récemment, les temps d’attente des notifications ont été plus longs lors de l’utilisation d’un webhook par rapport à l’interrogation de l’API directement avec l’opération */content*. Par conséquent, l’API Activité de gestion ne doit pas être considérée comme un système d’alerte de sécurité en temps réel. Microsoft propose d’autres produits pour cela. En ce qui concerne la sécurité, les notifications d’événements de l’API Activité de gestion peuvent être utilisées de façon plus appropriée pour déterminer les modèles d’utilisation sur de longues périodes de temps.

#### <a name="when-pulling-the-data-from-the-management-activity-api-there-is-sometimes-a-delay-of-more-than-3-to-5-days-why-is-this"></a>Lors de l’extraction des données de l’API Activité de gestion, il y a parfois un retard de plus de 3 à 5 jours. Pourquoi ?

Parfois, il existe des instances d’une panne temporaire ou d’autres problèmes dans le service Office 365. Dans ce cas, des enregistrements d’audit sont annulés et le service tente de les renvoyer. Bien que cela se produise pour 5 à 10 % des enregistrements environ, voici les enregistrements qui peuvent être retardés dans certaines situations. Si le retard dépasse 5 jours, consultez le tableau de bord de l’état des services dans le centre d’administration Office 365. Si nécessaire, vous pouvez aussi ouvrir un ticket avec le [support Microsoft](https://support.office.com/article/contact-support-for-business-products-admin-help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b#ID0EAADAAA=online).

#### <a name="i-am-encountering-a-throttling-error-in-the-management-activity-api-what-should-i-do"></a>Je rencontre une erreur de limitation dans l’API Activité de gestion. Que dois-je faire ?

Ouvrez un ticket avec le [support Microsoft](https://support.office.com/article/contact-support-for-business-products-admin-help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b#ID0EAADAAA=online) et demandez un nouveau seuil de limitation et incluez une justification professionnelle pour augmenter le seuil. Nous évaluerons la demande et si nous l’acceptons, nous augmenterons le seuil de limitation.