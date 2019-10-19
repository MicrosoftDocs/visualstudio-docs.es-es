---
title: 'IProcessDebugManager:: RemoveApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.RemoveApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::RemoveApplication
ms.assetid: 334e869d-81ae-4d30-9e89-89763ad4f184
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d079d9089dbc47ac272388c680fa585a3532eea8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576536"
---
# <a name="iprocessdebugmanagerremoveapplication"></a>IProcessDebugManager::RemoveApplication
Quita una aplicación de la lista de aplicaciones en ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT RemoveApplication(  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwAppCookie`  
 de La cookie proporcionada por `IProcessDebugManager::AddApplication` cuando la aplicación se agregó a la lista de aplicaciones.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método quita una aplicación de la lista de aplicaciones en ejecución.  
  
## <a name="see-also"></a>Vea también  
 [IProcessDebugManager:: AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)    
 [IProcessDebugManager (Interfaz)](../../winscript/reference/iprocessdebugmanager-interface.md)