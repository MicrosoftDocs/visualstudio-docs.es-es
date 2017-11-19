---
title: IProcessDebugManager::CreateDebugDocumentHelper | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IProcessDebugManager.CreateDebugDocumentHelper
apilocation: pdm.dll
helpviewer_keywords: IProcessDebugManager::CreateDebugDocumentHelper
ms.assetid: d644e192-1bcc-4768-a91e-239cd920adcd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0b57f941017a0eef7892d43be9ed0414645e55e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iprocessdebugmanagercreatedebugdocumenthelper"></a>IProcessDebugManager::CreateDebugDocumentHelper
Crea una nuevo auxiliar de documento de depuración para esta aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT CreateDebugDocumentHelper(  
   IUnknown*               punkOuter,  
   IDebugDocumentHelper**  pddh  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `punkOuter`  
 [in] Si el objeto devuelto es para que se agregue, `punkOuter` es un puntero de interfaz para el control `IUnknown`. En caso contrario, es un puntero nulo.  
  
 `pddh`  
 [out] El objeto de aplicación auxiliar del documento de depuración para esta aplicación.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método crea una nuevo auxiliar de documento de depuración para esta aplicación.  
  
## <a name="see-also"></a>Vea también  
 [IProcessDebugManager (Interfaz)](../../winscript/reference/iprocessdebugmanager-interface.md)