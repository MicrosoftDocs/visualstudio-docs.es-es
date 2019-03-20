---
title: ISimpleConnectionPoint::Unadvise | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Unadvise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Unadvise
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 189c07c10e93df9a61218b6a94a0b317999676d2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154665"
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
Finaliza una conexión de consulta previamente establecida mediante `ISimpleConnectionPoint::Advise`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwCookie`  
 [in] Símbolo (token) de la conexión finaliza, tal como lo devuelve `ISimpleConnectionPoint::Advise`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Cuando se termina una conexión de consulta, el punto de conexión llamadas la `Release` método en el puntero que se ha guardado para la conexión durante el `ISimpleConnectionPoint::Advise` método. Esa llamada invierte la `AddRef` que se realizó durante la `ISimpleConnectionPoint::Advise` cuando el punto de conexión llama el receptor de consulta `QueryInterface`.  
  
## <a name="see-also"></a>Vea también  
 [ISimpleConnectionPoint (Interfaz)](../../winscript/reference/isimpleconnectionpoint-interface.md)