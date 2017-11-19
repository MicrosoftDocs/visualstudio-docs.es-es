---
title: IProcessDebugManager::AddApplication | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IProcessDebugManager.AddApplication
apilocation: pdm.dll
helpviewer_keywords: IProcessDebugManager::AddApplication
ms.assetid: 73828299-11eb-4c58-ad70-f80f2d0eede8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a221aa0038b0b3fd5046b9ada08e2de86f33a895
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iprocessdebugmanageraddapplication"></a>IProcessDebugManager::AddApplication
Agrega una aplicación a la lista del Administrador de máquina depurar las aplicaciones en ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT AddApplication(  
   IDebugApplication*  pda,  
   DWORD*              pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pda`  
 [in] Aplicación de depuración que se va a agregar a la lista de aplicaciones en ejecución.  
  
 `pdwAppCookie`  
 [out] Cookie que se utiliza para quitar la aplicación desde el Administrador de depuración de la máquina.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método agrega una aplicación en el que se ejecuta la lista de aplicaciones en el Administrador de depuración de la máquina.  
  
## <a name="see-also"></a>Vea también  
 [IProcessDebugManager (interfaz)](../../winscript/reference/iprocessdebugmanager-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)