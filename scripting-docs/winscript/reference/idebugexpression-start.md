---
title: IDebugExpression::Start | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExpression.Start
apilocation: jscript.dll
helpviewer_keywords: IDebugExpression::Start
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14d293649e3a6a87c7f594e244378dc2a7e15ac6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
Comienza la evaluación de la expresión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdecb`  
 [in] Devolución de llamada para que indica cuándo se completa la evaluación de expresiones. Si este parámetro es `NULL`, se desencadena ningún evento y el cliente debe sondear el estado de la expresión utilizando `QueryIsComplete`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método comienza la evaluación de la expresión.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)   
 [IDebugExpression (Interfaz)](../../winscript/reference/idebugexpression-interface.md)