---
title: NotSentToMe
manager: sethgros
ms.date: 09/17/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- NotSentToMe
api_type:
- schema
ms.assetid: 7cb63269-622c-4198-9a21-f5a021bf6901
description: L’élément NotSentToMe indique si le propriétaire de la boîte aux lettres ne doit pas se trouver dans la propriété ToRecipients des messages entrants afin que la condition ou l’exception s’applique.
ms.openlocfilehash: 58efe4381fe0c9f5bd0645a9eba471a13b5e4064
ms.sourcegitcommit: 88ec988f2bb67c1866d06b361615f3674a24e795
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "44462611"
---
# <a name="notsenttome"></a>NotSentToMe

L’élément **NotSentToMe** indique si le propriétaire de la boîte aux lettres ne doit pas se trouver dans la propriété **ToRecipients** des messages entrants afin que la condition ou l’exception s’applique. 
  
```xml
<NotSentToMe>true | false</NotSentToMe>
```

 **Boolean**
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents.
  
### <a name="attributes"></a>Attributs

Aucune.
  
### <a name="child-elements"></a>Éléments enfants

Aucun.
  
### <a name="parent-elements"></a>Éléments parents

|**Élément**|**Description**|
|:-----|:-----|
|[Conditions](conditions.md) <br/> |Représente les conditions qui, lorsqu'elles sont remplies, vont déclencher les actions de règle pour une règle.  <br/> |
|[Exceptions](exceptions.md) <br/> |Représente les exceptions qui représentent toutes les conditions d'exception de règle disponibles pour une règle de boîte de réception.  <br/> |
   
## <a name="text-value"></a>Valeur texte

Une valeur de texte **true** indique que le propriétaire de la boîte aux lettres ne doit pas être dans la propriété **ToRecipients** des messages entrants pour que la condition ou l’exception s’applique. La valeur **false** indique que le propriétaire de la boîte aux lettres doit se trouver dans la propriété **ToRecipients** du message entrant afin que la condition ou l’exception s’applique. 
  
## <a name="remarks"></a>Remarques

Le schéma qui décrit cet élément se trouve dans le répertoire virtuel IIS qui héberge les services web Exchange.
  
## <a name="element-information"></a>Informations sur l'élément

|||
|:-----|:-----|
|Espace de noms  <br/> |https://schemas.microsoft.com/exchange/services/2006/messages  <br/> |
|Nom du schéma  <br/> |Schéma Messages  <br/> |
|Fichier de validation  <br/> |Messages. xsd  <br/> |
|Peut être vide  <br/> |True  <br/> |
   
## <a name="see-also"></a>Voir aussi



- [Éléments XML de EWS dans Exchange](ews-xml-elements-in-exchange.md)

