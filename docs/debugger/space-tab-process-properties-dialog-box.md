---
title: "Pesta&#241;a Espacio (Cuadro de di&#225;logo Propiedades del proceso) | Microsoft Docs"
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
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Pesta&#241;a Espacio (Cuadro de di&#225;logo Propiedades del proceso)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use la pestaña **Espacio** para examinar el espacio de direcciones de un proceso.  Para mostrar el [cuadro de diálogo Propiedades del proceso](../debugger/process-properties-dialog-box.md), cambie el foco a la ventana [Vista Procesos](../debugger/processes-view.md).  Seleccione el nodo de un proceso en el árbol y, a continuación, elija **Propiedades** en el menú **Ver**.  
  
 En la pestaña **Espacio** está disponible la configuración siguiente:  
  
|Entry|Descripción|  
|-----------|-----------------|  
|**Mostrar para espacio marcado como**|Use este cuadro de lista para seleccionar la categoría del espacio \(imagen, asignado, reservado o sin asignar\).|  
|**Bytes ejecutables**|Para la categoría seleccionada, la suma de todo el espacio de direcciones que usa este proceso.  La memoria ejecutable es memoria que pueden ejecutar los programas, pero no se puede leer ni escribir.|  
|**Bytes de solo lectura y ejecución**|Para la categoría seleccionada, la suma de todo el espacio de direcciones en uso con propiedades de solo lectura que usa este proceso.  La memoria de solo lectura y ejecución es memoria que se puede ejecutar y leer.|  
|**Bytes de ejecución, lectura y copia**|Para la categoría seleccionada, la suma de todo el espacio de direcciones en uso con propiedades de lectura y escritura que usa este proceso.  La memoria de ejecución, lectura y escritura es memoria que pueden ejecutar los programas, y que se puede leer y modificar.|  
|**Bytes de ejecución, escritura y copia**|Para la categoría seleccionada, la suma de todo el espacio de direcciones que pueden ejecutar los programas, y que se puede leer y escribir.  Este tipo de protección se usa cuando es necesario compartir la memoria entre los procesos.  Si los procesos que comparten la memoria solo la leen, todos usarán la misma memoria.  Si un proceso que comparte la memoria desea acceso de escritura, se realizará una copia de esta memoria para el proceso.|  
|**Bytes no accesibles**|Para la categoría seleccionada, la suma de todo el espacio de direcciones que no está disponible para un proceso.  Se generará una infracción de acceso si se intenta la lectura o escritura.|  
|**Bytes de solo lectura**|Para la categoría seleccionada, la suma de todo el espacio de direcciones que se puede ejecutar y leer.|  
|**Bytes de lectura y escritura**|Para la categoría seleccionada, la suma de todo el espacio de direcciones que permite la lectura y escritura.|  
|**Bytes de escritura y copia**|Para la categoría seleccionada, la suma de todo el espacio de direcciones que permite el uso compartido de memoria para la lectura, pero no para la escritura.  Cuando los procesos leen esta memoria, pueden compartirla.  Sin embargo, cuando un proceso que comparte la memoria desea tener acceso de lectura y escritura en esta memoria compartida, se realiza una copia de la memoria para escritura.|