---
title: IDebugStackFrame::GetLanguageString | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: cc20c3ce2f5d198e167b83ffddb65cedc84402d7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087742"
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