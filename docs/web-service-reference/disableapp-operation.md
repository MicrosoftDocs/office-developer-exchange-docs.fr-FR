---
title: Opération DisableApp
manager: sethgros
ms.date: 09/17/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 211731a3-2470-49af-bda3-1ddfc15a8e46
description: Opération de recherche plus d’informations sur la DisableApp EWS.
ms.openlocfilehash: be9e124d7464012ffa797a69192893d85804a004
ms.sourcegitcommit: 34041125dc8c5f993b21cebfc4f8b72f0fd2cb6f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "19755940"
---
# <a name="disableapp-operation"></a>Opération DisableApp

Trouvez des informations sur l’opération EWS **DisableApp** . 
  
L’opération **DisableApp** désactive une application de messagerie pour Outlook. 
  
Cette opération est une nouveauté d’Exchange Server 2013.
  
## <a name="using-the-disableapp-operation"></a>Utilisation de l’opération DisableApp

L’opération **DisableApp** prend deux arguments qui identifient l’application de messagerie pour désactiver la demande et la raison pourquoi il a été désactivé. 
  
### <a name="disableapp-operation-soap-headers"></a>En-têtes SOAP DisableApp opération

L’opération **DisableApp** permettre utiliser les en-têtes SOAP qui sont répertoriés dans le tableau suivant. 
  
|**Nom de l'en-tête**|**Élément**|**Description**|
|:-----|:-----|:-----|
|**RequestVersion** <br/> |[RequestServerVersion](requestserverversion.md) <br/> |Identifie la version du schéma pour la requête d’opération. Cet en-tête est applicable à une demande.  <br/> |
|**ServerVersion** <br/> |[ServerVersionInfo](serverversioninfo.md) <br/> |Identifie la version du serveur qui a répondu à la demande. Cet en-tête est applicable à une réponse.  <br/> |
   
## <a name="disableapp-operation-request-example-disable-a-mail-app-installed-in-a-mailbox"></a>Exemple de requête d’opération DisableApp : désactiver une application de messagerie installée dans une boîte aux lettres

L’exemple suivant d’une opération **DisableApp** demande montre comment un désactiver une application de messagerie. Vous trouverez l’identificateur de l’application dans le manifeste d’application qui est retourné dans une réponse de [l’opération GetAppManifests](getappmanifests-operation.md) . 
  
```XML
<?xml version="1.0" encoding="UTF-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"
               xmlns:t="http://schemas.microsoft.com/exchange/services/2006/types"
               xmlns:m="http://schemas.microsoft.com/exchange/services/2006/messages">
   <soap:Header>
      <t:RequestServerVersion Version="Exchange2013" />
      <t:MailboxCulture>en-US</t:MailboxCulture>
      <t:TimeZoneContext>
         <t:TimeZoneDefinition Id="GMT Standard Time"/>
      </t:TimeZoneContext>
   </soap:Header>
   <soap:Body >
      <m:DisableApp>
         <m:ID>1C50226D-04B5-4AB2-9FCD-42E236B59E4B</m:ID>
         <m:DisableReason>NoReason</m:DisableReason>
      </m:DisableApp>
   </soap:Body>
</soap:Envelope>
```

La demande SOAP body contient les éléments suivants :
  
- [DisableApp](disableapp.md)
    
- [ID (chaîne)](id-string.md)
    
- [DisableReason](disablereason.md)
    
## <a name="successful-disableapp-operation-response"></a>Réponse d’opération DisableApp réussie

L’exemple suivant montre une réponse positive à une demande d’opération **DisableApp** pour désactiver une application de messagerie. 
  
```XML
<?xml version="1.0" encoding="utf-8"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Header>
      <h:ServerVersionInfo MajorVersion="15" 
                           MinorVersion="0" 
                           MajorBuildNumber="556" 
                           MinorBuildNumber="14" 
                           Version="Exchange2013" 
                           xmlns:h="http://schemas.microsoft.com/exchange/services/2006/types" 
                           xmlns="http://schemas.microsoft.com/exchange/services/2006/types" 
                           xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
                           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"/>
   </s:Header>
   <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
           xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <DisableAppResponse ResponseClass="Success" 
                          xmlns="http://schemas.microsoft.com/exchange/services/2006/messages">
         <ResponseCode>NoError</ResponseCode>
      </DisableAppResponse>
   </s:Body>
</s:Envelope>
```

La réponse SOAP body contient les éléments suivants :
  
- [DisableAppResponse](disableappresponse.md)
    
- [ResponseCode](responsecode.md)
    
## <a name="disableapp-operation-error-response"></a>Réponse d’erreur d’opération DisableApp

L’exemple suivant montre une réponse d’erreur à une demande d’opération **DisableApp** . Il s’agit d’une réponse à une demande pour désactiver une application de messagerie qui n’est pas installée dans une boîte aux lettres. 
  
```XML
<?xml version="1.0" encoding="utf-8"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Header>
      <h:ServerVersionInfo MajorVersion="15" MinorVersion="0" MajorBuildNumber="556" MinorBuildNumber="14" Version="Exchange2013" xmlns:h="http://schemas.microsoft.com/exchange/services/2006/types" xmlns="http://schemas.microsoft.com/exchange/services/2006/types" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"/>
   </s:Header>
   <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <DisableAppResponse ResponseClass="Error" xmlns="http://schemas.microsoft.com/exchange/services/2006/messages">
         <MessageText>Extension ID 1C50226D-04B5-4AB2-9FCD-42E236B59E4A can't be found.</MessageText>
         <ResponseCode>ErrorExtensionNotFound</ResponseCode>
         <DescriptiveLinkKey>0</DescriptiveLinkKey>
      </DisableAppResponse>
   </s:Body>
</s:Envelope>
```

La réponse d’erreur corps SOAP contient les éléments suivants :
  
- [DisableAppResponse](disableappresponse.md)
    
- [MessageText](messagetext.md)
    
- [ResponseCode](responsecode.md)
    
- [DescriptiveLinkKey](descriptivelinkkey.md)
    
Pour les codes d’erreur générique à EWS, spécifiques à cette opération, consultez la rubrique [ResponseCode](responsecode.md).
  
## <a name="see-also"></a>Voir aussi

- [Opérations EWS dans Exchange](ews-operations-in-exchange.md)   
- [Opération InstallApp](installapp-operation.md)   
- [Opération UninstallApp](uninstallapp-operation.md)   
- [GetAppManifests](getappmanifests.md)   
- [Opération GetAppMarketplaceUrl](getappmarketplaceurl-operation.md)   
- [Compléments Outlook](http://msdn.microsoft.com/library/71e64bc9-e347-4f5d-8948-0a47b5dd93e6%28Office.15%29.aspx)
    
