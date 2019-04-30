---
title: IDebugProgram2::Execute | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6134c10f30d66011dca5e40c28b6cbe6a7c94ed
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430553"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Continúa ejecutando este programa desde un estado detenido. Se borra cualquier estado de ejecución anterior (por ejemplo, un paso), y el programa comienza a ejecutarse de nuevo.  
  
> [!NOTE]
> Este método está obsoleto. Use la [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) método en su lugar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Execute(  
   void  
);  
```  
  
```csharp  
int Execute();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cuando el usuario inicia la ejecución de un estado detenido en el subproceso del otro programa, este método se llama en este programa. Este método también se llama cuando el usuario selecciona el **iniciar** comando desde el **depurar** menú en el IDE. La implementación de este método puede ser tan sencilla como llamar a la [reanudar](../../../extensibility/debugger/reference/idebugthread2-resume.md) método en el subproceso actual en el programa.  
  
> [!WARNING]
> No enviar un evento de detención o a un evento (sincrónico) inmediato [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras se controla esta llamada; en caso contrario, el depurador puede dejar de responder.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)
