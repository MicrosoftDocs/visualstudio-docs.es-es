---
title: 'Idebugexpression (:: GetResultAsDebugProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsDebugProperty
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsDebugProperty
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 104c42f02d02be386711e687f02d333425834948
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575926"
---
# <a name="idebugexpressiongetresultasdebugproperty"></a>IDebugExpression::GetResultAsDebugProperty
Devuelve el resultado de la evaluación de la expresión como una propiedad de depuración y el valor devuelto de la operación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `phrResult`  
 enuncia El valor devuelto de la operación.  
  
 `ppdp`  
 enuncia Propiedad Debug de la expresión.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_PENDING`|La operación todavía está pendiente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el resultado de la evaluación de la expresión como un `IDebugProperty` y el `HRESULT` de la operación.  
  
 Este método devuelve `S_OK` y `phrResult` devuelve `E_ABORT` si `Abort` anula la operación.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz idebugexpression (](../../winscript/reference/idebugexpression-interface.md)  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)