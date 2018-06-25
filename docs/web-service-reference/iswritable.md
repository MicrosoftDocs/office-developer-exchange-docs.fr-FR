---
title: IsWritable
manager: sethgros
ms.date: 09/17/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d4af8eee-7001-4a8e-b9bd-d14882f2406b
description: L’élément IsWritable Spécifie si l’ou les destinataires d’Active Directory sous-jacent peut être écrite.
ms.openlocfilehash: 03f258d01ecfc12dfa4e09ac88f4a75340d2acf3
ms.sourcegitcommit: 34041125dc8c5f993b21cebfc4f8b72f0fd2cb6f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "19828158"
---
# <a name="iswritable"></a>IsWritable

L’élément **IsWritable** Spécifie si l’ou les destinataires d’Active Directory sous-jacent peut être écrite. 
  
```XML
<IsWritable> true | false </IsWritable>
```

 **Boolean**
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, éléments enfants et éléments parents.
  
### <a name="attributes"></a>Attributs

Aucun.
  
### <a name="child-elements"></a>Éléments enfants

Aucun.
  
### <a name="parent-elements"></a>Éléments parents

[Attribution (PersonaAttributionType)](attribution-personaattributiontype.md)
  
## <a name="text-value"></a>Valeur de texte

Une valeur de texte de **la valeur true** pour l’élément **IsWritable** indique que le contact ou un objet Active Directory est accessible en écriture. La valeur **false** indique que le contact ou un objet Active Directory n’est pas disponible pour un accès en écriture. 
  
## <a name="remarks"></a>Remarques

Cet élément est une nouveauté d'Exchange Server 2013.
  
Le schéma qui décrit cet élément se trouve dans le répertoire virtuel IIS qui héberge les services web Exchange.
  
