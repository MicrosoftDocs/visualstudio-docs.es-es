---
title: ISimpleConnectionPoint::DescribeEvents | Microsoft Docs
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
ms.openlocfilehash: 43a20a2d9580c80bc6aea5d22c6a0713f4843634
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088509"
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