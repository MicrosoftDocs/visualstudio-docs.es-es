---
title: Método Ijsdebugframe | Microsoft Docs
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
ms.openlocfilehash: b328d6071ae9dc96b8e7f62bad6d4417aa1730f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558195"
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
 [in] Para evaluar la expresión.  
  
 `ppDebugProperty`  
 [out] Objeto que representa el Explorador de propiedades.  
  
 `pError`  
 [out] El mensaje de error, si se produce un error.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Devuelve lo siguiente: S_OK: Evaluación es correcta, * ppDebugProperty contiene el resultado de la evaluación. S_FALSE: La evaluación produce un error (o no se admite la operación de evaluación), \*pError contiene el mensaje de error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugFrame (Interfaz)](../../winscript/reference/ijsdebugframe-interface.md)