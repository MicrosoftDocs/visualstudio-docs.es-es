---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ec541b6dc4ccae57628d4b33e7c188008da6edae
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064042"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método permite que el proveedor del puerto mostrar una advertencia antes de que el usuario se une a un proceso no seguro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Los valores devueltos son como sigue:  
  
- `S_OK`: Asociar al proceso es seguro y no se muestra ningún cuadro de diálogo de advertencia.  
  
- `S_FALSE`: Asociar podría ser un problema de seguridad y se muestra un cuadro de diálogo con una advertencia.  
  
- `FAILURE`: No se puede asociar al proceso.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
