---
title: 'Imachinedebugmanager (:: AddApplication | Microsoft Docs'
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
ms.openlocfilehash: 54ff617ac96c0eb3498b796d4f7fe49f95e1cc96
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573969"
---
# <a name="imachinedebugmanageraddapplication"></a>IMachineDebugManager::AddApplication
Agrega una aplicación a la lista de aplicaciones en ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pda`  
 de Aplicación a la lista de aplicaciones en ejecución.  
  
 `pdwAppCookie`  
 enuncia Cookie que se usa para quitar la aplicación del administrador de depuración del equipo.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El administrador de depuración de proceso llama a este método cada vez que se llama a `IProcessDebugManager::AddApplication`.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz imachinedebugmanager (](../../winscript/reference/imachinedebugmanager-interface.md)  
 [Imachinedebugmanager (:: RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)    
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)