---
title: État (HoldStatusType)
manager: sethgros
ms.date: 09/17/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: fee3f1f9-e868-49fa-a554-7ff096964718
description: L’élément Status spécifie l’état de conservation pour une boîte aux lettres.
ms.openlocfilehash: c40dc865d2b305ac86fa40d536e2d516a14260ab
ms.sourcegitcommit: 34041125dc8c5f993b21cebfc4f8b72f0fd2cb6f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "19829579"
---
# <a name="status-holdstatustype"></a>État (HoldStatusType)

L’élément **Status** Spécifie l’état de conservation pour une boîte aux lettres. 
  
```XML
<Status> NotOnHold | Pending | OnHold | PartialHold | Failed </Status>
```

 **HoldStatusType**
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, éléments enfants et éléments parents.
  
### <a name="attributes"></a>Attributs

Aucun.
  
### <a name="child-elements"></a>Éléments enfants

Aucun.
  
### <a name="parent-elements"></a>Éléments parents

[MailboxHoldStatus](mailboxholdstatus.md)
  
## <a name="text-value"></a>Valeur de texte

La valeur de texte de l’élément **Status** est l’état de conservation d’une boîte aux lettres. L’élément **Status** peut avoir les valeurs dans la liste suivante. 
  
> NotOnHold - la boîte aux lettres n’est pas en attente.
    
> En attente - la boîte aux lettres est en attente d’être placé soit publié en attente. 
    
> En attente - la suspension a été appliqué à la boîte aux lettres. 
    
> PartialHold - la suspension a été appliqué à des boîtes aux lettres, mais pas pour toutes les boîtes aux lettres.
    
> Échec - Échec de la suspension à appliquer à la boîte aux lettres.
    
## <a name="remarks"></a>Remarques

Cet élément est une nouveauté d'Exchange Server 2013.
  
Le schéma qui décrit cet élément se trouve dans le répertoire virtuel IIS qui héberge les services web Exchange.
  
## <a name="element-information"></a>Informations sur l'élément

|||
|:-----|:-----|
|Espace de noms  <br/> |http://schemas.microsoft.com/exchange/services/2006/types  <br/> |
|Nom du schéma  <br/> |Schéma Types  <br/> |
|Fichier de validation  <br/> |Types.xsd  <br/> |
|Peut être vide  <br/> ||
   
