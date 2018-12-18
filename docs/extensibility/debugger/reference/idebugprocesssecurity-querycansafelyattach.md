---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe132ddbd154e04e3cef1a20e826c3634c65bdb2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114234"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Este método permite que el proveedor del puerto mostrar una advertencia antes de que el usuario adjunta a un proceso no seguro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Los valores devueltos son como sigue:  
  
-   `S_OK`: Asociar al proceso es seguro para la ejecución y no se muestra ningún cuadro de diálogo de advertencia.  
  
-   `S_FALSE`: Asociar podría indicar un problema de seguridad y se muestra un cuadro de diálogo con una advertencia.  
  
-   `FAILURE`: Asociar al proceso se produce un error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)