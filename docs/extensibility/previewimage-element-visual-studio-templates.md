---
title: PreviewImage (elemento, plantillas de Visual Studio) | Microsoft Docs
description: Obtenga información sobre el elemento PreviewImage y cómo especifica el nombre de archivo de la imagen de vista previa que aparecerá en el cuadro de diálogo nuevo proyecto o agregar nuevo elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6fc7a370885d24a586262bebd4182daacd84a9b2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090231"
---
# <a name="previewimage-element-visual-studio-templates"></a>PreviewImage (elemento, plantillas de Visual Studio)
Especifica la imagen de vista previa, como un nombre de archivo, para la imagen de vista previa que aparecerá en el cuadro de diálogo **nuevo proyecto** o **Agregar nuevo elemento** .

 \<VSTemplate> \<TemplateData>
 \<PreviewImage>

## <a name="syntax"></a>Sintaxis

```
<PreviewImage>"filename"</PreviewImage>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 El texto debe ser una cadena que represente un nombre de archivo.

## <a name="remarks"></a>Observaciones
 `PreviewImage` es un elemento opcional.

## <a name="see-also"></a>Vea también
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md)
