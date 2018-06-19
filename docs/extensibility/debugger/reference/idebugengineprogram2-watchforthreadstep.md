---
title: IDebugEngineProgram2::WatchForThreadStep | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f7c897c4c5b8488766f72723f3e85909281abbf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112341"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Supervisa la ejecución (o se detiene ver ejecución) que se produzca en el subproceso especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```csharp  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pOriginatingProgram`  
 [in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa el programa que se está ejecutando paso.  
  
 `dwTid`  
 [in] Especifica el identificador del subproceso que se va a inspeccionar.  
  
 `fWatch`  
 [in] Es distinto de cero (`TRUE`) significa que empiece a ver para su ejecución en el subproceso identificado por `dwTid`; en caso contrario, cero (`FALSE`) significa dejar de supervisar para su ejecución en `dwTid`.  
  
 `dwFrame`  
 [in] Especifica un índice de marco que controla el tipo de paso. Cuando se trata de valor es cero (0), el tipo de paso es "Ir a" y debe detener el programa cada vez que el subproceso identificado por `dwTid` se ejecuta. Cuando `dwFrame` es distinto de cero, el tipo de paso es "saltarse" y el programa debe detenerse solo si el subproceso identificado por `dwTid` se ejecuta en un marco cuyo índice es igual o superior en la pila que `dwFrame`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cuando el Administrador de sesión de depuración (SDM) pasa un programa, identificado por la `pOriginatingProgram` parámetro, notifica a todos los demás programas asociados mediante una llamada a este método.  
  
 Este método es aplicable únicamente a la ejecución paso a paso en el mismo subproceso.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)