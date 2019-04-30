---
title: IActiveScriptSiteDebug32::GetDocumentContextFromPosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9a52abcfa4defb49526f944469c95a2247f5d85c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992514"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
Usa el motor de lenguaje para delegar `IDebugCodeContext::GetSourceContext`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwSourceContext`  
 [in] El contenido de origen como se proporciona en `ParseScriptText` o `AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Desplazamiento con respecto al inicio del bloque de script o el scriptlet de caracteres.  
  
 `uNumChars`  
 [in] Número de caracteres en este contexto.  
  
 `ppsc`  
 [out] El contexto del documento correspondiente a este intervalo de la posición del carácter.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Motores de lenguaje usan este método para delegar `IDebugCodeContext::GetSourceContext`.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSiteDebug32 (Interfaz)](../../winscript/reference/iactivescriptsitedebug32-interface.md)