---
title: 'Idebugapplication (:: HandleBreakPoint | Microsoft Docs'
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
ms.openlocfilehash: 30937817424e88f80cfa6afa8c874adfd2b2687b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574960"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Hace que el subproceso actual se bloquee y envíe una notificación del punto de interrupción al IDE del depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `br`  
 de Motivo de la interrupción.  
  
 `pbra`  
 enuncia Acción que se realizará cuando el depurador reanude la aplicación.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Un motor de lenguaje llama a este método en el contexto de un subproceso que llega a un punto de interrupción. Este método bloquea el subproceso actual y envía una notificación de punto de interrupción al IDE del depurador. Cuando el depurador reanuda la aplicación, el parámetro `pbra` especifica qué acción se debe realizar.  
  
> [!NOTE]
> El subproceso puede llamar al motor de lenguaje para realizar tareas como enumerar marcos de pila o evaluar expresiones durante el punto de interrupción.  
  
 Este método hace que se llame a `IApplicationDebugger::onHandleBreakPoint`.  
  
## <a name="see-also"></a>Vea también  
   de la [interfaz idebugapplication (](../../winscript/reference/idebugapplication-interface.md)  
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
   [enumeración breakreason (](../../winscript/reference/breakreason-enumeration.md)  
 [BREAKRESUMEACTION (Enumeración)](../../winscript/reference/breakresumeaction-enumeration.md)