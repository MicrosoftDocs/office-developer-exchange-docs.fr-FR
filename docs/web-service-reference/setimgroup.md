---
title: SetImGroup
manager: sethgros
ms.date: 09/17/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3c107b8d-714b-4cd5-ad1b-97b7cbcb90d6
description: L’élément SetImGroup représente une demande pour modifier le nom d’affichage d’un groupe de messagerie instantanée.
ms.openlocfilehash: 96e93ef595720325448c343c193f25b846ba415e
ms.sourcegitcommit: 88ec988f2bb67c1866d06b361615f3674a24e795
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "44438067"
---
# <a name="setimgroup"></a>SetImGroup

L’élément **SetImGroup** représente une demande pour modifier le nom d’affichage d’un groupe de messagerie instantanée. 
  
```XML
<SetImGroup>
   <GroupId/>
   <NewDisplayName/>
</SetImGroup>
```

 **SetImGroupType**
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents.
  
### <a name="attributes"></a>Attributs

Aucune.
  
### <a name="child-elements"></a>Éléments enfants

[GroupID](groupid.md)  |  [NewDisplayName](newdisplayname.md)
  
### <a name="parent-elements"></a>Éléments parents

Aucun.
  
## <a name="remarks"></a>Remarques

Cet élément est une nouveauté d'Exchange Server 2013.
  
Le schéma qui décrit cet élément se trouve dans le répertoire virtuel IIS qui héberge les services web Exchange.
  
## <a name="element-information"></a>Informations sur l'élément

|||
|:-----|:-----|
|Espace de noms  <br/> |https://schemas.microsoft.com/exchange/services/2006/messages  <br/> |
|Nom du schéma  <br/> |Schéma Messages  <br/> |
|Fichier de validation  <br/> |Messages. xsd  <br/> |
|Peut être vide  <br/> ||
   

