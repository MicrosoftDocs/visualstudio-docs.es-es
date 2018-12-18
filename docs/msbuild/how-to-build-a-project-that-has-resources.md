---
title: 'Cómo: Compilar un proyecto que tiene recursos | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e7724969a4677bc0d8480b794ae72b2dbee74a86
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180352"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Cómo: Compilar un proyecto que tiene recursos
Si está compilando versiones adaptadas de un proyecto, todos los elementos de la interfaz de usuario deben estar separados en archivos de recursos para los distintos idiomas. Si el proyecto utiliza solo cadenas, los archivos de recursos pueden utilizar archivos de texto. Como alternativa, puede usar archivos *.resx* como los archivos de recursos.  
  
## <a name="compile-resources-with-msbuild"></a>Compilación de recursos con MSBuild  
 La biblioteca de tareas comunes que se proporciona con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] incluye una tarea `GenerateResource` que se puede usar para compilar recursos en archivos *.resx* o de texto. Esta tarea incluye los parámetros `Sources` para especificar qué recursos de archivos se deben compilar y `OutputResources` para especificar nombres para los archivos de recursos de salida. Para obtener más información sobre la tarea `GenerateResource`, vea [GenerateResource (Tarea)](../msbuild/generateresource-task.md).  
  
#### <a name="to-compile-resources-with-msbuild"></a>Para compilar recursos con MSBuild  
  
1.  Identifique los archivos de recursos del proyecto y páselos a la tarea `GenerateResource`, ya sea como listas de elementos o como nombres de archivo.  
  
2.  Especifique el parámetro `OutputResources` de la tarea `GenerateResource`, lo que permite establecer los nombres de los archivos de recursos de salida.  
  
3.  Utilice el elemento `Output` de la tarea para almacenar el valor del parámetro `OutputResources` en un elemento.  
  
4.  Utilice el elemento creado a partir del elemento `Output` como una entrada en otra tarea.  
  
## <a name="example"></a>Ejemplo  
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
  
## <a name="example"></a>Ejemplo  
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
[MSBuild](../msbuild/msbuild.md)  
 [GenerateResource (Tarea)](../msbuild/generateresource-task.md)   
 [Csc (Tarea)](../msbuild/csc-task.md)   
 [Resgen.exe (generador de archivos de recursos)](/dotnet/framework/tools/resgen-exe-resource-file-generator)