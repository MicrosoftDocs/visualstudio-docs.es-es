---
title: IDebugStackFrame::GetLanguageString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetLanguageString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetLanguageString
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab0c0ab317754305ca2440748dd680e31750d8a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157040"
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
Devuelve una descripción de texto largos o corta del lenguaje.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fLong`  
 [in] Marca, donde `TRUE` devuelve una descripción larga y `FALSE` devuelve una descripción breve.  
  
 `pbstrLanguage`  
 [out] La descripción del lenguaje.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, si `fLong` es `FALSE`, este método proporciona solo el nombre del idioma asociado con el marco de pila. Cuando `fLong` es `TRUE`, este método puede proporcionar una descripción completa del producto.  
  
## <a name="see-also"></a>Vea también  
 [IDebugStackFrame (Interfaz)](../../winscript/reference/idebugstackframe-interface.md)