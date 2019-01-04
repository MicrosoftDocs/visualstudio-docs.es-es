---
title: Varios, XML, Editor de texto, Cuadro de diálogo Opciones
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 85af563d9fb20b12785a410cf7df7e612d17dbee
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941406"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Varios, XML, Editor de texto, cuadro de diálogo Opciones

Este cuadro de diálogo permite cambiar las opciones de finalización automática y esquema del Editor XML. Puede tener acceso a la **opciones** cuadro de diálogo desde el **herramientas** menú.

> [!NOTE]
> Estas opciones están disponibles cuando se selecciona el **Editor de texto** carpeta, el **XML** carpeta y, a continuación, el **varios** opción desde el **opciones** cuadro de diálogo.


## <a name="auto-insert"></a>Inserción automática
 **Etiquetas de cierre**

 Si se activa la configuración de autocompletar, el editor agrega automáticamente una etiqueta de cierre al escribir un corchete derecho (>) para cerrar una etiqueta inicial, si la etiqueta aún no está cerrada. Éste es el comportamiento predeterminado.

 La finalización de un elemento vacío no depende de la configuración de autocompletar. Siempre puede autocompletar un elemento vacío escribiendo una barra diagonal inversa (/).

 **Comillas de atributo**

 Al crear atributos XML, el editor inserta los caracteres `=" "` y coloca el carácter de intercalación (^) dentro de las comillas dobles.

 Esta opción está seleccionada de forma predeterminada.

 **Declaraciones de espacio de nombres**

 El editor inserta automáticamente declaraciones de espacio de nombres siempre que se necesitan.

 Esta opción está seleccionada de forma predeterminada.

 **Otro marcado (comentarios, CDATA)**

 Se completan automáticamente comentarios, CDATA, DOCTYPE, instrucciones de procesamiento y otro marcado.

 Esta opción está seleccionada de forma predeterminada.

## <a name="network"></a>Red
 **Descargar automáticamente DTD y esquemas**

 Los esquemas y las definiciones de tipo de documento (DTD) se descargan automáticamente desde ubicaciones HTTP. Esta característica utiliza System.Net con la detección automática del servidor proxy habilitada.

 Esta opción está seleccionada de forma predeterminada.

## <a name="outlining"></a>esquematizar
 **Especificar el modo de esquematización al abrir los archivos**

 Activa la característica de esquematización cuando se abre un archivo.

 Esta opción está seleccionada de forma predeterminada.

## <a name="caching"></a>Almacenamiento en memoria caché
 **Esquemas**

 Especifica la ubicación de la caché de esquema. El botón Examinar (**...** ) se abre el **Examinar directorio** cuadro de diálogo en la ubicación de caché de esquema actual. Puede seleccionar un directorio diferente, o puede seleccionar una carpeta en el cuadro de diálogo con el botón secundario y elija **abierto** ver lo que hay en el directorio.

## <a name="see-also"></a>Vea también

- [Propiedades del documento XML, ventana Propiedades](../xml-tools/xml-document-properties-properties-window.md)
- [Componentes del editor XML](../xml-tools/xml-editor-components.md)