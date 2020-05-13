---
title: Referencia de esquema de manifiesto de plantilla de Visual Studio ( Visual Studio Template Schema Reference ) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbe46851d9df85569be796b4147217bd7db450ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697981"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Referencia de esquema de manifiesto de plantilla de Visual Studio
Este esquema describe el formato de los archivos de manifiesto de plantilla de Visual Studio (*.vstman*) que se generan para las plantillas de proyecto o elemento de Visual Studio. El esquema también describe la ubicación y otra información relevante sobre la plantilla.

 : Dado que hay directorios de plantillas de proyecto y elemento sin elementos, un manifiesto nunca debe tener una combinación de plantillas de elemento y proyecto.

> [!IMPORTANT]
> Este manifiesto está disponible a partir de Visual Studio 2017.

## <a name="vstemplatemanifest-element"></a>Elemento VSTemplateManifest
 El elemento raíz del manifiesto.

### <a name="attributes"></a>Atributos

- **Versión**: una cadena que representa la versión del manifiesto de plantilla. Necesario.

- **Configuración regional:** cadena que representa la configuración regional o las configuraciones regionales del manifiesto de plantilla. El valor de configuración regional se aplica a todas las plantillas. Debe usar un manifiesto independiente para cada configuración regional. Opcional.

### <a name="child-elements"></a>Elementos secundarios

- **VSTemplateContainer** Opcional.

- **VSTemplateDir** Opcional.

### <a name="parent-element"></a>Elemento primario
 Ninguno.

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 El contenedor de los elementos de manifiesto de plantilla. Un manifiesto tiene un contenedor de plantillas para cada plantilla que define.

### <a name="attributes"></a>Atributos
 **VSTemplateType**: un valor de cadena que`"Project"`especifica `"Item"`el `"ProjectGroup"`tipo de la plantilla ( , , o ). Obligatorio

### <a name="child-elements"></a>Elementos secundarios

- **RelativePathOnDisk**: la ruta de acceso relativa del archivo de plantilla en el disco. Esta ubicación también define la ubicación de la plantilla en el árbol de plantillas que se muestra en el **cuadro de** diálogo Nuevo proyecto o Nuevo **elemento.** Para las plantillas implementadas como un directorio y archivos individuales, esta ruta de acceso hace referencia al directorio que contiene los archivos de plantilla. Para las plantillas implementadas como un archivo *.zip,* esta ruta de acceso debe ser la ruta de acceso al archivo *.zip.*

- **VSTemplateHeader: un elemento [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) que describe el encabezado.

### <a name="parent-element"></a>Elemento primario
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Describe el directorio donde se encuentra la plantilla. Un manifiesto puede contener varias entradas **VSTemplateDir** para proporcionar el nombre localizado y el criterio de ordenación para que los directorios controlen su apariencia en el árbol de categorías de plantilla.

 Debido a su diseño, las entradas **VSTemplateDir** deben aparecer solo en manifiestos no especificados en la configuración regional.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios

- **RelativePath**: La ruta de acceso de la plantilla. Solo puede haber una entrada por ruta, por lo que la primera ganará para todos los manifiestos.

- **LocalizedName**: un elemento **NameDescriptionIcon** que especifica el nombre localizado. Opcional.

- **SortOrder**: cadena que especifica el criterio de ordenación. Opcional.

- **ParentFolderOverrideName**: el nombre invalidado de la carpeta primaria. Opcional. Este elemento tiene un **atributo Name,** que es un valor de cadena que especifica el nombre.

### <a name="parent-element"></a>Elemento primario
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 Especifica el nombre y la descripción, posiblemente para las plantillas localizadas. Consulte **LocalizedName** arriba.

### <a name="attributes"></a>Atributos

- **Package**: un valor de cadena que especifica el paquete. Opcional.

- **ID**: un valor de cadena que especifica el identificador. Opcional.

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-element"></a>Elemento primario
 **LocalizedName**

## <a name="examples"></a>Ejemplos
 El código siguiente es un ejemplo de un archivo *.vstman* de plantilla de proyecto.

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

 El código siguiente es un ejemplo de un archivo *.vstman* de plantilla de elemento.

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
