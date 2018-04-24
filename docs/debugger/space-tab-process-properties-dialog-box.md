---
title: Pestaña espacio, cuadro de diálogo de propiedades de proceso | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee4b5a416c7d3eb466498e7cf4ff727134c0f20f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="space-tab-process-properties-dialog-box"></a>Pestaña Espacio (Cuadro de diálogo Propiedades del proceso)
Use la **espacio** pestaña para examinar el espacio de direcciones de un proceso. Para mostrar la [cuadro de diálogo de propiedades de proceso](../debugger/process-properties-dialog-box.md), mover el foco a un [vista procesos](../debugger/processes-view.md) ventana. Seleccione cualquier nodo de proceso en el árbol y después elija **propiedades** desde el **vista** menú.  
  
 Las siguientes opciones están disponibles en la **espacio** ficha:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Mostrar para espacio marcado como**|Utilice este cuadro de lista para seleccionar la categoría de espacio (imagen, asignado, reservado o sin asignar).|  
|**Bytes ejecutables**|Para la categoría seleccionada, la suma de todo el espacio de dirección que está usando este proceso. La memoria de ejecución es la memoria que puede ser ejecutada por programas, pero no pueden leer o escribir.|  
|**Bytes de solo lectura de exec**|Para la categoría seleccionada, la suma de todo el espacio de direcciones en uso con propiedades de solo lectura que está usando este proceso. Memoria de solo lectura de exec es que puede ejecutarse además de leer.|  
|**Bytes de Exec, lectura y escritura**|Para la categoría seleccionada, la suma de todo el espacio de direcciones en uso con propiedades de lectura y escritura que utiliza este proceso. Memoria de Exec, lectura y escritura es memoria que puede ejecutar los programas, así como leer y modificar.|  
|**Copia Bytes de escritura de exec**|Para la categoría seleccionada, la suma de todo el espacio de direcciones que puede ser ejecutada por programas, así como leer y escribir. Este tipo de protección se usa cuando se necesita la memoria se comparte entre los procesos. Si los procesos comparten la memoria únicamente para leerla, todos usarán la misma memoria. Si un proceso compartido desea acceso de escritura, se realizará una copia de esta memoria para el proceso.|  
|**Bytes sin acceso**|Para la categoría seleccionada, la suma de todo el espacio de dirección que impide que un proceso de usarlo. Se intenta leer o si escribe, se genera una infracción de acceso.|  
|**Bytes de solo lectura**|Para la categoría seleccionada, la suma de todo el espacio de direcciones que puede ejecutarse además de leer.|  
|**Bytes de lectura y escritura**|Para la categoría seleccionada, la suma de todo el espacio de dirección que permite leer y escribir.|  
|**Bytes de escritura y copia**|Para la categoría seleccionada, la suma de todo el espacio de dirección que permite compartir memoria para lectura pero no para escribir en él. Cuando los procesos estén leyendo esta memoria, pueden compartir la misma memoria. Sin embargo, cuando un proceso que comparte desea tener acceso de lectura/escritura a esta memoria compartida, se crea una copia de esa memoria para escribir en él.|