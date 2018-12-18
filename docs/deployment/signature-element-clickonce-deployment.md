---
title: '&lt;Firma&gt; elemento (implementación ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 60349c8337d41a03d488b7d14a3fb7bcaa24dbcd
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081519"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Firma&gt; elemento (implementación ClickOnce)
Contiene la información necesaria para firmar digitalmente este manifiesto de implementación.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Comentarios  
 Firmar un manifiesto de implementación mediante una firma con doble cifrado es opcional pero recomendado. Para obtener más información acerca de cómo firmar los archivos XML, vea la World Wide Web Consortium recomendación, "XML-Signature Syntax and Processing," se describe en [ http://www.w3.org/TR/xmldsig-core/ ](http://www.w3.org/TR/xmldsig-core/).  
  
 Si desea firmar el manifiesto, se deben proporcionar valores hash para todos los archivos. No se puede firmar un manifiesto con archivos que no se aplica un algoritmo hash, ya que los usuarios no pueden comprobar el contenido de este tipo de archivos.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se ilustra un `Signature` elemento en un manifiesto de implementación que se usa en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación.  
  
```xml  
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
 [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)