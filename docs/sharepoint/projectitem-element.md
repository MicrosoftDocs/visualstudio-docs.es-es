---
title: "ProjectItem Element"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ProjectItem element"
ms.assetid: df588235-12a1-4798-bc56-ef81843de17f
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# ProjectItem Element
  Representa un elemento de proyecto de SharePoint.  Este es el elemento raíz necesario del archivo .spdata.  
  
## Sintaxis  
  
```  
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
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|**DefaultFile**|Atributo **xs:string** opcional.<br /><br /> La ruta de acceso relativa, incluido el nombre de archivo, del archivo que se abre en el editor de Visual Studio al abrir el elemento de proyecto de SharePoint en el **Explorador de soluciones**.  La ruta de acceso es relativa desde la carpeta que contiene el archivo .spdata.|  
|**FeatureReceiverClass**|Atributo **xs:string** opcional.<br /><br /> El nombre completo de una clase de receptor de características para este elemento de proyecto de SharePoint.  Para obtener más información sobre los receptores de características, vea [Proporcionar información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|**FeatureReceiverAssembly**|Atributo **xs:string** opcional.<br /><br /> Especifica el nombre completo de un ensamblado que define un receptor de características para este elemento de proyecto de SharePoint.  Para obtener más información sobre los receptores de características, vea [Proporcionar información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  Para obtener más información sobre nombres de ensamblados completos, vea [Nombres de ensamblado](http://msdn.microsoft.com/library/8f8c2c90-f15d-400e-87e7-a757e4f04d0e).|  
|**SupportedTrustLevels**|Atributo **xs:string** opcional.<br /><br /> Especifica los niveles de confianza que admite este elemento de proyecto de SharePoint.  Este valor puede ser una de las cadenas siguientes: Sandboxed, FullTrust o All.  El valor All especifica Sandboxed y FullTrust.<br /><br /> En un tipo de elemento de proyecto de SharePoint personalizado, el valor de este atributo corresponde al valor que asigna a la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> en su implementación del método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>.  Si especifica un valor diferente para este atributo, Visual Studio sobrescribe el valor para que especifique el mismo nivel de confianza que especifica en la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A>.|  
|**SupportedDeploymentScopes**|Atributo **xs:string** opcional.<br /><br /> Especifica los ámbitos de implementación que admite este elemento de proyecto de SharePoint.  Este valor es una cadena separada por comas que está compuesta de una o varias de las cadenas siguientes: Farm, Site, Web, WebApplication o Package.  Por ejemplo, "Web, Sitio".<br /><br /> En un tipo de elemento de proyecto de SharePoint personalizado, el valor de este atributo corresponde al valor que asigna a la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> en su implementación del método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>.  Si especifica un valor diferente para este atributo, Visual Studio sobrescribe el valor para que especifique el mismo nivel de confianza que especifica en la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A>.|  
|**Type**|El atributo **xs:string** es obligatorio.<br /><br /> El identificador del elemento de proyecto de SharePoint.  En un tipo de elemento de proyecto de SharePoint personalizado, el identificador es la cadena que se pasa a <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  Para obtener más información, vea [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Para obtener una lista de los identificadores para los elementos de proyecto de SharePoint integrados incluidos con Visual Studio, vea [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Elemento opcional.<br /><br /> Representa una colección de elementos de datos personalizados que están asociados al elemento de proyecto de SharePoint.<br /><br /> Solo puede incluir un elemento **ExtensionData**.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Elemento opcional.<br /><br /> Representa una colección de valores de propiedad que se incluye con una característica cuando se implementa en SharePoint.<br /><br /> Solo puede incluir un elemento **FeatureProperties**.|  
|[Files \(Archivos\)](../sharepoint/files-element.md)|Elemento **FileCollectionType** opcional.<br /><br /> Especifica los archivos que se desea implementar con el elemento de proyecto de SharePoint, por ejemplo archivos del elemento Feature y la salida de proyectos dependientes que no son de SharePoint.<br /><br /> Debe incluir un elemento **ProjectItemFolder** o **Files**, pero no ambos.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Elemento **ProjectItemFolderType** opcional.<br /><br /> Representa una carpeta asignada.<br /><br /> Debe incluir un elemento **ProjectItemFolder** o **Files**, pero no ambos.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Elemento opcional.<br /><br /> Representa una colección de elementos web y controles ASPX que se designan como seguros para que cualquier usuario pueda obtener acceso a ella en cualquier página ASPX del sitio de SharePoint.<br /><br /> Solo puede incluir un elemento **SafeControls**.|  
  
### Elementos primarios  
 Ninguno.  
  
## Información de elemento  
  
|||  
|-|-|  
|**Espacio de nombres**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nombre de esquema**|Esquema de elemento de proyecto de SharePoint|  
|**Archivo de validación**|ProjectItemModelSchema.xsd|  
|**Puede estar vacío**|No|  
  
## Vea también  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  