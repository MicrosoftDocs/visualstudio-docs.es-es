---
title: Pestaña memoria, cuadro de diálogo de propiedades de proceso | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b43dd047e4ebdb145092dc3b9f37098b8db6322e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474624"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Pestaña Memoria (Cuadro de diálogo Propiedades del proceso)
Use la **memoria** ficha para mostrar cómo un proceso utiliza la memoria. Para mostrar la [cuadro de diálogo de propiedades de proceso](../debugger/process-properties-dialog-box.md), mover el foco a un [vista procesos](../debugger/processes-view.md) ventana. Seleccione cualquier nodo de proceso en el árbol y después elija **propiedades** desde el **vista** menú.  
  
 Las siguientes opciones están disponibles en la **memoria** ficha:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Bytes virtuales**|El tamaño actual (en bytes) de espacio de direcciones virtuales que el proceso está usando. El uso de espacio de direcciones virtuales no implica necesariamente correspondencia con el uso de disco o las páginas de memoria principal. Sin embargo, el espacio virtual es finito y utilizar demasiado pueden limitar la capacidad del proceso para cargar bibliotecas.|  
|**Bytes virtuales máximos**|El número máximo de bytes de espacio de direcciones virtuales del proceso ha usado en un momento determinado.|  
|**Espacio de trabajo**|El conjunto de páginas de memoria usadas recientemente por los subprocesos del proceso. Si la memoria libre del equipo está por encima de un umbral, las páginas se mantienen en el espacio de trabajo de un proceso incluso si no están en uso. Cuando la memoria disponible cae por debajo del umbral, se reducen las páginas del espacio de trabajo. Si son necesarias, estarán un error flexible y vuelven al espacio de trabajo antes de abandonar la memoria principal.|  
|**Conjunto de trabajo máximo**|El número máximo de páginas en el espacio de trabajo de este proceso en cualquier momento dado.|  
|**Bytes de bloque paginado**|La cantidad actual de bloque paginado que el proceso ha asignado. Bloque paginado es un área de memoria de sistema donde los componentes del sistema operativo adquieren espacio al llevar a cabo sus tareas asignadas. Páginas de bloque paginado se pueden paginar en el archivo de paginación cuando no tiene acceso al sistema durante largos periodos de tiempo.|  
|**Bytes del bloque no paginado**|El número actual de bytes en el bloque de memoria no paginado asignada por el proceso. El bloque no paginado es un área de memoria del sistema donde se adquiere espacio por componentes del sistema operativo como llevar a cabo sus tareas asignadas. Las páginas de bloque no paginado no se pueden paginar en el archivo de paginación; permanecen en la memoria principal mientras estén asignados.|  
|**Bytes privados**|El número actual de bytes que este proceso ha asignado no puede compartirse con otros procesos.|  
|**Bytes libres**|El espacio de direcciones virtuales sin usar total de este proceso.|  
|**Bytes reservados**|La cantidad total de memoria virtual reservada para uso futuro por este proceso.|  
|**Bytes de imagen libres**|La cantidad de espacio de direcciones virtuales que no está en uso o reservado por imágenes dentro de este proceso.|  
|**Bytes de imagen reservados**|La suma de toda la memoria virtual reservada por las imágenes que se ejecutan dentro de este proceso.|