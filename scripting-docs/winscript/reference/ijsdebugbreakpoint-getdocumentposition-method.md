---
title: 'Ijsdebugbreakpoint:: Getdocumentposition (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.GetDocumentPosition
apilocation:
- jscript9diag.dll
ms.assetid: 886df8ba-a59a-48a7-87f2-3b669e71528f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c33751b0173626814f042fdc54a7d496b644573
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727615"
---
# <a name="ijsdebugbreakpointgetdocumentposition-method"></a>IJsDebugBreakPoint::GetDocumentPosition (Método)
Devuelve la posición de la instrucción donde se enlazó el punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetDocumentPosition(  
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
 [IJsDebugBreakPoint (Interfaz)](../../winscript/reference/ijsdebugbreakpoint-interface.md)