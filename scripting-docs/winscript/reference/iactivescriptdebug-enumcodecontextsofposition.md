---
title: IActiveScriptDebug::EnumCodeContextsOfPosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::EnumCodeContextsOfPosition
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c364d00941a65272b4d22cc7674a0f0e6178f099
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009747"
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Utiliza un host inteligente para delegar el `IDebugDocumentContext::EnumCodeContexts` método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwSourceContext`  
 [in] Como se proporciona en el contexto de origen `IActiveScriptParse::ParseScriptText` o `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Desplazamiento con respecto al inicio del texto de la secuencia de comandos de caracteres.  
  
 `uNumChars`  
 [in] Número de caracteres en este contexto.  
  
 `ppescc`  
 [out] Un enumerador de los contextos de código en el intervalo especificado.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Hosts inteligentes usan este método para delegar el `IDebugDocumentContext::EnumCodeContexts` método.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptDebug (interfaz)](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)