---
title: Referencia de esquema de manifiesto de plantilla de Visual Studio | Microsoft Docs
description: Esta referencia de esquema describe el formato de los archivos de manifiesto de la plantilla de Visual Studio que se generan para las plantillas de proyecto o de elemento de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5f251b4511e2bff5bc20172e4018560205a378e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925838"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Referencia de esquema de manifiesto de plantilla de Visual Studio
Este esquema describe el formato de los archivos de manifiesto de plantilla de Visual Studio (*. vstman*) que se generan para las plantillas de proyecto o elemento de Visual Studio. El esquema también describe la ubicación y otra información relevante sobre la plantilla.

 : Dado que hay directorios de elementos y plantillas de proyecto independientes, un manifiesto nunca debe tener una combinación de plantillas de proyecto y elemento.

> [!IMPORTANT]
> Este manifiesto está disponible a partir de Visual Studio 2017.

## <a name="vstemplatemanifest-element"></a>Elemento VSTemplateManifest
 Elemento raíz del manifiesto.

### <a name="attributes"></a>Atributos

- **Versión**: una cadena que representa la versión del manifiesto de la plantilla. Necesario.

- **Locale**: una cadena que representa la configuración regional o las configuraciones regionales del manifiesto de la plantilla. El valor de configuración regional se aplica a todas las plantillas. Debe usar un manifiesto independiente para cada configuración regional. Opcional.

### <a name="child-elements"></a>Elementos secundarios

- **VSTemplateContainer** Opta.

- **VSTemplateDir** Opta.

### <a name="parent-element"></a>Elemento primario
 Ninguno.

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Contenedor de los elementos de manifiesto de la plantilla. Un manifiesto tiene un contenedor de plantilla para cada plantilla que define.

### <a name="attributes"></a>Atributos
 **VSTemplateType**: valor de cadena que especifica el tipo de la plantilla ( `"Project"` , `"Item"` o `"ProjectGroup"` ). Obligatorio

### <a name="child-elements"></a>Elementos secundarios

- **RelativePathOnDisk**: ruta de acceso relativa del archivo de plantilla en el disco. Esta ubicación también define la ubicación de la plantilla en el árbol de la plantilla que se muestra en el cuadro de diálogo **nuevo proyecto** o **nuevo elemento** . En el caso de las plantillas implementadas como un directorio y archivos individuales, esta ruta de acceso hace referencia al directorio que contiene los archivos de plantilla. En el caso de las plantillas implementadas como archivo *. zip* , esta ruta de acceso debe ser la ruta de acceso al archivo *. zip* .

- * * VSTemplateHeader: un elemento [TemplateData (](../extensibility/templatedata-element-visual-studio-templates.md) que describe el encabezado.

### <a name="parent-element"></a>Elemento primario
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Describe el directorio donde se encuentra la plantilla. Un manifiesto puede contener varias entradas **VSTemplateDir** para proporcionar un nombre localizado y un orden de ordenación para que los directorios controlen su apariencia en el árbol de categorías de plantilla.

 Debido a su diseño, las entradas de **VSTemplateDir** solo deberían aparecer en los manifiestos especificados no de la configuración regional.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios

- **RelativePath**: la ruta de acceso de la plantilla. Solo puede haber una entrada por ruta de acceso, por lo que la primera ganará en todos los manifiestos.

- **LocalizedName**: un elemento **NameDescriptionIcon** que especifica el nombre localizado. Opcional.

- **SortOrder**: una cadena que especifica el criterio de ordenación. Opcional.

- **ParentFolderOverrideName**: el nombre invalidado de la carpeta principal. Opcional. Este elemento tiene un atributo **Name** , que es un valor de cadena que especifica el nombre.

### <a name="parent-element"></a>Elemento primario
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 Especifica el nombre y la descripción, posiblemente para plantillas localizadas. Consulte **LocalizedName** anterior.

### <a name="attributes"></a>Atributos

- **Paquete**: valor de cadena que especifica el paquete. Opcional.

- **ID**: valor de cadena que especifica el identificador. Opcional.

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-element"></a>Elemento primario
 **LocalizedName**

## <a name="examples"></a>Ejemplos
 El código siguiente es un ejemplo de un archivo de plantilla de proyecto *. vstman* .

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>TestProjectTemplate</Name>
        <Description>TestProjectTemplate</Description>
        <Icon>TestProjectTemplate.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>TestProjectTemplate</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 El código siguiente es un ejemplo de un archivo de plantilla de elemento *. vstman* .

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```
