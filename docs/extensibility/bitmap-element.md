---
title: Bitmap (elemento) | Microsoft Docs
description: El elemento Bitmap define un mapa de bits. El mapa de bits se carga desde un recurso o desde un archivo. Este artículo contiene un ejemplo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 32f07857f2d04989b0de021988b2961d4a1553d2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068224"
---
# <a name="bitmap-element"></a>Bitmap (elemento)
Define un mapa de bits. El mapa de bits se carga desde un recurso o desde un archivo.

## <a name="syntax"></a>Sintaxis

```
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Necesario. GUID del identificador del comando GUID/ID.<br /><br /> El atributo GUID de un mapa de bits no está asociado a ningún VSPackage u otro grupo de comandos.  Debe ser único para la definición de mapa de bits y no debe usarse para ningún otro propósito.|
|resID|IDENTIFICADOR del identificador del comando GUID/ID. Se requiere el atributo resID o href.<br /><br /> El atributo resID es un identificador de recurso entero que determina la franja de mapa de bits que se va a cargar durante la combinación de la tabla de comandos.  Cuando se carga la tabla de comandos, los mapas de bits especificados por el identificador de recurso se cargarán desde el recurso del mismo módulo.|
|usedList|Obligatorio si el atributo resID está presente. Selecciona las imágenes disponibles en la franja de mapa de bits.|
|href|Ruta de acceso al mapa de bits. Se requiere el atributo resID o href.<br /><br /> Se busca en la ruta de acceso de inclusión el archivo de imagen indicado, que está incrustado en el binario resultante.  Durante la combinación de la tabla de comandos, se copia la imagen y no se requiere ninguna búsqueda o carga de recursos adicional.  Si el atributo usedList no está presente, todas las imágenes de la franja estarán disponibles. **Nota:**  Las imágenes se pueden proporcionar en uno de varios formatos que incluyen *. bmp*, *. png* y *. gif*.  Las versiones anteriores del compilador no eran compatibles con imágenes de mapa de bits de 32 bits que tenían información alfa para la transparencia parcial. La solución alternativa para estas versiones es usar el formato *. png* .|
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento bitmaps](../extensibility/bitmaps-element.md)|Agrupa los elementos de mapa de bits.|

## <a name="example"></a>Ejemplo

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Consulte también
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
