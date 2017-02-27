---
title: "Pesta&#241;a Archivo de paginaci&#243;n (Cuadro de di&#225;logo Propiedades del proceso) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Propiedades de procesos para Windows NT"
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Pesta&#241;a Archivo de paginaci&#243;n (Cuadro de di&#225;logo Propiedades del proceso)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use la pestaña **Archivo de paginación** para examinar el archivo de paginación de un proceso.  Para mostrar el [cuadro de diálogo Propiedades del proceso](../debugger/process-properties-dialog-box.md), cambie el foco a la ventana [Vista Procesos](../debugger/processes-view.md).  Seleccione el nodo de un proceso en el árbol y, a continuación, elija **Propiedades** en el menú **Ver**.  
  
 En la pestaña **Archivo de paginación** está disponible la configuración siguiente:  
  
|Entry|Descripción|  
|-----------|-----------------|  
|**Bytes de archivo de paginación**|Número actual de páginas del archivo de paginación que usa este proceso.  El archivo de paginación almacena las páginas de datos que usa el proceso pero que no se encuentran en otros archivos.  Todos los procesos usan el archivo de paginación, por lo que la falta de espacio puede producir errores durante la ejecución de otros procesos.|  
|**Bytes de archivo de paginación máximos**|Número máximo de páginas del archivo de paginación que este proceso ha usado.|  
|**Errores de página**|Número de errores de página de los subprocesos que se ejecutan en este proceso.  Un error de página se produce cuando un subproceso hace referencia a una página de memoria virtual que no está en su espacio de trabajo en la memoria principal.  Por lo tanto, la página no se recuperará desde el disco si está en la lista en espera y, por lo tanto, ya se encuentra en la memoria principal, o si otro proceso con el que se comparte la página la está usando.|