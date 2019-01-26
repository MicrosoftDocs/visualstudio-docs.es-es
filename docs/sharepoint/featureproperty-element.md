---
title: FeatureProperty (elemento) | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3c9407e78a32ad9f9d8ee4ecd1ae4462409decfc
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867915"
---
# <a name="featureproperty-element"></a>FeatureProperty (elemento)
  Representa una propiedad personalizada que se incluye con una característica cuando se implementa en SharePoint. Una vez implementada la característica, puede tener acceso a la propiedad en el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<FeatureProperty Key = "Key of the property value"  
    Value = "Property value" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|**Key**|Requiere **xs: String** atributo.<br /><br /> La clave que se usa para almacenar y recuperar el valor de propiedad. Cada propiedad debe tener una clave que es única dentro de la característica.|  
|**Valor**|Requiere **xs: String** atributo.<br /><br /> Valor de propiedad.|  
  
### <a name="child-elements"></a>Elementos secundarios
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Representa una colección de valores de propiedad que se incluyen con una característica cuando se implementa en SharePoint.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de las propiedades de característica, consulte [proporcionar información de implementación de paquete y en los elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Información de elemento
  
|||  
|-|-|  
|**Espacio de nombres**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Nombre de esquema**|Esquema de elemento de proyecto de SharePoint|  
|**Archivo de validación**|ProjectItemModelSchema.xsd|  
|**Puede estar vacío**|No|  
  
## <a name="see-also"></a>Vea también
 [Referencia de esquemas de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Proporcionar información de empaquetado e implementación de elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
