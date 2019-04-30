---
title: Idebugdocumenthelper | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 3b399f51fc042aa1ed297ab30a7bf2c9bc4befca
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000996"
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
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper (interfaz)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT_DOC_ATTR (Constantes)](../../winscript/reference/text-doc-attr-constants.md)