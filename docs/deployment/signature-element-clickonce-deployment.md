---
title: '&lt;&gt;Elemento Signature (implementación ClickOnce) | Microsoft Docs'
description: El elemento Signature contiene la información necesaria para firmar digitalmente este manifiesto de implementación. La firma de un manifiesto de implementación es opcional, pero se recomienda.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5d95398285d9106719f3c2444d54202b81cfee4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877504"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;&gt;Elemento Signature (implementación ClickOnce)
Contiene la información necesaria para firmar digitalmente este manifiesto de implementación.

## <a name="syntax"></a>Sintaxis

```xml

<Signature> 
   XML signature information 
</Signature>
```

## <a name="remarks"></a>Observaciones
 La firma de un manifiesto de implementación mediante una firma de sobre es opcional, pero se recomienda. Para obtener más información sobre la firma de archivos XML, vea la recomendación World Wide Web Consortium, "XML-Signature Syntax and Processing", que se describe en [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/) .

 Si desea firmar el manifiesto, se deben proporcionar los valores hash para todos los archivos. No se puede firmar un manifiesto con archivos a los que no se ha aplicado un algoritmo hash, ya que los usuarios no pueden comprobar el contenido de los archivos sin hash.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra un `Signature` elemento en un manifiesto de implementación que se usa en una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación de.

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
- [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)
