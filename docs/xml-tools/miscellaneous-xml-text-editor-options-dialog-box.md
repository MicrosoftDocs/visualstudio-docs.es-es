---
title: "Varios, XML, Editor de texto, Cuadro de di&#225;logo Opciones | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Varios, XML, Editor de texto, Cuadro de di&#225;logo Opciones
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este cuadro de diálogo permite cambiar las opciones de finalización automática y esquema del Editor XML.Puede tener acceso al cuadro de diálogo **Opciones** desde el menú **Herramientas**.  
  
> [!NOTE]
>  Estas opciones están disponibles cuando se selecciona la carpeta **Editor de texto**, la carpeta **XML** y, a continuación, la opción **Varios** del cuadro de diálogo **Opciones**.  
  
## Inserción automática  
 **Etiquetas de cierre**  
 Si se activa la configuración de autocompletar, el editor agrega automáticamente una etiqueta de cierre al escribir un corchete derecho \(\>\) para cerrar una etiqueta inicial, si la etiqueta aún no está cerrada.Éste es el comportamiento predeterminado.  
  
 La finalización de un elemento vacío no depende de la configuración de autocompletar.Siempre puede autocompletar un elemento vacío escribiendo una barra diagonal inversa \(\/\).  
  
 **Comillas de atributos**  
 Al crear atributos XML, el editor inserta los caracteres `=" "` y coloca el carácter de intercalación \(^\) dentro de las comillas dobles.  
  
 Esta opción está seleccionada de forma predeterminada.  
  
 **Declaraciones de espacio de nombres**  
 El editor inserta automáticamente declaraciones de espacio de nombres siempre que se necesitan.  
  
 Esta opción está seleccionada de forma predeterminada.  
  
 **Otro marcado \(Comentarios, CDATA\)**  
 Se completan automáticamente comentarios, CDATA, DOCTYPE, instrucciones de procesamiento y otro marcado.  
  
 Esta opción está seleccionada de forma predeterminada.  
  
## Red  
 **Descargar automáticamente DTD y esquemas**  
 Los esquemas y las definiciones de tipo de documento \(DTD\) se descargan automáticamente desde ubicaciones HTTP.Esta característica utiliza System.Net con la detección automática del servidor proxy habilitada.  
  
 Esta opción está seleccionada de forma predeterminada.  
  
## Esquematización  
 **Especificar el modo de esquematización al abrir los archivos**  
 Activa la característica de esquematización cuando se abre un archivo.  
  
 Esta opción está seleccionada de forma predeterminada.  
  
## Almacenamiento en caché  
 **Esquemas**  
 Especifica la ubicación de la caché de esquema.El botón Examinar \(**...**\) abre el cuadro de diálogo **Mostrar directorios** en la ubicación actual de la caché de esquema.Puede seleccionar otro directorio, o una carpeta del cuadro de diálogo, hacer clic con el botón secundario y elegir **Abrir** para ver lo que hay en el directorio.  
  
## Vea también  
 [Propiedades de documentos XML, Ventana Propiedades](../xml-tools/xml-document-properties-properties-window.md)   
 [Componentes del Editor XML](../xml-tools/xml-editor-components.md)