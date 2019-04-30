---
title: LocationFieldMRUPrefix (elemento) (plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationFieldMRUPrefix
helpviewer_keywords:
- <LocationFieldMRUPrefix> element [Visual Studio Templates]
- LocationFieldMRUPrefix element [Visual Studio Templates]
ms.assetid: 03443691-9eb5-46f4-9169-cc2552a04bcb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8c4c3fa4e64b302c6d1c9d0e393528d46fe072f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62907345"
---
# <a name="locationfieldmruprefix-element-visual-studio-templates"></a>Elemento LocationFieldMRUPrefix (plantillas de Visual Studio)
Especifica las rutas de acceso usados más recientemente (MRU) en el **nuevo proyecto** y **Agregar nuevo elemento** cuadro de diálogo.

## <a name="syntax"></a>Sintaxis

```xml
<LocationFieldMRUPrefix> ... </LocationFieldMRUPrefix>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="remarks"></a>Comentarios
 Este elemento solo debe usarse en plantillas generadas a través de la [!INCLUDE[vsipprvsip](../extensibility/includes/vsipprvsip_md.md)].

## <a name="see-also"></a>Vea también
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md)