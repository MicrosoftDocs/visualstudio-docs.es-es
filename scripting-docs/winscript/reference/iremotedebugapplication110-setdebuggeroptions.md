---
title: 'Iremotedebugapplication110 (:: SetDebuggerOptions | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::SetDebuggerOptions
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7168a4ef8ec70368c0ff691ba1f721275f9d65d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577417"
---
# <a name="iremotedebugapplication110setdebuggeroptions"></a>IRemoteDebugApplication110::SetDebuggerOptions
Se llama para actualizar las opciones del depurador. Se debe llamar a este método después de [iremotedebugapplication (:: ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md). El método [iremotedebugapplication (::D isconnectdebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) se restablece automáticamente a las opciones predeterminadas. El valor predeterminado de las opciones es 0 (SDO_NONE).  
  
> [!IMPORTANT]
> La [interfaz iremotedebugapplication (](../../winscript/reference/iremotedebugapplication-interface.md) se implementa mediante PDM v 11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetDebuggerOptions(        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,        [in] enum SCRIPT_DEBUGGER_OPTIONS value    );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `mask`  
 La máscara de [enumeración SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md) .  
  
 `value`  
 El valor de [enumeración SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md) .  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz iremotedebugapplication (](../../winscript/reference/iremotedebugapplication-interface.md)  
 [IRemoteDebugApplication110 (Interfaz)](../../winscript/reference/iremotedebugapplication110-interface.md)