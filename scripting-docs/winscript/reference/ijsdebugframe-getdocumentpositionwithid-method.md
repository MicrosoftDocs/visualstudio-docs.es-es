---
title: Getdocumentpositionwithid (método) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithId
apilocation:
- jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c37f31ca6b75ca826dbdab93847a1e70ff054c1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090017"
---
# <a name="ijsdebugframegetdocumentpositionwithid-method"></a>IJsDebugFrame::GetDocumentPositionWithId (Método)
Devuelve la posición actual de este marco de pila dentro del documento de nivel de usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetDocumentPositionWithId(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pDocumentId`  
 [out] Identificador único para un documento de origen (puntero a IDebugDocumentText).  
  
 `pCharacterOffset`  
 [out] El desplazamiento de carácter de base cero desde el principio de la secuencia de comandos.  
  
 `pStatementCharCount`  
 [out] La longitud de la instrucción actual, que comienza por el * pCharacterOffset, en caracteres.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugFrame (Interfaz)](../../winscript/reference/ijsdebugframe-interface.md)