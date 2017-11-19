---
title: IDebugSessionProviderEx:StartDebugSession | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugSessionProviderEx:StartDebugSession
apilocation: scrobj.dll
ms.assetid: 247337ca-476c-4aa7-8500-d84fd1d98176
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6f68d5bef91a71d475ea8b0c5131b5945b4c930
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsessionproviderexstartdebugsession"></a>IDebugSessionProviderEx:StartDebugSession
Inicia una sesión de depuración con la aplicación especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
   BOOL  fQuery  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pda`  
 [in] Especifica la aplicación de depuración.  
  
 `fQuery`  
 [in] True indica que una consulta.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método inicia una sesión de depuración con la aplicación especificada. El depurador debe llamar a `IRemoteDebugApplication::ConnectDebugger` antes de volver de esta llamada.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSessionProviderEx (interfaz)](../../winscript/reference/idebugsessionproviderex-interface.md)   
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)