---
title: ProjectItem (elemento) | Microsoft Docs
description: Obtiene información de referencia sobre el elemento ProjectItem, que representa un elemento de proyecto de SharePoint en la referencia de esquema XML de elementos de proyecto de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2b94b44bfa442805c4c785a48c9f60f56eb8e002
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950593"
---
# <a name="projectitem-element"></a>ProjectItem (elemento)
  Representa un elemento de proyecto de SharePoint. Este elemento es el elemento raíz necesario del archivo *. spdata* .

## <a name="syntax"></a>Sintaxis

```xml
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"
    SupportedTrustLevels = "Trust levels that the project item supports"
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"
    Type="Identifier for the project item">
  <Files>...</Files>
  <ProjectItemFolder>...</ProjectItemFolder>
  <SafeControls>...</SafeControls>
  <FeatureProperties>...</FeatureProperties>
  <ExtensionData>...</ExtensionData>
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|**DefaultFile**|Atributo **xs: String** opcional.<br /><br /> La ruta de acceso relativa, incluido el nombre de archivo, del archivo que se abre en el editor de Visual Studio al abrir el elemento de proyecto de SharePoint en **Explorador de soluciones**. La ruta de acceso es relativa a la carpeta que contiene el archivo *. spdata* .|
|**FeatureReceiverClass**|Atributo **xs: String** opcional.<br /><br /> Nombre completo de una clase de receptor de características para este elemento de proyecto de SharePoint. Para obtener más información acerca de los receptores de características, vea [proporcionar información de empaquetado e implementación en los elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|**FeatureReceiverAssembly**|Atributo **xs: String** opcional.<br /><br /> Especifica el nombre completo de un ensamblado que define un receptor de características para este elemento de proyecto de SharePoint. Para obtener más información acerca de los receptores de características, vea [proporcionar información de empaquetado e implementación en los elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Para obtener más información sobre los nombres de ensamblado completos, vea [nombres de ensamblados](/dotnet/framework/app-domains/assembly-names).|
|**SupportedTrustLevels**|Atributo **xs: String** opcional.<br /><br /> Especifica los niveles de confianza que admite este elemento de proyecto de SharePoint. Este valor puede ser una de las cadenas siguientes: Sandboxed, FullTrust o ALL. El valor All especifica tanto el espacio aislado como FullTrust.<br /><br /> En un tipo de elemento de proyecto de SharePoint personalizado, el valor de este atributo corresponde al valor que se asigna a la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> propiedad en la implementación del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método. Si especifica un valor diferente para este atributo, Visual Studio sobrescribe el valor para que especifique el mismo nivel de confianza que especifique en la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> propiedad.|
|**SupportedDeploymentScopes**|Atributo **xs: String** opcional.<br /><br /> Especifica los ámbitos de implementación que admite este elemento de proyecto de SharePoint. Este valor es una cadena delimitada por comas que consta de una o varias de las siguientes cadenas: granja, sitio, Web, aplicación web o paquete. Por ejemplo: `Web, Site`<br /><br /> En un tipo de elemento de proyecto de SharePoint personalizado, el valor de este atributo corresponde al valor que se asigna a la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> propiedad en la implementación del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método. Si especifica un valor diferente para este atributo, Visual Studio sobrescribe el valor para que especifique el mismo nivel de confianza que especifique en la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> propiedad.|
|**Tipo**|Atributo **xs: String** requerido.<br /><br /> Identificador del elemento de proyecto de SharePoint. En un tipo de elemento de proyecto de SharePoint personalizado, el identificador es la cadena que se pasa a <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Para obtener más información, vea [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Para obtener una lista de los identificadores de los elementos de proyecto de SharePoint integrados que se incluyen con Visual Studio, vea [extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md).|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Elemento opcional.<br /><br /> Representa una colección de elementos de datos personalizados que están asociados al elemento de proyecto de SharePoint.<br /><br /> Solo puede incluir un elemento **extensiondata (** .|
|[Featureproperties (](../sharepoint/featureproperties-element.md)|Elemento opcional.<br /><br /> Representa una colección de valores de propiedad que se incluyen con una característica cuando se implementa en SharePoint.<br /><br /> Solo puede incluir un elemento **featureproperties (** .|
|[Archivos](../sharepoint/files-element.md)|Elemento **FileCollectionType** opcional.<br /><br /> Especifica los archivos que se van a implementar con el elemento de proyecto de SharePoint, como los archivos de elemento de característica y la salida de proyectos dependientes que no son de SharePoint.<br /><br /> Incluya un elemento **files** o **projectitemfolder (** , pero no ambos.|
|[Projectitemfolder (](../sharepoint/projectitemfolder-element.md)|Elemento **ProjectItemFolderType** opcional.<br /><br /> Representa una carpeta asignada.<br /><br /> Incluya un elemento **files** o **projectitemfolder (** , pero no ambos.|
|[SafeControls](../sharepoint/safecontrols-element.md)|Elemento opcional.<br /><br /> Representa una colección de controles ASPX y elementos web que se designan como seguros para que cualquier usuario tenga acceso a cualquier página ASPX en el sitio de SharePoint.<br /><br /> Solo puede incluir un elemento **SafeControls** .|

### <a name="parent-elements"></a>Elementos primarios
 Ninguno.

## <a name="element-information"></a>Información de elemento

|Propiedad|Value|
|-|-|
|**Espacio de nombres**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nombre del esquema**|Esquema de elemento de proyecto de SharePoint|
|**Archivo de validación**|ProjectItemModelSchema. xsd|
|**Puede estar vacío**|No|

## <a name="see-also"></a>Consulte también
[Esquema de elemento de proyecto de SharePoint rseference](../sharepoint/sharepoint-project-item-schema-reference.md)
