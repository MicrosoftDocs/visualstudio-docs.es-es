---
title: IDebugDocumentTextEvents::onUpdateDocumentAttributes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onUpdateDocumentAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onUpdateDocumentAttributes
ms.assetid: 48fa909c-14c2-4ca4-af86-a5809c72dd39
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef8791a68086c02b7e1cc8d0a603deba63943af4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144776"
---
# <a name="idebugdocumenttexteventsonupdatedocumentattributes"></a>IDebugDocumentTextEvents::onUpdateDocumentAttributes
Indica que se cambian los atributos del documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT onUpdateDocumentAttributes(  
   TEXT_DOC_ATTR  textdocattr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `textdocattr`  
 [in] Los nuevos atributos de documento.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método indica que se han cambiado los atributos del documento.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentTextEvents (interfaz)](../../winscript/reference/idebugdocumenttextevents-interface.md)   
 [TEXT_DOC_ATTR (Constantes)](../../winscript/reference/text-doc-attr-constants.md)