---
title: IMachineDebugManagerEvents (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerEvents interface
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 369dc8d182efe7bf9697454d0e4b1c9c1a10c027
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagerevents-interface"></a>IMachineDebugManagerEvents (Interfaz)
Indica los cambios en el que se ejecuta mantenida por el Administrador de depuración de la máquina de lista de aplicaciones. Esta interfaz se puede utilizar el depurador IDE para mostrar una lista dinámica de las aplicaciones.  
  
 Además de los métodos heredados de `IUnknown`, el `IMachineDebugManagerEvents` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Controla el evento cuando se agrega una aplicación para el que se ejecuta lista de aplicaciones.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Controla el evento cuando se quita una aplicación desde el que se ejecuta lista de aplicaciones.|