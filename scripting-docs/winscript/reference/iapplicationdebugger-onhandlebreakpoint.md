---
title: 'Iapplicationdebugger (:: onHandleBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 3796ea1f50f0c4bcf945dbc10592c048db22757b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577842"
---
# <a name="iapplicationdebuggeronhandlebreakpoint"></a>IApplicationDebugger::onHandleBreakPoint
Controla un evento de punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `prpt`  
 de Subproceso en el que se produjo el punto de interrupción.  
  
 `br`  
 de Motivo del punto de interrupción.  
  
 `pError`  
 de Información de error en tiempo de ejecución, que se proporciona cuando se BREAKREASON_ERROR el valor de `br`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Se llama a este método cuando se visita un punto de interrupción y se llama a `IDebugApplication::HandleBreakPoint`.  
  
 La aplicación permanecerá suspendida hasta que el IDE del depurador llame a `IRemoteDebugApplication::ResumeFromBreakPoint`.  
  
## <a name="see-also"></a>Vea también  
   de la [interfaz iapplicationdebugger (](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)   
 [IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)   
 [BREAKREASON (Enumeración)](../../winscript/reference/breakreason-enumeration.md)