---
title: "Pesta&#241;a Memoria (Cuadro de di&#225;logo Propiedades del proceso) | Microsoft Docs"
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
  - "Propiedades de procesos para Windows NT"
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Pesta&#241;a Memoria (Cuadro de di&#225;logo Propiedades del proceso)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use la pestaña **Memoria** para mostrar cómo usa un proceso la memoria.  Para mostrar el [cuadro de diálogo Propiedades del proceso](../debugger/process-properties-dialog-box.md), cambie el foco a la ventana [Vista Procesos](../debugger/processes-view.md).  Seleccione el nodo de un proceso en el árbol y, a continuación, elija **Propiedades** en el menú **Ver**.  
  
 En la pestaña **Memoria** está disponible la configuración siguiente:  
  
|Entry|Descripción|  
|-----------|-----------------|  
|**Bytes virtuales**|Tamaño actual \(en bytes\) del espacio de direcciones virtuales que usa el proceso.  El uso del espacio de direcciones virtuales no implica necesariamente una correspondencia con el uso del disco o de páginas de memoria principal.  Sin embargo, el espacio virtual es finito y, si se usa en exceso, se puede limitar la capacidad del proceso para cargar las bibliotecas.|  
|**Bytes virtuales máximos**|Número máximo de bytes de espacio de direcciones virtuales que el proceso ha usado en un momento dado.|  
|**Espacio de trabajo**|Conjunto de páginas de memoria que han usado recientemente los subprocesos del proceso.  Si la memoria libre del equipo está por encima de un determinado umbral, las páginas permanecen en el espacio de trabajo de un proceso aunque no se usen.  Cuando la memoria libre desciende por debajo de un determinado umbral, las páginas se quitan del espacio de trabajo.  Si son necesarias, se producirá un error de página en memoria y regresarán al espacio de trabajo antes de dejar la memoria principal.|  
|**Espacio de trabajo máximo**|Número máximo de páginas en el espacio de trabajo de este proceso en un momento dado.|  
|**Bytes de bloque paginado**|Cantidad actual de bloque paginado que el proceso ha asignado.  El bloque paginado es un área de memoria de sistema donde los componentes del sistema operativo adquieren el espacio cuando logran las tareas que les han sido designadas.  Las páginas de bloque paginado se pueden transferir al archivo de paginación cuando el sistema no tenga acceso a las mismas durante períodos de tiempo ininterrumpidos.|  
|**Bytes de bloque no paginado**|Número actual de bytes del bloque no paginado asignado por el proceso.  El bloque no paginado es un área de memoria de sistema donde los componentes del sistema operativo adquieren el espacio cuando logran las tareas que les han sido designadas.  Las páginas de bloque no paginado no se pueden transferir al archivo de paginación; permanecen en memoria principal mientras estén asignadas.|  
|**Bytes privados**|Número actual de bytes asignados a este proceso que no se pueden compartir con otros procesos.|  
|**Bytes libres**|Espacio de direcciones virtuales total de este proceso que no está en uso.|  
|**Bytes reservados**|Cantidad total de memoria virtual reservada para que este proceso la use en un futuro.|  
|**Bytes de imagen libres**|Cantidad de espacio de direcciones virtuales que no está en uso o reservado por imágenes dentro de este proceso.|  
|**Bytes de imagen reservados**|Suma de la memoria virtual total reservada por las imágenes que se ejecutan dentro de este proceso.|