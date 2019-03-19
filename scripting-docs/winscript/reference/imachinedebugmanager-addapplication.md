---
title: IMachineDebugManager::AddApplication | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManager.AddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManager::AddApplication
ms.assetid: 7cd591b6-718c-4e77-acb7-a6dd147ddf57
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96c1b865c722a3cceab331b81b1204ee682b911f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155620"
---
# <a name="imachinedebugmanageraddapplication"></a>IMachineDebugManager::AddApplication
Agrega a la que se ejecuta una aplicación de lista de aplicaciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pda`  
 [in] Aplicación en el que se ejecuta la lista de aplicaciones.  
  
 `pdwAppCookie`  
 [out] Una cookie que se usa para quitar la aplicación desde el Administrador de depuración de la máquina.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El Administrador de depuración del proceso se llama a este método cada vez que `IProcessDebugManager::AddApplication` se llama.  
  
## <a name="see-also"></a>Vea también  
 [IMachineDebugManager (interfaz)](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IMachineDebugManager::RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)