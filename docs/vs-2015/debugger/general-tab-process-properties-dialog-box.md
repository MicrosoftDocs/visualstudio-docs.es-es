---
title: Ficha general, cuadro de diálogo Propiedades de proceso | Documentos de Microsoft
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
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1acc3826521ca6bd15b60563f9bd5e99ba70988e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282079"
---
# <a name="general-tab-process-properties-dialog-box"></a>Pestaña General (Cuadro de diálogo Propiedades del proceso)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use la **General** tab para obtener más información acerca de un proceso específico. Para mostrar el [cuadro de diálogo de propiedades de proceso](../debugger/process-properties-dialog-box.md), mover el foco a un [vista procesos](../debugger/processes-view.md) ventana. Seleccione cualquier nodo de proceso en el árbol y luego elija **propiedades** desde el **vista** menú.  
  
 Las siguientes opciones están disponibles en el **General** pestaña:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Nombre del módulo**|El nombre del módulo.|  
|**Identificador del proceso**|El identificador único de este proceso. Números de Id. de proceso se reutilizan, por lo que identifican a un proceso sólo durante la vigencia de ese proceso. El tipo de objeto de proceso se crea cuando se ejecuta un programa. Todos los subprocesos en un proceso de compartan el mismo espacio de direcciones y tengan acceso a los mismos datos.|  
|**Prioridad Base**|Prioridad base actual de este proceso. Los subprocesos de un proceso pueden aumentar y disminuir su propia prioridad base con respecto a la prioridad del proceso base.|  
|**Subprocesos**|El número de subprocesos activos actualmente en este proceso.|  
|**Tiempo de CPU**|Tiempo total de CPU empleado en este proceso y sus subprocesos. Igual al tiempo de usuario más tiempo privilegiado.|  
|**Tiempo de usuario**|El tiempo transcurrido acumulado que los subprocesos de este proceso han dedicado a ejecutar código en modo de usuario en subprocesos no inactivos. Las aplicaciones se ejecutan en modo de usuario, como hacen los subsistemas, como el Administrador de ventanas y el motor de gráficos.|  
|**Tiempo privilegiado**|El tiempo total transcurrido este proceso ha estado ejecutándose en modo privilegiado en subprocesos no inactivos. La capa de servicio, las rutinas ejecutivas y el núcleo de ejecutan en modo privilegiado. Controladores de dispositivos para la mayoría de los dispositivos que no sean impresoras y adaptadores de gráficos también se ejecutan en modo privilegiado. Algún trabajo que hace Windows para la aplicación puede aparecer en otros procesos del subsistema además de tiempo privilegiado.|  
|**Tiempo transcurrido**|El tiempo transcurrido total que se ha estado ejecutando este proceso.|



