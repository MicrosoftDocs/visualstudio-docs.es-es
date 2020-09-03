---
title: General (Pestaña), Propiedades del proceso (Cuadro de diálogo) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9256ca4141e9e4ec9e5ae218f1e5a11bf2fa5362
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182291"
---
# <a name="general-tab-process-properties-dialog-box"></a>Pestaña General (Cuadro de diálogo Propiedades del proceso)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use la pestaña **General** para obtener más información sobre un proceso determinado. Para mostrar el [Cuadro de diálogo Propiedades del proceso](../debugger/process-properties-dialog-box.md), mueva el foco a una ventana de la [Vista Procesos](../debugger/processes-view.md). Seleccione cualquier nodo de proceso del árbol y luego **Propiedades** en el menú **Vista**.  
  
 En la pestaña **General** están disponibles los valores siguientes:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Nombre del módulo**|El nombre del módulo.|  
|**Identificador del proceso**|Identificador único de este proceso. Los números de identificador de proceso se reutilizan, por lo que identifican un proceso solo mientras dura dicho proceso. Cuando se ejecuta un programa, se crea el tipo de objeto Proceso. Todos los subprocesos de un proceso comparten el mismo espacio de direcciones y tienen acceso a los mismos datos.|  
|**Base de prioridad**|Prioridad base actual de este proceso. Los subprocesos de un proceso pueden aumentar y reducir su propia prioridad base con respecto a la prioridad base del proceso.|  
|**Subprocesos**|Número de subprocesos activos actualmente en este proceso.|  
|**Tiempo de CPU**|Tiempo total de CPU dedicado a este proceso y sus subprocesos. Es igual al Tiempo de usuario más el Tiempo con privilegios.|  
|**Tiempo de usuario**|Tiempo transcurrido total que los subprocesos de este proceso han dedicado a ejecutar código en modo usuario en subprocesos no inactivos. Las aplicaciones se ejecutan en modo usuario, lo mismo que subsistemas como el administrador de ventanas y el motor de gráficos.|  
|**Tiempo con privilegios**|Tiempo transcurrido total que este proceso ha estado en ejecución en modo con privilegios en subprocesos no inactivos. La capa de servicio, las rutinas ejecutivas y el kernel se ejecutan en modo con privilegios. Los controladores de dispositivo de la mayoría de los dispositivos distintos a los adaptadores de gráficos e impresoras también se ejecutan en modo con privilegios. Algún trabajo que Windows realiza para la aplicación puede aparecer en otros procesos del subsistema, además de en Tiempo con privilegios.|  
|**Tiempo transcurrido**|Tiempo transcurrido total que este proceso ha estado ejecutándose.|
