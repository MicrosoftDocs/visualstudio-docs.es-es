---
title: 'Idebugexpression (:: Start | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Start
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Start
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c8c3666adfc83f3ad60b942cd3f7fe9eedfccba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576432"
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
Comienza la evaluación de la expresión.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdecb`  
 de Devolución de llamada para indicar cuándo se completa la evaluación de la expresión. Si este parámetro se `NULL`, no se desencadena ningún evento y el cliente debe sondear el estado de la expresión mediante `QueryIsComplete`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método inicia la evaluación de la expresión.  
  
## <a name="see-also"></a>Vea también  
 [Idebugexpression (:: Abort](../../winscript/reference/idebugexpression-abort.md)    
 [IDebugExpression (Interfaz)](../../winscript/reference/idebugexpression-interface.md)