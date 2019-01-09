---
title: IActiveScriptSiteDebug32::GetApplication | Documentos de Microsoft
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
ms.openlocfilehash: c71e33445db7745f71e374c586d079a9665776b2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087911"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
Devuelve el objeto de aplicación de depuración asociado a este sitio de la secuencia de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppda`  
 [out] Puntero al objeto de aplicación de depuración asociado con el sitio de la secuencia de comandos.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|El host no admite directamente la depuración.|  
  
## <a name="remarks"></a>Comentarios  
 El `GetApplication` método proporciona una forma de un host inteligente definir el objeto de aplicación a la que pertenece cada secuencia de comandos. Motores de script deben intentar llamar a este método para obtener su aplicación contenedora y recurrir a `IProcessDebugManager::GetDefaultApplication` si se produce un error.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSiteDebug32 (interfaz)](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)