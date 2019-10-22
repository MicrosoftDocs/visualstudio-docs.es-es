---
title: 'Idebugdocumentinfo (:: GetName | Microsoft Docs'
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
ms.openlocfilehash: bc098da29367a322bd93b4f60ba0e090aee9ee91
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570959"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Devuelve el nombre de documento especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dnt`  
 de El tipo de nombre de documento que se va a devolver.  
  
 `pbstrName`  
 enuncia Cadena que contiene el nombre.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|No se conoce el nombre de documento especificado.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el nombre de documento especificado.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz idebugdocumentinfo (](../../winscript/reference/idebugdocumentinfo-interface.md)  
 [DOCUMENTNAMETYPE (Enumeración)](../../winscript/reference/documentnametype-enumeration.md)