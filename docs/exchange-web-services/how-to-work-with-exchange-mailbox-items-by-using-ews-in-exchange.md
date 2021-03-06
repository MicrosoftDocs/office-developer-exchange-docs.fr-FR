---
title: Utilisations d’éléments de boîte aux lettres Exchange à l’aide d’EWS dans Exchange
manager: sethgros
ms.date: 09/17/2015
ms.audience: Developer
ms.assetid: 721deb84-f85d-45d0-84c1-0ed55f359969
description: Découvrez comment créer, obtenir, mettre à jour et supprimer des éléments à l’aide de l’API managée EWS ou d’EWS dans Exchange.
localization_priority: Priority
ms.openlocfilehash: e86affbe8efe0dfc312f5ed5fadec2547f1352ea
ms.sourcegitcommit: 88ec988f2bb67c1866d06b361615f3674a24e795
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "44527585"
---
# <a name="work-with-exchange-mailbox-items-by-using-ews-in-exchange"></a>Utilisations d’éléments de boîte aux lettres Exchange à l’aide d’EWS dans Exchange

Découvrez comment créer, obtenir, mettre à jour et supprimer des éléments à l’aide de l’API managée EWS ou d’EWS dans Exchange.
  
Vous pouvez utiliser l’API managée EWS ou EWS pour utiliser des éléments dans une boîte aux lettres. Vous pouvez utiliser des éléments génériques: des[éléments](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.item%28v=exchg.80%29.aspx) de l’API managée EWS ou des[éléments](https://msdn.microsoft.com/library/4dfe8f48-e7b4-444d-bdf9-a34e180f598b%28Office.15%29.aspx)de types EWS pour effectuer certaines opérations (telles que l’obtention ou la suppression d’un élément à l’aide de l’identificateur de ce dernier). Toutefois, la plupart du temps, vous devez utiliser un [élément fortement identifié](folders-and-items-in-ews-in-exchange.md#bk_item) pour effectuer une opération d’obtention ou de mise à jour, car vous devrez accéder aux propriétés propres à l’élément fortement identifié. 

Par exemple, vous ne pouvez pas utiliser un élément générique pour récupérer un élément qui contient une date de début et de fin. Pour ce faire, vous avez besoin d’un objet [de Rendez-vous](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.appointment%28v=exchg.80%29.aspx)ou d’un[CalendarItem](https://msdn.microsoft.com/library/b0c1fd27-b6da-46e5-88b8-88f00c71ba80%28Office.15%29.aspx) de type EWS. Si vous utilisez l’API managée EWS, vous devez toujours créer des éléments fortement identifiés, car la **classe**générique ne possède pas de constructeur. Si vous utilisez un élément qui n’est pas fortement identifié, vous pouvez vous servir de la **classe**de base afin d’utiliser cet élément. 
  
**Tableau 1. Méthodes d’API managée EWS et opérations EWS pour l’utilisation d’éléments**

|**Afin de...**|**Méthode d'API managée EWS**|**Opération EWS**|
|:-----|:-----|:-----|
|Créer un élément générique  <br/> |Aucune. Vous pouvez uniquement créer des types d’élément spécifiques à l’aide de l’API managée EWS. Vous ne pouvez pas créer d’éléments génériques.  <br/> |[CreateItem](https://msdn.microsoft.com/library/bcc68f9e-d511-4c29-bba6-ed535524624a%28Office.15%29.aspx) <br/> |
|Obtenir un élément  <br/> |[Item.Bind](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.item.bind%28v=exchg.80%29.aspx) <br/> |[GetItem](https://msdn.microsoft.com/library/e3590b8b-c2a7-4dad-a014-6360197b68e4%28Office.15%29.aspx) <br/> |
|Mettre à jour un élément  <br/> |[Item.Update](https://msdn.microsoft.com/library/office/dd635915%28v=exchg.80%29.aspx) <br/> |[UpdateItem](https://msdn.microsoft.com/library/5d027523-e0bc-4da2-b60b-0cb9fc1fdfe4%28Office.15%29.aspx) <br/> |
|Supprimer un élément  <br/> |[Item.Delete](https://msdn.microsoft.com/library/office/dd635072%28v=exchg.80%29.aspx) <br/> |[DeleteItem](../web-service-reference/deleteitem-operation.md) <br/> |
   
Dans cet article, vous découvrirez également à quel moment vous pouvez utiliser la classe de base générique et à quel moment vous devez utiliser un élément fortement identifié pour mener à bien votre tâche. Les exemples de code vous indiqueront comment utiliser la classe de base, ainsi que la marche à suivre lorsque vous ne pouvez pas utiliser cette dernière ou lorsqu’elle ne répond pas à vos besoins.
  
## <a name="create-an-item-by-using-the-ews-managed-api"></a>Création d’un élément à l’aide de l’API managée EWS
<a name="bk_createewsma"> </a>

L’API managée EWS ne possède pas de constructeur publiquement disponible pour la [classe](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.item%28v=exchg.80%29.aspx)d’élément. Par conséquent, afin de créer un élément, vous devez utiliser le constructeur approprié au type d’élément spécifique que vous souhaitez créer. Par exemple, utilisez le[constructeur de classe EmailMessage](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage.emailmessage%28v=exchg.80%29.aspx) pour créer un nouveau message électronique et le [constructeur de classe Contact](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.contact%28v=exchg.80%29.aspx) pour créer un contact. De même, le serveur ne renvoie jamais** d’objets**génériques dans les réponses. Tous les éléments génériques sont renvoyés sous forme d’objets **EmailMessage**. 
  
Lorsque vous connaissez le type d’élément à créer, vous pouvez effectuer la tâche en quelques étapes seulement. Les étapes sont similaires pour tous les types d’éléments :
  
1. Initialiser une nouvelle instance de l’une des classes[d’élément](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.item%28v=exchg.80%29.aspx)avec l’objet[ExchangeService](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.exchangeservice%28v=exchg.80%29.aspx)en tant que paramètre. 
    
2. Les schémas sont différents pour chaque type d’élément, c’est pourquoi plusieurs propriétés sont disponibles pour ces derniers.
    
3. Enregistrez l’élément, ou enregistrez et envoyez l’élément.
    
Par exemple, vous pouvez créer un objet[EmailMessage](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage%28v=exchg.80%29.aspx), définissez l’[objet](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.item.subject%28v=exchg.80%29.aspx), [corps](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.item.body%28v=exchg.80%29.aspx), et les propriétés[ToRecipients](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage.torecipients%28v=exchg.80%29.aspx), puis envoyez-le à l’aide de la méthode[EmailMessage.SendAndSaveCopy](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage.sendandsavecopy%28v=exchg.80%29.aspx). 
  
```cs
// Create an email message and provide it with connection 
// configuration information by using an ExchangeService object named service.
EmailMessage message = new EmailMessage(service);
// Set properties on the email message.
message.Subject = "Company Soccer Team";
message.Body = "Are you interested in joining?";
message.ToRecipients.Add("sadie@contoso.com");
// Send the email message and save a copy.
// This method call results in a CreateItem call to EWS.
message.SendAndSaveCopy();
```

Pour découvrir comment créer un élément de réunion ou de rendez-vous à l’aide de l’API managée EWS, voir[ Créer des rendez-vous et des réunions à l’aide d’EWS dans Exchange 2013](how-to-create-appointments-and-meetings-by-using-ews-in-exchange-2013.md).
  
## <a name="create-an-item-by-using-ews"></a>Création d’un élément à l’aide d’EWS
<a name="bk_createews"> </a>

Vous pouvez créer un élément générique ou un élément fortement identifié à l’aide d’EWS. Les étapes sont identiques pour tous les types d’éléments:
  
1. Utilisez l’opération [CreateItem](https://msdn.microsoft.com/library/bcc68f9e-d511-4c29-bba6-ed535524624a%28Office.15%29.aspx) pour créer un élément dans la banque d’informations Exchange. 
    
2. Utilisez l’élément [Items](https://msdn.microsoft.com/library/0811a73e-bf1f-4889-9219-73902dd47639%28Office.15%29.aspx) qui contiendra au moins un élément à créer. 
    
3. Définissez des propriétés sur l’élément.
    
Par exemple, vous pouvez créer un message électronique et l’envoyer à l’aide du code de l’exemple suivant. Il s’agit également de la demande XML que l’API Managée EWS envoie lorsque vous appelez la méthode[SendAndSaveCopy](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage.sendandsavecopy%28v=exchg.80%29.aspx). 
  
```XML
<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
               xmlns:m="https://schemas.microsoft.com/exchange/services/2006/messages" 
               xmlns:t="https://schemas.microsoft.com/exchange/services/2006/types" 
               xmlns:soap="https://schemas.xmlsoap.org/soap/envelope/">
  <soap:Header>
    <t:RequestServerVersion Version="Exchange2007_SP1" />
  </soap:Header>
  <soap:Body>
    <m:CreateItem MessageDisposition="SendAndSaveCopy">
      <m:SavedItemFolderId>
        <t:DistinguishedFolderId Id="sentitems" />
      </m:SavedItemFolderId>
      <m:Items>
        <t:Message>
          <t:Subject>Company Soccer Team</t:Subject>
          <t:Body BodyType="HTML">Are you interested in joining?</t:Body>
          <t:ToRecipients>
            <t:Mailbox>
              <t:EmailAddress>sadie@contoso.com </t:EmailAddress>
              </t:Mailbox>
          </t:ToRecipients>
        </t:Message>
      </m:Items>
    </m:CreateItem>
  </soap:Body>
</soap:Envelope>
```

Le serveur répond à la demande**CreateItem** par un message [GetItemResponse](https://msdn.microsoft.com/library/742a46a0-2475-45a0-b44f-90639a3f5a43%28Office.15%29.aspx), qui inclut [ResponseCode](https://msdn.microsoft.com/library/aa580757%28v=exchg.150%29.aspx) renvoyant la valeur **NoError**, indiquant que le message a bien été créé, et où apparaît l’élément [ItemId](https://msdn.microsoft.com/library/3350b597-57a0-4961-8f44-8624946719b4%28Office.15%29.aspx) du nouveau message. 
  
Pour découvrir comment créer un élément de réunion ou de rendez-vous à l’aide d’EWS, voir [Créer des rendez-vous et des réunions à l’aide d’EWS dans Exchange 2013](how-to-create-appointments-and-meetings-by-using-ews-in-exchange-2013.md).
  
## <a name="get-an-item-by-using-the-ews-managed-api"></a>Obtention d’un élément à l’aide de l’API managée EWS
<a name="bk_getewsma"> </a>

Pour utiliser l’API Managée EWS afin de récupérer un élément dont vous connaissez l’[Item.Id](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.item.id%28v=exchg.80%29.aspx), il vous suffit d’appeler simplement une des méthodes[Bind](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.item.bind%28v=exchg.80%29.aspx)sur l’élément et l’élément est récupéré. Pour une expérience optimale, nous vous recommandons de limiter les propriétés renvoyées à celles qui sont requises. Cet exemple renvoie la propriété **Id**de l’élément et la propriété** de l’objet**. 
  
Cet exemple suppose que le **service** est un objet[ExchangeService](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.exchangeservice%28v=exchg.80%29.aspx) valide et que l’utilisateur a bien été authentifié pour un serveur Exchange. La variable localeitemId est l’[Id de l’élément à mettre à jour. 
  
```cs
// As a best practice, limit the properties returned to only those that are required.
PropertySet propSet = new PropertySet(BasePropertySet.IdOnly, ItemSchema.Subject);
// Bind to the existing item by using the ItemId.
// This method call results in a GetItem call to EWS.
Item item = Item.Bind(service, itemId, propSet);

```

Si vous recherchez un élément qui répond à des critères spécifiques, procédez comme suit :
  
1. Établissez une liaison vers le dossier qui contient les éléments à obtenir.
    
2. Instanciez un[SearchFilter.SearchFilterCollection](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.searchfilter.searchfiltercollection%28v=exchg.80%29.aspx) ou un [PropertySet](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.propertyset%28v=exchg.80%29.aspx) pour filtrer les éléments à retenir. 
    
3. Instanciez un objet[ItemView](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.itemview%28v=EXCHG.80%29.aspx) ou [CalendarView](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.calendarview%28v=exchg.80%29.aspx)afin de spécifier le nombre d’éléments à retenir. 
    
4. Appelez la méthode[ExchangeService.FindItems](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.exchangeservice.finditems%28v=exchg.80%29.aspx) ou [ExchangeService.FindAppointments](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.exchangeservice.findappointments%28v=exchg.80%29.aspx). 
    
Par exemple, si vous souhaitez récupérer des messages électroniques non lus dans la boîte de réception, vous pouvez utiliser le code de l’exemple suivant. Cet exemple utilise un élément **SearchFilterCollection**pour limiter les résultats de la méthode**FindItems aux messages** non lus et limite l’élément**ItemView** afin de réduire les résultats à un seul élément. Ce code particulier fonctionne uniquement sur les objets[EmailMessage](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage%28v=exchg.80%29.aspx), car la valeur [EmailMessageSchema.IsRead](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessageschema.isread%28v=exchg.80%29.aspx) fait partie de la **SearchFilter**. 
  
```cs
// Bind the Inbox folder to the service object.
Folder inbox = Folder.Bind(service, WellKnownFolderName.Inbox);
// The search filter to get unread email.
SearchFilter sf = new SearchFilter.SearchFilterCollection(LogicalOperator.And, new SearchFilter.IsEqualTo(EmailMessageSchema.IsRead, false));
ItemView view = new ItemView(1);
// Fire the query for the unread items.
// This method call results in a FindItem call to EWS.
FindItemsResults<Item> findResults = service.FindItems(WellKnownFolderName.Inbox, sf, view);
```

Parallèlement, vous pouvez également utiliser un[PropertySet](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.item.bind%28v=exchg.80%29.aspx) pour limiter les résultats de la recherche, comme illustré dans l’exemple de code suivant. Cet exemple utilise la méthode[FindAppointments](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.exchangeservice.findappointments%28v=exchg.80%29.aspx)afin de récupérer un maximum de cinq rendez-vous qui se produisent dans les 30 jours suivants. Bien sûr, ce code fonctionne uniquement pour les éléments du calendrier. 
  
```cs
// Initialize values for the start and end times, and the number of appointments to retrieve.
DateTime startDate = DateTime.Now;
DateTime endDate = startDate.AddDays(30);
const int NUM_APPTS = 5;
// Bind the Calendar folder to the service object.
// This method call results in a GetFolder call to EWS.
CalendarFolder calendar = CalendarFolder.Bind(service, WellKnownFolderName.Calendar, new PropertySet());
// Set the start and end time and number of appointments to retrieve.
CalendarView cView = new CalendarView(startDate, endDate, NUM_APPTS);
// Limit the properties returned to the appointment's subject, start time, and end time.
cView.PropertySet = new PropertySet(AppointmentSchema.Subject, AppointmentSchema.Start, AppointmentSchema.End);
// Retrieve a collection of appointments by using the calendar view.
// This method call results in a FindAppointments call to EWS.
FindItemsResults<Appointment> appointments = calendar.FindAppointments(cView);
```

Notez que les informations que le serveur renvoie dans la réponse de la méthode **Bind** sont différentes des informations que le serveur renvoie pour une réponse de la méthode**FindItem** ou**FindAppointment**. La méthode**Bind** peut renvoyer toutes les propriétés schématisées, alors que les méthodes**FindItem**et**FindAppointment**ne les renvoient pas. Par conséquent, si vous avez besoin d’un accès complet à l’élément, vous devez utiliser la méthode**Bind**. Si vous ne disposez pas de l’élément **Id**de l’élément que vous souhaitez récupérer, utilisez les méthodes**FindItem** ou **FindAppointment**pour récupérer l’identité, puis utilisez la méthode **Bind **pour récupérer les propriétés dont vous avez besoin. 
  
Pour découvrir comment obtenir un élément de réunion ou de rendez-vous à l’aide de l’API managée EWS, voir[Obtenir des rendez-vous et des réunions à l’aide d’EWS dans Exchange](how-to-get-appointments-and-meetings-by-using-ews-in-exchange.md).
  
## <a name="get-an-item-by-using-ews"></a>Obtention d’un élément à l’aide d’EWS
<a name="bk_getews"> </a>

Si vous connaissez l’[ItemId](https://msdn.microsoft.com/library/3350b597-57a0-4961-8f44-8624946719b4%28Office.15%29.aspx) de l’élément à récupérer, vous pouvez obtenir ce dernier à l’aide de l’opération [GetItem](https://msdn.microsoft.com/library/e3590b8b-c2a7-4dad-a014-6360197b68e4%28Office.15%29.aspx). 
  
L’exemple suivant présente la requête XML permettant d’obtenir l’[objet](https://msdn.microsoft.com/library/c140d6c2-deb1-4f67-a908-9397197c4ae7%28Office.15%29.aspx) d’un élément comportant un **ItemId** spécifique. Il s’agit également de la requête XML que l’API Managée EWS envoie lorsque vous appelez la méthode[Bind](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.item.bind%28v=exchg.80%29.aspx) sur un**ItemId**. Les valeurs de certains attributs et éléments ont été raccourcies pour des raisons de lisibilité.
  
```XML
<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
               xmlns:m="https://schemas.microsoft.com/exchange/services/2006/messages" 
               xmlns:t="https://schemas.microsoft.com/exchange/services/2006/types" 
               xmlns:soap="https://schemas.xmlsoap.org/soap/envelope/">
  <soap:Header>
    <t:RequestServerVersion Version="Exchange2013" />
  </soap:Header>
  <soap:Body>
    <m:GetItem>
      <m:ItemShape>
        <t:BaseShape>IdOnly</t:BaseShape>
        <t:AdditionalProperties>
          <t:FieldURI FieldURI="item:Subject" />
        </t:AdditionalProperties>
      </m:ItemShape>
      <m:ItemIds>
        <t:ItemId Id="GJc/NAAA=" />
      </m:ItemIds>
    </m:GetItem>
  </soap:Body>
</soap:Envelope>
```

L’exemple suivant présente la réponse XML que le serveur renvoie après avoir effectué l’opération **GetItem**. La réponse indique que l’élément a été récupéré. Les valeurs de certains attributs et éléments ont été raccourcies pour des raisons de lisibilité. 
  
```XML
<?xml version="1.0" encoding="utf-8"?>
<s:Envelope xmlns:s="https://schemas.xmlsoap.org/soap/envelope/">
  <s:Header>
    <h:ServerVersionInfo MajorVersion="15" 
                         MinorVersion="0" 
                         MajorBuildNumber="815" 
                         MinorBuildNumber="6" 
                         Version="V2_7" 
                         xmlns:h="https://schemas.microsoft.com/exchange/services/2006/types" 
                         xmlns="https://schemas.microsoft.com/exchange/services/2006/types" 
                         xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
                         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"/>
  </s:Header>
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
          xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    <m:GetItemResponse xmlns:m="https://schemas.microsoft.com/exchange/services/2006/messages" 
                       xmlns:t="https://schemas.microsoft.com/exchange/services/2006/types">
      <m:ResponseMessages>
        <m:GetItemResponseMessage ResponseClass="Success">
          <m:ResponseCode>NoError</m:ResponseCode>
          <m:Items>
            <t:Message>
              <t:ItemId Id="GJc/NAAA=" ChangeKey="CQAAABYAAAAPxolXAHv3TaHUnjW8wWqXAAAGJd9Z"/>
              <t:Subject>Company Soccer Team</t:Subject>
            </t:Message>
          </m:Items>
        </m:GetItemResponseMessage>
      </m:ResponseMessages>
    </m:GetItemResponse>
  </s:Body>
</s:Envelope>
```

Si vous ne connaissez pas l’élément **ItemId** de l’élément que vous souhaitez récupérer, vous pouvez utiliser l’opération[FindItem](https://msdn.microsoft.com/library/ebad6aae-16e7-44de-ae63-a95b24539729%28Office.15%29.aspx) à cette fin. Pour pouvoir utiliser l’opération**FindItem**, vous devez d’abord identifier le dossier que vous recherchez. Vous pouvez identifier le dossier à l’aide de son **DistinguinguishedFolderName** ou à l’aide de l’élément [FolderId](https://msdn.microsoft.com/library/00d14e3e-4365-4f21-8f88-eaeea73b9bf7%28Office.15%29.aspx). Vous pouvez utiliser soit l’opération [FindFolder](https://msdn.microsoft.com/library/7a9855aa-06cc-45ba-ad2a-645c15b7d031%28Office.15%29.aspx) soit l’opération[SyncFolderHierarchy](https://msdn.microsoft.com/library/b31916b1-bc6c-4451-a475-b7c5417f752d%28Office.15%29.aspx) pour obtenir l’élément **FolderId** dont vous avez besoin. Ensuite, utilisez l’opération**FindItem** pour rechercher ce dossier et pour obtenir des résultats qui correspondent au filtre de recherche. Contrairement à l’API managée EWS, EWS n’offre pas d’opération de recherche distincte pour les rendez-vous. L’opération** FindItem**récupère des éléments de tous types. 
  
L’exemple suivant présente la demande d’opération **FindItem** XML qui est envoyée au serveur pour rechercher des rendez-vous prévus dans les 30 jours, dans le dossier de calendrier. Les valeurs de certains attributs et éléments ont été raccourcies pour des raisons de lisibilité. 
  
```XML
<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
               xmlns:m="https://schemas.microsoft.com/exchange/services/2006/messages"
               xmlns:t="https://schemas.microsoft.com/exchange/services/2006/types"
               xmlns:soap="https://schemas.xmlsoap.org/soap/envelope/">
  <soap:Header>
    <t:RequestServerVersion Version="Exchange2007_SP1" />
  </soap:Header>
  <soap:Body>
    <m:FindItem Traversal="Shallow">
      <m:ItemShape>
        <t:BaseShape>IdOnly</t:BaseShape>
        <t:AdditionalProperties>
          <t:FieldURI FieldURI="item:Subject" />
          <t:FieldURI FieldURI="calendar:Start" />
          <t:FieldURI FieldURI="calendar:End" />
        </t:AdditionalProperties>
      </m:ItemShape>
      <m:CalendarView MaxEntriesReturned="5" StartDate="2013-10-16T17:04:28.722Z" EndDate="2013-11-15T18:04:28.722Z" />
      <m:ParentFolderIds>
        <t:FolderId Id="AAAEOAAA=" ChangeKey="AgAAABYAAAAqRr3mNdNMSasqx/o9J13UAAAAAAA3" />
      </m:ParentFolderIds>
    </m:FindItem>
  </soap:Body>
</soap:Envelope>
```

Le serveur répond à la demande **FindItem** avec un message [FindItemResponse](https://msdn.microsoft.com/library/c8b316df-d4ab-49b8-96d4-8e9a016730ef%28Office.15%29.aspx) comprenant la valeur [ResponseCode](https://msdn.microsoft.com/library/4b84d670-74c9-4d6d-84e7-f0a9f76f0d93%28Office.15%29.aspx) de l’élément **NoError**, qui indique que l’opération a abouti. Si des éléments de calendrier répondent à des critères de filtre, ils sont inclus dans la réponse.
  
Notez que les informations que le serveur renvoie dans la réponse de l’opération **GetItem** sont différentes des informations que le serveur renvoie dans une réponse de l’opération**FindItem** ou **FindAppointment**. L’opération**GetItem** peut renvoyer toutes les propriétés schématisées, alors que les opérations**FindItem**et**FindAppointment**ne les renvoient pas. Par conséquent, si vous avez besoin d’un accès complet à l’élément, vous devez utiliser l’opération **GetItem**. Si vous ne disposez pas de l’**ItemId**de l’élément que vous souhaitez récupérer, utilisez les opérations**FindItem** ou **FindAppointment**pour récupérer l’**ItemId**, puis utilisez l’opération**GetItem**pour récupérer les éléments dont vous avez besoin. 
  
Pour découvrir comment obtenir un élément de réunion ou de rendez-vous à l’aide d’EWS, voir [Obtenir des rendez-vous et des réunions à l’aide d’EWS dans Exchange](how-to-get-appointments-and-meetings-by-using-ews-in-exchange.md).
  
## <a name="update-an-item-by-using-the-ews-managed-api"></a>Mise à jour d’un élément à l’aide de l’API managée EWS
<a name="bk_updateewsma"> </a>

Les étapes pour mettre à jour un élément à l’aide de l’API managée EWS sont similaires pour tous les types d’éléments. Toutefois, les propriétés sont différentes pour chaque type d’élément et la méthode [de Mise à jour](https://msdn.microsoft.com/library/office/dd635915%28v=exchg.80%29.aspx)présente de nombreuses méthodes surchargées parmi lesquelles faire votre choix. Pour mettre à jour un élément, procédez comme suit : 
  
1. Utilisez la méthode[Bind](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.item.bind%28v=exchg.80%29.aspx) pour obtenir la dernière version de l’élément, sauf si vous la possédez déjà. Pour mettre à jour des propriétés propres à un élément fortement identifié, vous devez établir une liaison avec ce type d’élément. Pour mettre à jour des propriétés disponibles sur le type d’élément générique, vous pouvez établir une liaison avec l’objet de l’[élément](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.item%28v=exchg.80%29.aspx). 
    
2. Mettez à jour les propriétés sur l’élément.
    
3. Appelez la méthode de**mise à jour**. 
    
Par exemple, vous pouvez mettre à jour l’objet d’un message électronique à l’aide du type d’élément générique, comme illustré dans le code de l’exemple suivant.
  
Cet exemple suppose que le **service** est un objet[ExchangeService](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.exchangeservice%28v=exchg.80%29.aspx) valide et que l’utilisateur a bien été authentifié pour un serveur Exchange. La variable localeitemId est l’[Id de l’élément à mettre à jour. 
  
```cs
// Bind to the existing item, using the ItemId.
// This method call results in a GetItem call to EWS.
Item item = Item.Bind(service, itemId);
// Update the Subject of the email.
item.Subject = "New subject";
// Save the updated email.
// This method call results in an UpdateItem call to EWS.
item.Update(ConflictResolutionMode.AlwaysOverwrite);
```

Pour découvrir comment mettre à jour un élément de réunion ou de rendez-vous à l’aide de l’API managée EWS, voir [ Mettre à jour des rendez-vous et des réunions à l’aide d’EWS dans Exchange](how-to-update-appointments-and-meetings-by-using-ews-in-exchange.md).
  
## <a name="update-an-item-by-using-ews"></a>Mise à jour d’un élément à l’aide d’EWS
<a name="bk_updateews"> </a>

Pour mettre à jour un élément à l’aide d’EWS, procédez comme suit :
  
1. Utilisez l’opération [GetItem](https://msdn.microsoft.com/library/e3590b8b-c2a7-4dad-a014-6360197b68e4%28Office.15%29.aspx) pour obtenir la dernière version de l’élément, sauf si vous la possédez déjà. 
    
2. Utilisez l’opération [UpdateItem](https://msdn.microsoft.com/library/5d027523-e0bc-4da2-b60b-0cb9fc1fdfe4%28Office.15%29.aspx) afin de spécifier des champs à mettre à jour et d’affecter de nouvelles valeurs à ces champs. 
    
L’exemple suivant présente la demande d’opération **UpdateItem** XML qui est envoyée au serveur pour mettre à jour l’[objet](https://msdn.microsoft.com/library/c140d6c2-deb1-4f67-a908-9397197c4ae7%28Office.15%29.aspx) du message électronique. Les valeurs de certains attributs et éléments ont été raccourcies pour des raisons de lisibilité. 
  
```XML
<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:m="https://schemas.microsoft.com/exchange/services/2006/messages" xmlns:t="https://schemas.microsoft.com/exchange/services/2006/types" xmlns:soap="https://schemas.xmlsoap.org/soap/envelope/">
  <soap:Header>
    <t:RequestServerVersion Version="Exchange2010_SP1" />
  </soap:Header>
  <soap:Body>
    <m:UpdateItem MessageDisposition="SaveOnly" ConflictResolution="AlwaysOverwrite">
      <m:ItemChanges>
        <t:ItemChange>
          <t:ItemId Id="APdZjAAA=" ChangeKey="CQAAABYAAAAqRr3mNdNMSasqx/o9J13UAAAAPdgr" />
          <t:Updates>
            <t:SetItemField>
              <t:FieldURI FieldURI="item:Subject" />
              <t:Message>
                <t:Subject>New subject</t:Subject>
              </t:Message>
            </t:SetItemField>
          </t:Updates>
        </t:ItemChange>
      </m:ItemChanges>
    </m:UpdateItem>
  </soap:Body>
</soap:Envelope>
```

Le serveur répond à la requête **UpdateItem** par un message [UpdateItemResponse](https://msdn.microsoft.com/library/023b79b4-c675-4669-9112-d85499ec4fc4%28Office.15%29.aspx) comprenant la valeur [ResponseCode](https://msdn.microsoft.com/library/aa580757%28v=exchg.150%29.aspx) de **NoError**, qui indique que l’élément a été mis à jour avec succès.
  
Pour découvrir comment mettre à jour un élément de réunion ou de rendez-vous à l’aide d’EWS, voir[Mettre à jour des rendez-vous et des réunions à l’aide d’EWS in Exchange](how-to-update-appointments-and-meetings-by-using-ews-in-exchange.md).
  
## <a name="delete-an-item-by-using-the-ews-managed-api"></a>Suppression d’un élément à l’aide de l’API managée EWS
<a name="bk_deleteewsma"> </a>

Vous pouvez supprimer des éléments en les déplaçant vers le dossier Éléments supprimés ou en les envoyant dans la corbeille. Si vous connaissez l’[ItemId](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.item.id%28v=exchg.80%29.aspx) de l’élément à supprimer, appelez simplement la méthode[Supprimer](https://msdn.microsoft.com/library/office/dd635072%28v=exchg.80%29.aspx)sur l’élément. 
  
Si vous devez rechercher l’élément avant de le supprimer, procédez comme suit :
  
1. Appelez la méthode [FindItems](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.exchangeservice.finditems%28v=exchg.80%29.aspx) ou [FindAppointments](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.exchangeservice.findappointments%28v=exchg.80%29.aspx)pour rechercher l’élément à supprimer. 
    
1. Instanciez un[PropertySet](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.propertyset%28v=exchg.80%29.aspx)et limitez-le aux propriétés à renvoyer, ou utilisez un[SearchFilterCollection](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.searchfilter.searchfiltercollection%28v=exchg.80%29.aspx)pour rechercher des éléments spécifiques. 
    
2. Instanciez un objet[ItemView](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.itemview%28v=EXCHG.80%29.aspx) ou[CalendarView](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.calendarview%28v=exchg.80%29.aspx)afin de spécifier le nombre d’éléments à retenir.  
    
2. Appelez la méthode[supprimer](https://msdn.microsoft.com/library/office/dd635072%28v=exchg.80%29.aspx). 
    
Par exemple, le code suivant indique comment déplacer un message électronique vers le dossier Éléments supprimés.
  
Cet exemple suppose que le **service** est un objet[ExchangeService](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.exchangeservice%28v=exchg.80%29.aspx) valide et que l’utilisateur a bien été authentifié pour un serveur Exchange. La variable localeitemId est l’[Id de l’élément à mettre à jour. 
  
```cs
// Bind to the existing item, using the ItemId.
// This method call results in a GetItem call to EWS.
Item item = Item.Bind(service, itemId);
// Delete the item by moving it to the Deleted Items folder.
// This method call results in a DeleteItem call to EWS.
item.Delete(DeleteMode.MoveToDeletedItems);
```

Pour plus d’informations sur la suppression d’éléments, voir [Supprimer les éléments à l’aide d’EWS dans Exchange](deleting-items-by-using-ews-in-exchange.md). Pour découvrir comment supprimer un élément de réunion ou de rendez-vous à l’aide de l’API managée EWS, voir [ Supprimer des rendez-vous et annuler des réunions à l’aide d’EWS dans Exchange](how-to-delete-appointments-and-cancel-meetings-by-using-ews-in-exchange.md).
  
## <a name="delete-an-item-by-using-ews"></a>Suppression d’un élément à l’aide d’EWS
<a name="bk_deleteews"> </a>

Vous pouvez supprimer un élément à l’aide de l’opération [DeleteItem](../web-service-reference/deleteitem-operation.md). 
  
L’exemple suivant présente la demande XML qui est envoyée au serveur pour déplacer le message vers le dossier Éléments supprimés. Les valeurs de certains attributs et éléments ont été raccourcies pour des raisons de lisibilité.
  
```XML
<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:m="https://schemas.microsoft.com/exchange/services/2006/messages" xmlns:t="https://schemas.microsoft.com/exchange/services/2006/types" xmlns:soap="https://schemas.xmlsoap.org/soap/envelope/">
  <soap:Header>
    <t:RequestServerVersion Version="Exchange2010_SP1" />
  </soap:Header>
  <soap:Body>
    <m:DeleteItem DeleteType="MoveToDeletedItems">
      <m:ItemIds>
        <t:ItemId Id="APdZjAAA=" ChangeKey="CQAAABYAAAAqRr3mNdNMSasqx/o9J13UAAANIFzC" />
      </m:ItemIds>
    </m:DeleteItem>
  </soap:Body>
</soap:Envelope>
```

Le serveur répond à la requête **UpdateItem** par un message [UpdateItemResponse](https://msdn.microsoft.com/library/86463d66-fe47-4a19-a81b-e24841e816ab%28Office.15%29.aspx) comprenant la valeur [ResponseCode](https://msdn.microsoft.com/library/aa580757%28v=exchg.150%29.aspx) de **NoError**, qui indique que l’élément a été supprimé avec succès.
  
Pour plus d’informations sur la suppression d’éléments, voir [Supprimer les éléments à l’aide d’EWS dans Exchange](deleting-items-by-using-ews-in-exchange.md). Pour découvrir comment supprimer un élément de réunion ou de rendez-vous à l’aide d’EWS, voir [ Supprimer des rendez-vous et annuler des réunions à l’aide d’EWS dans Exchange](how-to-delete-appointments-and-cancel-meetings-by-using-ews-in-exchange.md).
  
## <a name="move-or-copy-items-to-another-mailbox"></a>Déplacement ou copie d’éléments vers une autre boîte aux lettres
<a name="bk_movecopybtnmailboxes"> </a>

Vous pouvez déplacer ou copier des éléments d’une boîte aux lettres vers une autre à l’aide des opérations [ExportItems](https://msdn.microsoft.com/library/e2846abb-0b16-4732-bbd8-038a674672f6%28Office.15%29.aspx) et [UploadItems](https://msdn.microsoft.com/library/a88cbe99-7968-454d-a545-4f92c330909f%28Office.15%29.aspx). Pour plus d’informations, voir [Exportation et importation d’éléments à l’aide d’EWS dans Exchange](exporting-and-importing-items-by-using-ews-in-exchange.md).
  
## <a name="see-also"></a>Voir aussi

- [Dossiers et éléments dans EWS dans Exchange](folders-and-items-in-ews-in-exchange.md)    
- [Utiliser des dossiers à l’aide d’EWS dans Exchange](how-to-work-with-folders-by-using-ews-in-exchange.md)    
- [Supprimer des éléments à l’aide d’EWS dans Exchange](deleting-items-by-using-ews-in-exchange.md)
    

