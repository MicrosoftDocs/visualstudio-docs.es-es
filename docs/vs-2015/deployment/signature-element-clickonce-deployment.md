---
title: '&lt;Signature&gt; Element (ClickOnce Deployment) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db696546fdd64199753054b38fa2ac554f6a774f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295078"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Signature&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contiene la información necesaria para firmar digitalmente este manifiesto de implementación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Comentarios  
 Signing a deployment manifest using an envelope signature is optional, but recommended. For more information about signing XML files see the World Wide Web Consortium Recommendation, "XML-Signature Syntax and Processing," described at [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/).  
  
 If you want to sign your manifest, hashes must be provided for all files. A manifest with files that are not hashed cannot be signed, because users cannot verify the contents of unhashed files.  
  
## <a name="example"></a>Ejemplo  
 The following code example illustrates a `Signature` element in a deployment manifest used in a [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] deployment.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)
