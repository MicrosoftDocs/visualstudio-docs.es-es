---
title: Archivos .Targets de MSBuild | Microsoft Docs
ms.custom: 
ms.date: 02/24/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: bacd57684350553c0ad44f6e25578299894c264c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="msbuild-targets-files"></a>Archivos .Targets de MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] incluye varios archivos .targets que contienen elementos, propiedades, destinos y tareas para escenarios comunes. Estos archivos se importan automáticamente en la mayoría de los archivos del proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para simplificar el mantenimiento y la legibilidad.  

 Normalmente, los proyectos importan uno o más archivos .targets para definir su proceso de compilación. Por ejemplo un proyecto de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] creado por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] importará Microsoft.CSharp.targets, que importa Microsoft.Common.targets. El propio proyecto de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] definirá los elementos y las propiedades específicos de ese proyecto, pero las reglas de compilación estándar para un proyecto de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] se definen en los archivos .targets importados.  

 El valor `$(MSBuildToolsPath)` especifica la ruta de acceso de estos archivos .targets comunes. Si `ToolsVersion` es 4.0, los archivos están en la siguiente ubicación: `WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  

> [!NOTE]
>  Para obtener información sobre cómo crear sus propios destinos, consulte [Destinos](../msbuild/msbuild-targets.md). Para obtener información sobre cómo usar el elemento `Import` para insertar un archivo del proyecto en otro archivo del proyecto, consulte [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md) y [Cómo: Usar el mismo destino en varios archivos del proyecto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  

## <a name="common-targets-files"></a>Archivos .Targets comunes  

|Archivo .Targets|Description|  
|-------------------|-----------------|  
|Microsoft.Common.targets|Define los pasos en el proceso de compilación estándar para proyectos de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] y [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].<br /><br /> Importado mediante los archivos Microsoft.CSharp.targets y Microsoft.VisualBasic.targets, que incluyen la siguiente instrucción: `<Import Project="Microsoft.Common.targets" />`|  
|Microsoft.CSharp.targets|Define los pasos en el proceso de compilación estándar para proyectos de Visual C#.<br /><br /> Importado mediante los archivos del proyecto de Visual C# (.csproj), que incluyen la siguiente instrucción: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft.VisualBasic.targets|Define los pasos en el proceso de compilación estándar para proyectos de Visual Basic.<br /><br /> Importado mediante los archivos del proyecto de Visual Basic (.vbproj), que incluyen la siguiente instrucción: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|

## <a name="directorybuildtargets"></a>Directory.Build.targets
Directory.Build.targets es un archivo definido por el usuario que proporciona personalizaciones a los proyectos de un directorio. Este archivo se importa automáticamente de Microsoft.Common.targets, a menos que la propiedad **ImportDirectoryBuildTargets** esté establecida en **false**.

## <a name="see-also"></a>Vea también  
 [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild.md)
