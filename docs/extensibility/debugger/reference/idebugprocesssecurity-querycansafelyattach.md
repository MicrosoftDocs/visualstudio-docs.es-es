---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5315281b904a6a4144f8e06780048e25cd5e0221
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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