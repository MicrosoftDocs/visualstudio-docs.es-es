---
title: IDebugExpression::GetResultAsString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84255e364630245564a0cbab5d38c6dff38df0a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978477"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
Devuelve el resultado de la evaluación de expresión como una cadena y el valor devuelto de la operación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `phrResult`  
 [out] Valor devuelto de la operación.  
  
 `pbstrResult`  
 [out] El resultado de la evaluación de expresiones.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_PENDING`|La operación todavía está pendiente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el resultado de la evaluación de expresión como una cadena y la operación `HRESULT`.  
  
 Este método devuelve `S_OK` y `phrResult` devuelve `E_ABORT` si `Abort` anula la operación.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExpression (Interfaz)](../../winscript/reference/idebugexpression-interface.md)