---
title: Elemento Bitmap | Microsoft Docs
description: El elemento Bitmap define un mapa de bits. El mapa de bits se carga desde un recurso o desde un archivo. Este artículo contiene un ejemplo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c8f3daf25a3ffe025bcdef65dbaa6def942d0fb4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903325"
---
# <a name="bitmap-element"></a>Elemento Bitmap
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
|guid|Necesario. GUID del identificador de comando GUID/ID.<br /><br /> El atributo GUID de un mapa de bits no está asociado a ningún VSPackage u otro grupo de comandos.  Debe ser único para la definición de mapa de bits y no debe usarse para ningún otro propósito.|
|Resnum|Identificador del identificador de comando GUID/ID. Se requiere el resID o el atributo href.<br /><br /> El atributo resID es un identificador de recurso entero que determina la franja de mapa de bits que se va a cargar durante la combinación de tablas de comandos.  Cuando se carga la tabla de comandos, los mapas de bits especificados por el identificador de recurso se cargarán desde el recurso del mismo módulo.|
|usedList|Obligatorio si el atributo resID está presente. Selecciona las imágenes disponibles en la franja de mapa de bits.|
|href|Ruta de acceso al mapa de bits. Se requiere el resID o el atributo href.<br /><br /> La ruta de acceso de include busca el archivo de imagen indicado, que se incrusta en el binario resultante.  Durante la combinación de la tabla de comandos, se copia la imagen y no se requiere ninguna búsqueda o carga de recursos adicional.  Si el atributo usedList no está presente, todas las imágenes de la franja estarán disponibles. **Nota:**  Las imágenes se pueden proporcionar en uno de los distintos formatos *que incluyen.bmp*, *.png* y *.gif*.  Las versiones anteriores del compilador no admiten imágenes de mapa de bits de 32 bits que tenían información alfa para la transparencia parcial. La solución alternativa para estas versiones es usar el *.png* formato.|
|Condición|Opcional. Vea [Atributos condicionales.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Bitmaps](../extensibility/bitmaps-element.md)|Agrupa elementos Bitmap.|

## <a name="example"></a>Ejemplo

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Consulte también
- [Visual Studio de tabla de comandos (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
