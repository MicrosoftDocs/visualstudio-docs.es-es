---
title: Pestaña memoria, cuadro de diálogo de propiedades de proceso | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 92718a20f5deb19890a58d68af85e7f897f2440a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785149"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Pestaña Memoria (Cuadro de diálogo Propiedades del proceso)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use la **memoria** pestaña para mostrar cómo un proceso utiliza la memoria. Para mostrar el [cuadro de diálogo de propiedades de proceso](../debugger/process-properties-dialog-box.md), mover el foco a un [vista procesos](../debugger/processes-view.md) ventana. Seleccione cualquier nodo de proceso en el árbol y luego elija **propiedades** desde el **vista** menú.  
  
 Las siguientes opciones están disponibles en el **memoria** pestaña:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Bytes virtuales**|El tamaño actual (en bytes) del espacio de direcciones virtual que está usando el proceso. El uso de espacio de direcciones virtuales no implica necesariamente correspondencia con el uso del disco o de páginas de memoria principal. Sin embargo, el espacio virtual es finito y demasiado utilizar pueden limitar la capacidad del proceso para cargar bibliotecas.|  
|**Bytes virtuales máximos**|El número máximo de bytes de espacio de direcciones virtuales del proceso ha usado en cualquier momento.|  
|**Espacio de trabajo**|El conjunto de páginas de memoria usadas recientemente por los subprocesos del proceso. Si la memoria libre en el equipo está por encima de un umbral, las páginas quedan en el espacio de trabajo de un proceso incluso aunque no estén en uso. Cuando la memoria disponible cae por debajo del umbral, se recuperan las páginas del conjunto de trabajo. Si se necesitan, estarán soft genere un error en el espacio de trabajo antes de abandonar la memoria principal.|  
|**Conjunto de trabajo máximo**|El número máximo de páginas en el espacio de trabajo de este proceso en cualquier momento.|  
|**Bytes de bloque paginado**|La cantidad actual de bloque paginado, que el proceso ha asignado. Bloque paginado es un área de memoria del sistema donde los componentes del sistema operativo adquieren espacio al llevar a cabo sus tareas asignadas. Páginas de bloque paginado se puedan paginar en el archivo de paginación cuando no tiene acceso a por el sistema durante períodos prolongados de tiempo.|  
|**Bytes del bloque no paginado**|El número actual de bytes del bloque no paginado asignada por el proceso. El bloque no paginado es un área de memoria del sistema donde se adquiere espacio por componentes del sistema operativo como para realizar sus tareas asignadas. Las páginas de bloque no paginado se no se pueden paginar en el archivo de paginación; permanecen en la memoria principal como están asignados.|  
|**Bytes privados**|El número actual de bytes que este proceso ha asignado no puede compartirse con otros procesos.|  
|**Bytes libres**|El espacio de direcciones virtuales no utilizadas de total de este proceso.|  
|**Bytes reservados**|La cantidad total de memoria virtual reservada para uso futuro por este proceso.|  
|**Bytes de imagen libres**|La cantidad de espacio de direcciones virtuales que no está en uso o reservado por imágenes dentro de este proceso.|  
|**Bytes de imagen reservados**|La suma de toda la memoria virtual reservada por las imágenes que se ejecutan dentro de este proceso.|



