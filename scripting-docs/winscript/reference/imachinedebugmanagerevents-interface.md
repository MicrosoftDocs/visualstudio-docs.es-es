---
title: IMachineDebugManagerEvents (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: f9aab3d7abeecd22e830c68f174896df0e7df2da
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344045"
---
# <a name="imachinedebugmanagerevents-interface"></a>IMachineDebugManagerEvents (Interfaz)
Indica los cambios aplicados a la lista de aplicaciones en ejecución que mantiene el administrador de depuración de la máquina. Esta interfaz se puede usar el IDE del depurador para mostrar una lista dinámica de las aplicaciones.  
  
 Además de los métodos heredados de `IUnknown`, el `IMachineDebugManagerEvents` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Controla el evento cuando una aplicación se agrega a la ejecución lista de aplicaciones.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Controla el evento cuando se quita una aplicación de la ejecución lista de aplicaciones.|