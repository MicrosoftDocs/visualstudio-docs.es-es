---
title: IDebugDocumentTextAuthor::InsertText | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentTextAuthor.InsertText
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentTextAuthor::InsertText
ms.assetid: ef4e6a5b-8efa-4290-b498-c0f8a6aac09b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 248d89f7e1c29633a447bef672877682bfa44def
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextauthorinserttext"></a>IDebugDocumentTextAuthor::InsertText
Inserta un nuevo texto en el documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT InsertText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToInsert,  
   OLECHAR  pcharText[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cCharacterPosition`  
 [in] Ubicación para insertar texto.  
  
 `cNumToInsert`  
 [in] Número de caracteres que se va a insertar.  
  
 `pcharText[]`  
 [in] Un búfer que contiene los caracteres que se va a insertar.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método inserta el nuevo texto en el documento.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentTextAuthor (interfaz)](../../winscript/reference/idebugdocumenttextauthor-interface.md)   
 [IDebugDocumentTextAuthor::RemoveText](../../winscript/reference/idebugdocumenttextauthor-removetext.md)