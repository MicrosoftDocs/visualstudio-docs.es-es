---
title: IRemoteDebugApplicationEvents::OnBreakFlagChange | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnBreakFlagChange
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnBreakFlagChange
ms.assetid: 25684454-a0d8-47e0-85f5-2217069a9f45
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8b4caac89897f015fec7ac483b967f9b42676aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationeventsonbreakflagchange"></a>IRemoteDebugApplicationEvents::OnBreakFlagChange
Controla un evento cuando cambian las marcas de salto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT OnBreakFlagChange(  
   APPBREAKFLAGS                   abf,  
   IRemoteDebugApplicationThread*  prdatSteppingThread  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `abf`  
 [in] Las marcas de salto actual de la aplicación.  
  
 `prdatSteppingThread`  
 [in] El subproceso actualmente en ejecución.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método controla el evento cuando cambia la marca de interrupción.  
  
## <a name="see-also"></a>Vea también  
 [IRemoteDebugApplicationEvents (interfaz)](../../winscript/reference/iremotedebugapplicationevents-interface.md)   
 [APPBREAKFLAGS (Enumeración)](../../winscript/reference/appbreakflags-enumeration.md)