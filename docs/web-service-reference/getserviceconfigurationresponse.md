---
title: GetServiceConfigurationResponse
manager: sethgros
ms.date: 09/17/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- GetServiceConfigurationResponse
api_type:
- schema
ms.assetid: 313dac99-0e5c-4198-bafa-89e749934ac7
description: L’élément GetServiceConfigurationResponse définit une réponse à une demande de GetServiceConfiguration.
ms.openlocfilehash: 7abc81222125334de2a6ab6e4a618b48fe0caf4f
ms.sourcegitcommit: 34041125dc8c5f993b21cebfc4f8b72f0fd2cb6f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "19827668"
---
# <a name="getserviceconfigurationresponse"></a>GetServiceConfigurationResponse

L’élément **GetServiceConfigurationResponse** définit une réponse à une demande de GetServiceConfiguration. 
  
```XML
<GetServiceConfigurationResponse ResponseClass="">
   <MessageText/>
   <ResponseCode/>
   <DescriptiveLinkKey/>
   <MessageXml/>
   <ResponseMessages/>
</GetServiceConfigurationResponse>
```

 **GetServiceConfigurationResponseMessageType**
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, éléments enfants et éléments parents.
  
### <a name="attributes"></a>Attributs

|**Attribut**|**Description**|
|:-----|:-----|
|**ResponseClass** <br/> | Décrit l’état de la réponse. <br/><br/>Les valeurs suivantes sont valides pour cet attribut :  <br/><br/>-Réussite  <br/>-Avertissement  <br/>-Erreur  <br/> |
   
#### <a name="responseclass-attribute-values"></a>Valeurs des attributs ResponseClass

|**Valeur**|**Description**|
|:-----|:-----|
|**Opération réussie** <br/> |Décrit une demande est remplie.  <br/> |
|**Avertissement** <br/> | Décrit une demande qui n’a pas aboutie. Un message d’avertissement peut être renvoyée si une erreur s’est produite pendant le traite d’un élément dans la demande et les éléments suivants n’ont pas peuvent être traités. <br/><br/>Voici des exemples de sources d’avertissements :  <br/><br/>-La banque d’informations Exchange est en mode hors connexion pendant le traitement par lots.  <br/>-Services de domaine actives Directory (AD DS) est en mode hors connexion.  <br/>-Boîtes aux lettres ont été déplacés.  <br/>-La base de données de message (MDB) est en mode hors connexion.  <br/>-Un mot de passe a expiré.  <br/>-Un quota a été dépassé.  <br/> |
|**Erreur** <br/> | Décrit une demande ne peut pas être traitée. <br/><br/>Voici des exemples de sources d’erreurs :  <br/><br/>-Non valide attributs ou éléments  <br/>-Attributs ou éléments qui se trouvent en dehors des limites  <br/>-Une balise inconnue  <br/>-Un attribut ou un élément qui n’est pas valide dans le contexte  <br/>-Une tentative d’accès non autorisés par n’importe quel client  <br/>-Une panne côté serveur en réponse à un appel côté client valid  <br/><br/>  Vous trouverez plus d’informations sur l’erreur dans les éléments [ResponseCode](responsecode.md) et [MessageText](messagetext.md) .  <br/> |
   
### <a name="child-elements"></a>Éléments enfants

|**Élément**|**Description**|
|:-----|:-----|
|[MessageText](messagetext.md) <br/> |Fournit une description textuelle de l’état de la réponse.  <br/> |
|[ResponseCode](responsecode.md) <br/> |Fournit un code d’erreur qui identifie l’erreur spécifique qui a rencontré la demande.  <br/> |
|[DescriptiveLinkKey](descriptivelinkkey.md) <br/> |Actuellement inutilisée et réservée à un usage ultérieur. Cet élément contient une valeur de 0.  <br/> |
|[MessageXml](messagexml.md) <br/> |Fournit des informations de réponse d’erreur.  <br/> |
|[ResponseMessages (ArrayOfServiceConfigurationResponseMessageType)](responsemessages-arrayofserviceconfigurationresponsemessagetype.md) <br/> |Contient un tableau de messages de réponse de configuration de service.  <br/> |
   
### <a name="parent-elements"></a>Éléments parents

Aucun.
  
## <a name="text-value"></a>Valeur de texte

Aucun.
  
## <a name="remarks"></a>Remarques

Le schéma qui décrit cet élément se trouve dans le répertoire virtuel IIS qui héberge les services web Exchange.
  
## <a name="element-information"></a>Informations sur l'élément

|||
|:-----|:-----|
|Espace de noms  <br/> |http://schemas.microsoft.com/exchange/services/2006/messages  <br/> |
|Nom du schéma  <br/> |Schéma Messages  <br/> |
|Fichier de validation  <br/> |Messages.xsd  <br/> |
|Peut être vide  <br/> |False  <br/> |
   
## <a name="see-also"></a>Voir aussi

- [Éléments XML de EWS dans Exchange](ews-xml-elements-in-exchange.md)
