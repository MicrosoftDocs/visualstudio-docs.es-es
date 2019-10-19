---
title: 'Idebugasyncoperation (:: GetResult | Microsoft Docs'
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
ms.openlocfilehash: 55c51649a5bc3094dd306166e013a892ce67e236
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573284"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Proporciona el valor devuelto y el parámetro de objeto devuelto de la operación de depuración sincrónica.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `phrResult`  
 enuncia Si la operación se ha completado, `phrResult` es el valor devuelto de `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 enuncia Si la operación ha finalizado, `ppunkResult` es el parámetro de objeto devuelto por la operación.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_PENDING`|La operación no ha finalizado.|  
  
## <a name="remarks"></a>Comentarios  
 Si se ha completado la operación, este método devuelve el `HRESULT` y el parámetro de objeto de `IDebugSyncOperation::Execute`.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz idebugasyncoperation (](../../winscript/reference/idebugasyncoperation-interface.md)  
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)