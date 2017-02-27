---
title: "Pesta&#241;a General (Cuadro de di&#225;logo Propiedades de la ventana) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cuadro de diálogo Propiedades de la ventana, pestaña General"
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Pesta&#241;a General (Cuadro de di&#225;logo Propiedades de la ventana)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use la pestaña **General** para mostrar información sobre la ventana seleccionada.  Para mostrar el [cuadro de diálogo Propiedades de la ventana](../debugger/window-properties-dialog-box.md), cambie el foco a la ventana [Vista Ventanas](../debugger/windows-view.md).  Seleccione el nodo de una ventana en el árbol y, a continuación, elija **Propiedades** en el menú **Ver**.  
  
 En la pestaña **General** está disponible la configuración siguiente:  
  
|Entry|Descripción|  
|-----------|-----------------|  
|**Leyenda de ventana**|Texto de la leyenda de la ventana, o texto que contiene una ventana si es un control.|  
|**Identificador de ventana**|Identificador único de esta ventana.  Los números de identificador de ventana se reutilizan, ya que solo identifican una ventana durante su existencia.|  
|**Proc. de ventana**|Dirección virtual de la función de procedimiento de ventana que corresponde a esta ventana.  Este campo también indica si esta ventana es de Unicode, y si tiene subclases.|  
|**Rectángulo**|Rectángulo delimitador de la ventana.  También se muestra el tamaño del rectángulo.  Las unidades son píxeles en coordenadas de pantalla.|  
|**Rectángulo restaurado**|Rectángulo delimitador de la ventana restaurada.  También se muestra el tamaño del rectángulo.  El rectángulo restaurado sólo diferirá del rectángulo cuando la ventana se maximice o minimice.  Las unidades son píxeles en coordenadas de pantalla.|  
|**Rectángulo de cliente**|Rectángulo delimitador para el área de cliente de la ventana.  También se muestra el tamaño del rectángulo.  Las unidades son píxeles relativos a la parte superior izquierda del área de cliente de la ventana.|  
|**Ident. de instancia**|Identificador de instancia de la aplicación.  Los identificadores de instancia no son únicos.|  
|**Id. de control o Identificador de menú**|Si la ventana que se muestra es una ventana secundaria, aparece la etiqueta Id. de control.  Es un entero que identifica el identificador de control de esta ventana secundaria.  Si la ventana que se muestra no es una ventana secundaria, aparece la etiqueta de Identificador de menú.  Es un entero que identifica el identificador del menú asociado a esta ventana.|  
|**Datos del usuario**|Datos específicos de la aplicación que se adjuntan a esta estructura de ventana.|  
|**Bytes de ventana**|Número de bytes adicionales asociado a esta ventana.  La aplicación determina el significado de estos bytes.  Expanda el cuadro de lista para ver los valores de bytes en formato DWORD.|