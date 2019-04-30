---
title: IRemoteDebugApplicationEvents::OnBreakFlagChange | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnBreakFlagChange
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnBreakFlagChange
ms.assetid: 25684454-a0d8-47e0-85f5-2217069a9f45
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb19b6cfc423a1305276441305ef854c70f2d896
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62943788"
---
# <a name="iremotedebugapplicationeventsonbreakflagchange"></a>IRemoteDebugApplicationEvents::OnBreakFlagChange
Controla un evento cuando cambian las marcas de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OnBreakFlagChange(  
   APPBREAKFLAGS                   abf,  
   IRemoteDebugApplicationThread*  prdatSteppingThread  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `abf`  
 [in] Las marcas de interrupción actual de la aplicación.  
  
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