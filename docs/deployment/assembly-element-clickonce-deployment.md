---
title: '&lt;Assembly &gt; (elemento, implementación ClickOnce) | Microsoft Docs'
description: El elemento Assembly es el elemento raíz y es necesario en la implementación ClickOnce. Su primer elemento contenido debe ser un elemento assemblyIdentity.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dde3bdb5fc0e9c6ea256aaa4368623a8e8af18d6
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383240"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;Assembly &gt; (elemento, implementación ClickOnce)
El elemento de nivel superior para el manifiesto de implementación.

## <a name="syntax"></a>Syntax

```xml

      <assembly  
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 El `assembly` elemento es el elemento raíz y es obligatorio. Su primer elemento contenido debe ser un `assemblyIdentity` elemento. Los elementos de manifiesto deben estar en los siguientes espacios de nombres: `urn:schemas-microsoft-com:asm.v1` , `urn:schemas-microsoft-com:asm.v2` y `http://www.w3.org/2000/09/xmldsig#` . Los elementos secundarios del ensamblado también deben estar en estos espacios de nombres, por herencia o mediante el etiquetado.

 El elemento `assembly` tiene el siguiente atributo.

|Atributo|Descripción|
|---------------|-----------------|
|`manifestVersion`|Necesario. Este atributo debe establecerse en `1.0` .|

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra un `assembly` elemento en un manifiesto de implementación para una aplicación implementada mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Este ejemplo de código forma parte de un ejemplo mayor proporcionado para el tema [manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md) .

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
```

## <a name="see-also"></a>Vea también
- [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<assembly> Element](../deployment/assembly-element-clickonce-application.md)