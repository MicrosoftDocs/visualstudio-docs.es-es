---
title: Solucionar problemas de versión de .NET Framework de destino | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: troubleshooting
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6376abc29f6f06541b9cd7f3d181b97ab7b38e5f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="troubleshooting-net-framework-targeting-errors"></a>Solucionar problemas de versión de .NET Framework de destino
En este tema se describen los errores de MSBuild que pueden producirse debido a problemas de referencia y cómo pueden resolverse esos errores.  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Ha hecho referencia a un proyecto o ensamblado que tiene como destino una versión diferente de .NET Framework  
 Puede crear aplicaciones que hagan referencia a proyectos o ensamblados destinados a otra versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Por ejemplo, puede crear una aplicación destinada al perfil de cliente para [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] pero que hace referencia a un ensamblado destinado a .NET Framework 2.0. Pero si crea un proyecto destinado a una versión anterior de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], no puede establecer una referencia en ese proyecto a un proyecto o ensamblado destinado al propio perfil de cliente de [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] o [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]. Para resolver el error, asegúrese de que la aplicación tiene como destino un perfil o perfiles que sean compatibles con el perfil al que se destinan los proyectos o ensamblados a los que la aplicación hace referencia.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Ha cambiado el destino de un proyecto a una versión diferente de .NET Framework  
 Si cambia la versión de destino de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] para la aplicación, Visual Studio cambiará algunas de las referencias, pero es posible que deba actualizar algunas referencias manualmente. Por ejemplo, podría ocurrir uno de los errores anteriormente mencionados si cambia una aplicación para que se destine a [!INCLUDE[net_v35SP1_long](../msbuild/includes/net_v35sp1_long_md.md)] y la aplicación tiene recursos o valores que se basan en el perfil de cliente para [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)].  
  
 Para corregir la configuración de la aplicación, abra el **Explorador de soluciones**, elija **Mostrar todos los archivos** y, a continuación, edite el archivo app.config en el editor XML de Visual Studio. Cambie la versión en la configuración para que coincida con la versión adecuada de .NET Framework. Por ejemplo, puede cambiar la configuración de la versión de 4.0.0.0 a 2.0.0.0. De igual manera, para una aplicación con recursos agregados, abra el **Explorador de soluciones**, elija el botón **Mostrar todos los archivos**, expanda **Mi proyecto** (Visual Basic) o **Propiedades** (C#) y, a continuación modifique el archivo Resources.resx en el Editor XML de Visual Studio. Cambie la versión de 4.0.0.0 a 2.0.0.0.  
  
 Si la aplicación tiene recursos como iconos o mapas de bits o valores como cadenas de conexión de datos, también puede resolver el error quitando todos los elementos en la página **Configuración** del **Diseñador de proyectos** y, a continuación, volver a agregar los parámetros necesarios.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Ha cambiado el destino de un proyecto a una versión diferente de .NET Framework y las referencias no se resuelven  
 Si cambia el destino de un proyecto a una versión diferente de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], las referencias pueden no resolverse correctamente en algunos casos. Las referencias completas explícitas a ensamblados a menudo provocan este problema, pero puede resolverlo quitando las referencias que no se resuelvan y agregándolas luego de nuevo al proyecto. También puede editar el archivo de proyecto para reemplazar las referencias. En primer lugar, quite las referencias de la forma siguiente:  
  
```xml  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 A continuación, reemplácelas por la forma simple:  
  
```xml  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
>  Después de cerrar y volver a abrir el proyecto, también debe volver a generarlo para garantizar que todas las referencias se resuelven correctamente.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Usar como destino una versión de .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile)  (Perfil de cliente de .NET Framework)  
 [Elegir una versión específica de .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [Compatibilidad con múltiples versiones (multi-targeting)](../msbuild/msbuild-multitargeting-overview.md)