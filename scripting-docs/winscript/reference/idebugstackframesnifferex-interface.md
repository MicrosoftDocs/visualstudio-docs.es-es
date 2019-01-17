---
title: IDebugStackFrameSnifferEx (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 76f10d6bbb34c61e87a1be0f61dcd7db168274e7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348495"
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