---
title: 'Idebugapplication (:: SetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.SetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::SetName
ms.assetid: 7b0ddc58-6f20-4ce3-9bdf-81a6c1d64256
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a3e5115d4adc3fc3dfa93f10c90cb0d2b36f0e4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571101"
---
# <a name="idebugapplicationsetname"></a>IDebugApplication::SetName
Establece el nombre de la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SetName(  
   LPCOLESTR  pstrName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrName`  
 de El nombre de la aplicación.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El nombre proporcionado a este método se devuelve en las llamadas subsiguientes al método `IRemoteDebugApplication::GetName`.  
  
 Se debe llamar a este método antes de llamar al método `IProcessDebugManager::AddApplication`.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz idebugapplication (](../../winscript/reference/idebugapplication-interface.md)  
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)