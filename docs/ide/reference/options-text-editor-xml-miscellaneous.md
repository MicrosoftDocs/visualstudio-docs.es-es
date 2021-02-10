---
title: Opciones, editor de texto, XML y varios
description: Obtenga información sobre cómo usar la página Varios de la sección XAML para cambiar las opciones de autocompletar y esquema del editor XML.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: d3451a2a8d64edbf0f9000c9e58387704ed815ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932283"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Opciones, editor de texto, XML y varios

Use la página de opciones **Varios** para cambiar los valores de finalización automática y esquema del Editor XML. Para acceder a otras opciones de XML, elija **Herramientas** > **Opciones** > **Editor de texto** > **XML** y, a continuación, elija **Varios**.

## <a name="auto-insert"></a>Inserción automática

**Etiquetas de cierre**

El editor de texto agrega etiquetas de cierre al crear elementos XML. Si se selecciona la etiqueta de inicio de un elemento, el editor inserta la etiqueta de cierre correspondiente, incluido el prefijo de espacio de nombres. Esta casilla está activada de forma predeterminada.

**Comillas de atributo**

Al crear atributos XML, el editor inserta los caracteres `="` y `"` y coloca el carácter de intercalación ( **^** ) dentro de las comillas. Esta casilla está activada de forma predeterminada.

**Declaraciones de espacio de nombres**

El editor inserta automáticamente declaraciones de espacios de nombres cuando son necesarias. Esta casilla está activada de forma predeterminada.

**Otro tipo de marcado (Comentarios, CDATA)**

Finalización automática de comentarios, CDATA, DOCTYPE, instrucciones de proceso y otro tipo de marcado. Esta casilla está activada de forma predeterminada.

## <a name="network"></a>Red

**Descargar automáticamente DTD y esquemas**

Los esquemas y las definiciones de tipos de documentos (DTD) se descargan automáticamente desde ubicaciones HTTP. Esta función utiliza System.Net con la opción de detección de servidores proxy automáticos habilitada. Esta casilla está activada de forma predeterminada.

## <a name="outlining"></a>esquematizar

**Especificar el modo de esquematización al abrir los archivos**

Activa la función de esquematización al abrir un archivo. Esta casilla está activada de forma predeterminada.

## <a name="caching"></a>Almacenamiento en memoria caché

**Esquemas**

Especifica la ubicación de la caché de esquemas. El botón **Examinar** abre la ubicación actual de la caché de esquema en una nueva ventana. La ubicación predeterminada es *%VsInstallDir%\xml\Schemas*.

## <a name="see-also"></a>Consulte también

- [Opciones de XML: formato](options-text-editor-xml-formatting.md)
- [Herramientas XML en Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
