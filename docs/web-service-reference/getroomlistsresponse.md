---
title: GetRoomListsResponse
manager: sethgros
ms.date: 09/17/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- GetRoomListsResponse
api_type:
- schema
ms.assetid: 8c736f68-1026-496a-b12f-c169c078abd0
description: L’élément GetRoomListsResponse définit la réponse à une demande d’opération GetRoomLists.
ms.openlocfilehash: 8231435f7dc348a070852f57d6152550326b5df6
ms.sourcegitcommit: 34041125dc8c5f993b21cebfc4f8b72f0fd2cb6f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "19756739"
---
# <a name="getroomlistsresponse"></a>GetRoomListsResponse

L’élément **GetRoomListsResponse** définit la réponse à une demande [d’opération GetRoomLists](getroomlists-operation.md) . 
  
- [ResponseMessages](responsemessages.md)
- [GetRoomListsResponse](getroomlistsresponse.md)
  
```XML
<GetRoomListsResponse ResponseClass="">   
<MessageText/>   
<ResponseCode/>   
<DescriptiveLinkKey/>   
<MessageXml/>   
<RoomLists/>
</GetRoomListsResponse>
```

 **GetRoomListsResponseMessageType**
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
|**Avertissement** <br/> | Décrit une demande qui n’a pas aboutie. Un message d’avertissement peut être renvoyée si une erreur s’est produite pendant le traite d’un élément dans la demande et les éléments suivants n’ont pas peuvent être traités. <br/><br/>Voici des exemples de sources d’avertissements :  <br/><br/>-La banque d’informations Exchange est en mode hors connexion pendant le traitement par lots.  <br/>-Le service d’annuaire Active Directory est en mode hors connexion.  <br/>-Boîtes aux lettres ont été déplacés.  <br/>-La base de données de message (MDB) est en mode hors connexion.  <br/>-Un mot de passe a expiré.  <br/>-Un quota a été dépassé.  <br/> |
|**Erreur** <br/> | Décrit une demande ne peut pas être traitée. <br/><br/>Voici des exemples de sources d’erreurs :  <br/><br/>-Non valide attributs ou éléments  <br/>-Attributs ou éléments hors limites  <br/>-Balise inconnue  <br/>-Attribut ou un élément non valide dans le contexte  <br/>-Tentative d’accès non autorisé par n’importe quel client  <br/>Échec du côté serveur en réponse à un appel côté client valid  <br/><br/>  Vous trouverez plus d’informations sur l’erreur dans les éléments [ResponseCode](responsecode.md) et [MessageText](messagetext.md) .  <br/>- |
   
### <a name="child-elements"></a>Éléments enfants

|**Élément**|**Description**|
|:-----|:-----|
|[MessageText](messagetext.md) <br/> |Fournit une description textuelle de l’état de la réponse.  <br/> |
|[ResponseCode](responsecode.md) <br/> |Fournit un code d’erreur qui identifie l’erreur spécifique qui a rencontré la demande.  <br/> |
|[DescriptiveLinkKey](descriptivelinkkey.md) <br/> |Actuellement inutilisée et réservée à un usage ultérieur. Cet élément contient une valeur de 0.  <br/> |
|[MessageXml](messagexml.md) <br/> |Fournit des informations de réponse d’erreur.  <br/> |
|[RoomLists](roomlists.md) <br/> |Fournit une liste des adresses de messagerie et les noms complets qui représentent des listes de salles de réunion.  <br/> |
   
### <a name="parent-elements"></a>Éléments parents

|**Élément**|**Description**|
|:-----|:-----|
|[ResponseMessages](responsemessages.md) <br/> |Contient les messages de réponse pour une demande de Services Web Exchange.  <br/> |
   
## <a name="element-information"></a>Informations sur l'élément

|||
|:-----|:-----|
|Espace de noms  <br/> |http://schemas.microsoft.com/exchange/services/2006/messages  <br/> |
|Nom du schéma  <br/> |Schéma Messages  <br/> |
|Fichier de validation  <br/> |Messages.xsd  <br/> |
|Peut être vide  <br/> |False  <br/> |
   
## <a name="see-also"></a>Voir aussi

- [Opération GetRoomLists](getroomlists-operation.md)
- [Éléments XML de EWS dans Exchange](ews-xml-elements-in-exchange.md)
