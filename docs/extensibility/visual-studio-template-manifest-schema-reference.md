---
title: Visual Studio referencia de esquema de manifiesto de plantilla | Microsoft Docs
description: Esta referencia de esquema describe el formato de los archivos de manifiesto Visual Studio plantilla que se generan para las plantillas Visual Studio proyecto o elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 259d2dd050f4681053f331bfd4ec39dd7b214059
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905389"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio de esquema de manifiesto de plantilla
Este esquema describe el formato de los archivos de manifiesto Visual Studio plantilla *(.vstman)* que se generan para las plantillas Visual Studio proyecto o elemento. El esquema también describe la ubicación y otra información relevante sobre la plantilla.

 : dado que hay directorios de plantilla de proyecto y elemento independientes, un manifiesto nunca debe tener una combinación de plantillas de elemento y de proyecto.

> [!IMPORTANT]
> Este manifiesto está disponible a partir de Visual Studio 2017.

## <a name="vstemplatemanifest-element"></a>Elemento VSTemplateManifest
 Elemento raíz del manifiesto.

### <a name="attributes"></a>Atributos

- **Versión:** cadena que representa la versión del manifiesto de plantilla. Necesario.

- **Configuración regional:** cadena que representa la configuración regional o las configuraciones regionales del manifiesto de plantilla. El valor de configuración regional se aplica a todas las plantillas. Debe usar un manifiesto independiente para cada configuración regional. Opcional.

### <a name="child-elements"></a>Elementos secundarios

- **VSTemplateContainer** Opcional.

- **VSTemplateDir** Opcional.

### <a name="parent-element"></a>Elemento primario
 Ninguno.

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Contenedor de los elementos del manifiesto de plantilla. Un manifiesto tiene un contenedor de plantillas para cada plantilla que define.

### <a name="attributes"></a>Atributos
 **VSTemplateType:** valor de cadena que especifica el tipo de la plantilla ( `"Project"` `"Item"` , o `"ProjectGroup"` ). Obligatorio

### <a name="child-elements"></a>Elementos secundarios

- **RelativePathOnDisk:** ruta de acceso relativa del archivo de plantilla en disco. Esta ubicación también define la ubicación de la plantilla en el árbol de plantillas que se muestra en el **cuadro de diálogo** Nuevo proyecto o **Nuevo** elemento. Para las plantillas implementadas como un directorio y archivos individuales, esta ruta de acceso hace referencia al directorio que contiene los archivos de plantilla. Para las plantillas implementadas *como un.zip,* esta ruta de acceso debe ser la ruta de *acceso.zip* archivo.

- **VSTemplateHeader: elemento [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) que describe el encabezado.

### <a name="parent-element"></a>Elemento primario
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Describe el directorio donde se encuentra la plantilla. Un manifiesto puede contener varias **entradas VSTemplateDir** para proporcionar el nombre localizado y la ordenación de los directorios para controlar su apariencia en el árbol de categorías de plantilla.

 Debido a su diseño, las **entradas de VSTemplateDir** solo deben aparecer en manifiestos no especificados de configuración regional.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios

- **RelativePath:** ruta de acceso de la plantilla. Solo puede haber una entrada por ruta de acceso, por lo que la primera ganará para todos los manifiestos.

- **LocalizedName:** elemento **NameDescriptionIcon** que especifica el nombre localizado. Opcional.

- **SortOrder:** cadena que especifica el criterio de ordenación. Opcional.

- **ParentFolderOverrideName:** nombre invalidado de la carpeta primaria. Opcional. Este elemento tiene un **atributo Name,** que es un valor de cadena que especifica el nombre.

### <a name="parent-element"></a>Elemento primario
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 Especifica el nombre y la descripción, posiblemente para las plantillas localizadas. Consulte **LocalizedName anteriormente.**

### <a name="attributes"></a>Atributos

- **Paquete:** valor de cadena que especifica el paquete. Opcional.

- **ID:** valor de cadena que especifica el identificador. Opcional.

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-element"></a>Elemento primario
 **LocalizedName**

## <a name="examples"></a>Ejemplos
 El código siguiente es un ejemplo de un archivo *.vstman de* plantilla de proyecto.

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

 El código siguiente es un ejemplo de un archivo *.vstman de* plantilla de elemento.

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
