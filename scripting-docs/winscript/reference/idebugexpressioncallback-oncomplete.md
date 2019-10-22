---
title: 'Idebugexpressioncallback (:: alcompletar | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionCallBack.onComplete
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExpressionCallBack::onComplete
ms.assetid: d0b89db3-38e7-44e0-93fe-60205f9149dd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fd142cc7ecbcd984be1943da05fa782260b10f8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576419"
---
# <a name="idebugexpressioncallbackoncomplete"></a>IDebugExpressionCallBack::onComplete
Indica que la evaluación de la expresión ha finalizado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Se llama a este método cuando se completa la evaluación de la expresión. Se puede llamar al método `IDebugExpression::GetResultAsString` desde este controlador de eventos.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz idebugexpressioncallback (](../../winscript/reference/idebugexpressioncallback-interface.md)  
 [IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)