---
title: Ficha general, cuadro de diálogo Propiedades de procesar | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51e55ef780fc76c41f7122cd2970c1e36268c872
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="general-tab-process-properties-dialog-box"></a>Pestaña General (Cuadro de diálogo Propiedades del proceso)
Use la **General** tab para obtener más información acerca de un proceso específico. Para mostrar la [cuadro de diálogo de propiedades de proceso](../debugger/process-properties-dialog-box.md), mover el foco a un [vista procesos](../debugger/processes-view.md) ventana. Seleccione cualquier nodo de proceso en el árbol y después elija **propiedades** desde el **vista** menú.  
  
 Las siguientes opciones están disponibles en la **General** ficha:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Nombre del módulo**|El nombre del módulo.|  
|**Identificador del proceso**|El identificador único de este proceso. Números de Id. de proceso se reutilizan, por lo que identifican un proceso sólo durante la vigencia de este proceso. El tipo de objeto de proceso se crea cuando se ejecuta un programa. Todos los subprocesos de un proceso comparten el mismo espacio de direcciones y tengan acceso a los mismos datos.|  
|**Prioridad Base**|La prioridad base actual de este proceso. Subprocesos dentro de un proceso pueden aumentar y disminuir su propia prioridad base con respecto a la prioridad base del proceso.|  
|**Subprocesos**|El número de subprocesos activos actualmente en este proceso.|  
|**Tiempo de CPU**|Tiempo de CPU total empleado en este proceso y sus subprocesos. Es igual a tiempo de usuario más tiempo con privilegios.|  
|**Tiempo de usuario**|El tiempo transcurrido acumulado que los subprocesos de este proceso han invertido en ejecutar código en modo de usuario en subprocesos no inactivos. Las aplicaciones se ejecutan en modo de usuario, como sucede con subsistemas como el Administrador de ventanas y el motor de gráficos.|  
|**Tiempo privilegiado**|El tiempo total transcurrido este proceso ha estado ejecutándose en modo privilegiado en subprocesos no inactivos. El nivel de servicio, las rutinas de ejecutivo y el Kernel se ejecutan en modo privilegiado. Controladores de dispositivo para la mayoría de los dispositivos que no sean adaptadores de gráficos y las impresoras también se ejecutan en modo privilegiado. Algún trabajo encargada de Windows para la aplicación puede aparecer en otros procesos del subsistema además de tiempo privilegiado.|  
|**Tiempo transcurrido**|El tiempo total de transcurrido que este proceso ha estado ejecutándose.|