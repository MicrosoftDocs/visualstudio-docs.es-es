---
title: IMachineDebugManager::AddApplication | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IMachineDebugManager.AddApplication
apilocation: scrobj.dll
helpviewer_keywords: IMachineDebugManager::AddApplication
ms.assetid: 7cd591b6-718c-4e77-acb7-a6dd147ddf57
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77c31084ccc24a6bace18f009eb8372a4f68a428
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanageraddapplication"></a>IMachineDebugManager::AddApplication
Agrega una aplicación en el que se ejecuta lista de aplicaciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pda`  
 [in] Aplicación en el que se ejecuta lista de aplicaciones.  
  
 `pdwAppCookie`  
 [out] Cookie que se utiliza para quitar la aplicación desde el Administrador de depuración de la máquina.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El Administrador de depuración del proceso llama a este método cada vez que `IProcessDebugManager::AddApplication` se llama.  
  
## <a name="see-also"></a>Vea también  
 [IMachineDebugManager (interfaz)](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IMachineDebugManager::RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)