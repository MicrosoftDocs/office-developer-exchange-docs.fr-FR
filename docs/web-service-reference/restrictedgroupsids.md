---
title: RestrictedGroupSids
manager: sethgros
ms.date: 09/17/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- RestrictedGroupSids
api_type:
- schema
ms.assetid: 569ab552-5616-444a-a7f5-de366a684a34
description: L’élément RestrictedGroupSids représente une collection de groupes restreints à partir d’un jeton d’utilisateur.
ms.openlocfilehash: fcfee809261c7ed0a4e0d092c091841fec641e46
ms.sourcegitcommit: 34041125dc8c5f993b21cebfc4f8b72f0fd2cb6f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "19829201"
---
# <a name="restrictedgroupsids"></a>RestrictedGroupSids

L’élément **RestrictedGroupSids** représente une collection de groupes restreints à partir d’un jeton d’utilisateur. 
  
```xml
<RestrictedGroupSids>
   <RestrictedGroupIdentifier/>
</RestrictedGroupSids>
```

 **NonEmptyArrayOfRestrictedGroupIdentifiersType**
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, éléments enfants et éléments parents.
  
### <a name="attributes"></a>Attributs

Aucun.
  
### <a name="child-elements"></a>Éléments enfants

|**Élément**|**Description**|
|:-----|:-----|
|[RestrictedGroupIdentifier](restrictedgroupidentifier.md) <br/> |Représente l’identificateur de sécurité (SID) de groupe et les attributs d’un groupe restreint.  <br/> |
   
### <a name="parent-elements"></a>Éléments parents

|**Élément**|**Description**|
|:-----|:-----|
|[SerializedSecurityContext](serializedsecuritycontext.md) <br/> |Utilisé dans l’en-tête SOAP pour sérialisation de jeton de l’authentification de serveur à serveur. Sérialisation de jeton n’est pas pris en charge.  <br/> |
   
## <a name="remarks"></a>Remarques

Le schéma qui décrit cet élément se trouve dans le répertoire virtuel EWS de l'ordinateur qui exécute Microsoft Exchange Server 2007 sur lequel le rôle de serveur d'accès au client est installé.
  
## <a name="element-information"></a>Informations sur l'élément

|||
|:-----|:-----|
|Espace de noms  <br/> |http://schemas.microsoft.com/exchange/services/2006/types  <br/> |
|Nom du schéma  <br/> |Schéma Types  <br/> |
|Fichier de validation  <br/> |Types.xsd  <br/> |
|Peut être vide  <br/> |False  <br/> |
   
## <a name="see-also"></a>Voir aussi



- [Éléments XML de EWS dans Exchange](ews-xml-elements-in-exchange.md)
