---
title: Nom (EmailAddress)
manager: sethgros
ms.date: 09/17/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- Name
api_type:
- schema
ms.assetid: c719c55f-d625-4e64-846f-50ac91881443
description: L’élément Name représente le nom complet de l’utilisateur de boîte aux lettres.
ms.openlocfilehash: 2c6b29f1b069f9cc72ac84e7aebfff99437e630a
ms.sourcegitcommit: 88ec988f2bb67c1866d06b361615f3674a24e795
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "44466954"
---
# <a name="name-emailaddress"></a>Nom (EmailAddress)

L’élément **Name** représente le nom complet de l’utilisateur de boîte aux lettres. 
  
```xml
<Name/>
```

**String**

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents.
  
### <a name="attributes"></a>Attributs

Aucune.
  
### <a name="child-elements"></a>Éléments enfants

Aucun.
  
### <a name="parent-elements"></a>Éléments parents

|**Élément**|**Description**|
|:-----|:-----|
|[E-mail (EmailAddressType)](email-emailaddresstype.md) <br/> |Représente l’utilisateur de boîte aux lettres pour une requête GetUserAvailability.  <br/> <br/>Voici le XPath de cet élément :  <br/><br/>  `/GetUserAvailabilityRequest/MailboxDataArray/MailboxData[i]/Email` <br/> |
|[Boîte aux lettres (disponibilité)](mailbox-availability.md) <br/> | Représente l’utilisateur de boîte aux lettres pour une demande SetUserOofSettings ou GetUserOofSettings.  <br/><br/>  Voici les expressions XPath de cet élément :  <br/><br/>  `/GetUserOofSettingsRequest/Mailbox` <br/><br/>  `/SetUserOofSettingsRequest/Mailbox` <br/> |
   
## <a name="text-value"></a>Valeur texte

Une valeur de texte est requise si cet élément est utilisé.
  
## <a name="remarks"></a>Remarques

Cet élément peut apparaître au plus une fois dans l’élément [email (EmailAddressType)](email-emailaddresstype.md) . Cet élément n’est pas obligatoire. 
  
> [!NOTE]
> Le schéma qui décrit cet élément se trouve dans le répertoire virtuel EWS de l'ordinateur qui exécute MicrosoftExchange Server 2007 pour lequel le rôle serveur d'accès au client est installé. 
  
## <a name="element-information"></a>Informations sur l'élément

|||
|:-----|:-----|
|Espace de noms  <br/> |https://schemas.microsoft.com/exchange/services/2006/types  <br/> |
|Nom du schéma  <br/> |Schéma Types  <br/> |
|Fichier de validation  <br/> |Types.xsd  <br/> |
|Peut être vide  <br/> |False  <br/> |
   
## <a name="see-also"></a>Voir aussi

- [Opération GetUserAvailability](getuseravailability-operation.md)
- [GetUserAvailabilityRequest](getuseravailabilityrequest.md)
- [Obtention de la disponibilité des utilisateurs](https://msdn.microsoft.com/library/d4133fcb-9b0f-4e6b-aadf-a389da83516a%28Office.15%29.aspx)

