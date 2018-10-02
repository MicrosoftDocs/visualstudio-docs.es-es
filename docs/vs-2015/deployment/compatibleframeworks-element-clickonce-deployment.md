---
title: '&lt;compatibleFrameworks&gt; elemento (implementación ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: c5abcc6e7c4308cf0d60c78cd4ef0f052403bb1f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577625"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt; elemento (implementación ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [ &lt;compatibleFrameworks&gt; elemento (implementación ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/compatibleframeworks-element-clickonce-deployment).  
  
Identifica las versiones de .NET Framework en las que se puede instalar y ejecutar esta aplicación.  
  
> [!NOTE]
>  [MageUI.exe](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14) no admite el `compatibleFrameworks` elemento cuando se guarda un manifiesto de aplicación que ya se ha firmado con un certificado mediante [MageUI.exe](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). En su lugar, debe usar [Mage.exe](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
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
 El `compatibleFrameworks` elemento es necesario para los manifiestos de implementación que tienen como destino el [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] en tiempo de ejecución proporcionado por [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] o una versión posterior. El `compatibleFrameworks` elemento contiene uno o varios `framework` elementos que especifican las versiones de .NET Framework en el que se puede ejecutar esta aplicación. El [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] en tiempo de ejecución ejecutará la aplicación en la primera disponible `framework` en esta lista.  
  
 En la tabla siguiente se enumera el atributo que el `compatibleFrameworks` admite el elemento.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`S` `upportUrl`|Opcional. Especifica una dirección URL donde se puede descargar la versión de .NET Framework compatible preferida.|  
  
## <a name="framework"></a>marco de trabajo  
 Requerido. En la tabla siguiente se enumera los atributos que el `framework` admite el elemento.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`targetVersion`|Requerido. Especifica el número de versión de .NET Framework de destino.|  
|`profile`|Requerido. Especifica el perfil de .NET Framework de destino.|  
|`supportedRuntime`|Requerido. Especifica el número de versión del tiempo de ejecución asociada con el destino es .NET Framework.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código muestra un `compatibleFrameworks` elemento en un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifiesto de implementación. Esta implementación se puede ejecutar en el [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)]. También puede ejecutar en el [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] porque es un superconjunto de la [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)].  
  
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



