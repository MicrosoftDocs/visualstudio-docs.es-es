---
title: IApplicationDebugger::onHandleBreakPoint | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onHandleBreakPoint
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onHandleBreakPoint
ms.assetid: 31adcecd-d6c1-4222-ab2c-32ec2fefb322
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3be067d3b8c3e3268ac2caf1614b70efff6f665
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725305"
---
# <a name="iapplicationdebuggeronhandlebreakpoint"></a>IApplicationDebugger::onHandleBreakPoint
Controla un evento de punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `prpt`  
 [in] El subproceso donde se produjo el punto de interrupción.  
  
 `br`  
 [in] La razón para el punto de interrupción.  
  
 `pError`  
 [in] Proporciona información de error en tiempo de ejecución, cuando el valor de `br` es BREAKREASON_ERROR.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Se llama a este método cuando se alcanza un punto de interrupción y `IDebugApplication::HandleBreakPoint` se llama.  
  
 La aplicación permanecerá suspendida hasta que el depurador IDE llama `IRemoteDebugApplication::ResumeFromBreakPoint`.  
  
## <a name="see-also"></a>Vea también  
 [IApplicationDebugger (interfaz)](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)   
 [IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)   
 [BREAKREASON (Enumeración)](../../winscript/reference/breakreason-enumeration.md)