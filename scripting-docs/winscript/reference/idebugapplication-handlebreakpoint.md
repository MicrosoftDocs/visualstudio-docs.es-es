---
title: IDebugApplication::HandleBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b05288a8863b2c555493d4a3f7ea8e2b7537d5a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146726"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Hace que el subproceso actual se bloquea y envía una notificación del punto de interrupción en el IDE del depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `br`  
 [in] La razón por la interrupción.  
  
 `pbra`  
 [out] Acción necesaria cuando el depurador reanuda la aplicación.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Un motor de lenguaje llama a este método en el contexto de un subproceso que alcanza un punto de interrupción. Este método bloquea el subproceso actual y envía una notificación de punto de interrupción en el IDE del depurador. Cuando el depurador reanuda la aplicación, el `pbra` parámetro especifica qué acción realizar.  
  
> [!NOTE]
>  El motor de lenguaje puede llamarse mediante el subproceso para realizar tareas tales como enumerar la pila de marcos o evaluación expresiones durante el punto de interrupción.  
  
 Este método provoca que `IApplicationDebugger::onHandleBreakPoint` llamarse.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplication (interfaz)](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [BREAKREASON (enumeración)](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION (Enumeración)](../../winscript/reference/breakresumeaction-enumeration.md)