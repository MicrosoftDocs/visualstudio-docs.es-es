---
title: Pestaña Espacio, Propiedades del proceso (cuadro de diálogo) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: de5df4c55feba8c9aaba0def7585029cc71426b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189423"
---
# <a name="space-tab-process-properties-dialog-box"></a>Pestaña Espacio, Propiedades del proceso (cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use la pestaña **Espacio** para examinar el espacio de direcciones de un proceso. Para que se muestre el cuadro de diálogo [Propiedades del proceso](../debugger/process-properties-dialog-box.md), mueva el foco a una ventana [Vista Procesos](../debugger/processes-view.md). Seleccione cualquier nodo de proceso en el árbol y, a continuación, seleccione **Propiedades** en el menú **Ver**.  
  
 En la pestaña **Espacio** están disponibles los valores siguientes:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Mostrar para espacio marcado como**|Use este cuadro de lista para seleccionar la categoría de espacio (imagen, asignado, reservado o sin asignar).|  
|**Bytes ejecutables**|En la categoría seleccionada, corresponde a la suma de todo el espacio de direcciones que usa este proceso. La memoria ejecutable es la memoria que pueden ejecutar los programas, pero no se puede leer ni escribir en ella.|  
|**Bytes de solo lectura y ejecución**|En la categoría seleccionada, corresponde a la suma de todo el espacio de direcciones en uso con propiedades de solo lectura que utiliza este proceso. La memoria de ejecución y lectura es la memoria que se puede ejecutar y leer.|  
|**Bytes de ejecución, lectura y copia**|En la categoría seleccionada, corresponde a la suma de todo el espacio de direcciones en uso con propiedades de lectura y escritura que utiliza este proceso. La memoria de ejecución, lectura y copia es la memoria que pueden ejecutar los programas, y que se puede leer y modificar.|  
|**Bytes de ejecución, escritura y copia**|En la categoría seleccionada, corresponde a la suma de todo el espacio de direcciones que pueden ejecutar los programas, y se puede leer y escribir en ella. Este tipo de protección se usa cuando es necesario compartir la memoria entre los procesos. Si los procesos de uso compartido solo leen la memoria, todos usarán la misma memoria. Si un proceso de uso compartido debe tener acceso de escritura, se realizará una copia de esta memoria para el proceso.|  
|**Bytes no accesibles**|En la categoría seleccionada, corresponde a la suma de todo el espacio de direcciones que impide que un proceso lo utilice. Si se intentan realizar operaciones de escritura o lectura, se genera una infracción de acceso.|  
|**Bytes de solo lectura**|En la categoría seleccionada, corresponde a la suma de todo el espacio de direcciones que se puede ejecutar y leer.|  
|**Bytes de lectura y escritura**|En la categoría seleccionada, corresponde a la suma de todo el espacio de direcciones que permite realizar operaciones de lectura y escritura.|  
|**Bytes de escritura y copia**|En la categoría seleccionada, corresponde a la suma de todo el espacio de direcciones que permite el uso compartido de la memoria para operaciones de lectura, pero no de escritura. Si los procesos leen esta memoria, pueden compartir la misma memoria. Sin embargo, si un proceso de uso compartido quiere tener acceso de lectura y escritura a esta memoria compartida, se realiza una copia de esa memoria para escritura.|
