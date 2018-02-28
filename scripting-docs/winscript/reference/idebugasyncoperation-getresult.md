---
title: IDebugAsyncOperation::GetResult | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugAsyncOperation.GetResult
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60181904408010f35fa4d99d182216e665583aab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Proporciona el valor devuelto y el parámetro de objeto de valor devuelto de la operación sincrónica de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `phrResult`  
 [out] Si la operación se completa, `phrResult` es el valor devuelto de `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 [out] Si la operación se completa, `ppunkResult` es el parámetro del objeto devuelto por la operación.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_PENDING`|No se complete la operación.|  
  
## <a name="remarks"></a>Comentarios  
 Si ha completado la operación, este método devuelve el `HRESULT` y objeto de parámetro de `IDebugSyncOperation::Execute`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugAsyncOperation (interfaz)](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)