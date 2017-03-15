---
title: "Cómo: Compilar un proyecto que tiene recursos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
caps.latest.revision: 14
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: f0c10c20b96ebbbaaad4047349d7586b584b8b57
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-build-a-project-that-has-resources"></a>Cómo: Compilar un proyecto que tiene recursos
Si está compilando versiones adaptadas de un proyecto, todos los elementos de la interfaz de usuario deben estar separados en archivos de recursos para los distintos idiomas. Si el proyecto utiliza solo cadenas, los archivos de recursos pueden utilizar archivos de texto. Como alternativa, puede utilizar archivos .resx como los archivos de recursos.  
  
## <a name="compiling-resources-with-msbuild"></a>Compilar recursos con MSBuild  
 La biblioteca de tareas comunes que se proporciona con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] incluye una tarea `GenerateResource` que se puede utilizar para compilar recursos en archivos .resx o de texto. Esta tarea incluye los parámetros `Sources` para especificar qué recursos de archivos se deben compilar y `OutputResources` para especificar nombres para los archivos de recursos de salida. Para obtener más información sobre la tarea `GenerateResource`, consulte [GenerateResource (Tarea)](../msbuild/generateresource-task.md).  
  
#### <a name="to-compile-resources-with-msbuild"></a>Para compilar recursos con MSBuild  
  
1.  Identifique los archivos de recursos del proyecto y páselos a la tarea `GenerateResource`, ya sea como listas de elementos o como nombres de archivo.  
  
2.  Especifique el parámetro `OutputResources` de la tarea `GenerateResource`, lo que permite establecer los nombres de los archivos de recursos de salida.  
  
3.  Utilice el elemento `Output` de la tarea para almacenar el valor del parámetro `OutputResources` en un elemento.  
  
4.  Utilice el elemento creado a partir del elemento `Output` como una entrada en otra tarea.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo de código se muestra cómo el elemento `Output` especifica que el atributo `OutputResources` de la tarea `GenerateResource` contendrá los archivos de recursos compilados `alpha.resources` y `beta.resources` y que estos dos archivos se colocarán dentro de la lista de elementos `Resources`. Mediante la identificación de estos archivos .resources como una colección de elementos del mismo nombre, puede utilizarlos fácilmente como entradas para otra tarea, como la tarea [Csc](../msbuild/csc-task.md).  
  
 Esta tarea es equivalente a utilizar el modificador **/compile** para [Resgen.exe](http://msdn.microsoft.com/Library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4):  
  
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
 [GenerateResource (tarea)](../msbuild/generateresource-task.md)   
 [Csc (tarea)](../msbuild/csc-task.md)   
 [Resgen.exe (generador de archivos de recursos)](http://msdn.microsoft.com/Library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)
