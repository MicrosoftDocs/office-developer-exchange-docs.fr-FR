---
title: RecipientTrackingEvent
manager: sethgros
ms.date: 09/17/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- RecipientTrackingEvent
api_type:
- schema
ms.assetid: 2bffdac7-c2f5-4805-ae7e-bd865301acb6
description: L’élément RecipientTrackingEvent contient des informations pour un seul événement pour un destinataire.
ms.openlocfilehash: e9a014cdfac122f112205cfa5032535a770f9d82
ms.sourcegitcommit: 88ec988f2bb67c1866d06b361615f3674a24e795
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "44465484"
---
# <a name="recipienttrackingevent"></a>RecipientTrackingEvent

L’élément **RecipientTrackingEvent** contient des informations pour un seul événement pour un destinataire. 
  
```XML
<RecipientTrackingEvent>
   <Date/>
   <Recipient/>
   <DeliveryStatus/>
   <EventDescription/>
   <EventData/>
   <Server/>
   <InternalId/>
   <BccRecipient/>
   <HiddenRecipient/>
   <UniquePathId/>
   <RootAddress/>
   <Properties/>
</RecipientTrackingEvent>
```

 **RecipientTrackingEventType**
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents.
  
### <a name="attributes"></a>Attributs

Aucune.
  
### <a name="child-elements"></a>Éléments enfants

|**Élément**|**Description**|
|:-----|:-----|
|[Date (MessageTracking)](date-messagetracking.md) <br/> |Cet élément est obligatoire.  <br/> |
|[Destinataire](recipient.md) <br/> |Cet élément est obligatoire.  <br/> |
|[DeliveryStatus](deliverystatus.md) <br/> |Cet élément est obligatoire.  <br/> |
|[Systèmedescription](eventdescription.md) <br/> |Cet élément est obligatoire.  <br/> |
|[EventData](eventdata.md) <br/> |Cet élément est facultatif.  <br/> |
|[Serveur (MessageTracking)](server-messagetracking.md) <br/> |Cet élément est obligatoire.  <br/> |
|[InternalId](internalid.md) <br/> |Cet élément est obligatoire.  <br/> |
|[BccRecipient](bccrecipient.md) <br/> |Cet élément est facultatif.  <br/> |
|[HiddenRecipient](hiddenrecipient.md) <br/> |Cet élément est facultatif.  <br/> |
|[UniquePathId](uniquepathid.md) <br/> |Cet élément est facultatif.  <br/> |
|[RootAddress](rootaddress.md) <br/> |Cet élément est facultatif.  <br/> |
|[Propriétés (ArrayOfTrackingPropertiesType)](properties-arrayoftrackingpropertiestype.md) <br/> |Cet élément est facultatif.  <br/> |
   
### <a name="parent-elements"></a>Éléments parents

|**Élément**|**Description**|
|:-----|:-----|
|[RecipientTrackingEvents](recipienttrackingevents.md) <br/> |Contient une liste d’un ou plusieurs événements de suivi pour un destinataire.  <br/> |
   
## <a name="text-value"></a>Valeur de texte

Aucun.
  
## <a name="remarks"></a>Remarques

Le schéma qui décrit cet élément se trouve dans le répertoire virtuel IIS qui héberge les services web Exchange.
  
## <a name="element-information"></a>Informations sur l'élément

|||
|:-----|:-----|
|Espace de noms  <br/> |https://schemas.microsoft.com/exchange/services/2006/types  <br/> |
|Nom du schéma  <br/> |Schéma Types  <br/> |
|Fichier de validation  <br/> |Types.xsd  <br/> |
|Peut être vide  <br/> |False  <br/> |
   
## <a name="see-also"></a>Voir aussi



[Opération de GetMessageTrackingReport](getmessagetrackingreport-operation.md)


- [Éléments XML de EWS dans Exchange](ews-xml-elements-in-exchange.md)

