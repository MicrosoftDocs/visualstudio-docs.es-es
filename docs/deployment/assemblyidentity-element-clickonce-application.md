---
title: "&lt;assemblyIdentity&gt; elemento (aplicación ClickOnce) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: "20"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: b731522897512300459a32f8e01c4d54277eaa5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;assemblyIdentity&gt; elemento (aplicación ClickOnce)
Identifica la aplicación implementada en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El `assemblyIdentity` elemento es necesario. No contiene elementos secundarios y tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Name`|Requerido. Identifica el nombre de la aplicación.<br /><br /> Si `Name` contiene caracteres especiales, como las comillas simples o dobles, puede producir un error de la aplicación Activar.|  
|`Version`|Requerido. Especifica el número de versión de la aplicación en el formato siguiente:`major.minor.build.revision`|  
|`publicKeyToken`|Opcional. Especifica una cadena hexadecimal de 16 caracteres que representa los últimos 8 bytes de la `SHA-1` valor hash de la clave pública con la que se firma la aplicación o el ensamblado. La clave pública que se usa para firmar el catálogo debe tener 2048 bits o mayor.<br /><br /> Aunque la firma de un ensamblado es opcional, pero recomendable, este atributo es necesario. Si un ensamblado está firmado, debería copiar un valor de un ensamblado autofirmado o utilizar un valor "ficticio" de todos los ceros.|  
|`processorArchitecture`|Requerido. Especifica el procesador. Los valores válidos son `msil` para todos los procesadores, `x86` para Windows de 32 bits, `IA64` para Windows de 64 bits, y `Itanium` para procesadores Itanium de Intel de 64 bits.|  
|`language`|Requerido. Identifica los códigos de idioma de dos partes (por ejemplo, `en-US`) del ensamblado. Este elemento está en la `asmv2` espacio de nombres. Si no se especifica, el valor predeterminado es `neutral`.|  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="description"></a>Descripción  
 En el ejemplo de código siguiente se muestra un `assemblyIdentity` elemento en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).  
  
### <a name="code"></a>Código  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity > elemento](../deployment/assemblyidentity-element-clickonce-deployment.md)