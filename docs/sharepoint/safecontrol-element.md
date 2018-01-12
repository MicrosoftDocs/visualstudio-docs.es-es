---
title: SafeControl (elemento) | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SafeControl element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7458120d7a130de96a1a271c83e5376fe94481f3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="safecontrol-element"></a>SafeControl (Elemento)
  Representa un control ASPX o elemento Web que se designa como seguro para que cualquier usuario tenga acceso en cualquier página ASPX del sitio de SharePoint.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|**Ensamblado**|Opcional **xs: String** atributo.<br /><br /> El nombre del ensamblado donde se define el control ASPX o elemento Web. De forma predeterminada, este atributo se usa el **$SharePoint.Project.AssemblyFullName$** parámetro reemplazable para el nombre del ensamblado. Para obtener más información, consulte [parámetros reemplazables](../sharepoint/replaceable-parameters.md).|  
|**IsSafe**|Opcional **xs: Boolean** atributo.<br /><br /> Especifica si el control ASPX o elemento Web es seguro para los usuarios de confianza tener acceso.|  
|**IsSafeAgainstScript**|Opcional **xs: Boolean** atributo.<br /><br /> Especifica si los usuarios de confianza pueden ver o editar las propiedades del control ASPX o elemento Web.|  
|**Name**|Opcional **xs: String** atributo.<br /><br /> El nombre de esta entrada de control seguro en la colección.|  
|**Espacio de nombres**|Opcional **xs: String** atributo.<br /><br /> El espacio de nombres del control ASPX o elemento Web.|  
|**TypeName**|Opcional **xs: String** atributo.<br /><br /> El nombre de tipo del control ASPX o elemento Web.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Representa una colección de controles ASPX y elementos Web que se designan como seguros para cualquier usuario tenga acceso en cualquier página ASPX del sitio de SharePoint.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de controles seguros, vea [proporcionar información de implementación en los elementos de proyecto de empaquetado e](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Información de elemento  
  
|||  
|-|-|  
|**Espacio de nombres**|http://schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nombre del esquema**|Esquema de elemento de proyecto de SharePoint|  
|**Archivo de validación**|ProjectItemModelSchema.xsd|  
|**Puede estar vacío**|No|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Proporcionar información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  