---
title: IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs
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
ms.openlocfilehash: 17be4d47db15a80b2560d71f747e5b93b7e17474
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868344"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Supervisa la ejecución (o se detiene la ejecución inspeccionando) que se produzca en el subproceso especificado.  
  
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
 [in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa el programa que se va a escalonado.  
  
 `dwTid`  
 [in] Especifica el identificador del subproceso que se va a inspeccionar.  
  
 `fWatch`  
 [in] Distinto de cero (`TRUE`) significa que empiece a mirar para su ejecución en el subproceso identificado por `dwTid`; en caso contrario, cero (`FALSE`) significa Detener ejecución inspeccionando en `dwTid`.  
  
 `dwFrame`  
 [in] Especifica un índice de fotograma que controla el tipo de paso. Cuando se trata de valor es cero (0), el tipo de paso es "step into" y debe detener el programa cada vez que el subproceso identificado por `dwTid` ejecuta. Cuando `dwFrame` es distinto de cero, el tipo de paso es "saltar" y debe detener el programa sólo si el subproceso identificado por `dwTid` se está ejecutando en un marco cuyo índice es igual o superior en la pila que `dwFrame`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cuando el Administrador de depuración de la sesión (SDM) los pasos de un programa, identificado por el `pOriginatingProgram` parámetro, notifica a todos los demás programas asociados mediante una llamada a este método.  
  
 Este método solo es aplicable a ejecución paso a paso en el mismo subproceso.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)