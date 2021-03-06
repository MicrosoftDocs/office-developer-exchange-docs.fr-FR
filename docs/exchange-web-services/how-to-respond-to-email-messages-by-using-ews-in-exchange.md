---
title: Répondre à des messages électroniques à l’aide d’EWS dans Exchange
manager: sethgros
ms.date: 09/17/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: 9d584991-4d67-4d36-ae2f-99970af8488f
description: Découvrez comment répondre aux messages électroniques à l’aide de l’API managée EWS ou EWS dans Exchange.
ms.openlocfilehash: 81599051f603654cdf8a50b789b37d7e76664a53
ms.sourcegitcommit: 88ec988f2bb67c1866d06b361615f3674a24e795
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "44455708"
---
# <a name="respond-to-email-messages-by-using-ews-in-exchange"></a>Répondre à des messages électroniques à l’aide d’EWS dans Exchange

Découvrez comment répondre aux messages électroniques à l’aide de l’API managée EWS ou EWS dans Exchange.
  
Vous pouvez utiliser l’API managée EWS ou EWS pour répondre aux messages en y répondant ou en les transférant à des destinataires.
  
**Tableau 1. Méthodes de l’API managée EWS et opérations EWS pour répondre aux messages électroniques**

|**Tâche**|**Méthode d'API managée EWS**|**Opération EWS**|
|:-----|:-----|:-----|
|Répondre à un message électronique  <br/> |[EmailMessage. Reply](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage.reply%28v=exchg.80%29.aspx) <br/> [EmailMessage. CreateReply](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage.createreply%28v=exchg.80%29.aspx) <br/> |[CreateItem](https://msdn.microsoft.com/library/fe6bb7fc-8918-4e6e-b0a1-b7e0ef44c3d1%28Office.15%29.aspx), où l’élément [Items](https://msdn.microsoft.com/library/d61ef1cc-ddfc-480a-9625-7b436cb33ae0%28Office.15%29.aspx) a un élément enfant de [ReplyToItem](https://msdn.microsoft.com/library/35ee751a-41c0-4216-ad8b-78f7ada43a2f%28Office.15%29.aspx) ou [ReplyAllToItem](https://msdn.microsoft.com/library/8ca970ca-ca73-40db-9233-7b271cc5f44f%28Office.15%29.aspx).  <br/> |
|Transférer un message électronique  <br/> |[EmailMessage. Forward](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage.forward%28v=exchg.80%29.aspx) <br/> [EmailMessage. CreateForward](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage.createforward%28v=exchg.80%29.aspx) <br/> |[CreateItem](https://msdn.microsoft.com/library/fe6bb7fc-8918-4e6e-b0a1-b7e0ef44c3d1%28Office.15%29.aspx), où l’élément [Items](https://msdn.microsoft.com/library/d61ef1cc-ddfc-480a-9625-7b436cb33ae0%28Office.15%29.aspx) a un élément enfant de [ForwardItem](https://msdn.microsoft.com/library/97786086-8b91-4471-8af8-d21e8d66de87%28Office.15%29.aspx).  <br/> |
   
## <a name="reply-to-an-email-message-by-using-the-ews-managed-api"></a>Répondre à un message électronique à l’aide de l’API managée EWS
<a name="bk_replyewsma"> </a>

L’API managée EWS fournit deux méthodes que vous pouvez utiliser pour répondre aux messages : [reply](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage.reply%28v=exchg.80%29.aspx) et [CreateReply](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage.createreply%28v=exchg.80%29.aspx). La méthode **reply** prend seulement deux paramètres : le message de réponse à ajouter au corps existant et une valeur **booléenne** qui indique si la réponse doit être envoyée à tous les destinataires (true) ou uniquement à l’expéditeur (false). Si vous avez besoin d’ajouter des destinataires à un message, de définir des propriétés supplémentaires sur une réponse ou d’ajouter une pièce jointe, utilisez la méthode **CreateReply** , qui vous permet de définir toutes les [Propriétés de première classe](email-properties-and-elements-in-ews-in-exchange.md) disponibles sur un objet [EmailMessage](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage%28v=exchg.80%29.aspx) . 
  
L’exemple de code suivant montre comment utiliser la méthode **reply** pour répondre à un message électronique. 
  
Cet exemple suppose que le **service** est un objet[ExchangeService](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.exchangeservice%28v=exchg.80%29.aspx) valide et que l’utilisateur a bien été authentifié pour un serveur Exchange. La variable locale *ItemId* est l' [ID](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.item.id%28v=exchg.80%29.aspx) de l’élément auquel répondre. L’exemple appelle la [méthode FindRecentlySent](#bk_findlast) pour vérifier que le message a été marqué comme ayant répondu à. 
  
```cs
// As a best practice, limit the properties returned by the Bind method to only those that are required.
PropertySet propSet = new PropertySet(BasePropertySet.IdOnly, ItemSchema.LastModifiedTime);
// Bind to the email message to reply to by using the ItemId.
// This method call results in a GetItem call to EWS.
EmailMessage message = EmailMessage.Bind(service, ItemId, propSet);
string myReply = "This is the message body of the email reply.";
bool replyToAll = false;
// Send the response message.
// This method call results in a CreateItem call to EWS.
message.Reply(myReply, replyToAll);
// Verify that the response was sent by calling FindRecentlySent.
FindRecentlySent(message);
```

L’exemple de code suivant montre comment utiliser la méthode **CreateReply** pour répondre à un message électronique. 
  
```cs
// Bind to the email message to reply to by using the ItemId.
// This method call results in a GetItem call to EWS.
EmailMessage message = EmailMessage.Bind(service, ItemId, BasePropertySet.IdOnly);
// Create the reply response message from the original email message.
// Indicate whether the message is a reply or reply all type of reply.
bool replyToAll = true;
ResponseMessage responseMessage = message.CreateReply(replyToAll);
// Prepend the reply to the message body. 
string myReply = "This is the message body of the email reply.";
responseMessage.BodyPrefix = myReply;
// Send the response message.
// This method call results in a CreateItem call to EWS.
responseMessage.SendAndSaveCopy();
// Check that the response was sent by calling FindRecentlySent.
FindRecentlySent(message);
```

Si vous devez ajouter une pièce jointe au message de réponse, remplacez l’appel à la méthode **méthodesendandsavecopy** par le code suivant. 
  
```cs
EmailMessage reply = responseMessage.Save();
reply.Attachments.AddFileAttachment("attachmentname.txt");
reply.Update(ConflictResolutionMode.AutoResolve);
reply.SendAndSaveCopy();
```

## <a name="reply-to-an-email-message-by-using-ews"></a>Répondre à un message électronique à l’aide d’EWS
<a name="bk_replyews"> </a>

L’exemple de code suivant montre comment répondre à un message à l’aide d’EWS. Utilisez l’opération [CreateItem](https://msdn.microsoft.com/library/fe6bb7fc-8918-4e6e-b0a1-b7e0ef44c3d1%28Office.15%29.aspx) avec l’attribut **MessageDisposition** défini sur **méthodesendandsavecopy** pour envoyer le message et enregistrer la réponse dans le dossier éléments envoyés. Incluez l’élément [ReplyAllToItem](https://msdn.microsoft.com/library/8ca970ca-ca73-40db-9233-7b271cc5f44f%28Office.15%29.aspx) en tant qu’enfant de l’élément [Items](https://msdn.microsoft.com/library/d61ef1cc-ddfc-480a-9625-7b436cb33ae0%28Office.15%29.aspx) pour répondre à tout le monde sur le thread de message ou incluez l’élément [ReplyToItem](https://msdn.microsoft.com/library/35ee751a-41c0-4216-ad8b-78f7ada43a2f%28Office.15%29.aspx) pour répondre uniquement à l’expéditeur. 
  
Il s’agit également de la demande XML que l’API managée EWS envoie lors de l’appel de la méthode [reply](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage.reply%28v=exchg.80%29.aspx) ou [CreateReply](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage.createreply%28v=exchg.80%29.aspx) . 
  
```XML
<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
               xmlns:m="https://schemas.microsoft.com/exchange/services/2006/messages"
               xmlns:t="https://schemas.microsoft.com/exchange/services/2006/types"
               xmlns:soap="https://schemas.xmlsoap.org/soap/envelope/">
  <soap:Header>
    <t:RequestServerVersion Version=" Exchange2007_SP1" />
  </soap:Header>
  <soap:Body>
    <m:CreateItem MessageDisposition="SendAndSaveCopy">
      <m:Items>
        <t:ReplyAllToItem>
          <t:ReferenceItemId Id="AAMkADE4="
                             ChangeKey="CQAAABYA" />
          <t:NewBodyContent BodyType="HTML">This is the message body of the email reply.</t:NewBodyContent>
        </t:ReplyAllToItem>
      </m:Items>
    </m:CreateItem>
  </soap:Body>
</soap:Envelope>
```

Le serveur répond à la demande **CreateItem** avec un message [CreateItemResponse](https://msdn.microsoft.com/library/742a46a0-2475-45a0-b44f-90639a3f5a43%28Office.15%29.aspx) qui inclut la valeur d’élément [ResponseCode](https://msdn.microsoft.com/library/4b84d670-74c9-4d6d-84e7-f0a9f76f0d93%28Office.15%29.aspx) **NOERROR**, ce qui indique que la réponse a été créée et envoyée.
  
Si vous devez ajouter une pièce jointe à votre message de réponse, appelez l’opération **CreateItem** comme indiqué ci-dessus, mais remplacez **MessageDisposition** par **SaveOnly**. Appelez ensuite l’opération [CreateAttachment](https://msdn.microsoft.com/library/e066db95-6963-4507-a8d0-8efad287f550%28Office.15%29.aspx) , suivie de l’opération [SendItem](https://msdn.microsoft.com/library/337b89ef-e1b7-45ed-92f3-8abe4200e4c7%28Office.15%29.aspx) . 
  
## <a name="forward-an-email-message-by-using-the-ews-managed-api"></a>Transférer un message électronique à l’aide de l’API managée EWS
<a name="bk_forwardewsma"> </a>

L’API managée EWS fournit deux méthodes que vous pouvez utiliser pour transférer des messages : [Forward](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage.forward%28v=exchg.80%29.aspx) et [CreateForward](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage.createforward%28v=exchg.80%29.aspx). La méthode **Forward** ne prend que deux paramètres : le message à ajouter au corps existant, ainsi qu’un tableau ou une collection de destinataires, en fonction de la surcharge que vous choisissez d’utiliser. Si vous devez ajouter une pièce jointe au message que vous transférez ou définir des propriétés supplémentaires sur le nouveau message, utilisez la méthode **CreateForward** , qui vous permet de définir toutes les propriétés disponibles sur un objet [EmailMessage](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage%28v=exchg.80%29.aspx) . 
  
L’exemple de code suivant montre comment utiliser la méthode **Forward** pour transférer un message électronique à un destinataire. 
  
Cet exemple suppose que le **service** est un objet[ExchangeService](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.exchangeservice%28v=exchg.80%29.aspx) valide et que l’utilisateur a bien été authentifié pour un serveur Exchange. La variable locale *ItemId* est l' [ID](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.item.id%28v=exchg.80%29.aspx) de l’élément à transférer. L’exemple appelle la [méthode FindRecentlySent](#bk_findlast) pour vérifier que le message a été marqué comme transféré. 
  
```cs
// Bind to the email message to reply to by using the ItemId.
// This method call results in a GetItem call to EWS.
EmailMessage message = EmailMessage.Bind(service, ItemId, BasePropertySet.IdOnly);
string myForward = "This is the message body of the forwarded email.";
// Send the response message.
// This method call results in a CreateItem call to EWS.
message.Forward(myForward, "sadie@contoso.com");
// Verify that the forwarded response was sent by calling FindRecentlySent.
FindRecentlySent(message);
```

L’exemple de code suivant montre comment utiliser la méthode **CreateForward** pour transférer un message électronique à un destinataire. 
  
```cs
// Bind to the email message to reply to by using the ItemId.
// This method call results in a GetItem call to EWS.
EmailMessage message = EmailMessage.Bind(service, ItemId, BasePropertySet.IdOnly);
// Create the reply response message from the original email message.
// Indicate whether the message is a reply or reply all type of reply.
ResponseMessage forwardMessage = message.CreateForward();
// Set properties on the email message.
forwardMessage.ToRecipients.Add("sadie@contoso.com");
forwardMessage.Body = "Sadie,<br><br>I thought you'd be interested in this thread.<br><br>-Mack";
// Send and save a copy of the replied email message in the default Sent Items folder. 
forwardMessage.SendAndSaveCopy();
// Verify that the forwarded message was sent by calling FindRecentlySent.
FindRecentlySent(message);
```

Si vous devez ajouter une pièce jointe au message transféré, remplacez l’appel à la méthode **méthodesendandsavecopy** par le code suivant. 
  
```cs
EmailMessage forward = forwardMessage.Save();
forward.Attachments.AddFileAttachment("attachmentname.txt");
forward.Update(ConflictResolutionMode.AutoResolve);
forward.SendAndSaveCopy();
```

## <a name="forward-an-email-message-by-using-ews"></a>Transférer un message électronique à l’aide d’EWS
<a name="bk_forwardews"> </a>

L’exemple de code suivant montre comment transférer un message à l’aide d’EWS. Utilisez l’opération [CreateItem](https://msdn.microsoft.com/library/fe6bb7fc-8918-4e6e-b0a1-b7e0ef44c3d1%28Office.15%29.aspx) avec l’attribut **MessageDisposition** défini sur **méthodesendandsavecopy** pour envoyer le message et enregistrer la réponse dans le dossier éléments envoyés. L’élément [ForwardItem](https://msdn.microsoft.com/library/97786086-8b91-4471-8af8-d21e8d66de87%28Office.15%29.aspx) indique que l’élément est un message transféré. 
  
Il s’agit également de la demande XML que l’API managée EWS envoie lors de l’appel de la méthode [Forward](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage.forward%28v=exchg.80%29.aspx) ou [CreateForward](https://msdn.microsoft.com/library/microsoft.exchange.webservices.data.emailmessage.createforward%28v=exchg.80%29.aspx) . 
  
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
      <m:Items>
        <t:ForwardItem>
          <t:ToRecipients>
            <t:Mailbox>
              <t:EmailAddress>sadie@contoso.com</t:EmailAddress>
            </t:Mailbox>
          </t:ToRecipients>
          <t:ReferenceItemId Id="AAAMkADE="
                             ChangeKey="CQAAABYA" />
          <t:NewBodyContent BodyType="HTML">This is the message body of the forwarded email.</t:NewBodyContent>
        </t:ForwardItem>
      </m:Items>
    </m:CreateItem>
  </soap:Body>
</soap:Envelope>
```

Le serveur répond à la demande **CreateItem** avec un message [CreateItemResponse](https://msdn.microsoft.com/library/742a46a0-2475-45a0-b44f-90639a3f5a43%28Office.15%29.aspx) qui inclut la valeur d’élément [ResponseCode](https://msdn.microsoft.com/library/4b84d670-74c9-4d6d-84e7-f0a9f76f0d93%28Office.15%29.aspx) **NOERROR**, ce qui indique que le message transféré a été créé et envoyé avec succès.
  
Si vous devez ajouter une pièce jointe à votre message de réponse, appelez l’opération **CreateItem** , mais remplacez **MessageDisposition** par **SaveOnly**. Appelez ensuite l’opération [CreateAttachment](https://msdn.microsoft.com/library/e066db95-6963-4507-a8d0-8efad287f550%28Office.15%29.aspx) , suivie de l’opération [SendItem](https://msdn.microsoft.com/library/337b89ef-e1b7-45ed-92f3-8abe4200e4c7%28Office.15%29.aspx) . 
  
## <a name="find-the-message-last-replied-to-or-forwarded-by-using-the-ews-managed-api"></a>Rechercher la dernière réponse ou transfert d’un message à l’aide de l’API managée EWS
<a name="bk_findlast"> </a>

L’exemple de code suivant montre comment rechercher le dernier verbe exécuté et l’heure à laquelle le dernier verbe a été exécuté sur l’élément spécifié. Cette méthode est appelée à partir d’autres exemples de code d’API managée EWS de cette rubrique pour vérifier que les éléments auxquels vous avez répondu ou transférés ont été marqués comme ayant répondu à ou transférés dans votre boîte de réception. 
  
L’exemple utilise la propriété étendue [PidTagLastVerbExecuted](https://msdn.microsoft.com/library/cc841968.aspx) (0x10820003) pour déterminer si le message était une réponse, une réponse tous ou un transfert, et la propriété étendue [PidTagLastVerbExecutionTime](https://msdn.microsoft.com/library/cc839918.aspx) (0x10820040) pour déterminer à quel moment la réponse ou le transfert a été envoyé. 
  
```cs
public static void FindRecentlySent(EmailMessage messageToCheck)
{
    // Create extended property definitions for PidTagLastVerbExecuted and PidTagLastVerbExecutionTime.
    ExtendedPropertyDefinition PidTagLastVerbExecuted = new ExtendedPropertyDefinition(0x1081, MapiPropertyType.Integer);
    ExtendedPropertyDefinition PidTagLastVerbExecutionTime = new ExtendedPropertyDefinition(0x1082, MapiPropertyType.SystemTime);
    PropertySet propSet = new PropertySet(BasePropertySet.IdOnly, EmailMessageSchema.Subject, PidTagLastVerbExecutionTime, PidTagLastVerbExecuted);
    messageToCheck = EmailMessage.Bind(service, messageToCheck.Id, propSet);
    // Determine the last verb executed on the message and display output.
    object responseType;
    if (messageToCheck.TryGetProperty(PidTagLastVerbExecuted, out responseType))
    {
        object ReplyTime = null;
        switch (((Int32)responseType))
        {
            case 102: Console.WriteLine("A reply was sent to the '" + messageToCheck.Subject.ToString() + "' email message at");
                break;
            case 103: Console.WriteLine("A reply all was sent to the '" + messageToCheck.Subject.ToString() + "' email message at");
                break;
            case 104: Console.WriteLine("The '" + messageToCheck.Subject.ToString() + "' email message was forwarded at");
                break;
        }
        if (messageToCheck.TryGetProperty(PidTagLastVerbExecutionTime, out ReplyTime))
        {
            Console.WriteLine(((DateTime)ReplyTime).ToString() + ".");
        }
    }
    else
    {
        Console.WriteLine("No changes were made to  '" + messageToCheck.Subject.ToString() + "'.");
    }
}
```

## <a name="see-also"></a>Voir aussi


- [Courrier électronique et les services EWS d'Exchange](email-and-ews-in-exchange.md)
    
- [Envoyer des messages électroniques à l’aide d’EWS dans Exchange](how-to-send-email-messages-by-using-ews-in-exchange.md)
    

