---
title: ISimpleConnectionPoint::DescribeEvents | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 42dab9558d46eae0fbb640c60264a79877708321
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734025"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Devuelve el identificador DISPID y el nombre de cada evento en un intervalo especificado de eventos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 [in] Índice del primer evento para recuperar.  
  
 `cEvents`  
 [in] Número de eventos se van a recuperar.  
  
 `prgid`  
 [out] Matriz de valores DISPID de eventos.  
  
 `prgbstr`  
 [out] Matriz de nombres de evento.  
  
 `pcEventsFetched`  
 [out] El número real de eventos capturados.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`S_FALSE`|Se solicitaron más eventos que no estaba disponible. Eventos disponibles se representan con DISPID_NULL y un BSTR null.|  
|`E_INVALIDARG`|No se pudo obtener ningún elemento.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el identificador DISPID y el nombre de cada evento en un intervalo especificado de eventos.  
  
## <a name="see-also"></a>Vea también  
 [ISimpleConnectionPoint (Interfaz)](../../winscript/reference/isimpleconnectionpoint-interface.md)