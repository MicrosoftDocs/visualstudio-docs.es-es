---
title: "Pesta&#241;a Salida (Cuadro de di&#225;logo Opciones de mensaje) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "opciones de mensaje, salida"
ms.assetid: 22dd48c2-6d17-41b1-b84c-9ddeaef68411
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Pesta&#241;a Salida (Cuadro de di&#225;logo Opciones de mensaje)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use la pestaña **Salida** para especificar qué datos de cada mensaje desea mostrar en la [vista Mensajes](../debugger/messages-view.md).  Para abrir el [cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md), elija **Mensajes de registro** en el menú **Spy**.  
  
 En la pestaña **Salida** está disponible la configuración siguiente:  
  
 **Números de línea**  
 Se muestran los números de línea.  
  
 **Nivel de anidamiento de mensajes**  
 A los mensajes anidados se les aplica un prefijo con un punto por nivel.  
  
 **Parámetros de mensaje originales**  
 Se muestran los valores hexadecimales **wParam** e **lParam**.  
  
 **Parámetros de mensaje descodificados**  
 Se muestran los resultados de la descodificación de los valores **lParam** y **wParam** específica del mensaje.  
  
 **Valores devueltos originales**  
 Se muestra el valor hexadecimal devuelto para **lResult**.  
  
 **Valores devueltos descodificados**  
 Se muestran los resultados de la descodificación del valor devuelto **lResult** específica del mensaje.  
  
 **Hora de origen del mensaje**  
 Tiempo transcurrido desde que se inició el sistema Windows \(sólo para los mensajes expuestos\).  
  
 **Posición del mouse en el mensaje**  
 Coordenadas de pantalla del mouse cuando se expuso el mensaje \(sólo para los mensajes expuestos\).  
  
 **Líneas como máximo**  
 Limita el número de líneas que se conservan en la vista Mensajes actualmente seleccionada.  
  
 **Registrar los mensajes también en el archivo**  
 Especifique un archivo de salida para el registro de mensajes.  Este archivo de salida se escribe simultáneamente con la ventana de registro de mensajes.  
  
 **Guardar configuración como predeterminada**  
 Guarda la configuración anterior para las nuevas ventanas de secuencias de mensajes.  Esta configuración se guarda al salir de Spy\+\+.