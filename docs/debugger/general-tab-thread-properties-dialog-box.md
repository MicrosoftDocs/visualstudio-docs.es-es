---
title: "Ficha general, cuadro de diálogo de propiedades de subproceso | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d8d53c373c58e31f2a2719df8afa6dd0da9cd3c6
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2018
---
# <a name="general-tab-thread-properties-dialog-box"></a>Pestaña General (Cuadro de diálogo Propiedades del subproceso)
Utilice este cuadro de diálogo para obtener más información acerca de un subproceso concreto. Para mostrar este cuadro de diálogo, mueva el foco a un [vista de subprocesos](../debugger/threads-view.md) ventana o abra [vista mensajes](../debugger/messages-view.md) y expanda un mensaje. Seleccione cualquier nodo de subproceso en el árbol y después elija **propiedades** desde el **vista** menú.  
  
 El **propiedades del subproceso** cuadro de diálogo contiene un panel, el **General** ficha. Las siguientes opciones están disponibles:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Nombre del módulo**|El nombre del módulo.|  
|**Identificador de subproceso**|El identificador único de este subproceso. Tenga en cuenta que los números de Id. de subproceso se reutilizan; un subproceso que identifican solo durante la duración del subproceso.|  
|**Identificador del proceso**|El identificador único de este proceso. Números de Id. de proceso se reutilizan, por lo que identifican un proceso sólo durante la vigencia de este proceso. El tipo de objeto de proceso se crea cuando se ejecuta un programa. Todos los subprocesos de un proceso comparten el mismo espacio de direcciones y tengan acceso a los mismos datos. Elija este valor para ver las propiedades del identificador del proceso.|  
|**Estado de subprocesos.**|El estado actual del subproceso. Un subproceso de ejecución está usando un procesador; un subproceso en espera está a punto de utilizar uno. Un subproceso de la lista está esperando para usar un procesador porque no hay ninguno libre. Un subproceso en transición está esperando un recurso para su ejecución, como la espera de la pila de ejecución de la paginación del disco. Un subproceso en espera no necesita el procesador porque está esperando que se complete una operación periférica o hasta que esté disponible un recurso.|  
|**Motivo de espera**|Esto solo es aplicable cuando el subproceso está en el estado de espera. Los pares de eventos se usan para comunicarse con subsistemas protegidos.|  
|**Tiempo de CPU**|Tiempo de CPU total empleado en este proceso y sus subprocesos. Es igual al tiempo de usuario + tiempo con privilegios.|  
|**Tiempo de usuario**|El tiempo total que este subproceso invirtió en ejecutar código en modo de usuario. Las aplicaciones se ejecutan en modo de usuario, como sucede con subsistemas como el Administrador de ventanas y el motor de gráficos.|  
|**Tiempo privilegiado**|El tiempo total que este subproceso invirtió en ejecutar código en modo privilegiado. Cuando se llama a un servicio de sistema de Windows, el servicio a menudo se ejecutará en modo privilegiado para obtener acceso a los datos privados del sistema. Estos datos están protegidos contra el acceso por subprocesos que se ejecutan en modo de usuario. Las llamadas al sistema pueden ser explícitas o implícitas, como cuando se produce un error de página o una interrupción.|  
|**Tiempo transcurrido**|El tiempo total transcurrido (en segundos) que se ha estado ejecutando este subproceso.|  
|**Prioridad actual**|La prioridad dinámica actual de este subproceso. Subprocesos dentro de un proceso pueden aumentar y disminuir su propia prioridad base con respecto a la prioridad base del proceso.|  
|**Prioridad base**|La prioridad base actual de este subproceso.|  
|**Dirección de inicio**|Dirección virtual inicial para este subproceso.|  
|**PC de usuario**|El contador de programa del usuario para el subproceso.|  
|**Cambios de contexto**|El número de cambios de un subproceso a otro. Modificadores de subproceso pueden producirse dentro de un único proceso o entre procesos. Un cambio de subproceso puede deberse porque un subproceso solicita otra para obtener información, o por un subproceso que se ve relegado cuando esté listo para ejecutar un subproceso de prioridad más alto.|