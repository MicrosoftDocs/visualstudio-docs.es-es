---
title: ISimpleConnectionPoint::DescribeEvents | Microsoft Docs
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
ms.openlocfilehash: 1b5824f945ad25f177fc169b58157377bf53bcce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786424"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Devuelve el identificador DISPID y el nombre para cada evento en un intervalo especificado de eventos.  
  
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
 [in] Índice del primer evento a recuperar.  
  
 `cEvents`  
 [in] Número de eventos para recuperar.  
  
 `prgid`  
 [out] Matriz de valores DISPID de eventos.  
  
 `prgbstr`  
 [out] Matriz de nombres de evento.  
  
 `pcEventsFetched`  
 [out] El número real de eventos capturado.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`S_FALSE`|Se solicitaron más eventos que estaban disponibles. Eventos disponibles se representan con DISPID_NULL y null BSTR.|  
|`E_INVALIDARG`|No se pudo obtener ningún elemento.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el identificador DISPID y el nombre para cada evento en un intervalo especificado de eventos.  
  
## <a name="see-also"></a>Vea también  
 [ISimpleConnectionPoint (Interfaz)](../../winscript/reference/isimpleconnectionpoint-interface.md)