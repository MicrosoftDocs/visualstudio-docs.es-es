---
title: 'IActiveScriptSiteDebug32:: GetDocumentContextFromPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b43b16f46cc62b6c70460d79c194b5e0d2cfede0
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835282"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
Lo usa el motor de lenguaje para delegar `IDebugCodeContext::GetSourceContext` .  
  
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
 de El contenido de origen tal como se proporciona a `ParseScriptText` o `AddScriptlet` .  
  
 `uCharacterOffset`  
 de Desplazamiento de caracteres en relación con el inicio del bloque de script o el Scriptlet.  
  
 `uNumChars`  
 de Número de caracteres en este contexto.  
  
 `ppsc`  
 enuncia Contexto del documento correspondiente a este intervalo de posiciones de caracteres.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se ha llevado a cabo de forma correcta.|  
  
## <a name="remarks"></a>Comentarios  
 Los motores de lenguaje utilizan este método para delegar `IDebugCodeContext::GetSourceContext` .  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSiteDebug32 (Interfaz)](../../winscript/reference/iactivescriptsitedebug32-interface.md)