---
title: Pestaña General, cuadro de diálogo Propiedades del subproceso | Microsoft Docs
description: Vea el cuadro de diálogo Propiedades del subproceso para obtener información sobre un subproceso, incluido el nombre del módulo, el identificador del subproceso, el identificador del proceso, el estado del subproceso, el motivo de la espera y el tiempo de CPU.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 02ba7d14dad8e4755170ffca7853aa9cc6c85a19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870550"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Pestaña General (Cuadro de diálogo Propiedades del subproceso)
Use este cuadro de diálogo para saber más sobre un subproceso específico. Para mostrar este cuadro de diálogo, mueva el foco a una ventana [Vista de subprocesos](../debugger/threads-view.md) o abra [Vista de mensajes](../debugger/messages-view.md) y expanda un mensaje. Seleccione cualquier nodo de subproceso en el árbol y, después, elija **Propiedades** en el menú **Vista**.

 El cuadro de diálogo **Propiedades del subproceso** contiene un panel, la pestaña **General**. Las siguientes configuraciones están disponibles:

|Entrada|Descripción|
|-----------|-----------------|
|**Nombre del módulo**|El nombre del módulo.|
|**Identificador de subproceso**|Identificador único de este subproceso. Tenga en cuenta que se reutilizan los números de identificador de subproceso; estos identifican un subproceso solo mientras dure este.|
|**Identificador del proceso**|Identificador único de este proceso. Los números de identificador de proceso se reutilizan, por lo que identifican un proceso solo mientras dura dicho proceso. Cuando se ejecuta un programa, se crea el tipo de objeto Proceso. Todos los subprocesos de un proceso comparten el mismo espacio de direcciones y tienen acceso a los mismos datos. Elija este valor para ver las propiedades del identificador de proceso.|
|**Estado del subproceso**|Estado actual del subproceso. Un subproceso en ejecución está utilizando un procesador; un subproceso en espera está a punto de usar uno. Un subproceso listo está esperando para usar un procesador porque no hay ninguno disponible. Un subproceso en transición está esperando a que se ejecute un recurso, como esperar a que su pila de ejecución se pagine en el disco. Un subproceso en espera no necesita el procesador porque está esperando a que se complete una operación periférica o a que se libere un recurso.|
|**Motivo de espera**|Esto solo es aplicable cuando el subproceso está en estado de espera. Se usan pares de eventos para comunicarse con subsistemas protegidos.|
|**Tiempo de CPU**|Tiempo total de CPU empleado en este proceso y sus subprocesos. Igual al tiempo de usuario + tiempo con privilegios.|
|**Tiempo de usuario**|El tiempo total transcurrido que este subproceso ha empleado en ejecutar código en modo de usuario. Las aplicaciones se ejecutan en modo de usuario, igual que los subsistemas, como el administrador de ventanas y el motor de gráficos.|
|**Tiempo con privilegios**|El tiempo total transcurrido que este subproceso ha empleado en ejecutar código en modo con privilegios. Cuando se llama a un servicio del sistema Windows, el servicio a menudo se ejecuta en modo con privilegios para obtener acceso a los datos privados del sistema. Estos datos se protegen del acceso mediante subprocesos que se ejecutan en modo de usuario. Las llamadas al sistema pueden ser explícitas o implícitas, como cuando se produce un error de página o una interrupción.|
|**Tiempo transcurrido**|El tiempo total transcurrido (en segundos) que se ha estado ejecutando este subproceso.|
|**Prioridad actual**|Prioridad dinámica actual de este subproceso. Los subprocesos de un proceso pueden aumentar y reducir su propia prioridad base en relación con la prioridad base del proceso.|
|**Prioridad base**|Prioridad base actual de este subproceso.|
|**Dirección de inicio**|Dirección virtual de inicio para este subproceso.|
|**PC de usuario**|Contador de programa del usuario del subproceso.|
|**Cambios de contexto**|Número de modificadores de un subproceso a otro. Los modificadores de subprocesos pueden producirse dentro de un único proceso o entre procesos. Un cambio de subproceso puede deberse a un subproceso que solicita a otro información o a que un subproceso se adelantó cuando un subproceso de prioridad más alta estaba listo para ejecutarse.|