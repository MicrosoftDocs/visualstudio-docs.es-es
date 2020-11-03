---
title: Procedimiento Compilar un proyecto que tiene recursos | Microsoft Docs
description: Obtenga información sobre cómo compilar un proyecto que tiene recursos y cómo compilar recursos mediante MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e6a71a34b4ce208b093f7982ba3516b0229c8644
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436682"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Cómo: Compilar un proyecto que tiene recursos

Si está compilando versiones adaptadas de un proyecto, todos los elementos de la interfaz de usuario deben estar separados en archivos de recursos para los distintos idiomas. Si el proyecto utiliza solo cadenas, los archivos de recursos pueden utilizar archivos de texto. Como alternativa, puede usar archivos *.resx* como los archivos de recursos.

## <a name="compile-resources-with-msbuild"></a>Compilación de recursos con MSBuild

La biblioteca de tareas comunes que se proporciona con MSBuild incluye una tarea `GenerateResource` que se puede usar para compilar recursos en archivos *.resx* o de texto. Esta tarea incluye los parámetros `Sources` para especificar qué recursos de archivos se deben compilar y `OutputResources` para especificar nombres para los archivos de recursos de salida. Para obtener más información sobre la tarea `GenerateResource`, vea [GenerateResource (Tarea)](../msbuild/generateresource-task.md).

#### <a name="to-compile-resources-with-msbuild"></a>Para compilar recursos con MSBuild

1. Identifique los archivos de recursos del proyecto y páselos a la tarea `GenerateResource`, ya sea como listas de elementos o como nombres de archivo.

2. Especifique el parámetro `OutputResources` de la tarea `GenerateResource`, lo que permite establecer los nombres de los archivos de recursos de salida.

3. Utilice el elemento `Output` de la tarea para almacenar el valor del parámetro `OutputResources` en un elemento.

4. Utilice el elemento creado a partir del elemento `Output` como una entrada en otra tarea.

## <a name="example-1"></a>Ejemplo 1

En el siguiente ejemplo de código se muestra cómo el elemento `Output` especifica que el atributo `OutputResources` de la tarea `GenerateResource` va a contener los archivos de recursos compilados *alpha.resources* y *beta.resources* y que estos dos archivos se van a colocar dentro de la lista de elementos `Resources`. Al identificar estos archivos *.resources* como una colección de elementos del mismo nombre, puede usarlos fácilmente como entradas para otra tarea, como la tarea [Csc](../msbuild/csc-task.md).

Esta tarea es equivalente a utilizar el modificador **/compile** para [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator):

`Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`

```xml
<GenerateResource
    Sources="alpha.resx; beta.txt"
    OutputResources="alpha.resources; beta.resources">
    <Output TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

## <a name="example-2"></a>Ejemplo 2

El siguiente proyecto de ejemplo contiene dos tareas: la tarea `GenerateResource` para compilar recursos y la tarea `Csc` para compilar los archivos de código fuente y los archivos de recursos compilados. Los archivos de recursos compilados por la tarea `GenerateResource` se almacenan en el elemento `Resources` y se pasan a la tarea `Csc`.

```xml
<Project DefaultTargets = "Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <Target Name="Resources">
        <GenerateResource
            Sources="alpha.resx; beta.txt"
            OutputResources="alpha.resources; beta.resources">
            <Output TaskParameter="OutputResources"
                ItemName="Resources"/>
        </GenerateResource>
    </Target>

    <Target Name="Build" DependsOnTargets="Resources">
        <Csc Sources="hello.cs"
                Resources="@(Resources)"
                OutputAssembly="hello.exe"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Vea también

- [MSBuild](../msbuild/msbuild.md)
- [GenerateResource (tarea)](../msbuild/generateresource-task.md)
- [Tarea Csc](../msbuild/csc-task.md)
- [Resgen.exe (generador de archivos de recursos)](/dotnet/framework/tools/resgen-exe-resource-file-generator)
