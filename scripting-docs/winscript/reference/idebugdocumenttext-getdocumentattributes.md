---
title: IDebugDocumentText::GetDocumentAttributes | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentText.GetDocumentAttributes
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentText::GetDocumentAttributes
ms.assetid: 8c544ca1-8db4-4bca-973e-09315d9a0ee5
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e3121538612be48628b24965e118130875c51a0b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgetdocumentattributes"></a>IDebugDocumentText::GetDocumentAttributes
Devuelve los atributos del documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetDocumentAttributes(  
   TEXT_DOC_ATTR*  ptextdocattr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ptextdocattr`  
 [out] Los atributos de texto del documento.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve los atributos del documento.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentText (interfaz)](../../winscript/reference/idebugdocumenttext-interface.md)   
 [TEXT_DOC_ATTR (Constantes)](../../winscript/reference/text-doc-attr-constants.md)