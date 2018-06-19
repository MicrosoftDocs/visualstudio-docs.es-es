---
title: IDebugDocumentHelper::SetDebugDocumentHost | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDebugDocumentHost
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDebugDocumentHost
ms.assetid: b26a03c3-8a3f-47b0-b916-4c65d5500f10
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d1377edaa5b10a7ebb06713e512010be010a9d3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726375"
---
# <a name="idebugdocumenthelpersetdebugdocumenthost"></a>IDebugDocumentHelper::SetDebugDocumentHost
Establece el `IDebugDocumentHost` para este documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SetDebugDocumentHost(  
   IDebugDocumentHost*  pddh  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pddh`  
 [in] El host de documento de depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El `IDebugDocumentHost` interfaz se usa para colorear la sintaxis de host inteligente, capturar texto aplazada y devolver objetos de control de recién creado en el documento contextos.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentHelper (interfaz)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHost (Interfaz)](../../winscript/reference/idebugdocumenthost-interface.md)