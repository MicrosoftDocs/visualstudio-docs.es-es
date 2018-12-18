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
ms.openlocfilehash: 56d6e63c41db274634b2593989800ea0392b93a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726765"
---
# <a name="idebugstackframesnifferex-interface"></a>IDebugStackFrameSnifferEx (Interfaz)
Proporciona una manera para enumerar los marcos de pila lógica conocidos por un componente. Motores de script normalmente implementan esta interfaz. El Administrador de depuración de proceso utiliza esta interfaz para buscar todos los marcos de pila asociada a un subproceso determinado.  
  
> [!NOTE]
>  Esta interfaz se llama desde el subproceso de interés. Implementación de la interfaz debe identificar el subproceso actual y devuelve un enumerador correspondiente.  
  
 Además de los métodos heredados de `IDebugStackFrameSniffer`, el `IDebugStackFrameSnifferEx` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Devuelve un enumerador de los marcos de pila del subproceso actual.|