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
ms.openlocfilehash: dccd9210908922951c20378868c33b3389cbed4f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432248"
---
# <a name="idebugstackframesnifferex-interface"></a>IDebugStackFrameSnifferEx (Interfaz)
Proporciona una manera de enumerar los marcos de pila lógicos conocidos por un componente. Motores de script normalmente implementan esta interfaz. El Administrador de depuración de proceso utiliza esta interfaz para buscar todos los marcos de pila asociada con un subproceso determinado.  
  
> [!NOTE]
> Esta interfaz se llama desde dentro del subproceso de interés. La implementación de interfaz debe identificar el subproceso actual y devolver un enumerador correspondiente.  
  
 Además de los métodos heredados de `IDebugStackFrameSniffer`, el `IDebugStackFrameSnifferEx` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Devuelve un enumerador de marcos de pila del subproceso actual.|