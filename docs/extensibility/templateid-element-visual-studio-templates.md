---
title: Elemento TemplateID (Plantillas de Visual Studio) Microsoft Docs
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
ms.openlocfilehash: 8eb5abac9c837b3022354d6da743ac8f21d5e41d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699067"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID (Elemento, Plantillas de Visual Studio)
Especifica un identificador para una plantilla de elemento que se clasifica en un grupo de plantillas de elemento por el [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) elemento.

 \<VSTemplate \<> TemplateData> \<TemplateID>

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
 A `string` que representa un identificador para una plantilla de elemento que `TemplateGroupID` se clasifica en un grupo de plantillas de elemento por el elemento.

## <a name="remarks"></a>Observaciones
 `TemplateID` es un elemento opcional.

 Si un archivo .vstemplate `TemplateID` omite el elemento, el elemento [Name](../extensibility/name-element-visual-studio-templates.md) se utiliza como identificador de la plantilla.

 El valor `TemplateID` del elemento se utiliza junto con el registro del sistema de proyectos\\(HKEY_LOCAL_MACHINE, SOFTWARE, Microsoft, VisualStudio, 11,0, Projects ) para filtrar las plantillas que aparecen en el cuadro de diálogo **Agregar nuevo elemento.**

## <a name="see-also"></a>Vea también
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)
