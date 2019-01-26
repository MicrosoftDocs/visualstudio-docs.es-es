---
title: Referencia de esquema del manifiesto de plantilla de Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba9f4123b69a2decbcc46433e85082a4897b378d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999475"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Referencia de esquema del manifiesto de plantilla de Visual Studio
Este esquema describe el formato del manifiesto de plantilla de Visual Studio (*vstman*) los archivos que se generan para las plantillas de proyecto o elemento de Visual Studio. El esquema también describe la ubicación y otra información relevante acerca de la plantilla.  
  
 : Dado que hay un elemento independiente y directorios de la plantilla de proyecto, un manifiesto nunca debe tener una combinación de las plantillas de proyecto y elemento.  
  
> [!IMPORTANT]
>  Este manifiesto está disponible a partir de Visual Studio 2017.  
  
## <a name="vstemplatemanifest-element"></a>Elemento VSTemplateManifest  
 El elemento raíz del manifiesto.  
  
### <a name="attributes"></a>Atributos  
  
-   **Versión**: Una cadena que representa la versión del manifiesto de plantilla. Obligatorio.  
  
-   **Locale**: Una cadena que representa la configuración regional o configuraciones regionales del manifiesto de plantilla. El valor de configuración regional se aplica a todas las plantillas. Debe usar un manifiesto independiente para cada configuración regional. Opcional.  
  
### <a name="child-elements"></a>Elementos secundarios  
  
-   **VSTemplateContainer** Optional.  
  
-   **VSTemplateDir** opcional.  
  
### <a name="parent-element"></a>Elemento primario  
 Ninguno.  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 El contenedor de la plantilla de manifiesto de elementos. Un manifiesto tiene un contenedor de plantilla para cada plantilla que define.  
  
### <a name="attributes"></a>Atributos  
 **VSTemplateType**: Valor de cadena que especifica el tipo de la plantilla (`"Project"`, `"Item"`, o `"ProjectGroup"`). Obligatorio  
  
### <a name="child-elements"></a>Elementos secundarios  
  
-   **RelativePathOnDisk**:  La ruta de acceso relativa del archivo de plantilla en el disco. Esta ubicación también define la posición de la plantilla en el árbol de la plantilla se muestra en el **nuevo proyecto** o **nuevo elemento** cuadro de diálogo. Plantillas que se implementa como un directorio y los archivos individuales, esta ruta de acceso hace referencia al directorio que contiene los archivos de plantilla. Para implementar plantillas como un *.zip* archivo, esta ruta de acceso debe ser la ruta de acceso a la *.zip* archivo.  
  
-   **VSTemplateHeader: Un [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) elemento que describe el encabezado.  
  
### <a name="parent-element"></a>Elemento primario  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 Describe el directorio donde se encuentra la plantilla. Un manifiesto puede contener varios **VSTemplateDir** entradas para proporcionar el nombre traducido y orden de los directorios a controlar su apariencia en el árbol de categorías de plantilla.  
  
 Debido a su diseño, **VSTemplateDir** entradas deben aparecer solo en los manifiestos de configuración regional no especificados.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios  
  
-   **RelativePath**: La ruta de acceso de la plantilla. Puede haber solo una entrada por cada ruta de acceso, por lo que tendrán prioridad en la primera de ellas para todos los manifiestos.  
  
-   **LocalizedName**: Un **NameDescriptionIcon** elemento que especifica el nombre localizado. Opcional.  
  
-   **SortOrder**: Una cadena que especifica el criterio de ordenación. Opcional.  
  
-   **ParentFolderOverrideName**: Nombre de la carpeta principal invalidado. Opcional. Este elemento tiene un **nombre** atributo, que es un valor de cadena que especifica el nombre.  
  
### <a name="parent-element"></a>Elemento primario  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 Especifica el nombre y la descripción, posiblemente para las plantillas localizadas. Consulte **LocalizedName** anteriormente.  
  
### <a name="attributes"></a>Atributos  
  
-   **Paquete**: Valor de cadena que especifica el paquete. Opcional.  
  
-   **ID**: Valor de cadena que especifica el identificador. Opcional.  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-element"></a>Elemento primario  
 **LocalizedName**  
  
## <a name="examples"></a>Ejemplos  
 El código siguiente es un ejemplo de una plantilla de proyecto *vstman* archivo.  
  
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
  
 El código siguiente es un ejemplo de una plantilla de elemento *vstman* archivo.  
  
```xml  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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