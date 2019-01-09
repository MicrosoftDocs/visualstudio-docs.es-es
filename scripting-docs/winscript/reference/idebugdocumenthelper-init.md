---
title: Idebugdocumenthelper | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Init
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4bcb64b7bbb1c61e7f031d872f7d1440fd17833
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086637"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
El `Init` método inicializa una aplicación auxiliar de documento de depuración con un nombre y atributos iniciales.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pda`  
 [in] La aplicación de depuración asociada con este documento.  
  
 `pszShortName`  
 [in] Una cadena terminada en null que contiene el nombre corto del documento.  
  
 `pszLongName`  
 [in] Una cadena terminada en null que contiene el nombre largo del documento.  
  
 `docAttr`  
 [in] Especifica los atributos del documento de texto.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método inicializa una aplicación auxiliar de documento de depuración con un nombre y atributos iniciales.  
  
 Este documento no aparece en el árbol hasta `IDebugDocumentHelper::Attach` se llama.  
  
## <a name="see-also"></a>Vea también  
 [Idebugdocumenthelper](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper (interfaz)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT_DOC_ATTR (Constantes)](../../winscript/reference/text-doc-attr-constants.md)