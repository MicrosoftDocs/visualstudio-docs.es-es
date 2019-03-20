---
title: Enumeración SCRIPT_DEBUGGER_OPTIONS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SCRIPT_DEBUGGER_OPTIONS Enumeration
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25f74902e2fea451ae5ddaf75d215c3a6c70b050
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155048"
---
# <a name="scriptdebuggeroptions-enumeration"></a>Enumeración SCRIPT_DEBUGGER_OPTIONS
Indica un conjunto de opciones o capacidades que se aplican al depurador adjunto. Utilizado en [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) y [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Estas constantes se implementan mediante PDM v10.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Valor|Descripción|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|Se establece ninguna opción.|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|Indica que el tiempo de ejecución del script debe provocar eventos BREAKREASON_ERROR cuando se produce una excepción. Esta opción se puede definida por el depurador o establecida por el código de usuario a través de `Debug.enableFirstChanceExceptions(<true&#124;false>)`.|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|Indica que el depurador asociado es compatible con trabajos web.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)