---
title: IDebugProgram2::CauseBreak | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::CauseBreak
helpviewer_keywords: IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 48029ed4e925073b0d121a88846aa2f0af0a51cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
Las solicitudes que el programa de detener la ejecución del siguiente momento uno de sus intentos de subprocesos para ejecutar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Un [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) evento se envía cuando el programa intenta ejecutar código después de que se llama a este método a continuación.  
  
 Este método es asincrónico en que el método vuelve inmediatamente sin tener que esperar necesariamente para que detenga el programa.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)