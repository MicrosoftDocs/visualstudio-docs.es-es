---
title: IDebugStackFrameSniffer (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41fff384bc9075d94fcfa84d94350fec72ebc64a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348885"
---
# <a name="idebugstackframesniffer-interface"></a>IDebugStackFrameSniffer (Interfaz)
Proporciona una manera de enumerar los marcos de pila lógicos conocidos por un componente. Motores de script normalmente implementan esta interfaz. El Administrador de depuración de proceso utiliza esta interfaz para buscar todos los marcos de pila asociada con un subproceso determinado.  
  
> [!NOTE]
>  El depurador llama a esta interfaz desde dentro del subproceso de interés. El motor de scripts debe identificar el subproceso actual y devolver un enumerador correspondiente.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos heredados de `IUnknown`, el `IDebugStackFrameSniffer` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Devuelve un enumerador de marcos de pila del subproceso actual.|