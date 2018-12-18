---
title: 'Ijsdebugprocess:: CreateBreakpoint (método) | Documentos de Microsoft'
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
ms.openlocfilehash: 10d734f32d092d341dbb1b02a5cc7a0c127223a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728125"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>IJsDebugProcess::CreateBreakPoint (Método)
Establece el punto de interrupción en la posición del documento especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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