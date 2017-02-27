---
title: "Pesta&#241;a Clase (Cuadro de di&#225;logo Propiedades de la ventana) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cuadro de diálogo Propiedades de la ventana, pestaña Clase"
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Pesta&#241;a Clase (Cuadro de di&#225;logo Propiedades de la ventana)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use la pestaña **Clase** para mostrar información sobre la clase de la ventana seleccionada.  Para mostrar el [cuadro de diálogo Propiedades de la ventana](../debugger/window-properties-dialog-box.md), cambie el foco a la ventana [Vista Ventanas](../debugger/windows-view.md).  Seleccione el nodo de una ventana en el árbol y, a continuación, elija **Propiedades** en el menú **Ver**.  
  
 En la pestaña **Clase** está disponible la configuración siguiente:  
  
|Entry|Descripción|  
|-----------|-----------------|  
|**Nombre de clase**|Nombre \(o número ordinal\) de esta clase de ventana.|  
|**Estilos de clase**|Combinación de códigos de estilos de clase.|  
|**Bytes de clase**|Datos específicos de la aplicación asociados a esta clase de ventana.|  
|**Átomo de clase**|Átomo de la clase que devuelve la llamada **RegisterClass**.|  
|**Ident. de instancia**|Identificador de instancia del módulo que registró la clase.  Los identificadores de instancia no son únicos.|  
|**Bytes de ventana**|Número de bytes adicionales asociado a cada ventana de esta clase.  La aplicación determina el significado de estos bytes.  Expanda el cuadro de lista para ver los valores de bytes en formato DWORD.|  
|**Proc. de ventana**|Dirección actual de la función **WndProc** para las ventanas de esta clase.  No es lo mismo que **Proc. de ventana** de la pestaña **General** si la ventana tiene subclases.|  
|**Nombre del menú**|Nombre del menú principal que está asociado a ventanas de esta clase \(es "ninguno" si no hay ningún menú\).|  
|**Ident. de icono**|Identificador del icono que está asociado a las ventanas de esta clase \(es "ninguno" si no hay ningún icono\).|  
|**Ident. de cursor**|Identificador del cursor que está asociado a las ventanas de esta clase \(es "ninguno" si no hay ningún cursor\).|  
|**Pincel de fondo**|Identificador del pincel de fondo que está asociado a las ventanas de esta clase, o uno de los colores COLOR\_\* predefinidos para pintar el fondo de la ventana \(es "ninguno" si no hay ningún pincel\).|