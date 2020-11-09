---
title: Metadatos de los elementos conocidos de MSBuild | Microsoft Docs
description: Obtenga información sobre los metadatos de MSBuild asignados a cada elemento tras su creación y algunos metadatos de MSBuild opcionales que puede definir para controlar el comportamiento de la compilación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 047fe5ef6edc57681b8382a9f2a1069991e0f513
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049018"
---
# <a name="msbuild-well-known-item-metadata"></a>Metadatos de los elementos conocidos de MSBuild

Los metadatos de elementos son valores asociados a elementos. MSBuild asigna algunos de ellos a elementos al crearse estos, pero también puede definir los metadatos que necesite. Algunos valores de metadatos definidos por el usuario tienen significado para MSBuild, tareas específicas o SDK como el SDK de .NET.

En la primera tabla de este artículo se describen los metadatos asignados a cada elemento en el momento de su creación. En la tabla siguiente se muestran algunos metadatos opcionales que tienen significado para MSBuild, que puede definir para controlar el comportamiento de la compilación. En cada ejemplo, se usó la siguiente declaración de elementos para incluir el archivo *C:\MyProject\Source\Program.cs* en el proyecto.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Metadatos de elementos|Descripción|
|-------------------|-----------------|
|%(FullPath)|Contiene la ruta de acceso completa del elemento. Por ejemplo:<br /><br /> *C:\MyProject\Source\Program.cs*|
|%(RootDir)|Contiene el directorio raíz del elemento. Por ejemplo:<br /><br /> *C:\\*|
|%(Filename)|Contiene el nombre de archivo del elemento, sin la extensión. Por ejemplo:<br /><br /> *Program*|
|%(Extension)|Contiene la extensión de nombre de archivo del elemento. Por ejemplo:<br /><br /> *.cs*|
|%(RelativeDir)|Contiene la ruta de acceso especificada en el atributo `Include`, hasta la última barra diagonal inversa (\\). Por ejemplo:<br /><br /> *Source\\*<br /><br /> Si el atributo `Include` es una ruta de acceso completa, `%(RelativeDir)` comienza por el directorio raíz `%(RootDir)`.  Por ejemplo: <br /><br /> *C:\MyProject\Source\\*|
|%(Directory)|Contiene el directorio del elemento, sin el directorio raíz. Por ejemplo:<br /><br /> *MyProject\\Source\\*|
|%(RecursiveDir)|Si el atributo `Include` contiene el carácter comodín \*\*, este metadato especifica la parte de la ruta de acceso que reemplaza el carácter comodín. Para obtener más información sobre los caracteres comodín, vea [Cómo: Seleccionar los archivos que se van a compilar](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Si la carpeta *C:\MySolution\MyProject\Source\\* contiene el archivo *Program.cs* y si el archivo de proyecto contiene este elemento:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> entonces el valor de `%(MyItem.RecursiveDir)` sería *MySolution\MyProject\Source\\* .|
|%(Identity)|El elemento especificado en el atributo `Include`. Por ejemplo:<br /><br /> *Source\Program.cs*|
|%(ModifiedTime)|Contiene la marca de tiempo correspondiente a la última modificación del elemento. Por ejemplo:<br /><br /> `2004-07-01 00:21:31.5073316`|
|%(CreatedTime)|Contiene la marca de tiempo correspondiente a la creación del elemento. Por ejemplo:<br /><br /> `2004-06-25 09:26:45.8237425`|
|%(AccessedTime)|Contiene la marca de tiempo correspondiente a la última vez que se tuvo acceso al elemento.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Consulte también

- [Metadatos de elementos MSBuild comunes](common-msbuild-item-metadata.md)
- [Elementos](../msbuild/msbuild-items.md)
- [Procesamiento por lotes](../msbuild/msbuild-batching.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
