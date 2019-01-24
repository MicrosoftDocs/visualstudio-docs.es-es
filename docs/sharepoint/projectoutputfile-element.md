---
title: ProjectOutputFile (elemento) | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ea476c2d2b73ec9c59f7d3f7cfbc9a0b0cab5bd7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53948620"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile (elemento)
  Representa la salida de un proyecto independiente para incluir con el elemento de proyecto cuando se implementa en SharePoint.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## <a name="type"></a>Tipo  
 **ProjectOutputFileType**  
  
## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|**ProjectId**|Requiere **xs: String** atributo.<br /><br /> El GUID del proyecto dependiente que tiene la salida que van a incluir. Esto corresponde a la **ProjectGuid** elemento en el archivo de proyecto dependiente.|  
|**ProjectPath**|Requiere **xs: String** atributo.<br /><br /> La ruta de acceso relativa, incluido el nombre de archivo de proyecto del proyecto dependiente que tiene la salida que van a incluir. Esta ruta de acceso es relativa a la carpeta raíz del proyecto de SharePoint que contiene el elemento de proyecto de SharePoint.|  
|**Target**|Opcional **xs: String** atributo.<br /><br /> Ruta de acceso donde el resultado del proyecto dependiente se va a implementar en el servidor de SharePoint, relativa a la carpeta raíz de implementación. La carpeta raíz de implementación viene determinada por el tipo de implementación especificado por el **tipo** atributo.<br /><br /> Para obtener más información, vea las descripciones de los **Deployment Path** y **Deployment Root** propiedades de SharePoint elementos de proyecto en [soluciones de desarrollo de SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Requiere **xs: String** atributo.<br /><br /> El tipo de implementación que se usará para la salida del proyecto dependiente. Para obtener más información acerca de los valores posibles, vea la descripción para el **tipo de implementación** propiedad de los elementos de proyecto de SharePoint en [soluciones de desarrollo de SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Elementos secundarios
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Archivos](../sharepoint/files-element.md)|Especifica los archivos que se incluirá con el elemento de proyecto de SharePoint cuando se implementa en SharePoint.|  
  
## <a name="remarks"></a>Comentarios  
 Use la **ProjectOutputFile** elemento para incluir el resultado de un proyecto en la implementación del elemento de proyecto de SharePoint. Puede especificar un proyecto diferente, o el mismo proyecto que contiene el elemento de proyecto. Para obtener más información, consulte [proporcionar información de empaquetado e implementación de elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Información de elemento
  
|||  
|-|-|  
|**Espacio de nombres**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>SharePointProjectItemModel/SharePointTools/2010|  
|**Nombre de esquema**|Esquema de elemento de proyecto de SharePoint|  
|**Archivo de validación**|ProjectItemModelSchema.xsd|  
|**Puede estar vacío**|No|  
  
## <a name="see-also"></a>Vea también
 [Referencia de esquemas de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Proporcionar información de empaquetado e implementación de elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
