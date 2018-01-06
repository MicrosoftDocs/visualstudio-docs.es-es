---
title: Referencia de esquema del manifiesto de plantilla de Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 87f676ef30da7c667c4ce2b688520a49ed1931c3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Referencia de esquema del manifiesto de plantilla de Visual Studio
Este esquema describe el formato de los archivos de manifiesto (.vstman) de plantillas de Visual Studio generado para las plantillas de proyecto o un elemento de Visual Studio y describe la ubicación y otra información relevante acerca de la plantilla.  
  
 : Dado que hay un elemento independiente y directorios de plantillas de proyecto, un manifiesto nunca debería tener una combinación de plantillas de proyecto y elemento.  
  
> [!IMPORTANT]
>  Este manifiesto está disponible a partir de Visual Studio de 2017.  
  
## <a name="vstemplatemanifest-element"></a>Elemento VSTemplateManifest  
 El elemento raíz del manifiesto.  
  
### <a name="attributes"></a>Atributos  
  
-   **Versión**: una cadena que representa la versión del manifiesto de plantilla. Requerido.  
  
-   **Configuración regional**: una cadena que representa la configuración regional o configuraciones regionales del manifiesto de plantilla. El valor de configuración regional se aplica a todas las plantillas, por lo que debe usar un manifiesto independiente para cada configuración regional. Opcional.  
  
### <a name="child-elements"></a>Elementos secundarios  
  
-   **VSTemplateContainer** opcional.  
  
-   **VSTemplateDir** opcional.  
  
### <a name="parent-element"></a>Elemento Parent  
 Ninguno.  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 El contenedor de la plantilla de manifiesto de elementos. Un manifiesto tiene un contenedor de plantilla para cada plantilla que define.  
  
### <a name="attributes"></a>Atributos  
 **VSTemplateType** : un valor de cadena que especifica el tipo de la plantilla (`"Project"`, `"Item"`, o `"ProjectGroup"`). Obligatorio  
  
### <a name="child-elements"></a>Elementos secundarios  
  
-   **RelativePathOnDisk**: la ruta de acceso relativa del archivo de plantilla en el disco. Esta ubicación también define la posición de la plantilla en el árbol de la plantilla se muestra en el **nuevo proyecto** o **nuevo elemento** cuadro de diálogo. Para las plantillas que se implementa como un directorio y los archivos individuales, esta ruta de acceso hace referencia al directorio que contiene los archivos de plantilla. Para las plantillas que se implementa como un archivo .zip, esta ruta de acceso debe ser la ruta de acceso al archivo zip.  
  
-   **VSTemplateHeader** : A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) elemento que describe el encabezado.  
  
### <a name="parent-element"></a>Elemento Parent  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 Describe el directorio donde se encuentra la plantilla. Un manifiesto puede contener varios **VSTemplateDir** entradas para proporcionar el nombre traducido y ordenación para los directorios de ordenación para controlar su aparición en el árbol de categorías de plantilla.  
  
 Debido a su diseño, **VSTemplateDir** entradas deben aparecer solo en los manifiestos especificados no son: configuración regional.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios  
  
-   **RelativePath**: la ruta de acceso de la plantilla. Puede haber sólo una entrada por cada ruta de acceso, por lo que tendrán prioridad en la primera de ellas para todos los manifiestos.  
  
-   **LocalizedName**: A **NameDescriptionIcon** elemento que especifica el nombre localizado. Opcional.  
  
-   **SortOrder** : una cadena que especifica el criterio de ordenación. Opcional.  
  
-   **ParentFolderOverrideName**: el nombre de la carpeta principal invalidado. Opcional. Este elemento tiene un **nombre** atributo, que es un valor de cadena que especifica el nombre.  
  
### <a name="parent-element"></a>Elemento Parent  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 Especifica el nombre y la descripción, posiblemente para plantillas de otros idiomas. Vea **LocalizedName** anteriormente.  
  
### <a name="attributes"></a>Atributos  
  
-   **Paquete**: un valor de cadena que especifica el paquete. Opcional.  
  
-   **Id. de**: un valor de cadena que especifica el identificador. Opcional.  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-element"></a>Elemento Parent  
 **LocalizedName**  
  
## <a name="examples"></a>Ejemplos  
 El siguiente es un ejemplo de un archivo de .vstman de plantilla de proyecto.  
  
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
  
 El siguiente es un ejemplo de un archivo de .vstman de plantilla de elemento.  
  
```  
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