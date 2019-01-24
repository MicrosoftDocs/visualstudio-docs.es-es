---
title: Método Ijsdebugframe | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 574af7823add67a00fc8add922b5e352fa1b369c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091928"
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