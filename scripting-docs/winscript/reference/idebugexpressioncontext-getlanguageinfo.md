---
title: IDebugExpressionContext::GetLanguageInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.GetLanguageInfo
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::GetLanguageInfo
ms.assetid: 35e25662-0b2a-4c3f-bce4-f01726bc04a8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed5546f07a81d9c2825f3dbdc4f2bb28887948f9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145322"
---
# <a name="idebugexpressioncontextgetlanguageinfo"></a>IDebugExpressionContext::GetLanguageInfo
Devuelve un nombre y GUID para el lenguaje que posee este contexto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetLanguageInfo(  
   BSTR*  pbstrLanguageName,  
   GUID*  pLanguageID  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrLanguageName`  
 [out] El nombre del idioma.  
  
 `pLanguageID`  
 [out] El identificador único para el idioma.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve un nombre y GUID para el lenguaje que posee este contexto.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExpressionContext (Interfaz)](../../winscript/reference/idebugexpressioncontext-interface.md)