---
title: '&lt;&gt;elemento compatibleFrameworks (implementación ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: ef54062bd74c9395e187503dd12db1c0cd70d822
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675417"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;&gt;elemento compatibleFrameworks (implementación ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifica las versiones de .NET Framework en las que se puede instalar y ejecutar esta aplicación.  
  
> [!NOTE]
> [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14) no admite el `compatibleFrameworks` elemento cuando se guarda un manifiesto de aplicación que ya se ha firmado con un certificado mediante [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). En su lugar, debe usar [Mage.exe](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
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
  
## <a name="elements-and-attributes"></a>Atributos y elementos  
 El `compatibleFrameworks` elemento es necesario para los manifiestos de implementación que tienen como destino el [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tiempo de ejecución proporcionado por [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] o posterior. El `compatibleFrameworks` elemento contiene uno o más `framework` elementos que especifican las versiones .NET Framework en las que se puede ejecutar esta aplicación. El [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tiempo de ejecución ejecutará la aplicación en la primera disponible `framework` en esta lista.  
  
 En la tabla siguiente se muestra el atributo que el `compatibleFrameworks` elemento admite.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`S` `upportUrl`|Opcional. Especifica una dirección URL en la que se puede descargar la versión de .NET Framework compatible preferida.|  
  
## <a name="framework"></a>marco de trabajo  
 Necesario. En la tabla siguiente se enumeran los atributos que `framework` admite el elemento.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`targetVersion`|Necesario. Especifica el número de versión del .NET Framework de destino.|  
|`profile`|Necesario. Especifica el perfil de la .NET Framework de destino.|  
|`supportedRuntime`|Necesario. Especifica el número de versión del tiempo de ejecución asociado a la .NET Framework de destino.|  
  
## <a name="remarks"></a>Observaciones  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra un `compatibleFrameworks` elemento en un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifiesto de implementación. Esta implementación se puede ejecutar en el [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] . También se puede ejecutar en [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] porque es un superconjunto de [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] .  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Consulte también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)
