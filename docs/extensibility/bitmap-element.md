---
title: Elemento de mapa de bits ( Bitmap Element) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d663351aad7d381dd5bfe4cbaa0a263cc70b821
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739998"
---
# <a name="bitmap-element"></a>Elemento de mapa de bits
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
|guid|Necesario. GUID del identificador de comando GUID/ID.<br /><br /> El atributo guid de un mapa de bits no está asociado a ningún VSPackage u otro grupo de comandos.  Debe ser único para la definición de mapa de bits y no debe utilizarse para ningún otro propósito.|
|Resnum|ID del identificador de comando GUID/ID. Se requiere el atributo resID o href.<br /><br /> El atributo resID es un identificador de recurso entero que determina la franja de mapa de bits que se va a cargar durante la combinación de la tabla de comandos.  Cuando se carga la tabla de comandos, los mapas de bits especificados por el identificador de recurso se cargarán desde el recurso del mismo módulo.|
|usedList|Necesario si el atributo resID está presente. Selecciona las imágenes disponibles en la tira de mapa de bits.|
|href|Ruta de acceso al mapa de bits. Se requiere el atributo resID o href.<br /><br /> Se busca la ruta de inclusión para el archivo de imagen indicado, que está incrustado en el binario resultante.  Durante la combinación de la tabla de comandos, se copia la imagen y no se requiere ninguna búsqueda o carga de recursos adicionales.  Si el atributo usedList no está presente, todas las imágenes de la tira están disponibles. **Nota:**  Las imágenes se pueden suministrar en uno de varios formatos que incluyen *.bmp*, *.png*y *.gif*.  Las versiones anteriores del compilador no admiten imágenes de mapa de bits de 32 bits que tenían información alfa para la transparencia parcial. La solución alternativa para estas versiones es utilizar el formato *.png.*|
|Condición|Opcional. Consulte [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Mapas de bits](../extensibility/bitmaps-element.md)|Agrupa elementos de mapa de bits.|

## <a name="example"></a>Ejemplo

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Consulte también
- [Archivos de tabla de comandos de Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
