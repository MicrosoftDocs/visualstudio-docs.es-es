---
title: IDebugDocumentHelper::DefineScriptBlock | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b6ec86dacc2e3a8f3d9e28a6db744b778ff01eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Indica a la aplicación auxiliar que un determinado intervalo de caracteres es un bloque de script que se controla mediante el motor de secuencia de comandos determinada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ulCharOffset`  
 [in] Ubicación del inicio del bloque de script.  
  
 `cChars`  
 [in] Número de caracteres del bloque de script.  
  
 `pas`  
 [in] El motor de scripts para este bloque de script.  
  
 `fScriptlet`  
 [in] Marca que indica si el bloque de script es un Subscript.  
  
 `pdwSourceContext`  
 [out] El contexto de origen para el bloque de script.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Un host inteligente puede utilizar este método cuando sus documentos contienen bloques de scripts incrustados. Un motor de lenguaje puede utilizar este método cuando su código contiene scripts incrustados para otros idiomas.  
  
 El motor de scripts es responsable de todas las sintaxis color y código contexto búsquedas en el bloque de script.  
  
 El `DefineScriptBlock` método debe llamarse una vez se ha agregado el texto (por ejemplo, si se usa el `IDebugDocumentHelper::AddDBCSText` método) pero antes de la secuencia de comandos se ha analizado el bloque (por ejemplo, si se usa el `IActiveScriptParse ::ParseScriptText` método).  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentHelper (interfaz)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)