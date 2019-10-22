---
title: 'IJsDebugFrame:: Evaluate (método) | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.Evaluate
apilocation:
- jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6227b97c1fd5fae32db3e13ef72751726c36b043
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573495"
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate (Método)
Evalúa una expresión en el contexto de este marco de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pExpressionText`  
 de Expresión que se va a evaluar.  
  
 `ppDebugProperty`  
 enuncia Objeto que representa el explorador de propiedades.  
  
 `pError`  
 enuncia Mensaje de error, si se produce un error.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Devuelve lo siguiente: S_OK: la evaluación se realiza correctamente, * ppDebugProperty contiene el resultado de la evaluación. S_FALSE: la evaluación produce un error (o no se admite la operación de evaluación), \*pError contiene el mensaje de error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugFrame (Interfaz)](../../winscript/reference/ijsdebugframe-interface.md)