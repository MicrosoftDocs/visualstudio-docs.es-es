---
title: Uso del mismo destino en varios archivos de proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41c1ed02a32136d6c80e24f0644e0fab660e8ed0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Cómo: Utilizar el mismo destino en varios archivos de proyecto
Si ha creado varios archivos de proyecto con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], es posible que haya detectado la necesidad de utilizar las mismas tareas y destinos en los distintos archivos de proyecto. En lugar de incluir la descripción completa de estas tareas o destinos en cada archivo de proyecto, puede guardar un destino en un archivo de proyecto independiente y, a continuación, importarlo en un proyecto que necesite utilizar dicho destino.  
  
## <a name="using-the-import-element"></a>Uso del elemento Import  
 El elemento `Import` se utiliza para insertar un archivo de proyecto en otro archivo de proyecto. El archivo de proyecto que se importa debe ser un archivo de proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] válido y contener código XML correcto. El atributo `Project` especifica la ruta de acceso al archivo de proyecto importado. Para obtener más información sobre el elemento `Import`, vea [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md).  
  
#### <a name="to-import-a-project"></a>Para importar un proyecto  
  
1.  En el archivo de proyecto de importación, defina todas las propiedades y elementos utilizados como parámetros para las propiedades y elementos del proyecto importado.  
  
2.  Utilice el elemento `Import` para importar el proyecto. Por ejemplo:  
  
     `<Import Project="MyCommon.targets"/>`  
  
3.  A continuación del elemento `Import`, defina todas las propiedades y elementos que deben reemplazar las definiciones predeterminadas de las propiedades y los elementos del proyecto importado.  
  
## <a name="order-of-evaluation"></a>Orden de evaluación  
 Cuando [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] alcanza un elemento `Import`, el proyecto importado se inserta de manera efectiva en el proyecto de importación en la ubicación del elemento `Import`. Por tanto, la ubicación del elemento `Import` puede afectar a los valores de propiedades y elementos. Es importante comprender las propiedades y elementos que especifica el proyecto importado, así como las propiedades y los elementos que utiliza dicho proyecto.  
  
 Cuando se compila el proyecto, primero se evalúan todas las propiedades y después, los elementos. Por ejemplo, en el código XML siguiente se define el archivo de proyecto importado MyCommon.targets:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyCommon</Name>  
    </PropertyGroup>  
  
    <Target Name="Go">  
        <Message Text="Name=$(Name)"/>  
    </Target>  
</Project>  
```  
  
 En el código XML siguiente se define MyApp.proj, que importa MyCommon.targets:  
  
```xml  
<Project  
    DefaultTargets="Go"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyApp</Name>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
 Cuando se compila el proyecto, se muestra el mensaje siguiente:  
  
 `Name="MyCommon"`  
  
 Dado que el proyecto se importa una vez definida la propiedad `Name` en MyApp.proj, la definición de `Name` en MyCommon.targets reemplaza la definición en MyApp.proj. Si se importara el proyecto antes de definir la propiedad Name, la compilación mostraría el siguiente mensaje:  
  
 `Name="MyApp"`  
  
#### <a name="use-the-following-approach-when-importing-projects"></a>Utilice el enfoque siguiente al importar los proyectos  
  
1.  En el archivo de proyecto, defina todas las propiedades y los elementos utilizados como parámetros para las propiedades y los elementos del proyecto importado.  
  
2.  Importe el proyecto.  
  
3.  En el archivo de proyecto, defina todas las propiedades y los elementos que deben reemplazar las definiciones predeterminadas de propiedades y elementos del proyecto importado.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra el archivo MyCommon.targets importado por el segundo ejemplo de código. El archivo .targets evalúa las propiedades del proyecto de importación para configurar la compilación.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>  
        <appname>$(MSBuildProjectName)</appname>  
    <PropertyGroup>  
    <Target Name="Build">  
        <Csc Sources="hello.cs"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se importa el archivo MyCommon.targets.  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor>RETAIL</Flavor>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
## <a name="see-also"></a>Vea también  
 [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Destinos](../msbuild/msbuild-targets.md)