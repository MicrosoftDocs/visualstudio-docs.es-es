---
title: "Elemento &lt;Signature&gt; (Implementaci&#243;n ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Signature> (elemento) [manifiesto de implementación ClickOnce]"
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;Signature&gt; (Implementaci&#243;n ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene la información necesaria para firmar digitalmente este manifiesto de implementación.  
  
## Sintaxis  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## Comentarios  
 Firmar un manifiesto de implementación mediante una firma con doble cifrado es opcional, pero se recomienda hacerlo.  Para obtener más información sobre cómo firmar los archivos XML, vea la Recomendación de World Wide Web Consortium, "XML\-Signature Syntax and Processing," que se describe en [http:\/\/www.w3.org\/TR\/xmldsig\-core\/](http://www.w3.org/TR/xmldsig-core/).  
  
 Si desea firmar su manifiesto, deben proporcionarse un algoritmo hash para todos los archivos.  No se puede firmar un manifiesto con archivos a los que no se aplica un algoritmo hash, ya que los usuarios no pueden comprobar el contenido de este tipo de archivos.  
  
## Ejemplo  
 En el ejemplo de código siguiente se ilustra un elemento `Signature` en un manifiesto utilizado en una implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
```  
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />  
    <SignatureMethod Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
      </Transforms>  
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>d2z5AE...</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>  
4PHj6SaopoLp...  
  </SignatureValue>  
  <KeyInfo>  
    <X509Data>  
      <X509Certificate>  
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...  
      </X509Certificate>  
    </X509Data>  
  </KeyInfo>  
</Signature>  
```  
  
## Vea también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)