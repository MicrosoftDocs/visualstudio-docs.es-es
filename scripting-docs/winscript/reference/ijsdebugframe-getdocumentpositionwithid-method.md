---
title: 'Ijsdebugframe:: Getdocumentpositionwithid (método) | Documentos de Microsoft'
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
ms.openlocfilehash: f11e9ad51094522adec99ef82681f42ac500a251
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727735"
---
# <a name="ijsdebugframegetdocumentpositionwithid-method"></a>IJsDebugFrame::GetDocumentPositionWithId (Método)
Devuelve la posición actual de este marco de pila dentro del documento de nivel de usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetDocumentPositionWithId(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pDocumentId`  
 [out] Identificador único para un documento de origen (puntero a la IDebugDocumentText).  
  
 `pCharacterOffset`  
 [out] El desplazamiento de carácter de base cero desde el principio de la secuencia de comandos.  
  
 `pStatementCharCount`  
 [out] La longitud de la instrucción actual, que comienza en * pCharacterOffset, en caracteres.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugFrame (Interfaz)](../../winscript/reference/ijsdebugframe-interface.md)