---
title: Ficha general, cuadro de diálogo de propiedades de subproceso | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e8604c2d31f6bb50e9e77efbf6423f56ed719c0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714821"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Pestaña General (Cuadro de diálogo Propiedades del subproceso)
Utilice este cuadro de diálogo para obtener más información acerca de un subproceso concreto. Para mostrar este cuadro de diálogo, mueva el foco a un [vista de subprocesos](../debugger/threads-view.md) ventana, o bien abra [vista mensajes](../debugger/messages-view.md) y expanda un mensaje. Seleccione cualquier nodo de subproceso en el árbol y luego elija **propiedades** desde el **vista** menú.

 El **Thread Properties** cuadro de diálogo contiene un panel, el **General** ficha. Las siguientes opciones están disponibles:

|Entrada|Descripción|
|-----------|-----------------|
|**Nombre del módulo**|El nombre del módulo.|
|**Identificador de subproceso**|El identificador único de este subproceso. Tenga en cuenta que los números de Id. de subproceso se reutilizan; identifican un subproceso sólo durante la vigencia de ese subproceso.|
|**Identificador del proceso**|El identificador único de este proceso. Números de Id. de proceso se reutilizan, por lo que identifican a un proceso sólo durante la vigencia de ese proceso. El tipo de objeto de proceso se crea cuando se ejecuta un programa. Todos los subprocesos en un proceso de compartan el mismo espacio de direcciones y tengan acceso a los mismos datos. Elija este valor para ver las propiedades del identificador del proceso.|
|**Estado del subproceso**|El estado actual del subproceso. Un subproceso de ejecución está usando un procesador; un subproceso en espera está a punto de usar uno. Un subproceso listo está esperando para usar un procesador porque no hay ninguno libre. Un subproceso en transición está esperando un recurso para ejecutarse, por ejemplo, esperando su pila de ejecución se pagine desde el disco. Un subproceso en espera no es necesario el procesador porque está esperando una operación periférica o que esté disponible un recurso.|
|**Motivo de espera**|Esto solo es aplicable cuando el subproceso está en estado de espera. Pares de eventos se usan para comunicarse con subsistemas protegidos.|
|**Tiempo de CPU**|Tiempo total de CPU empleado en este proceso y sus subprocesos. Es igual al tiempo de usuario + tiempo con privilegios.|
|**Tiempo de usuario**|El tiempo transcurrido total que este subproceso ha estado ejecutando código en modo de usuario. Las aplicaciones se ejecutan en modo de usuario, como los subsistemas como el Administrador de ventanas y el motor de gráficos.|
|**Tiempo con privilegios**|El tiempo transcurrido total que este subproceso ha estado ejecutando código en modo privilegiado. Cuando se llama a un servicio de sistema de Windows, el servicio a menudo se ejecutará en modo privilegiado para obtener acceso a datos privados del sistema. Dichos datos están protegidos frente al acceso por subprocesos que se ejecutan en modo de usuario. Las llamadas al sistema pueden ser explícitas o implícitas, como cuando se produce un error de página o una interrupción.|
|**Tiempo transcurrido**|El tiempo total transcurrido (en segundos) ha sido ejecutando este subproceso.|
|**Prioridad actual**|La prioridad dinámica actual de este subproceso. Los subprocesos de un proceso pueden aumentar y disminuir su propia prioridad base con respecto a la prioridad base del proceso.|
|**Prioridad base**|Prioridad base actual de este subproceso.|
|**Dirección de inicio**|Dirección virtual inicial para este subproceso.|
|**PC de usuario**|El contador de programas del usuario para el subproceso.|
|**Cambios de contexto**|El número de cambios de un subproceso a otro. Conmutadores de subprocesos pueden aparecer dentro de un único proceso o entre procesos. Un cambio de subproceso puede deberse a otro pide información de un subproceso o por un subproceso se ha pospuesto cuando esté listo para ejecutar un subproceso con mayor prioridad.|