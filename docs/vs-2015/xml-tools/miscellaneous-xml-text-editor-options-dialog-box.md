---
title: Varios, XML, editor de texto, opciones (cuadro de diálogo) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d30564c11951d6ffec420c6a2ea95c41695de3dd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656236"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Varios, XML, Editor de texto, Cuadro de diálogo Opciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este cuadro de diálogo permite cambiar las opciones de finalización automática y esquema del Editor XML. Puede tener acceso al cuadro de diálogo **Opciones** desde el menú **herramientas** .

> [!NOTE]
> Estas opciones están disponibles cuando se selecciona la carpeta **Editor de texto** , la carpeta **XML** y, a continuación, la opción **varios** del cuadro de diálogo **Opciones** .

## <a name="auto-insert"></a>Inserción automática
 **Etiquetas de cierre** Si se activa la opción Autocompletar, el editor agrega automáticamente una etiqueta de cierre cuando se escribe un corchete angular de cierre (>) para cerrar una etiqueta de apertura, si la etiqueta no está ya cerrada. Éste es el comportamiento predeterminado.

 La finalización de un elemento vacío no depende de la configuración de autocompletar. Siempre puede autocompletar un elemento vacío escribiendo una barra diagonal inversa (/).

 **Comillas de atributo** Al crear atributos XML, el editor inserta los caracteres `=" "` y coloca el símbolo de intercalación (^) dentro de las comillas dobles.

 Esta opción está seleccionada de forma predeterminada.

 **Declaraciones de espacios de nombres** El editor inserta automáticamente declaraciones de espacio de nombres siempre que se necesiten.

 Esta opción está seleccionada de forma predeterminada.

 **Otro marcado (comentarios, CDATA)** Los comentarios, CDATA, DOCTYPE, las instrucciones de procesamiento y otro marcado se completan automáticamente.

 Esta opción está seleccionada de forma predeterminada.

## <a name="network"></a>Red
 **Descargar automáticamente DTD y esquemas** Los esquemas y las definiciones de tipo de documento (DTD) se descargan automáticamente desde ubicaciones HTTP. Esta característica utiliza System.Net con la detección automática del servidor proxy habilitada.

 Esta opción está seleccionada de forma predeterminada.

## <a name="outlining"></a>esquematizar
 **Especificar el modo de esquematización al abrir los archivos** Activa la característica de esquematización al abrir un archivo.

 Esta opción está seleccionada de forma predeterminada.

## <a name="caching"></a>Almacenamiento en memoria caché
 **Esquemas** Especifica la ubicación de la caché de esquema. El botón Examinar ( **...** ) abre el cuadro de diálogo **examinar directorio** en la ubicación actual de la caché de esquemas. Puede seleccionar un directorio diferente, o puede seleccionar una carpeta en el cuadro de diálogo, hacer clic con el botón derecho y elegir **abrir** para ver qué hay en el directorio.

## <a name="see-also"></a>Vea también
 [Propiedades de documento XML, ventana Propiedades](../xml-tools/xml-document-properties-properties-window.md) [componentes del editor XML](../xml-tools/xml-editor-components.md)
