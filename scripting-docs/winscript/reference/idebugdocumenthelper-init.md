---
title: 'IDebugDocumentHelper:: init | Microsoft Docs'
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
ms.openlocfilehash: 13e6379052707aa44c0fa52f4cb30db2c4c4fa99
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576862"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
El método `Init` Inicializa una aplicación auxiliar de documentos de depuración con un nombre y atributos iniciales.  
  
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
 de La aplicación de depuración asociada a este documento.  
  
 `pszShortName`  
 de Una cadena terminada en null que contiene el nombre corto del documento.  
  
 `pszLongName`  
 de Una cadena terminada en null que contiene el nombre largo del documento.  
  
 `docAttr`  
 de Especifica atributos de documento de texto.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método inicializa una aplicación auxiliar de documento de depuración con un nombre y atributos iniciales.  
  
 Este documento no aparece en el árbol hasta que se llama a `IDebugDocumentHelper::Attach`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
   de la [interfaz IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [TEXT_DOC_ATTR (Constantes)](../../winscript/reference/text-doc-attr-constants.md)