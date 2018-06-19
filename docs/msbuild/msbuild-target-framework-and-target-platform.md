---
title: Versión de .NET Framework de destino y plataforma de destino de MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93eff2375e9b1cab043a30acaf5ebec31ba8e89f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31578281"
---
# <a name="msbuild-target-framework-and-target-platform"></a>Plataforma de destino de MSBuild
Un proyecto se puede compilar para su ejecución en una *plataforma de destino*, que es una versión determinada de .NET Framework, y en una *plataforma de destino*, que es una arquitectura de software determinada.  Por ejemplo, puede diseñar una aplicación para que se ejecute en .NET Framework 2.0 en una plataforma de 32 bits compatible con la familia de procesadores 802x86 ("x86"). La combinación de la plataforma de destino y la plataforma de destino se denomina *contexto de destino*.  
  
## <a name="target-framework-and-profile"></a>Plataforma de destino y perfil objetivo  
 La versión de .NET Framework de destino es la versión concreta de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] para la que se ha compilado su proyecto. Es necesario especificar una versión del marco de trabajo de destino, ya que esto permite habilitar las características del compilador y las referencias de ensamblado exclusivas de esa versión del marco.  
  
 Actualmente, se pueden usar las versiones siguientes de .NET Framework:  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 (incluida en Visual Studio 2005)  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.0 (incluida en [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 (incluida en [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5.2  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6 (incluida en [!INCLUDE[vs_dev14](../misc/includes/vs_dev14_md.md)])  

-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6.1  

-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6.2  

-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.7  

-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.7.1  
  
 Las versiones de .NET Framework difieren entre sí en la lista de ensamblados a los que se puede hacer referencia en cada una de ellas. Por ejemplo, solo puede compilar aplicaciones de Windows Presentation Foundation (WPF) si el proyecto tiene como destino.NET Framework 3.0 o versiones posteriores.  
  
 El marco de trabajo de destino se especifica en la propiedad `TargetFrameworkVersion` del archivo de proyecto. Puede cambiar la plataforma de destino de un proyecto mediante las páginas de propiedades del proyecto en el entorno de desarrollo integrado (IDE) de Visual Studio. Para obtener más información, consulte [Cómo: Usar como destino una versión de .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Los valores disponibles para `TargetFrameworkVersion` son `v2.0`, `v3.0`, `v3.5`, `v4.5.2`, `v4.6`, `v.4.6.1`, `v4.6.2`, `4.7` y `4.7.1`.  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 Un *perfil objetivo* es un subconjunto de una plataforma de destino. Por ejemplo, .NET Framework 4 Client Profile no incluye referencias a los ensamblados de MSBuild.  
  
 El perfil de destino se especifica en la propiedad `TargetFrameworkProfile` de un archivo de proyecto. Puede cambiar el perfil objetivo mediante el control de plataforma de destino en las páginas de propiedades del proyecto del IDE. Para obtener más información, consulte [Cómo: Usar como destino una versión de .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>Plataforma de destino  
 Una *plataforma* es una combinación de hardware y de software que define un entorno en tiempo de ejecución determinado. Por ejemplo,  
  
-   `x86` designa un sistema operativo Windows de 32 bits que se ejecuta en un procesador Intel 80x86 o su equivalente.  

-   `x64` designa un sistema operativo Windows de 64 bits que se ejecuta en un procesador Intel x64 o su equivalente.
  
-   `Xbox` designa la plataforma Microsoft Xbox 360.  
  
 Una *plataforma de destino* es la plataforma específica para la que se ha compilado el proyecto. La plataforma de destino se especifica en la propiedad de compilación `PlatformTarget` de un archivo de proyecto. Puede cambiar la plataforma de destino mediante las páginas de propiedades del proyecto o el **Administrador de configuración** del IDE.  
  
```xml  
<PropertyGroup>  
   <PlatformTarget>x86</PlatformTarget>  
</PropertyGroup>  
  
```  
  
 Una *configuración de destino* es un subconjunto de una plataforma de destino. Por ejemplo, la configuración `x86``Debug` no incluye la mayoría de las optimizaciones de código. La configuración de destino se especifica en la propiedad de compilación `Configuration` de un archivo de proyecto. Puede cambiar la configuración de destino mediante las páginas de propiedades del proyecto o el **Administrador de configuración**.  
  
```xml  
<PropertyGroup>  
   <PlatformTarget>x86</PlatformTarget>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con múltiples versiones (multi-targeting)](../msbuild/msbuild-multitargeting-overview.md)