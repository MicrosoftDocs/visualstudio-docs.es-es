---
title: ProjectItem (elemento) | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e7c9a32a7fa84d8adc064aa3a3ac035999295791
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890107"
---
# <a name="projectitem-element"></a>ProjectItem (elemento)
  Representa un elemento de proyecto de SharePoint. Este elemento, el elemento raíz necesario de la *.spdata* archivo.  
  
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
|**DefaultFile**|Opcional **xs: string** atributo.<br /><br /> La ruta de acceso relativa, incluido el nombre de archivo del archivo que se abre en el editor de Visual Studio al abrir el elemento de proyecto de SharePoint en **el Explorador de soluciones**. La ruta de acceso es relativa con respecto a la carpeta que contiene el *.spdata* archivo.|  
|**FeatureReceiverClass**|Opcional **xs: String** atributo.<br /><br /> El nombre completo de una clase de receptor de características para este elemento de proyecto de SharePoint. Para obtener más información acerca de los receptores de características, consulte [proporcionar información de empaquetado e implementación de elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|**FeatureReceiverAssembly**|Opcional **xs: String** atributo.<br /><br /> Especifica el nombre completo de un ensamblado que define un receptor de características para este elemento de proyecto de SharePoint. Para obtener más información acerca de los receptores de características, consulte [proporcionar información de empaquetado e implementación de elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Para obtener más información acerca de los nombres de ensamblado completo, vea [nombres de ensamblado](/dotnet/framework/app-domains/assembly-names).|  
|**SupportedTrustLevels**|Opcional **xs: String** atributo.<br /><br /> Especifica los niveles de confianza que admite este elemento de proyecto de SharePoint. Este valor puede ser una de las siguientes cadenas: En un espacio aislado, de plena confianza, o todos. El valor All especifica Sandboxed y plena confianza.<br /><br /> En un tipo de elemento de proyecto de SharePoint personalizado, el valor de este atributo corresponde al valor que se asigna a la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> propiedad en la implementación de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método. Si especifica un valor diferente para este atributo, Visual Studio sobrescribe el valor de manera que especifique el mismo nivel de confianza que se especifica en el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> propiedad.|  
|**SupportedDeploymentScopes**|Opcional **xs: String** atributo.<br /><br /> Especifica los ámbitos de implementación que admite este elemento de proyecto de SharePoint. Este valor es una cadena delimitada por comas que consta de una o varias de las siguientes cadenas: Granja de servidores de sitio, Web, WebApplication o paquete. Por ejemplo: `Web, Site`.<br /><br /> En un tipo de elemento de proyecto de SharePoint personalizado, el valor de este atributo corresponde al valor que se asigna a la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> propiedad en la implementación de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método. Si especifica un valor diferente para este atributo, Visual Studio sobrescribe el valor de manera que especifique el mismo nivel de confianza que se especifica en el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> propiedad.|  
|**Type**|Requiere **xs: String** atributo.<br /><br /> El identificador para el elemento de proyecto de SharePoint. En un tipo de elemento de proyecto de SharePoint personalizado, el identificador es una cadena que se pasa a la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Para obtener más información, vea [Cómo: Definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Para obtener una lista de los identificadores para los elementos de proyecto de SharePoint integrados incluidos con Visual Studio, consulte [elementos de proyecto de SharePoint ampliar](../sharepoint/extending-sharepoint-project-items.md).|  
  
### <a name="child-elements"></a>Elementos secundarios
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Elemento opcional.<br /><br /> Representa una colección de elementos de datos personalizados que están asociados con el elemento de proyecto de SharePoint.<br /><br /> Puede incluir una sola **ExtensionData** elemento.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Elemento opcional.<br /><br /> Representa una colección de valores de propiedad que se incluyen con una característica cuando se implementa en SharePoint.<br /><br /> Puede incluir una sola **FeatureProperties** elemento.|  
|[Archivos](../sharepoint/files-element.md)|Opcional **FileCollectionType** elemento.<br /><br /> Especifica los archivos para implementar con el elemento de proyecto de SharePoint, como los archivos de elemento de característica y la salida de los proyectos de SharePoint que no son dependientes.<br /><br /> Incluir un **archivos** o un **ProjectItemFolder** elemento, pero no ambos.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Opcional **ProjectItemFolderType** elemento.<br /><br /> Representa una carpeta asignada.<br /><br /> Incluir un **archivos** o un **ProjectItemFolder** elemento, pero no ambos.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Elemento opcional.<br /><br /> Representa una colección de controles ASPX y elementos Web que se designan como seguros para cualquier usuario tenga acceso en cualquier página ASPX del sitio de SharePoint.<br /><br /> Puede incluir una sola **SafeControls** elemento.|  
  
### <a name="parent-elements"></a>Elementos primarios
 Ninguno.  
  
## <a name="element-information"></a>Información de elemento
  
|||  
|-|-|  
|**Espacio de nombres**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>SharePointProjectItemModel/SharePointTools/2010|  
|**Nombre de esquema**|Esquema de elemento de proyecto de SharePoint|  
|**Archivo de validación**|ProjectItemModelSchema.xsd|  
|**Puede estar vacío**|No|  
  
## <a name="see-also"></a>Vea también
[Rseference de esquema de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
