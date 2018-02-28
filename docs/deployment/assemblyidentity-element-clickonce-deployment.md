---
title: "&lt;assemblyIdentity&gt; elemento (implementación de ClickOnce) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 51643b8db91c9f8c2961b319d47cdfb7789f6a4d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity&gt; elemento (implementación de ClickOnce)
Identifica el ensamblado primario de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El `assemblyIdentity` elemento es necesario. No contiene elementos secundarios y tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`name`|Requerido. Identifica el nombre legible de la implementación con fines informativos.<br /><br /> Si `name` contiene caracteres especiales, como las comillas simples o dobles, puede producir un error de la aplicación Activar.|  
|`version`|Requerido. Especifica el número de versión del ensamblado, en el siguiente formato: `major.minor.build.revision`.<br /><br /> Este valor se debe incrementar en un manifiesto actualizado para desencadenar una actualización de la aplicación.|  
|`publicKeyToken`|Requerido. Especifica una cadena hexadecimal de 16 caracteres que representa los últimos 8 bytes del valor hash SHA-1 de la clave pública con la que se firma el manifiesto de implementación. La clave pública que se utiliza para firmar debe tener 2048 bits o mayor.<br /><br /> Aunque la firma de un ensamblado es opcional, pero recomendable, este atributo es necesario. Si un ensamblado está firmado, debería copiar un valor de un ensamblado autofirmado o utilizar un valor "ficticio" de todos los ceros.|  
|`processorArchitecture`|Requerido. Especifica el procesador. Los valores válidos son `msil` para todos los procesadores, `x86` para Windows de 32 bits, `IA64` para Windows de 64 bits, y `Itanium` para procesadores Itanium de Intel de 64 bits.|  
|`type`|Requerido. Para la compatibilidad con la tecnología de instalación en paralelo de Windows. El único valor permitido es `win32`.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra un `assemblyIdentity` elemento en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de implementación. Este ejemplo de código forma parte de un ejemplo mayor proporcionado para el [manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md) tema.  
  
```  
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