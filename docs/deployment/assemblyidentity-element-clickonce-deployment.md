---
title: '&lt;&gt;elemento assemblyIdentity (implementación ClickOnce) | Microsoft Docs'
description: El elemento assemblyIdentity es necesario en la implementación ClickOnce. No contiene ningún elemento secundario y tiene atributos que se describen en este artículo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a692d37771070f1835fc791515d5dbc24ce6b1b
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383189"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity &gt; (elemento, implementación de ClickOnce)
Identifica el ensamblado principal de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.

## <a name="syntax"></a>Syntax

```xml

      <assemblyIdentity  
   name 
   version
   publicKeyToken
   processorArchitecture
    type
/>
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 El elemento `assemblyIdentity` es obligatorio. No contiene elementos secundarios y tiene los atributos siguientes.

|Atributo|Descripción|
|---------------|-----------------|
|`name`|Necesario. Identifica el nombre legible de la implementación con fines informativos.<br /><br /> Si `name` contiene caracteres especiales, como comillas simples o dobles, puede que la aplicación no se active.|
|`version`|Necesario. Especifica el número de versión del ensamblado, en el siguiente formato: `major.minor.build.revision` .<br /><br /> Este valor se debe incrementar en un manifiesto actualizado para desencadenar una actualización de la aplicación.|
|`publicKeyToken`|Necesario. Especifica una cadena hexadecimal de 16 caracteres que representa los últimos 8 bytes del valor hash SHA-1 de la clave pública con la que se firma el manifiesto de implementación. La clave pública que se usa para firmar debe ser de 2048 bits o superior.<br /><br /> Aunque se recomienda la firma de un ensamblado, pero es opcional, este atributo es obligatorio. Si un ensamblado está sin firmar, debe copiar un valor de un ensamblado autofirmado o usar un valor "ficticio" de todos los ceros.|
|`processorArchitecture`|Necesario. Especifica el procesador. Los valores válidos son `msil` para todos los procesadores, `x86` para windows de 32 bits, `IA64` para Windows de 64 bits y `Itanium` para procesadores Itanium de Intel 64 bits.|
|`type`|Necesario. Por compatibilidad con la tecnología de instalación en paralelo de Windows. El único valor permitido es `win32` .|

## <a name="remarks"></a>Comentarios

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra un `assemblyIdentity` elemento en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de implementación. Este ejemplo de código forma parte de un ejemplo mayor proporcionado para el tema [manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md) .

```xml
<!-- Identify the deployment. -->
<assemblyIdentity
  name="My Application Deployment.app"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>Vea también
- [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<assemblyIdentity> Element](../deployment/assemblyidentity-element-clickonce-application.md)