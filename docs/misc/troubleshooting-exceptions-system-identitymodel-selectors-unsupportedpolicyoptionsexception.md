---
title: "Soluci&#243;n de problemas de excepciones: System.IdentityModel.Selectors.UnsupportedPolicyOptionsException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.IdentityModel.Selectors.UnsupportedPolicyOptionsException (excepción)"
  - "UnsupportedPolicyOptionsException (excepción)"
ms.assetid: 1151127d-81a1-4d87-8462-924ab9d1ee01
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.IdentityModel.Selectors.UnsupportedPolicyOptionsException
Una excepción <xref:System.IdentityModel.Selectors.UnsupportedPolicyOptionsException> indica que se ha proporcionado una directiva al sistema que incluye opciones no admitidas. Entre las restricciones que pueden producir estos errores se incluye la siguiente:  
  
 Un destinatario ha solicitado un token del servicio de token de seguridad local y ha especificado http:\/\/schemas.xmlsoap.org\/ws\/2005\/05\/identity\/issuer\/self como emisor del token. Sin embargo, uno de los requisitos especificados en la directiva no es compatible con el servicio de token de seguridad local de CardSpace. Para obtener más información, vea [A Technical Reference for the Information Card Profile V1.0](http://go.microsoft.com/fwlink/?LinkId=102401). Entre los ejemplos de opciones no compatibles se incluyen los siguientes:  
  
-   Una demanda solicitada por el destinatario no figura en la lista de demandas compatibles especificada en la sección [Supported Claim Types](http://go.microsoft.com/fwlink/?LinkId=102402) de "A Technical Reference for the Information Card Profile V1.0".  
  
-   El tipo de token no es de SAML 1.0 ni 1.1.  
  
-   Para sitios que no sean SSL, una clave no es simétrica.  
  
-   KeyWrapAlgorithm es distinto del algoritmo predeterminado.  
  
-   Se especifica en la directiva un elemento no admitido. Los elementos admitidos son los siguientes:  
  
    -   EncryptionAlgorithm  
  
    -   CanonicalizationAlgorithm  
  
    -   SignWith  
  
    -   TokenType  
  
    -   ClaimsElement  
  
    -   KeyType  
  
    -   KeySize  
  
    -   EncryptWith  
  
    -   RequestType  
  
    -   SecondaryParameters  
  
    -   KeyWrapAlgorithm  
  
-   wst:RequestType no es de tipo Issue.  
  
-   Para los tipos de claves asimétricas, un tamaño de clave no es 2048.  
  
## Vea también  
 <xref:System.IdentityModel.Selectors.UnsupportedPolicyOptionsException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)