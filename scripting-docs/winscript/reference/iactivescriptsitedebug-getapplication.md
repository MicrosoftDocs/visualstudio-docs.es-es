---
title: IActiveScriptSiteDebug::GetApplication | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSiteDebug.GetApplication
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSiteDebug::GetApplication
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e33bf254d2e688451f1b69a3b3eb1b676a9e9b1a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebuggetapplication"></a>IActiveScriptSiteDebug::GetApplication
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
 [IActiveScriptSiteDebug (interfaz)](../../winscript/reference/iactivescriptsitedebug-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)