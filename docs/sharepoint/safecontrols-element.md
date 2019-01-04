---
title: SafeControls (elemento) | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e08b414858db389e507dc9395d218807c9530db6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875973"
---
# <a name="safecontrols-element"></a>SafeControls (elemento)
  Una colección de controles ASPX y elementos Web que se designan como seguros para cualquier usuario tenga acceso en cualquier página ASPX del sitio de SharePoint.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<SafeControls>  
  <SafeControl.../>  
</SafeControls>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Elemento opcional.<br /><br /> Representa un control ASPX o elemento Web que se designa como seguro para que cualquier usuario tenga acceso en cualquier página ASPX del sitio de SharePoint.|  
  
### <a name="parent-elements"></a>Elementos primarios
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa un elemento de proyecto de SharePoint. Este elemento, el elemento raíz necesario de la *.spdata* archivo.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información sobre los controles seguros, vea [proporcionar información de empaquetado e implementación de elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
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
