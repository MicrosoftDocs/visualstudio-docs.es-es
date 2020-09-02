---
title: 'IDebugThread2:: GetName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 509db8c30aabd8a4163ea433bb06a99d4bfa2fb9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153039"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el nombre de un subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName (   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrName`  
 enuncia Devuelve el nombre del subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El nombre recuperado es siempre un nombre que se puede mostrar y este nombre describe el subproceso. El nombre del subproceso podría derivarse de una arquitectura en tiempo de ejecución que admita subprocesos con nombre, o podría ser un nombre derivado del motor de depuración. Como alternativa, el nombre del subproceso se puede establecer mediante una llamada al método [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) .  
  
## <a name="see-also"></a>Consulte también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
