---
title: Guid
manager: sethgros
ms.date: 09/17/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 49dcf69f-bf8d-4be6-a24c-03bbd13f4fe5
description: L’élément GUID spécifie l’identificateur global unique de la boîte aux lettres.
ms.openlocfilehash: 4db66b5ae2c67f64f75c69a3d77cfa2b587775be
ms.sourcegitcommit: 88ec988f2bb67c1866d06b361615f3674a24e795
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "44530774"
---
# <a name="guid"></a>Guid

L’élément **GUID** spécifie l’identificateur global unique de la boîte aux lettres. 
  
```XML
<Guid></Guid>
```

 **GuidType**
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents.
  
### <a name="attributes"></a>Attributs

Aucune.
  
### <a name="child-elements"></a>Éléments enfants

Aucun.
  
### <a name="parent-elements"></a>Éléments parents

|**Élément**|**Description**|
|:-----|:-----|
|[SearchableMailbox](searchablemailbox.md) <br/> |Spécifie une boîte aux lettres renvoyée à partir d’une demande **GetSearchableMailboxes** .  <br/> |
   
## <a name="text-value"></a>Valeur texte

La valeur de texte de l’élément **GUID** est une valeur GUID qui identifie de manière unique une boîte aux lettres. 
  
## <a name="remarks"></a>Remarques

Cet élément est une nouveauté d'Exchange Server 2013.
  
Le schéma qui décrit cet élément se trouve dans le répertoire virtuel IIS qui héberge les services web Exchange.
  
## <a name="element-information"></a>Informations sur l'élément

|||
|:-----|:-----|
|Espace de noms  <br/> |https://schemas.microsoft.com/exchange/services/2006/types  <br/> |
|Nom du schéma  <br/> |Schéma type  <br/> |
|Validation File  <br/> |types. xsd  <br/> |
|Peut être vide  <br/> ||
   
## <a name="see-also"></a>Voir aussi



- [Éléments XML de EWS dans Exchange](ews-xml-elements-in-exchange.md)

