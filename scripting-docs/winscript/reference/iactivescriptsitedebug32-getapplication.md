---
title: 'IActiveScriptSiteDebug32:: GetApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 93c4a8fe6e5c2aac8b07f896810dcd03060b46d0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572200"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
Devuelve el objeto de la aplicación de depuración asociado a este sitio de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppda`  
 enuncia Puntero al objeto de la aplicación de depuración asociado al sitio del script.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|El host no admite directamente la depuración.|  
  
## <a name="remarks"></a>Comentarios  
 El método `GetApplication` proporciona una forma para que un host inteligente defina el objeto de aplicación al que pertenece cada script. Los motores de script deben intentar llamar a este método para obtener su aplicación contenedora y recurrir a `IProcessDebugManager::GetDefaultApplication` si se produce un error.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)  
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)