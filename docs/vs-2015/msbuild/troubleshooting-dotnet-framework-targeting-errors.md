---
title: Solucionar problemas de versión de .NET Framework de destino | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0599e6c5e117c6ba9c4f6c0de904284c487910f9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574237"
---
# <a name="troubleshooting-net-framework-targeting-errors"></a>Solucionar problemas de versión de .NET Framework de destino
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [solución de problemas de errores de compatibilidad de .NET Framework](https://docs.microsoft.com/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
  
En este tema se describen los errores de MSBuild que pueden producirse debido a problemas de referencia y cómo pueden resolverse esos errores.  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Ha hecho referencia a un proyecto o ensamblado que tiene como destino una versión diferente de .NET Framework  
 Puede crear aplicaciones que hagan referencia a proyectos o ensamblados destinados a otra versión de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Por ejemplo, puede crear una aplicación destinada al perfil de cliente para [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] pero que hace referencia a un ensamblado destinado a .NET Framework 2.0. Sin embargo, si crea un proyecto destinado a una versión anterior de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], no puede establecer una referencia en ese proyecto a un proyecto o ensamblado destinado al propio perfil de cliente de [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] o [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)]. Para resolver el error, asegúrese de que la aplicación tiene como destino un perfil o perfiles que sean compatibles con el perfil al que se destinan los proyectos o ensamblados a los que la aplicación hace referencia.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Ha cambiado el destino de un proyecto a una versión diferente de .NET Framework  
 Si cambia la versión de destino de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] para la aplicación, Visual Studio cambiará algunas de las referencias, pero es posible que deba actualizar algunas referencias manualmente. Por ejemplo, podría ocurrir uno de los errores anteriormente mencionados si cambia una aplicación para que se destine a [!INCLUDE[net_v35SP1_long](../includes/net-v35sp1-long-md.md)] y la aplicación tiene recursos o valores que se basan en el perfil de cliente para [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)].  
  
 Para corregir la configuración de la aplicación, abra el **Explorador de soluciones**, elija **Mostrar todos los archivos** y, a continuación, edite el archivo app.config en el editor XML de Visual Studio. Cambie la versión en la configuración para que coincida con la versión adecuada de .NET Framework. Por ejemplo, puede cambiar la configuración de la versión de 4.0.0.0 a 2.0.0.0. De igual manera, para una aplicación con recursos agregados, abra el **Explorador de soluciones**, elija el botón **Mostrar todos los archivos**, expanda **Mi proyecto** (Visual Basic) o **Propiedades** (C#) y, a continuación modifique el archivo Resources.resx en el Editor XML de Visual Studio. Cambie la versión de 4.0.0.0 a 2.0.0.0.  
  
 Si la aplicación tiene recursos como iconos o mapas de bits o valores como cadenas de conexión de datos, también puede resolver el error quitando todos los elementos en la página **Configuración** del **Diseñador de proyectos** y, a continuación, volver a agregar los parámetros necesarios.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Ha cambiado el destino de un proyecto a una versión diferente de .NET Framework y las referencias no se resuelven  
 Si cambia el destino de un proyecto a una versión diferente de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], las referencias pueden no resolverse correctamente en algunos casos. Las referencias completas explícitas a ensamblados a menudo provocan este problema, pero puede resolverlo quitando las referencias que no se resuelvan y agregándolas luego de nuevo al proyecto. También puede editar el archivo de proyecto para reemplazar las referencias. En primer lugar, quite las referencias de la forma siguiente:  
  
```  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 A continuación, reemplácelas por la forma simple:  
  
```  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
>  Después de cerrar y volver a abrir el proyecto, también debe volver a generarlo para garantizar que todas las referencias se resuelven correctamente.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Usar como destino una versión de .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [.NET Framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)  (Perfil de cliente de .NET Framework)  
 [Elegir una versión específica de .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [Compatibilidad con múltiples versiones (multi-targeting)](../msbuild/msbuild-multitargeting-overview.md)



