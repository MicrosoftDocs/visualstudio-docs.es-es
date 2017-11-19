---
title: IDebugProgram2::GetProcess | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::GetProcess
helpviewer_keywords: IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6d085c149c72393f0179ad6b6b50334426777d9c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Obtener el proceso que se ejecuta este programa.  
  
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
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 A menos que un motor de depuración (Alemania) implementa la [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) implementación de Alemania de este método de interfaz, siempre debería devolver `E_NOTIMPL` porque un Alemania no puede determinar qué proceso se ejecuta en y, por tanto, no se puede satisface una implementación de este método.  
  
 Implementar la `IDebugEngineLaunch2` interfaz significa que la DE debe saber cómo crear un proceso; por lo tanto, la implementación de Alemania de la [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz es capaz de saber qué proceso se ejecuta en.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)