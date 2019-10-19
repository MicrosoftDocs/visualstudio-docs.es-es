---
title: 'Iremotedebugapplicationevents (:: OnBreakFlagChange | Microsoft Docs'
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
ms.openlocfilehash: 71e9a29b6dcc5cd6864ce4edffe9e5f96b64ba9e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561710"
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
 de Marcas de interrupción actuales para la aplicación.  
  
 `prdatSteppingThread`  
 de Subproceso que se está ejecutando actualmente.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método controla el evento cuando cambia la marca de interrupción.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz iremotedebugapplicationevents (](../../winscript/reference/iremotedebugapplicationevents-interface.md)  
 [APPBREAKFLAGS (Enumeración)](../../winscript/reference/appbreakflags-enumeration.md)