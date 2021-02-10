---
title: Archivos .targets de MSBuild | Microsoft Docs
description: Obtenga información sobre los archivos .targets de MSBuild que contienen elementos, propiedades, destinos y tareas para escenarios comunes.
ms.custom: SEO-VS-2020
ms.date: 02/24/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .targets files
- MSBuild, .targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ee685fc3deada1a3ac36082fa916b50986900f81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971250"
---
# <a name="msbuild-targets-files"></a>Archivos .targets de MSBuild

MSBuild incluye varios archivos *.targets* que contienen elementos, propiedades, destinos y tareas para escenarios comunes. Estos archivos se importan automáticamente en la mayoría de los archivos del proyecto de Visual Studio para simplificar el mantenimiento y la legibilidad.

 Normalmente, los proyectos importan uno o más archivos *.targets* para definir su proceso de compilación. Por ejemplo, un proyecto de C# creado por Visual Studio importa *Microsoft.CSharp.targets*, que importa *Microsoft.Common.targets*. El propio proyecto de C# define los elementos y las propiedades específicos de ese proyecto, pero las reglas de compilación estándar de un proyecto de C# se definen en los archivos *.targets* importados.

 El valor `$(MSBuildToolsPath)` especifica la ruta de acceso de estos archivos *.targets* comunes. Si `ToolsVersion` es 4.0, los archivos están en la ubicación siguiente: *\<WindowsInstallationPath>\Microsoft.NET\Framework\v4.0.30319\\*

> [!NOTE]
> Para obtener información sobre cómo crear sus propios destinos, consulte [Destinos](../msbuild/msbuild-targets.md). Para obtener información sobre cómo usar el elemento `Import` para insertar un archivo de proyecto en otro, vea [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md) y [Cómo: Usar el mismo destino en varios archivos de proyecto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).

## <a name="common-targets-files"></a>Archivos .targets comunes

| Archivo *.targets* | Descripción |
|---------------------------------| - |
| *Microsoft.Common.targets* | Define los pasos en el proceso de compilación estándar para proyectos de Visual Basic y C#.<br /><br /> Importado por los archivos *Microsoft.CSharp.targets* y *Microsoft.VisualBasic.targets*, que incluyen la siguiente instrucción: `<Import Project="Microsoft.Common.targets" />` |
| *Microsoft.CSharp.targets* | Define los pasos en el proceso de compilación estándar para proyectos de Visual C#.<br /><br /> Importado por los archivos de proyecto de Visual C# ( *.csproj*), que incluyen la siguiente instrucción: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft.VisualBasic.targets* | Define los pasos en el proceso de compilación estándar para proyectos de Visual Basic.<br /><br /> Importado por los archivos de proyecto de Visual Basic ( *.vbproj*), que incluyen la siguiente instrucción: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory.Build.targets

*Directory.Build.targets* es un archivo definido por el usuario que proporciona personalizaciones a proyectos de un directorio. Este archivo se importa automáticamente desde *Microsoft.Common.targets*, a menos que la propiedad **ImportDirectoryBuildTargets** esté establecida en **false**. Para más información, [personalice su compilación](customize-your-build.md).

## <a name="see-also"></a>Vea también

- [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
