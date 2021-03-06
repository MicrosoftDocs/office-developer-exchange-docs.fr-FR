---
title: DaylightTime
manager: sethgros
ms.date: 09/17/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- DaylightTime
api_type:
- schema
ms.assetid: 9f551ee4-d945-477c-b981-9554b197d26d
description: L’élément DaylightTime représente un décalage par rapport à l’heure par rapport au temps universel coordonné (UTC) représenté par l’élément bias (UTC) dans les régions où l’heure d’été est observée. Cet élément contient également des informations sur le moment où se produit la transition vers l’heure d’été à partir de l’heure standard.
ms.openlocfilehash: 350fcb4ce278f423c62fcc5ecaa160eda71e4a2c
ms.sourcegitcommit: 88ec988f2bb67c1866d06b361615f3674a24e795
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "44455652"
---
# <a name="daylighttime"></a>DaylightTime

L’élément **DaylightTime** représente un décalage par rapport à l’heure par rapport au temps universel coordonné (UTC) représenté par l’élément [bias (UTC)](bias-utc.md) dans les régions où l’heure d’été est observée. Cet élément contient également des informations sur le moment où se produit la transition vers l’heure d’été à partir de l’heure standard. 
  
- [TimeZone (disponibilité)](timezone-availability.md) 
- [DaylightTime](daylighttime.md)
  
```xml
<DaylightTime>
   <Bias>int</Bias>
   <Time>string</Time>
   <DayOrder>short</DayOrder>
   <Month>short</Month>
   <DayOfWeek>Sunday or Monday or Tuesday or Wednesday or Thursday or Friday or Saturday</DayOfWeek>
   <Year>string</Year>
</DaylightTime>
```

**SerializableTimeZoneTime**

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents.
  
### <a name="attributes"></a>Attributs

Aucune.
  
### <a name="child-elements"></a>Éléments enfants

|**Élément**|**Description**|
|:-----|:-----|
|[Bias](bias.md) <br/> |Représente le décalage à partir de l’offset UTC identifié par l’élément [bias (UTC)](bias-utc.md) pour l’heure standard et l’heure d’été. Cette valeur est exprimée en minutes.  <br/> |
|[Time](time.md) <br/> |Représente l’heure de transition du jour et de l’heure standard et de l’heure d’été.  <br/> |
|[DayOrder](dayorder.md) <br/> |Représente la _n_th occurrence du jour spécifiée dans l’élément [DayOfWeek (TimeZone)](dayofweek-timezone.md) qui représente la date de transition de et de l’heure standard et de l’heure d’été.  <br/> |
|[Month](month.md) <br/> |Représente le mois de transition de l’année, de l’heure standard et de l’heure d’été.  <br/> |
|[DayOfWeek (TimeZone)](dayofweek-timezone.md) <br/> |Représente le jour de la semaine où se produit la transition vers et à partir de l’heure et de l’heure d’été.  <br/> |
|[Année](year.md) <br/> |Permet de définir un fuseau horaire qui change en fonction de l’année. Cet élément est facultatif. Cet élément a été introduit dans Microsoft Exchange Server 2007 Service Pack 1 (SP1).  <br/> |
   
### <a name="parent-elements"></a>Éléments parents

|**Élément**|**Description**|
|:-----|:-----|
|[TimeZone (disponibilité)](timezone-availability.md) <br/> | Contient des éléments qui identifient les informations de fuseau horaire.<br/><br/>Cet élément contient également des informations sur la transition entre l’heure standard et l’heure d’été.<br/><br/>`/GetUserAvailabilityResponse/FreeBusyResponseArray/FreeBusyResponse/FreeBusyView/WorkingHours/TimeZone` <br/><br/>`/GetUserAvailabilityRequest/TimeZone` <br/> |
   
## <a name="example"></a>Exemple

La requête GetUserAvailability partielle suivante représente une application cliente dans un emplacement qui reconnaît l’heure d’été.
  
```xml
<TimeZone xmlns="https://schemas.microsoft.com/exchange/services/2006/types">
  <Bias>480</Bias>
  <StandardTime>
    <Bias>0</Bias>
    <Time>02:00:00</Time>
    <DayOrder>5</DayOrder>
    <Month>10</Month>
    <DayOfWeek>Sunday</DayOfWeek>
  </StandardTime>
  <DaylightTime>
    <Bias>-60</Bias>
    <Time>02:00:00</Time>
    <DayOrder>1</DayOrder>
    <Month>4</Month>
    <DayOfWeek>Sunday</DayOfWeek>
  </DaylightTime>
</TimeZone>
```

## <a name="element-information"></a>Informations sur l'élément

|||
|:-----|:-----|
|Espace de noms  <br/> |https://schemas.microsoft.com/exchange/services/2006/types  <br/> |
|Nom du schéma  <br/> |Schéma Types  <br/> |
|Fichier de validation  <br/> |Types.xsd  <br/> |
|Peut être vide  <br/> |False  <br/> |
   
## <a name="see-also"></a>Voir aussi

- [Opération GetUserAvailability](getuseravailability-operation.md)
- [Obtention de la disponibilité des utilisateurs](https://msdn.microsoft.com/library/d4133fcb-9b0f-4e6b-aadf-a389da83516a%28Office.15%29.aspx)

