---
title: IDebugStackFrameSnifferEx (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSnifferEx interface
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc6e892c00a2d86e784857f08772550897e1ec4e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157191"
---
# <a name="idebugstackframesnifferex-interface"></a>IDebugStackFrameSnifferEx (Interfaz)
Proporciona una manera de enumerar los marcos de pila lógicos conocidos por un componente. Motores de script normalmente implementan esta interfaz. El Administrador de depuración de proceso utiliza esta interfaz para buscar todos los marcos de pila asociada con un subproceso determinado.  
  
> [!NOTE]
>  Esta interfaz se llama desde dentro del subproceso de interés. La implementación de interfaz debe identificar el subproceso actual y devolver un enumerador correspondiente.  
  
 Además de los métodos heredados de `IDebugStackFrameSniffer`, el `IDebugStackFrameSnifferEx` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Devuelve un enumerador de marcos de pila del subproceso actual.|