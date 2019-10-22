---
title: Ficha general, cuadro de diálogo Propiedades de proceso | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6116beb67baf072d9c9762a1e8c67408cc915f29
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62849820"
---
# <a name="general-tab-process-properties-dialog-box"></a>Pestaña General (Cuadro de diálogo Propiedades del proceso)
Use la **General** tab para obtener más información acerca de un proceso específico. Para mostrar el [cuadro de diálogo de propiedades de proceso](../debugger/process-properties-dialog-box.md), mover el foco a un [vista procesos](../debugger/processes-view.md) ventana. Seleccione cualquier nodo de proceso en el árbol y luego elija **propiedades** desde el **vista** menú.

 Las siguientes opciones están disponibles en el **General** pestaña:

|Entrada|Descripción|
|-----------|-----------------|
|**Nombre del módulo**|El nombre del módulo.|
|**Identificador del proceso**|El identificador único de este proceso. Números de Id. de proceso se reutilizan, por lo que identifican a un proceso sólo durante la vigencia de ese proceso. El tipo de objeto de proceso se crea cuando se ejecuta un programa. Todos los subprocesos en un proceso de compartan el mismo espacio de direcciones y tengan acceso a los mismos datos.|
|**Base de prioridad**|Prioridad base actual de este proceso. Los subprocesos de un proceso pueden aumentar y disminuir su propia prioridad base con respecto a la prioridad del proceso base.|
|**Subprocesos**|El número de subprocesos activos actualmente en este proceso.|
|**Tiempo de CPU**|Tiempo total de CPU empleado en este proceso y sus subprocesos. Igual al tiempo de usuario más tiempo privilegiado.|
|**Tiempo de usuario**|El tiempo transcurrido acumulado que los subprocesos de este proceso han dedicado a ejecutar código en modo de usuario en subprocesos no inactivos. Las aplicaciones se ejecutan en modo de usuario, como hacen los subsistemas, como el Administrador de ventanas y el motor de gráficos.|
|**Tiempo con privilegios**|El tiempo total transcurrido este proceso ha estado ejecutándose en modo privilegiado en subprocesos no inactivos. La capa de servicio, las rutinas ejecutivas y el núcleo de ejecutan en modo privilegiado. Controladores de dispositivos para la mayoría de los dispositivos que no sean impresoras y adaptadores de gráficos también se ejecutan en modo privilegiado. Algún trabajo que hace Windows para la aplicación puede aparecer en otros procesos del subsistema además de tiempo privilegiado.|
|**Tiempo transcurrido**|El tiempo transcurrido total que se ha estado ejecutando este proceso.|