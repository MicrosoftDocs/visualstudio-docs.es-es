---
title: Archivos .Targets de MSBuild | Microsoft Docs
ms.date: 02/24/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa0366fed1a405acfa600e9af594e32c1ab47346
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623754"
---
# <a name="msbuild-targets-files"></a>Archivos .targets de MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] incluye varios archivos *.targets* que contienen elementos, propiedades, destinos y tareas para escenarios comunes. Estos archivos se importan automáticamente en la mayoría de los archivos del proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para simplificar el mantenimiento y la legibilidad.

 Normalmente, los proyectos importan uno o más archivos *.targets* para definir su proceso de compilación. Por ejemplo, un proyecto de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] creado por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] importa *Microsoft.CSharp.targets*, que importa *Microsoft.Common.targets*. El propio proyecto de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] define los elementos y las propiedades específicos de ese proyecto, pero las reglas de compilación estándar de un proyecto de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] se definen en los archivos *.targets* importados.

 El valor `$(MSBuildToolsPath)` especifica la ruta de acceso de estos archivos *.targets* comunes. Si `ToolsVersion` es 4.0, los archivos están en la siguiente ubicación: *\<WindowsInstallationPath>\Microsoft.NET\Framework\v4.0.30319\\*

> [!NOTE]
>  Para obtener información sobre cómo crear sus propios destinos, consulte [Destinos](../msbuild/msbuild-targets.md). Para obtener información sobre cómo usar el elemento `Import` para insertar un archivo de proyecto en otro, vea [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md) y [Cómo: Usar el mismo destino en varios archivos de proyecto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).

## <a name="common-targets-files"></a>Archivos .targets comunes

| Archivo *.targets* | Descripción |
|---------------------------------| - |
| *Microsoft.Common.targets* | Define los pasos en el proceso de compilación estándar para proyectos de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] y [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].<br /><br /> Importado por los archivos *Microsoft.CSharp.targets* y *Microsoft.VisualBasic.targets*, que incluyen la siguiente instrucción: `<Import Project="Microsoft.Common.targets" />` |
| *Microsoft.CSharp.targets* | Define los pasos en el proceso de compilación estándar para proyectos de Visual C#.<br /><br /> Importado por los archivos de proyecto de Visual C# (*.csproj*), que incluyen la siguiente instrucción: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft.VisualBasic.targets* | Define los pasos en el proceso de compilación estándar para proyectos de Visual Basic.<br /><br /> Importado por los archivos de proyecto de Visual Basic (*.vbproj*), que incluyen la siguiente instrucción: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory.Build.targets
*Directory.Build.targets* es un archivo definido por el usuario que proporciona personalizaciones a proyectos de un directorio. Este archivo se importa automáticamente desde *Microsoft.Common.targets*, a menos que la propiedad **ImportDirectoryBuildTargets** esté establecida en **false**.

## <a name="see-also"></a>Vea también
- [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
