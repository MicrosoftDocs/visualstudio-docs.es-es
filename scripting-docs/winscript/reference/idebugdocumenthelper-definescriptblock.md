---
title: IDebugDocumentHelper::D efineScriptBlock | Microsoft Docs
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
ms.openlocfilehash: 6a2418b18e80ac86b672b3847f24ef9084ed1252
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576974"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Indica a la aplicación auxiliar que un intervalo determinado de caracteres es un bloque de script controlado por el motor de scripts determinado.  
  
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
 de Ubicación del inicio del bloque de script.  
  
 `cChars`  
 de Número de caracteres del bloque de script.  
  
 `pas`  
 de Motor de scripts para este bloque de script.  
  
 `fScriptlet`  
 de Marca que indica si el bloque de script es un Scriptlet.  
  
 `pdwSourceContext`  
 enuncia Contexto de origen para el bloque de script.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Un host inteligente puede utilizar este método cuando sus documentos contienen bloques de scripts incrustados. Un motor de lenguaje puede utilizar este método cuando su código contiene scripts incrustados para otros lenguajes.  
  
 El motor de scripts es responsable de todo el color de la sintaxis y las búsquedas de contexto de código en el bloque de script.  
  
 Se debe llamar al método `DefineScriptBlock` después de que se haya agregado el texto (por ejemplo, mediante el método `IDebugDocumentHelper::AddDBCSText`) pero antes de que se haya analizado el bloque de script (por ejemplo, mediante el método `IActiveScriptParse ::ParseScriptText`).  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHelper:: AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)    
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)