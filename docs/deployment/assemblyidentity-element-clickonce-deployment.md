---
title: '&lt;assemblyIdentity&gt; elemento (implementación ClickOnce) | Microsoft Docs'
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3749fdbdebaaf48cbbf073486e2e44ae2f2519d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859271"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity&gt; elemento (implementación ClickOnce)
Identifica el ensamblado principal de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
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
 El `assemblyIdentity` elemento es necesario. No contiene elementos secundarios y tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`name`|Obligatorio. Identifica el nombre legible de la implementación con fines informativos.<br /><br /> Si `name` contiene caracteres especiales, como las comillas simples o dobles, es posible que no activa la aplicación.|  
|`version`|Obligatorio. Especifica el número de versión del ensamblado, en el siguiente formato: `major.minor.build.revision`.<br /><br /> Este valor se debe incrementar en un manifiesto actualizado para desencadenar una actualización de la aplicación.|  
|`publicKeyToken`|Obligatorio. Especifica una cadena hexadecimal de 16 caracteres que representa los últimos 8 bytes del valor hash SHA-1 de la clave pública con la que se firma el manifiesto de implementación. La clave pública que se usa para iniciar sesión debe ser 2048 bits o superior.<br /><br /> Aunque al firmar un ensamblado es opcional pero recomendado, este atributo es necesario. Si un ensamblado está firmado, debe copiar un valor de un ensamblado autofirmado o usar un valor "ficticio" de todos los ceros.|  
|`processorArchitecture`|Obligatorio. Especifica el procesador. Los valores válidos son `msil` para todos los procesadores, `x86` para Windows de 32 bits, `IA64` para Windows de 64 bits, y `Itanium` para procesadores Itanium de Intel de 64 bits.|  
|`type`|Obligatorio. Por compatibilidad con la tecnología de instalación en paralelo de Windows. El único valor permitido es `win32`.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se ilustra un `assemblyIdentity` elemento en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de implementación. Este ejemplo de código forma parte de un ejemplo más extenso proporcionado para el [manifiesto de implementación ClickOnce](../deployment/clickonce-deployment-manifest.md) tema.  
  
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
 [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity > elemento](../deployment/assemblyidentity-element-clickonce-application.md)