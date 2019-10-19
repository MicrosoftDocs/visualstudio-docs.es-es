---
title: Isimpleconnectionpoint (::D escribeEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5000689d588fe3f63ec5408893187bba8d13d63
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571821"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Devuelve el DISPID y el nombre de cada evento de un intervalo de eventos especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `iEvent`  
 de Índice del primer evento que se va a recuperar.  
  
 `cEvents`  
 de Número de eventos que se van a recuperar.  
  
 `prgid`  
 enuncia Matriz de valores de DISPID de evento.  
  
 `prgbstr`  
 enuncia Matriz de nombres de evento.  
  
 `pcEventsFetched`  
 enuncia Número real de eventos capturados.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`S_FALSE`|Se solicitaron más eventos de los que estaban disponibles. Los eventos no disponibles se representan con DISPID_NULL y un BSTR nulo.|  
|`E_INVALIDARG`|No se pudo capturar ningún elemento.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el DISPID y el nombre de cada evento de un intervalo de eventos especificado.  
  
## <a name="see-also"></a>Vea también  
 [ISimpleConnectionPoint (Interfaz)](../../winscript/reference/isimpleconnectionpoint-interface.md)