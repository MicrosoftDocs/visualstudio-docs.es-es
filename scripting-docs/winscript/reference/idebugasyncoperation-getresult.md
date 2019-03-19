---
title: IDebugAsyncOperation::GetResult | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.GetResult
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49cf761c85fce3f8fc2f6705d114ab042e0c2ecd
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158005"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Proporciona el valor devuelto y el parámetro de objeto de valor devuelto de la operación de depuración sincrónica.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `phrResult`  
 [out] Si la operación se ha completado, `phrResult` es el valor devuelto de `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 [out] Si la operación se ha completado, `ppunkResult` es el parámetro de objeto devuelto por la operación.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_PENDING`|No se completó la operación.|  
  
## <a name="remarks"></a>Comentarios  
 Si se ha completado la operación, este método devuelve el `HRESULT` y objeto de parámetro de `IDebugSyncOperation::Execute`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugAsyncOperation (interfaz)](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)