---
title: SearchableMailboxes
manager: sethgros
ms.date: 09/17/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: eb0a7897-c642-4c93-a238-be03128af54e
description: L’élément SearchableMailboxes contient un tableau de boîtes aux lettres renvoyé à partir d’une demande GetSearchableMailboxes.
ms.openlocfilehash: 5e8fdfbf4e0087b3fc514cd68b92b746cfb70db4
ms.sourcegitcommit: 34041125dc8c5f993b21cebfc4f8b72f0fd2cb6f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "19829289"
---
# <a name="searchablemailboxes"></a>SearchableMailboxes

L’élément **SearchableMailboxes** contient un tableau de boîtes aux lettres renvoyé à partir d’une demande **GetSearchableMailboxes** . 
  
```XML
<SearchableMailboxes>
   <SearchableMailbox/>
</SearchableMailboxes>
```

 **ArrayOfSearchableMailboxesType**
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, éléments enfants et éléments parents.
  
### <a name="attributes"></a>Attributs

Aucun.
  
### <a name="child-elements"></a>Éléments enfants

[SearchableMailbox](searchablemailbox.md)
  
### <a name="parent-elements"></a>Éléments parents

[GetSearchableMailboxesResponse](getsearchablemailboxesresponse.md)
  
## <a name="remarks"></a>Remarques

Cet élément est une nouveauté d'Exchange Server 2013.
  
Le schéma qui décrit cet élément se trouve dans le répertoire virtuel IIS qui héberge les services web Exchange.
  
## <a name="element-information"></a>Informations sur l'élément

|||
|:-----|:-----|
|Espace de noms  <br/> |http://schemas.microsoft.com/exchange/services/2006/messages  <br/> |
|Nom du schéma  <br/> |Schéma Messages  <br/> |
|Fichier de validation  <br/> |Messages.xsd  <br/> |
|Peut être vide  <br/> ||
   
