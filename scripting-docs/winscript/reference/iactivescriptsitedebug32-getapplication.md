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
ms.openlocfilehash: bb7fdf5a6d0b380a8024cfdfa70282bcf80ba16d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725025"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
Devuelve el objeto de aplicación de depuración asociado a este sitio de la secuencia de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppda`  
 [out] Puntero al objeto de aplicación de depuración asociados al sitio de la secuencia de comandos.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|El host no admite directamente la depuración.|  
  
## <a name="remarks"></a>Comentarios  
 El `GetApplication` método proporciona una manera para que un host inteligente definir el objeto de aplicación a la que pertenece cada secuencia de comandos. Motores de scripts deben intentar llamar a este método para obtener su aplicación contenedora y recurrir a `IProcessDebugManager::GetDefaultApplication` si se produce un error.  
  
## <a name="see-also"></a>Vea también  
 [Interfaz IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)