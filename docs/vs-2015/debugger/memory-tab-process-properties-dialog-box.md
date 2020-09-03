---
title: Pestaña Memoria del cuadro de diálogo Propiedades del proceso | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b70c5a982da866cbeb9e9907859ad4d270d79bd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203299"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Pestaña Memoria del cuadro de diálogo Propiedades del proceso
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use la pestaña **Memoria** para mostrar el uso de la memoria por parte de un proceso. Para mostrar el [cuadro de diálogo Propiedades del proceso](../debugger/process-properties-dialog-box.md), mueva el foco a la ventana [Vista Procesos](../debugger/processes-view.md). Seleccione cualquier nodo de proceso en el árbol y, después, elija **Propiedades** en el menú **Vista**.  
  
 En la pestaña **Memoria** están disponibles los valores siguientes:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Bytes virtuales**|Tamaño actual (en bytes) del espacio de direcciones virtuales que el proceso usa. El uso del espacio de direcciones virtuales no implica necesariamente un uso equivalente de páginas de disco o de memoria principal. Sin embargo, el espacio virtual es finito y, al usarlo en exceso, se puede limitar la capacidad del proceso para cargar bibliotecas.|  
|**Bytes virtuales máximos**|Número máximo de bytes de espacio de direcciones virtuales que el proceso ha usado en un momento dado.|  
|**Espacio de trabajo**|Conjunto de páginas de memoria usadas recientemente por los subprocesos del proceso. Si la memoria disponible del equipo está por encima de un umbral, las páginas se mantienen en el espacio de trabajo de un proceso, incluso aunque no se estén usando. Si la memoria disponible pasa a estar por debajo del umbral, se recuperarán las páginas desde el espacio de trabajo. Si son necesarias, se produce un error de página y devuelven al espacio de trabajo antes de abandonar la memoria principal.|  
|**Espacio de trabajo máximo**|Número máximo de páginas del espacio de trabajo de este proceso en cualquier momento.|  
|**Bytes de bloque paginado**|Cantidad actual de bloque paginado que el proceso ha asignado. El bloque paginado es un área de memoria del sistema donde los componentes del sistema operativo adquieren espacio a medida que realizan sus tareas designadas. Las páginas de bloque paginado se pueden paginar en el archivo de paginación cuando el sistema no tiene acceso a estas durante períodos de tiempo prolongados.|  
|**Bytes de bloque no paginado**|Número actual de bytes del bloque no paginado que el proceso ha asignado. El bloque no paginado es un área de memoria del sistema donde los componentes del sistema operativo adquieren espacio a medida que realizan sus tareas designadas. Las páginas del bloque no paginado no se pueden paginar en el archivo de paginación; permanecen en la memoria principal siempre y cuando se asignen.|  
|**Bytes privados**|Número actual de bytes que este proceso ha asignado y no es posible compartir con otros procesos.|  
|**Bytes libres**|Espacio total de direcciones virtuales sin usar de este proceso.|  
|**Bytes reservados**|Cantidad total de memoria virtual reservada para el uso futuro por parte de este proceso.|  
|**Bytes de imagen libres**|Cantidad de espacio de direcciones virtuales que no está en uso o está reservada por las imágenes dentro de este proceso.|  
|**Bytes de imagen reservados**|Suma de toda la memoria virtual reservada por las imágenes que se ejecutan dentro de este proceso.|
