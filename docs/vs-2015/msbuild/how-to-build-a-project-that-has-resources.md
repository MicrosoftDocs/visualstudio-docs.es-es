---
title: 'Cómo: Compilar un proyecto que tiene recursos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fb77db891e824f5f2900ef191049e65cb2c89a98
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686515"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Cómo: Compilar un proyecto que tiene recursos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si está compilando versiones adaptadas de un proyecto, todos los elementos de la interfaz de usuario deben estar separados en archivos de recursos para los distintos idiomas. Si el proyecto utiliza solo cadenas, los archivos de recursos pueden utilizar archivos de texto. Como alternativa, puede utilizar archivos .resx como los archivos de recursos.  
  
## <a name="compiling-resources-with-msbuild"></a>Compilar recursos con MSBuild  
 La biblioteca de tareas comunes que se proporciona con [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] incluye una tarea `GenerateResource` que se puede utilizar para compilar recursos en archivos .resx o de texto. Esta tarea incluye los parámetros `Sources` para especificar qué recursos de archivos se deben compilar y `OutputResources` para especificar nombres para los archivos de recursos de salida. Para obtener más información sobre la tarea `GenerateResource`, consulte [GenerateResource (Tarea)](../msbuild/generateresource-task.md).  
  
#### <a name="to-compile-resources-with-msbuild"></a>Para compilar recursos con MSBuild  
  
1. Identifique los archivos de recursos del proyecto y páselos a la tarea `GenerateResource`, ya sea como listas de elementos o como nombres de archivo.  
  
2. Especifique el parámetro `OutputResources` de la tarea `GenerateResource`, lo que permite establecer los nombres de los archivos de recursos de salida.  
  
3. Utilice el elemento `Output` de la tarea para almacenar el valor del parámetro `OutputResources` en un elemento.  
  
4. Utilice el elemento creado a partir del elemento `Output` como una entrada en otra tarea.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo de código se muestra cómo el elemento `Output` especifica que el atributo `OutputResources` de la tarea `GenerateResource` contendrá los archivos de recursos compilados `alpha.resources` y `beta.resources` y que estos dos archivos se colocarán dentro de la lista de elementos `Resources`. Mediante la identificación de estos archivos .resources como una colección de elementos del mismo nombre, puede utilizarlos fácilmente como entradas para otra tarea, como la tarea [Csc](../msbuild/csc-task.md).  
  
 Esta tarea es equivalente a utilizar el modificador **/compile** para [Resgen.exe](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4):  
  
 `Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`  
  
```  
<GenerateResource  
    Sources="alpha.resx; beta.txt"  
    OutputResources="alpha.resources; beta.resources">  
    <Output TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
## <a name="example"></a>Ejemplo  
 El siguiente proyecto de ejemplo contiene dos tareas: la tarea `GenerateResource` para compilar recursos y la tarea `Csc` para compilar los archivos de código fuente y los archivos de recursos compilados. Los archivos de recursos compilados por la tarea `GenerateResource` se almacenan en el elemento `Resources` y se pasan a la tarea `Csc`.  
  
```  
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
[MSBuild](msbuild.md)  
 [GenerateResource (tarea)](../msbuild/generateresource-task.md)   
 [Csc (tarea)](../msbuild/csc-task.md)   
 [Resgen.exe (generador de archivos de recursos)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)
