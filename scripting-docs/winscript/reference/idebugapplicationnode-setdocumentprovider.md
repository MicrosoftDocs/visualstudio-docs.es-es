---
title: IDebugApplicationNode::SetDocumentProvider | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.SetDocumentProvider
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::SetDocumentProvider
ms.assetid: 7cb587ca-d84e-4b5e-9b94-e973cca55a03
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95c80bf04c129b2410b97b2e01861a1007457239
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725475"
---
# <a name="idebugapplicationnodesetdocumentprovider"></a>IDebugApplicationNode::SetDocumentProvider
Establece el proveedor de documento para este nodo de la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SetDocumentProvider(  
   IDebugDocumentProvider*  pddp  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pddp`  
 [in] El proveedor de documento para este nodo de la aplicación.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método establece el proveedor de documento para este nodo de la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationNode (Interfaz)](../../winscript/reference/idebugapplicationnode-interface.md)