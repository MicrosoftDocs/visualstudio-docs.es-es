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
- IDebugDocumentHelper.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Attach
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0f397f70d994d0997163a06766d32c35e9b2ab7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090147"
---
# <a name="idebugdocumenthelperattach"></a>IDebugDocumentHelper::Attach
Este documento se agrega al árbol del documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pddhParent`  
 [in] El árbol del documento donde se agregará en este documento. Puede ser NULL.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método en este documento agrega al documento de árbol, con `pddhParent` como elemento primario. Si el `pddhParent` es `NULL`, este documento será el documento de nivel superior.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [IDebugDocumentHelper (Interfaz)](../../winscript/reference/idebugdocumenthelper-interface.md)