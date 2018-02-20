---
title: "Cómo: Hacer referencia al nombre o la ubicación del archivo de proyecto | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7a688473b4657d905397d4798451b4860578ef0d
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Cómo: Hacer referencia al nombre o ubicación del archivo de proyecto
Puede utilizar el nombre o la ubicación del proyecto en el archivo del proyecto sin tener que crear su propia propiedad. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proporciona propiedades reservadas que hacen referencia al nombre de archivo del proyecto y a otras propiedades relacionadas con el proyecto. Para obtener más información sobre las propiedades reservadas, consulte [Propiedades reservadas y conocidas de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="using-the-msbuildprojectname-property"></a>Utilizar la propiedad MSBuildProjectName  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proporciona algunas propiedades reservadas que se pueden usar en los archivos del proyecto sin tener que definirlas cada vez. Por ejemplo, la propiedad reservada `MSBuildProjectName` proporciona una referencia al nombre del archivo del proyecto.  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>Para utilizar la propiedad MSBuildProjectName  
  
-   Haga referencia a la propiedad en el archivo del proyecto con la notación $(), como haría con cualquier propiedad. Por ejemplo:  
  
    ```xml  
    <CSC Sources = "@(CSFile)"   
        OutputAssembly = "$(MSBuildProjectName).exe"/>  
    </CSC>  
    ```  
  
 Una ventaja de utilizar una propiedad reservada es que cualquier cambio en el nombre del archivo del proyecto se incorpora automáticamente. La próxima vez que compile el proyecto, el archivo de salida tendrá el nuevo nombre, sin que tenga que hacer nada más.  
  
> [!NOTE]
>  Las propiedades reservadas no se pueden volver a definir en el archivo del proyecto.  
  
## <a name="example"></a>Ejemplo  
 El siguiente archivo del proyecto de ejemplo hace referencia al nombre del proyecto como una propiedad reservada para especificar el nombre de salida.  
  
```xml  
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vea también  
[MSBuild](../msbuild/msbuild.md)  
 [Propiedades reservadas y conocidas de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)