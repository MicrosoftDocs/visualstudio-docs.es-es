---
title: "&lt;compatibleFrameworks&gt; elemento (implementación de ClickOnce) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: "15"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: bb8c31d37bd37f4e2db8415ef1815caec0ec185a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt; elemento (implementación de ClickOnce)
Identifica las versiones de .NET Framework en las que se puede instalar y ejecutar esta aplicación.  
  
> [!NOTE]
>  [MageUI.exe](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) no admite el `compatibleFrameworks` elemento cuando se guarda un manifiesto de aplicación que ya se ha firmado con un certificado mediante [MageUI.exe](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). En su lugar, debe usar [Mage.exe](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<compatibleFrameworks  
      SupportUrl>   
   <framework  
      targetVersion  
      profile  
      supportedRuntime  
   />   
</ compatibleFrameworks>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El `compatibleFrameworks` elemento es necesario para los manifiestos de implementación que tienen como destino el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en tiempo de ejecución proporcionado por [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] o una versión posterior. El `compatibleFrameworks` elemento contiene uno o varios `framework` elementos que especifican las versiones de .NET Framework en el que puede ejecutar esta aplicación. El [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en tiempo de ejecución ejecutará la aplicación en la primera disponible `framework` en esta lista.  
  
 La tabla siguiente muestra el atributo que el `compatibleFrameworks` admite el elemento.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`S` `upportUrl`|Opcional. Especifica una dirección URL donde se puede descargar la versión de .NET Framework compatible preferida.|  
  
## <a name="framework"></a>marco de trabajo  
 Requerido. En la tabla siguiente se enumera los atributos que la `framework` admite el elemento.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`targetVersion`|Obligatorio. Especifica el número de versión de .NET Framework de destino.|  
|`profile`|Obligatorio. Especifica el perfil de la versión de .NET Framework de destino.|  
|`supportedRuntime`|Obligatorio. Especifica el número de versión del tiempo de ejecución asociado a la versión de .NET Framework de destino.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código muestra un `compatibleFrameworks` elemento en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de implementación. Puede ejecutar esta implementación el [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]. También puede ejecutarse en el [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] porque es un supraconjunto de la [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)