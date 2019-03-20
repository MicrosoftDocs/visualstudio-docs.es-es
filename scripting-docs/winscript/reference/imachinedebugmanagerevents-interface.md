---
title: IMachineDebugManagerEvents (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerEvents interface
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fcfcc2aed0fedefdc149b83e911d33cd3b54cdef
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153128"
---
# <a name="imachinedebugmanagerevents-interface"></a>IMachineDebugManagerEvents (Interfaz)
Indica los cambios aplicados a la lista de aplicaciones en ejecución que mantiene el administrador de depuración de la máquina. Esta interfaz se puede usar el IDE del depurador para mostrar una lista dinámica de las aplicaciones.  
  
 Además de los métodos heredados de `IUnknown`, el `IMachineDebugManagerEvents` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Controla el evento cuando una aplicación se agrega a la ejecución lista de aplicaciones.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Controla el evento cuando se quita una aplicación de la ejecución lista de aplicaciones.|