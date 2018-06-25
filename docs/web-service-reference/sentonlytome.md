---
title: SentOnlyToMe
manager: sethgros
ms.date: 09/17/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- SentOnlyToMe
api_type:
- schema
ms.assetid: b6d4dea5-812d-4b29-917d-071ebd7ddd92
description: L’élément SentOnlyToMe indique si le propriétaire de la boîte aux lettres doit être le seul à la propriété ToRecipients des messages entrants afin que l’exception ou la condition à appliquer.
ms.openlocfilehash: 91c31069652a35dc7a38ad6b6e1512cc07d67a98
ms.sourcegitcommit: 34041125dc8c5f993b21cebfc4f8b72f0fd2cb6f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "19829353"
---
# <a name="sentonlytome"></a>SentOnlyToMe

L’élément **SentOnlyToMe** indique si le propriétaire de la boîte aux lettres doit être le seul à la propriété **ToRecipients** des messages entrants afin que l’exception ou la condition à appliquer. 
  
```XML
<SentOnlyToMe/>true | false</SentOnlyToMe>
```

 **Boolean**
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, éléments enfants et éléments parents.
  
### <a name="attributes"></a>Attributs

Aucun.
  
### <a name="child-elements"></a>Éléments enfants

Aucun.
  
### <a name="parent-elements"></a>Éléments parents

|**Élément**|**Description**|
|:-----|:-----|
|[Conditions](conditions.md) <br/> |Représente les conditions qui, lorsqu'elles sont remplies, vont déclencher les actions de règle pour une règle.  <br/> |
|[Exceptions](exceptions.md) <br/> |Représente toutes les conditions d’exception de règle disponibles pour une règle de boîte de réception.  <br/> |
   
## <a name="text-value"></a>Valeur de texte

Une valeur de texte de **la valeur true** indique que le propriétaire de la boîte aux lettres doit être le seul à la propriété **ToRecipients** des messages entrants afin que l’exception ou la condition à appliquer. La valeur **false** indique que le propriétaire de la boîte aux lettres ne doit pas être le seul à la propriété **ToRecipients** des messages entrants afin que l’exception ou la condition à appliquer. 
  
## <a name="remarks"></a>Remarques

Le schéma qui décrit cet élément se trouve dans le répertoire virtuel IIS qui héberge les services web Exchange.
  
## <a name="element-information"></a>Informations sur l'élément

|||
|:-----|:-----|
|Espace de noms  <br/> |http://schemas.microsoft.com/exchange/services/2006/messages  <br/> |
|Nom du schéma  <br/> |Schéma Messages  <br/> |
|Fichier de validation  <br/> |Messages.xsd  <br/> |
|Peut être vide  <br/> |True  <br/> |
   
## <a name="see-also"></a>Voir aussi



- [Éléments XML de EWS dans Exchange](ews-xml-elements-in-exchange.md)
