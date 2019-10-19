---
title: 'Idebugdocumentinfo (:: GetDocumentClassId | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetDocumentClassId
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetDocumentClassId
ms.assetid: 3b858794-2c0c-42ba-b98c-cd820ebace20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 996e6d751807bba1e1a74cbb7e579db25193c32b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569086"
---
# <a name="idebugdocumentinfogetdocumentclassid"></a>IDebugDocumentInfo::GetDocumentClassId
Devuelve un `CLSID` que identifica el tipo de documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetDocumentClassId(  
   CLSID*  pclsidDocument  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pclsidDocument`  
 enuncia @No__t_0 que identifica el tipo de documento.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método permite que el IDE del depurador hospede visores personalizados para este documento.  
  
 Si el documento no tiene datos visibles, el valor devuelto de `pclsidDocument` se `CLSID_NULL`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentInfo (Interfaz)](../../winscript/reference/idebugdocumentinfo-interface.md)