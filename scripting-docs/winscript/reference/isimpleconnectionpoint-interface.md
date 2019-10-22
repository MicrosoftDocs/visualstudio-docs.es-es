---
title: Interfaz Isimpleconnectionpoint (| Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 549d7f38b01937f992b240cb6f1d651bc848236c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571787"
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint (Interfaz)
Proporciona una manera sencilla de describir y enumerar los eventos desencadenados en un punto de conexión determinado. Esta interfaz también facilita el enlace de un objeto `IDispatch` a esos eventos. El administrador de depuración de proceso (PDM) implementa esta interfaz y la utilizan los motores de scripts.  
  
 Esta interfaz está disponible en `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz de `ISimpleConnectionPoint` expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Establece una conexión entre el objeto de punto de conexión simple y el receptor del cliente.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Devuelve el DISPID y el nombre de cada evento de un intervalo de eventos especificado.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Devuelve el número de eventos expuestos en esta interfaz.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Finaliza una conexión de consulta previamente establecida a través de `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty (Interfaz)](../../winscript/reference/idebugproperty-interface.md)