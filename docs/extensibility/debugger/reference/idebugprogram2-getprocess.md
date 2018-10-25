---
title: IDebugProgram2::GetProcess | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3528b4c323f1fee68a5ed17368646608e63e6fbb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49947870"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Obtener el proceso que se ejecuta este programa en.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppProcess`  
 [out] Devuelve el [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interfaz que representa el proceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 A menos que implemente un motor de depuración (DE) la [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) interfaz, la implementación de la DE este método siempre debe devolver `E_NOTIMPL` porque no puede determinar a DE proceso que se está ejecutando en y, por tanto, no se puede satisfacer una implementación de este método.  
  
 Implementar el `IDebugEngineLaunch2` interfaz significa que la DE debe saber cómo crear un proceso; por lo tanto, la implementación del DE la [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) es capaz de saber qué proceso se ejecuta en la interfaz.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)