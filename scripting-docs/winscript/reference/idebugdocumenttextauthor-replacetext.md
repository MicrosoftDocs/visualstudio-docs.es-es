---
title: IDebugDocumentTextAuthor::ReplaceText | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentTextAuthor.ReplaceText
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentTextAuthor::ReplaceText
ms.assetid: f89304e6-5be0-45a5-947d-2c59c3c0a05e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aa7ef34d035ad89a096414c285b4f66a4f4fa1e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextauthorreplacetext"></a>IDebugDocumentTextAuthor::ReplaceText
Reemplaza el texto del documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT ReplaceText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToReplace,  
   OLECHAR  pcharText[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cCharacterPosition`  
 [in] Iniciar ubicación del intervalo de caracteres para reemplazar.  
  
 `cNumToReplace`  
 [in] Número de caracteres que se va a reemplazar.  
  
 `pcharText[]`  
 [in] Un búfer que contiene los nuevos caracteres para reemplazar los caracteres anteriores.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método reemplaza el texto del documento.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentTextAuthor (Interfaz)](../../winscript/reference/idebugdocumenttextauthor-interface.md)