---
title: Elemento Featureproperty (| Microsoft Docs
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
ms.openlocfilehash: 61eeea33c6941624ed18a00db482590590a44a8f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546528"
---
# <a name="featureproperty-element"></a>FeatureProperty (elemento)
  Representa una propiedad personalizada que se incluye con una característica cuando se implementa en SharePoint. Una vez implementada una característica, puede tener acceso a la propiedad en el código.

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
|**Clave**|Atributo **xs: String** requerido.<br /><br /> La clave que se usa para almacenar y recuperar el valor de propiedad. Cada propiedad debe tener una clave que sea única dentro de la característica.|
|**Valor**|Atributo **xs: String** requerido.<br /><br /> El valor de propiedad.|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Featureproperties (](../sharepoint/featureproperties-element.md)|Representa una colección de valores de propiedad que se incluyen con una característica cuando se implementa en SharePoint.|

## <a name="remarks"></a>Comentarios
 Para obtener más información sobre las propiedades de las características, vea [proporcionar información de paquete e implementación en los elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Información de elemento

|Propiedad|Value|
|-|-|
|**Espacio de nombres**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nombre del esquema**|Esquema de elemento de proyecto de SharePoint|
|**Archivo de validación**|ProjectItemModelSchema. xsd|
|**Puede estar vacío**|No|

## <a name="see-also"></a>Vea también
- [Referencia de esquemas de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Proporcionar información de empaquetado e implementación en los elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
