---
title: Pestaña espacio, cuadro de diálogo de propiedades de proceso | Documentos de Microsoft
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
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 03b73263f6db5e702a44b8854517ec5ee132b561
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259927"
---
# <a name="space-tab-process-properties-dialog-box"></a>Pestaña Espacio (Cuadro de diálogo Propiedades del proceso)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use la **espacio** pestaña para examinar el espacio de direcciones de un proceso. Para mostrar el [cuadro de diálogo de propiedades de proceso](../debugger/process-properties-dialog-box.md), mover el foco a un [vista procesos](../debugger/processes-view.md) ventana. Seleccione cualquier nodo de proceso en el árbol y luego elija **propiedades** desde el **vista** menú.  
  
 Las siguientes opciones están disponibles en el **espacio** pestaña:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Mostrar para espacio marcado como**|Utilice este cuadro de lista para seleccionar la categoría de espacio (imagen, asignado, reservado o sin asignar).|  
|**Bytes ejecutables**|Para la categoría seleccionada, la suma de todo el espacio de dirección que está usando este proceso. La memoria de ejecución es la memoria que se pueden ejecutar programas, pero no pueden leer o escribir.|  
|**Bytes de solo lectura de exec**|Para la categoría seleccionada, la suma de todo el espacio de direcciones en uso con propiedades de solo lectura que está usando este proceso. Memoria de solo lectura de exec es que puede ejecutarse además de leer.|  
|**Bytes de lectura y escritura-Exec**|Para la categoría seleccionada, la suma de todo el espacio de direcciones en uso con las propiedades de lectura y escritura que utiliza este proceso. Memoria de exec-lectura y escritura es que se pueden ejecutar los programas, así como leer y modificar.|  
|**Copia Bytes de escritura de exec**|Para la categoría seleccionada, la suma de todo el espacio de direcciones que se puede ejecutar los programas, así como leer y escribir. Este tipo de protección se usa cuando se necesita la memoria se comparte entre procesos. Si los procesos comparten solo leen la memoria, todos ellos utilizarán la misma memoria. Si un proceso compartido desea acceso de escritura, se realizará una copia de esta memoria para el proceso.|  
|**Bytes no accesibles**|Para la categoría seleccionada, la suma de todo el espacio de dirección que impide que un proceso de usarlo. Se intenta leer o si escribe, se genera una infracción de acceso.|  
|**Bytes de solo lectura**|Para la categoría seleccionada, la suma de todo el espacio de direcciones que puede ejecutarse además de leer.|  
|**Bytes de lectura y escritura**|Para la categoría seleccionada, la suma de todo el espacio de direcciones que permite leer y escribir.|  
|**Bytes de escritura y copia**|Para la categoría seleccionada, la suma de todo el espacio de direcciones que permite compartir memoria para lectura pero no para escribir en él. Cuando los procesos estén leyendo esta memoria, pueden compartir la misma memoria. Sin embargo, cuando un proceso de uso compartido desea tener acceso de lectura/escritura a esta memoria compartida, se realiza una copia de la memoria para escribir en él.|



