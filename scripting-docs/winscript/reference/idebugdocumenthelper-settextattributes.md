---
title: 'IDebugDocumentHelper:: SetTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetTextAttributes
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetTextAttributes
ms.assetid: 31657738-9e4c-436a-be61-23f4185d452e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cc5e5955652fd8b59d4c502e68d97a729ded141
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569459"
---
# <a name="idebugdocumenthelpersettextattributes"></a>IDebugDocumentHelper::SetTextAttributes
Establece los atributos de un intervalo de texto, invalidando otros atributos en ese texto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SetTextAttributes(  
   ULONG              ulCharOffset,  
   ULONG              cChars,  
   SOURCE_TEXT_ATTR*  pstaTextAttr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ulCharOffset`  
 de Ubicación del inicio del intervalo de texto.  
  
 `cChars`  
 de Número de caracteres del intervalo.  
  
 `pstaTextAttr`  
 de Atributos de texto de origen para el intervalo de texto.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Es un error llamar a `SetTextAttributes` en un intervalo de texto antes de que se agregue el texto al documento. Llame a los métodos `AddDBCSText`, `AddUnicodeText` o `AddDeferredText` para agregar texto al documento.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHelper:: AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)    
 [IDebugDocumentHelper:: AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)    
 [IDebugDocumentHelper:: AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [SOURCE_TEXT_ATTR (Enumeración)](../../winscript/reference/source-text-attr-enumeration.md)