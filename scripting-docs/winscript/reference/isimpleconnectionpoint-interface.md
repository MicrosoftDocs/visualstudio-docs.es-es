---
title: ISimpleConnectionPoint (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de40f66a9e5721b8dacac634c6fb77982017c155
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733915"
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint (Interfaz)
Proporciona una manera sencilla para describir y enumerar los eventos que se desencadena en un punto de conexión determinado. Esta interfaz también resulta muy sencillo enlazar un `IDispatch` objeto a esos eventos. Esta interfaz está implementada por el Administrador de depurar de proceso (PDM) y utilizada por motores de scripts.  
  
 Esta interfaz está disponible en `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Además de los métodos heredados de `IUnknown`, el `ISimpleConnectionPoint` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Establece una conexión entre el objeto de punto de conexión simple y el receptor del cliente.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Devuelve el identificador DISPID y el nombre de cada evento en un intervalo especificado de eventos.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Devuelve el número de eventos que se exponen en esta interfaz.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Finaliza una conexión de consulta previamente establecida mediante `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty (Interfaz)](../../winscript/reference/idebugproperty-interface.md)