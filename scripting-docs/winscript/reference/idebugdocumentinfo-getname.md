---
title: IDebugDocumentInfo::GetName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetName
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9975563c27b986190fbd2731c3f36b1e32719c0b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160331"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Devuelve el nombre del documento especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dnt`  
 [in] El tipo de nombre del documento para devolver.  
  
 `pbstrName`  
 [out] Cadena que contiene el nombre.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|No se conoce el nombre del documento especificado.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el nombre del documento especificado.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentInfo (interfaz)](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [DOCUMENTNAMETYPE (Enumeración)](../../winscript/reference/documentnametype-enumeration.md)