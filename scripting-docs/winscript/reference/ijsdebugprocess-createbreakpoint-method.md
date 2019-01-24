---
title: Método Ijsdebugprocess | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateBreakPoint
apilocation:
- jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 661e584133f4ec3c4e571d157a63844c5b1145b7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097570"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>IJsDebugProcess::CreateBreakPoint (Método)
Establece el punto de interrupción en la posición del documento especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `documentId`  
 [in] Puntero a IDebugDocumentText.  
  
 `characterOffset`  
 [in] Desplazamiento de caracteres desde el principio del archivo.  
  
 `characterCount`  
 [in] Longitud del texto del documento dentro del que se debe insertar el punto de interrupción.  
  
 `isEnabled`  
 [in] Especifica si el punto de interrupción está habilitado.  
  
 `ppDebugBreakPoint`  
 [out] Objeto que representa el punto de interrupción creado.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugProcess (Interfaz)](../../winscript/reference/ijsdebugprocess-interface.md)