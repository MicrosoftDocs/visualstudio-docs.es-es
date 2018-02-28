---
title: IDebugApplication::HandleBreakPoint | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplication.HandleBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16b05533c566cb90529766d81fb7197dbc284664
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Hace que el subproceso actual se bloquee y envía una notificación del punto de interrupción en el depurador IDE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `br`  
 [in] El motivo de la interrupción.  
  
 `pbra`  
 [out] Acción a realizar cuando el depurador reanuda la aplicación.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Un motor de lenguaje llama a este método en el contexto de un subproceso que visita un punto de interrupción. Este método bloquea el subproceso actual y envía una notificación de punto de interrupción en el depurador IDE. Cuando el depurador reanuda la aplicación, el `pbra` parámetro especifica qué acción realizar.  
  
> [!NOTE]
>  El motor del lenguaje puede llamarse mediante el subproceso para realizar tareas tales como la pila de enumerar los marcos o expresiones evalúan durante el punto de interrupción.  
  
 Este método provoca `IApplicationDebugger::onHandleBreakPoint` para llamarlo.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplication (interfaz)](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [Enumeración BREAKREASON](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION (Enumeración)](../../winscript/reference/breakresumeaction-enumeration.md)