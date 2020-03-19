---
title: Opciones, editor de texto, XML y varios
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: dd468945b1ab9ac83b219b9c8c396f017065e2be
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568131"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Opciones, editor de texto, XML y varios

Use la página de opciones **Varios** para cambiar los valores de finalización automática y esquema del Editor XML. Para acceder a otras opciones de XML, elija **Herramientas** > **Opciones** > **Editor de texto** > **XML** y, a continuación, elija **Varios**.

## <a name="auto-insert"></a>Inserción automática

**Etiquetas de cierre**

El editor de texto agrega etiquetas de cierre al crear elementos XML. Si se selecciona una etiqueta de inicio de elemento, el editor inserta la etiqueta de cierre correspondiente, incluido un prefijo de espacio de nombres coincidente. Esta casilla se encuentra activada de forma predeterminada.

**Comillas de atributo**

Al crear atributos XML, el editor inserta los caracteres `="` y `"` y coloca el carácter de intercalación ( **^** ) dentro de las comillas. Esta casilla se encuentra activada de forma predeterminada.

**Declaraciones de espacio de nombres**

El editor inserta automáticamente declaraciones de espacio de nombres siempre que se necesitan. Esta casilla se encuentra activada de forma predeterminada.

**Otro marcado (comentarios, CDATA)**

Se completan automáticamente comentarios, CDATA, DOCTYPE, instrucciones de procesamiento y otro marcado. Esta casilla se encuentra activada de forma predeterminada.

## <a name="network"></a>Red

**Descargar automáticamente DTD y esquemas**

Los esquemas y las definiciones de tipo de documento (DTD) se descargan automáticamente desde ubicaciones HTTP. Esta característica usa System.Net con la detección automática del servidor proxy habilitada. Esta casilla se encuentra activada de forma predeterminada.

## <a name="outlining"></a>Esquematización

**Especificar el modo de esquematización al abrir los archivos**

Activa la característica de esquematización cuando se abre un archivo. Esta casilla se encuentra activada de forma predeterminada.

## <a name="caching"></a>Almacenamiento en memoria caché

**Esquemas**

Especifica la ubicación de la caché de esquema. El botón **Examinar** abre la ubicación actual de la caché de esquema en una nueva ventana. La ubicación predeterminada es *%VsInstallDir%\xml\Schemas*.

## <a name="see-also"></a>Vea también

- [Opciones de XML: formato](options-text-editor-xml-formatting.md)
- [Herramientas XML en Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
