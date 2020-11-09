---
title: '&lt;assemblyIdentity &gt; (elemento, aplicación ClickOnce) | Microsoft Docs'
description: El elemento assemblyIdentity es necesario en la aplicación ClickOnce. No contiene ningún elemento secundario y tiene atributos que se describen en este artículo.
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
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c86d5d1fd1e25b498405197b68efd9553ed64f16
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383214"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;assemblyIdentity &gt; (elemento, aplicación ClickOnce)
Identifica la aplicación implementada en una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación de.

## <a name="syntax"></a>Syntax

```xml

      <assemblyIdentity
   name
   version
   publicKeyToken
   processorArchitecture
   language
/>
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 El elemento `assemblyIdentity` es obligatorio. No contiene elementos secundarios y tiene los atributos siguientes.

|Atributo|Descripción|
|---------------|-----------------|
|`Name`|Necesario. Identifica el nombre de la aplicación.<br /><br /> Si `Name` contiene caracteres especiales, como comillas simples o dobles, puede que la aplicación no se active.|
|`Version`|Necesario. Especifica el número de versión de la aplicación en el formato siguiente: `major.minor.build.revision`|
|`publicKeyToken`|Opcional. Especifica una cadena hexadecimal de 16 caracteres que representa los últimos 8 bytes del `SHA-1` valor hash de la clave pública con la que se firma la aplicación o el ensamblado. La clave pública que se usa para firmar el catálogo debe ser de 2048 bits o superior.<br /><br /> Aunque se recomienda la firma de un ensamblado, pero es opcional, este atributo es obligatorio. Si un ensamblado está sin firmar, debe copiar un valor de un ensamblado autofirmado o usar un valor "ficticio" de todos los ceros.|
|`processorArchitecture`|Necesario. Especifica el procesador. Los valores válidos son `msil` para todos los procesadores, `x86` para windows de 32 bits, `IA64` para Windows de 64 bits y `Itanium` para procesadores Itanium de Intel 64 bits.|
|`language`|Necesario. Identifica los códigos de idioma de dos partes (por ejemplo, `en-US` ) del ensamblado. Este elemento está en el `asmv2` espacio de nombres. Si no se especifica, el valor predeterminado es `neutral` .|

## <a name="examples"></a>Ejemplos

### <a name="description"></a>Descripción
 En el ejemplo de código siguiente se muestra un `assemblyIdentity` elemento en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación. Este ejemplo de código forma parte de un ejemplo más grande proporcionado en el [manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).

### <a name="code"></a>Código

```xml
<asmv1:assemblyIdentity
  name="My Application Deployment.exe"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  type="win32" />
```

## <a name="see-also"></a>Consulte también
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<assemblyIdentity> Element](../deployment/assemblyidentity-element-clickonce-deployment.md)