---
title: 'Idebugdocumenttextauthor (:: ReplaceText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextAuthor.ReplaceText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextAuthor::ReplaceText
ms.assetid: f89304e6-5be0-45a5-947d-2c59c3c0a05e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: beca5d0ce19a38346ef9b03e39169769c90ea008
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572038"
---
# <a name="idebugdocumenttextauthorreplacetext"></a>IDebugDocumentTextAuthor::ReplaceText
Reemplaza el texto del documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT ReplaceText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToReplace,  
   OLECHAR  pcharText[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cCharacterPosition`  
 de Ubicación de inicio del intervalo de caracteres que se va a reemplazar.  
  
 `cNumToReplace`  
 de Número de caracteres que se van a reemplazar.  
  
 `pcharText[]`  
 de Búfer que contiene los nuevos caracteres para reemplazar los caracteres antiguos.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método reemplaza el texto del documento.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentTextAuthor (Interfaz)](../../winscript/reference/idebugdocumenttextauthor-interface.md)