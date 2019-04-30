---
title: IDebugDocumentHelper::DefineScriptBlock | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a320e4e43a983ace4decbaa68de0b1a7df7d457
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783029"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Indica a la aplicación auxiliar que un determinado intervalo de caracteres es un bloque de script que se controla mediante el motor de secuencia de comandos determinada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
 [in] Marca que indica si el bloque de script es scriptlet.  
  
 `pdwSourceContext`  
 [out] El contexto de origen para el bloque de script.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Un host inteligente puede usar este método cuando sus documentos contienen bloques de script incrustado. Un motor de lenguaje puede utilizar este método cuando su código contiene scripts incrustados para otros idiomas.  
  
 El motor de scripts es responsable de todas las sintaxis color y el código de contexto búsquedas en el bloque de script.  
  
 El `DefineScriptBlock` debe llamarse al método después de agregar el texto (por ejemplo, si se usa el `IDebugDocumentHelper::AddDBCSText` método) pero antes de la secuencia de comandos que se ha analizado el bloque (por ejemplo, si se usa el `IActiveScriptParse ::ParseScriptText` método).  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentHelper (interfaz)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)