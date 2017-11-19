---
title: IActiveScriptSiteDebug32::GetDocumentContextFromPosition | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 71136a1b3cb136cbc0a97cf39f59f1f4e950048b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
Utilizado por el motor de lenguaje para delegar `IDebugCodeContext::GetSourceContext`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwSourceContext`  
 [in] El contenido de origen con arreglo a `ParseScriptText` o `AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Desplazamiento con respecto al inicio del bloque de script o scriptlet de caracteres.  
  
 `uNumChars`  
 [in] Número de caracteres en este contexto.  
  
 `ppsc`  
 [out] El contexto del documento correspondiente a este intervalo de posición de carácter.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Motores de idioma use este método para delegar `IDebugCodeContext::GetSourceContext`.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSiteDebug32 (Interfaz)](../../winscript/reference/iactivescriptsitedebug32-interface.md)