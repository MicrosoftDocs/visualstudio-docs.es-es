---
title: IDebugDocumentInfo::GetName | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: da369c328c2f92915c60b1c50517938bf76d5202
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726595"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Devuelve el nombre del documento especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dnt`  
 [in] El tipo del nombre de documento para devolver.  
  
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