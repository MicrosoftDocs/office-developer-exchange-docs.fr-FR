---
title: Condition
manager: sethgros
ms.date: 09/17/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- Condition
api_type:
- schema
ms.assetid: 0790a3f2-cb31-4036-a757-7821aa0722cb
description: L’élément Condition identifie la condition qui doit être remplie pour la partie de l’action de la règle doit être exécutée.
ms.openlocfilehash: ed605946f99aa63416337cd0e731c931176a8ed4
ms.sourcegitcommit: 34041125dc8c5f993b21cebfc4f8b72f0fd2cb6f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "19755531"
---
# <a name="condition"></a>Condition

L’élément **Condition** identifie la condition qui doit être remplie pour la partie de l’action de la règle doit être exécutée. 
  
```xml
<Condition>
   <AllInternal/>
</Condition>
```

 **ProtectionRuleConditionType**
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, éléments enfants et éléments parents.
  
### <a name="attributes"></a>Attributs

Aucun.
  
### <a name="child-elements"></a>Éléments enfants

|**Élément**|**Description**|
|:-----|:-----|
|[AllInternal](allinternal.md) <br/> |Renvoie **la valeur true** si tous les destinataires d’un message électronique sont internes à l’organisation de l’expéditeur.  <br/> |
|[Et (ProtectionRuleAndType)](and-protectionruleandtype.md) <br/> |Spécifie que tous les éléments enfants doivent correspondre pour prendre la **valeur true**. Spécifie qu’il doit y avoir plusieurs conditions d’enfants de règle de protection.  <br/> |
|[RecipientIs](recipientis.md) <br/> |Spécifie que n’importe quel destinataire du message électronique correspond à un des destinataires spécifiés dans les éléments de [valeur (ProtectionRuleValueType)](value-protectionrulevaluetype.md) enfants.  <br/> |
|[SenderDepartments](senderdepartments.md) <br/> |Spécifie que le service de l’expéditeur correspond à l’un des services spécifiés dans les éléments de [valeur (ProtectionRuleValueType)](value-protectionrulevaluetype.md) enfants.  <br/> |
|[True](true.md) <br/> |Spécifie une condition qui correspond toujours.  <br/> |
   
### <a name="parent-elements"></a>Éléments parents

|**Élément**|**Description**|
|:-----|:-----|
|[Règle](rule.md) <br/> |Contient une règle de protection unique.  <br/> |
   
## <a name="text-value"></a>Valeur de texte

Aucun.
  
## <a name="remarks"></a>Remarques

Le schéma qui décrit cet élément se trouve dans le répertoire virtuel IIS qui héberge les services web Exchange.
  
## <a name="element-information"></a>Informations sur l'élément

|||
|:-----|:-----|
|Espace de noms  <br/> |http://schemas.microsoft.com/exchange/services/2006/types  <br/> |
|Nom du schéma  <br/> |Schéma Types  <br/> |
|Fichier de validation  <br/> |Types.xsd  <br/> |
|Peut être vide  <br/> |False  <br/> |
   
## <a name="see-also"></a>Voir aussi



- [Éléments XML de EWS dans Exchange](ews-xml-elements-in-exchange.md)
