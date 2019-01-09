---
title: IProcessDebugManager::GetDefaultApplication | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.GetDefaultApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::GetDefaultApplication
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6ae3b1bec5fc3aba6ad8e53343f929d133f05493
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091395"
---
# <a name="iprocessdebugmanagergetdefaultapplication"></a>IProcessDebugManager::GetDefaultApplication
Devuelve un objeto de aplicación predeterminado para el proceso actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetDefaultApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppda`  
 [out] El objeto de aplicación de depuración para esta aplicación.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método crea un nuevo objeto de aplicación de depuración y lo agrega a la que se ejecuta la lista de aplicaciones, si es necesario.  
  
 Motores de lenguaje deben usar la aplicación especificada por el `GetDefaultApplication` método si se están ejecutando en un host que no proporciona una aplicación.  
  
## <a name="see-also"></a>Vea también  
 [IProcessDebugManager (Interfaz)](../../winscript/reference/iprocessdebugmanager-interface.md)