---
title: '&lt;Firma&gt; elemento (implementación de ClickOnce) | Documentos de Microsoft'
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
ms.openlocfilehash: 5637bad77e2d4e09d6d04007f0e0da3ed8af68df
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Firma&gt; elemento (implementación de ClickOnce)
Contiene la información necesaria para firmar digitalmente este manifiesto de implementación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Comentarios  
 Firmar un manifiesto de implementación mediante una firma con doble cifrado es opcional, pero se recomienda. Para obtener más información acerca de la firma XML archivos Consulte la World Wide Web Consortium recomendación, "XML-Signature Syntax and Processing," se describe en [ http://www.w3.org/TR/xmldsig-core/ ](http://www.w3.org/TR/xmldsig-core/).  
  
 Si desea firmar el manifiesto, se deben proporcionar valores hash para todos los archivos. No se puede firmar un manifiesto con archivos que no se aplica un algoritmo hash, ya que los usuarios no pueden comprobar el contenido de este tipo de archivos.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra un `Signature` elemento en un manifiesto de implementación utilizado en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación.  
  
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