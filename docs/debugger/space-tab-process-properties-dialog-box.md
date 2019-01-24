---
title: Pestaña espacio, cuadro de diálogo de propiedades de proceso | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9cc3489cd07576521356a40c9d4abd42507aee9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853260"
---
# <a name="space-tab-process-properties-dialog-box"></a>Pestaña Espacio (Cuadro de diálogo Propiedades del proceso)
Use la **espacio** pestaña para examinar el espacio de direcciones de un proceso. Para mostrar el [cuadro de diálogo de propiedades de proceso](../debugger/process-properties-dialog-box.md), mover el foco a un [vista procesos](../debugger/processes-view.md) ventana. Seleccione cualquier nodo de proceso en el árbol y luego elija **propiedades** desde el **vista** menú.  
  
 Las siguientes opciones están disponibles en el **espacio** pestaña:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Mostrar para espacio marcado como**|Utilice este cuadro de lista para seleccionar la categoría de espacio (imagen, asignado, reservado o sin asignar).|  
|**Bytes ejecutables**|Para la categoría seleccionada, la suma de todo el espacio de dirección que está usando este proceso. La memoria de ejecución es la memoria que se pueden ejecutar programas, pero no pueden leer o escribir.|  
|**Bytes de solo lectura y ejecución**|Para la categoría seleccionada, la suma de todo el espacio de direcciones en uso con propiedades de solo lectura que está usando este proceso. Memoria de solo lectura de exec es que puede ejecutarse además de leer.|  
|**Bytes de ejecución, lectura y copia**|Para la categoría seleccionada, la suma de todo el espacio de direcciones en uso con las propiedades de lectura y escritura que utiliza este proceso. Memoria de exec-lectura y escritura es que se pueden ejecutar los programas, así como leer y modificar.|  
|**Copia Bytes de escritura de exec**|Para la categoría seleccionada, la suma de todo el espacio de direcciones que se puede ejecutar los programas, así como leer y escribir. Este tipo de protección se usa cuando se necesita la memoria se comparte entre procesos. Si los procesos comparten solo leen la memoria, todos ellos utilizarán la misma memoria. Si un proceso compartido desea acceso de escritura, se realizará una copia de esta memoria para el proceso.|  
|**Bytes no accesibles**|Para la categoría seleccionada, la suma de todo el espacio de dirección que impide que un proceso de usarlo. Se intenta leer o si escribe, se genera una infracción de acceso.|  
|**Bytes de solo lectura**|Para la categoría seleccionada, la suma de todo el espacio de direcciones que puede ejecutarse además de leer.|  
|**Bytes de lectura y escritura**|Para la categoría seleccionada, la suma de todo el espacio de direcciones que permite leer y escribir.|  
|**Bytes de escritura y copia**|Para la categoría seleccionada, la suma de todo el espacio de direcciones que permite compartir memoria para lectura pero no para escribir en él. Cuando los procesos estén leyendo esta memoria, pueden compartir la misma memoria. Sin embargo, cuando un proceso de uso compartido desea tener acceso de lectura/escritura a esta memoria compartida, se realiza una copia de la memoria para escribir en él.|