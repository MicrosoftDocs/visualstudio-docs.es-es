---
title: TemplateID (elemento, plantillas de Visual Studio) | Microsoft Docs
description: Obtenga información sobre el elemento TemplateID y cómo especifica un identificador para una plantilla de elemento clasificada por el elemento TemplateGroupID en un grupo de plantillas de elementos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 734af9de80da5f095f9ad7f0e52023659fea6b67
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903187"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID (Elemento, Plantillas de Visual Studio)
Especifica un identificador para una plantilla de elemento que se clasifica en un grupo de plantillas de elementos mediante el elemento [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) .

 \<VSTemplate> \<TemplateData>
 \<TemplateID>

## <a name="syntax"></a>Sintaxis

```
<TemplateID> ... </TemplateID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="text-value"></a>Valor de texto
 `string`Que representa un identificador de una plantilla de elemento que se clasifica en un grupo de plantillas de elementos por el `TemplateGroupID` elemento.

## <a name="remarks"></a>Observaciones
 `TemplateID` es un elemento opcional.

 Si un archivo. vstemplate omite el `TemplateID` elemento, se usa el elemento [Name](../extensibility/name-element-visual-studio-templates.md) como identificador de la plantilla.

 El valor del `TemplateID` elemento se utiliza junto con el registro del sistema del proyecto (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\ ) para filtrar plantillas que aparecen en el cuadro de diálogo **Agregar nuevo elemento** .

## <a name="see-also"></a>Consulte también
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas de proyecto y de elemento](../ide/creating-project-and-item-templates.md)
