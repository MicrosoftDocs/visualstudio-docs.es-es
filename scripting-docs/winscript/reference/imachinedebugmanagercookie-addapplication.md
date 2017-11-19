---
title: IMachineDebugManagerCookie::AddApplication | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IMachineDebugManagerCookie.AddApplication
apilocation: scrobj.dll
helpviewer_keywords: IMachineDebugManagerCookie::AddApplication
ms.assetid: 4d5503c5-aca9-4cf7-9900-f77bf5f3263d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c452c4fe2826c7c5372c7598a14731e14077925
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagercookieaddapplication"></a>IMachineDebugManagerCookie::AddApplication
Agrega una aplicación en el que se ejecuta lista de aplicaciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwDebugAppCookie,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pda`  
 [in] Aplicación en el que se ejecuta lista de aplicaciones.  
  
 `dwDebugAppCookie`  
 [in] Cookie que identifica la aplicación de depuración.  
  
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
 [IMachineDebugManagerCookie (interfaz)](../../winscript/reference/imachinedebugmanagercookie-interface.md)   
 [IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)