---
title: Procedimiento Compilar los mismos archivos de código fuente con diferentes opciones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- source files, building with different options
- MSBuild, properties
- project properties, modifying
- Hello World example [Visual Studio]
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3bce742d4ce0374cb7270b964354d65a03e917d0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045608"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Procedimiento Compilar los mismos archivos de código fuente con diferentes opciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al compilar proyectos, con frecuencia se compilan los mismos componentes con distintas opciones de compilación. Por ejemplo, puede crear una compilación de depuración con información de símbolos o una compilación de versión sin información de símbolos, pero con optimizaciones habilitadas. También puede compilar un proyecto que se ejecute en una plataforma concreta, como x86 o [!INCLUDE[vcprx64](../includes/vcprx64-md.md)]. En todos estos casos, la mayoría de las opciones de compilación permanecen iguales; solo unas cuantas opciones cambian para controlar la configuración de compilación. Con [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], se utilizan propiedades y condiciones para crear configuraciones de compilación diferentes.  
  
## <a name="using-properties-to-modify-projects"></a>Usar propiedades para modificar proyectos  
 El elemento `Property` define una variable a la cual se hace referencia varias veces en un archivo de proyecto, como la ubicación de un directorio temporal, o para establecer los valores de propiedades que se utilizan en varias configuraciones, como una compilación de depuración y una compilación de versión. Para obtener más información sobre las propiedades, consulte [Propiedades de MSBuild](msbuild-properties1.md).  
  
 Puede usar las propiedades para cambiar la configuración de la compilación sin tener que cambiar el archivo de proyecto. El atributo `Condition` de los elementos `Property` y `PropertyGroup` le permite cambiar el valor de las propiedades. Para obtener más información sobre las condiciones de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], consulte [Condiciones](../msbuild/msbuild-conditions.md).  
  
#### <a name="to-set-a-group-of-properties-based-on-another-property"></a>Para establecer un grupo de propiedades basado en otra propiedad  
  
- Utilice un atributo `Condition` en un elemento `PropertyGroup` similar al siguiente:  
  
    ```  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
    ```  
  
#### <a name="to-define-a-property-based-on-another-property"></a>Para definir una propiedad basada en otra propiedad  
  
- Use un atributo `Condition` en un elemento `Property` similar al siguiente:  
  
    ```  
    <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>  
    ```  
  
## <a name="specifying-properties-on-the-command-line"></a>Especificar propiedades en la línea de comandos  
 Una vez que el archivo de proyecto está escrito para aceptar varias configuraciones, debe tener la capacidad de cambiar dichas configuraciones siempre que compile el proyecto. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proporciona esta capacidad al permitir especificar propiedades en la línea de comandos mediante los modificadores **/Property** o **/p**.  
  
#### <a name="to-set-a-project-property-at-the-command-line"></a>Para establecer una propiedad de proyecto en la línea de comandos  
  
- Utilice el modificador **/property** con la propiedad y el valor de la propiedad. Por ejemplo:  
  
    ```  
    msbuild file.proj /property:Flavor=Debug  
    ```  
  
     - O  
  
    ```  
    Msbuild file.proj /p:Flavor=Debug  
    ```  
  
#### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Para especificar más de una propiedad del proyecto en la línea de comandos  
  
- Use el modificador **/property** o **/p** varias veces con la propiedad y los valores de la propiedad, o use un modificador **/property** o **/p** y separe varias propiedades con punto y coma (;). Por ejemplo:  
  
  ```  
  msbuild file.proj /p:Flavor=Debug;Platform=x86  
  ```  
  
   - o bien:  
  
  ```  
  msbuild file.proj /p:Flavor=Debug /p:Platform=x86  
  ```  
  
  Las variables de entorno también se tratan como propiedades y se incorporan automáticamente mediante [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Para obtener más información sobre cómo usar variables de entorno, vea [Cómo: Usar Variables de entorno en una compilación](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
  El valor de propiedad que se especifica en la línea de comandos tiene prioridad sobre cualquier valor que se establece para la misma propiedad en el archivo de proyecto, y ese valor en el archivo de proyecto tiene prioridad sobre el valor de una variable de entorno.  
  
  Puede cambiar este comportamiento mediante el atributo `TreatAsLocalProperty` en una etiqueta de proyecto. Para los nombres de propiedad que se muestran con ese atributo, el valor de propiedad que se especifica en la línea de comandos no tiene prioridad sobre el valor en el archivo de proyecto. Más adelante en este tema encontrará un ejemplo.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente, el proyecto "Hello World", contiene dos grupos de propiedades nuevas que se pueden utilizar para crear una compilación de depuración y una compilación de versión.  
  
 Para compilar la versión de depuración de este proyecto, escriba:  
  
```  
msbuild consolehwcs1.proj /p:flavor=debug  
```  
  
 Para compilar la versión comercial de este proyecto, escriba:  
  
```  
msbuild consolehwcs1.proj /p:flavor=retail  
```  
  
```  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <!-- Sets the default flavor of an environment variable called   
    Flavor is not set or specified on the command line -->  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
    </PropertyGroup>  
  
    <!-- Define the DEBUG settings -->  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
  
    <!-- Define the RETAIL settings -->  
    <PropertyGroup Condition="'$(Flavor)'=='RETAIL'">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>yes</Optimize>  
    </PropertyGroup>  
  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>HelloWorldCS</appname>  
    </PropertyGroup>  
  
    <!-- Specify the inputs by type and file name -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input files  
        of type CSFile -->  
        <CSC  Sources = "@(CSFile)"  
            DebugType="$(DebugType)"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe" >  
  
            <!-- Set the OutputAssembly attribute of the CSC  
            task to the name of the executable file that is   
            created -->  
            <Output TaskParameter="OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el atributo `TreatAsLocalProperty`. La propiedad `Color` tiene un valor de `Blue` en el archivo de proyecto y de `Green` en la línea de comandos. Con `TreatAsLocalProperty="Color"` en la etiqueta del proyecto, la propiedad en la línea de comandos (`Green`) no invalida la propiedad que se define en el archivo del proyecto (`Blue`).  
  
 Para compilar el proyecto, escriba el siguiente comando:  
  
```  
msbuild colortest.proj /t:go /property:Color=Green  
```  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0" TreatAsLocalProperty="Color">  
  
    <PropertyGroup>  
        <Color>Blue</Color>  
    </PropertyGroup>  
  
    <Target Name="go">  
        <Message Text="Color: $(Color)" />  
    </Target>  
</Project>  
  
<!--  
  Output with TreatAsLocalProperty="Color" in project tag:  
     Color: Blue  
  
  Output without TreatAsLocalProperty="Color" in project tag:  
     Color: Green  
-->  
```  
  
## <a name="see-also"></a>Vea también  
[MSBuild](msbuild.md)  
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Elemento Project (MSBuild)](../msbuild/project-element-msbuild.md)
