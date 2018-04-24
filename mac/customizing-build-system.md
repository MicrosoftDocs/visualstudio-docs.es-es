---
title: Personalización del sistema de compilación
description: ''
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 649289700aa984235f432528a59b970762d26be0
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="customizing-the-build-system"></a>Personalización del sistema de compilación

MSBuild es un motor de compilación desarrollado por Microsoft que permite la compilación de aplicaciones de .NET principalmente. El marco de trabajo Mono además tiene su propia implementación del motor de compilación de Microsoft, denominado **xbuild**. Pero xbuild ha quedado desfasado en favor de MSBuild en todos los sistemas operativos.

**MSBuild** se usa principalmente como sistema de compilación para los proyectos de Visual Studio para Mac. 

MSBuild toma un conjunto de entradas, como archivos de código fuente, y las transforma en salidas, como archivos ejecutables. Consigue este resultado mediante la invocación de herramientas como el compilador. 


## <a name="msbuild-file"></a>Archivo de MSBuild

MSBuild usa un archivo XML, denominado archivo de proyecto, que define los *elementos* que forman parte del proyecto (por ejemplo, los recursos de imagen) y las *propiedades* necesarias para compilar el proyecto. Este archivo de proyecto siempre tiene una extensión de archivo que termina en `proj`, como `.csproj` para proyectos de C#. 

### <a name="viewing-the-msbuild-file"></a>Visualización del archivo de MSBuild

Para buscar el archivo MSBuild, haga clic con el botón derecho en el nombre del proyecto y seleccione **Mostrar en Finder**. La ventana de Finder muestra todos los archivos y las carpetas relacionados con el proyecto, incluido el archivo `.csproj`, como se muestra en la imagen siguiente:

![](media/customizing-build-system-image1.png)

Para mostrar el archivo `.csproj` en una nueva pestaña de Visual Studio para Mac, haga clic con el botón derecho en el nombre del proyecto y vaya a **Herramientas > Editar archivo**:

![](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>Composición del archivo de MSBuild

Todos los archivos de MSBuild contienen un elemento raíz obligatorio `Project`, como:

```
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

Normalmente, el proyecto también importará un archivo `.targets`. Este archivo contiene muchas de las reglas que describen cómo procesar y compilar los distintos archivos. La importación normalmente aparece hacia la parte inferior del archivo `proj` y, en los proyectos de C#, su aspecto es similar al siguiente:

```
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

El archivo de destinos es otro archivo de MSBuild. Este archivo contiene código de MSBuild que se puede reutilizar en varios proyectos. Por ejemplo, el archivo `Microsoft.CSharp.targets`, que se encuentra en un directorio representado por la propiedad `MSBuildBinPath` (o variable), contiene la lógica para compilar ensamblados de C# a partir de archivos de código fuente de C#.

### <a name="items-and-properties"></a>Elementos y propiedades

Hay dos tipos de datos fundamentales en MSBuild: *elementos* y *propiedades*, que se explican más detalladamente en las secciones siguientes.

#### <a name="properties"></a>Propiedades

Las propiedades son pares clave-valor que se usan para almacenar valores que afectan a la compilación, como las opciones del compilador.

Se establecen mediante un elemento PropertyGroup y pueden contener cualquier número de elementos PropertiesGroups, que pueden contener cualquier número de propiedades. 

Por ejemplo, el elemento PropertyGroup de una aplicación de consola sencilla podría parecerse al siguiente XML:

```
<PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
        <ProjectGuid>{E248730E-1393-43CC-9183-FFA42F63BE81}</ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>refactoring</RootNamespace>
        <AssemblyName>refactoring</AssemblyName>
        <TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
    </PropertyGroup>
```

Con la sintaxis `$()` se puede hacer referencia a propiedades desde expresiones. Por ejemplo, `$(Foo)` se evalúa como el valor de la propiedad `Foo`. Si no se ha establecido la propiedad, se evalúa como una cadena vacía, sin ningún error.

#### <a name="items"></a>Elementos

Los elementos proporcionan una manera de trabajar con entradas del sistema de compilación, como listas o conjuntos, y suelen representar a archivos. Cada elemento tiene un *tipo* de elemento, una *especificación* de elemento y *metadatos* opcionales arbitrarios. Tenga en cuenta que MSBuild no funciona en elementos individuales, sino que toma todos los elementos de un tipo dado, lo que se denomina un *conjunto* de elementos.

Los elementos se crean al declarar un `ItemGroup`. Puede haber cualquier número de elementos ItemGroups, que pueden contener cualquier número de elementos. 

Por ejemplo, el siguiente fragmento de código crea las pantallas de inicio de iOS. Las pantallas de inicio tienen el tipo de compilación `BundleResource`, con la especificación como ruta de acceso a la imagen:

```
 <ItemGroup>
    <BundleResource Include="Resources\Default-568h%402x.png" />
    <BundleResource Include="Resources\Default%402x.png" />
    <BundleResource Include="Resources\Default.png" />
    <BundleResource Include="Resources\Default-Portrait.png" />
    <BundleResource Include="Resources\Default-Portrait%402x.png" />
    <BundleResource Include="Resources\Default-Landscape%402x.png" />
  </ItemGroup>
 ```
 
 Con la sintaxis `@()` se puede hacer referencia a conjuntos de elementos desde expresiones. Por ejemplo, `@(BundleResource)` se evalúa como el conjunto de elementos BundleResource, lo que significa todos los elementos de BundleResource. Si no hay ningún elemento de este tipo, estará vacío, sin ningún error.

## <a name="resources-for-learning-msbuild"></a>Recursos de aprendizaje de MSBuild

Los siguientes recursos pueden usarse para obtener información más detallada sobre MSBuild:

* [Información general sobre MSDN](https://msdn.microsoft.com/library/dd393574.aspx)
* [Conceptos de MSDN](https://msdn.microsoft.com/library/dd637714.aspx)


