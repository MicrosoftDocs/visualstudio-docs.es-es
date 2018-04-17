---
title: IDebugProcessEx2::Detach | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0423ae28bfee6e9acf10e2a9682e58a973c37d70
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Este método le informa que el proceso que una sesión ya no está depurando el proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pSession`  
 [in] Un valor que identifica de forma única la sesión para separar este proceso de.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La interfaz se pasa en `pSession` es tratará solo como una cookie, un valor que identifica de forma única el Administrador de sesión de depuración que originalmente asociado a este proceso, si ninguno de los métodos en la interfaz proporcionada es funcional.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)