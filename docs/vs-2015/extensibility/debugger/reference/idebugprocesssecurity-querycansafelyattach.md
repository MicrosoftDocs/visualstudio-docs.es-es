---
title: 'IDebugProcessSecurity:: QueryCanSafelyAttach | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187954"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método permite al proveedor del puerto mostrar una advertencia antes de que el usuario se adjunte a un proceso no seguro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Los valores devueltos son los siguientes:  
  
- `S_OK`: La asociación al proceso es segura y no se muestra ningún cuadro de diálogo de advertencia.  
  
- `S_FALSE`: La asociación puede ser un problema de seguridad y se muestra un cuadro de diálogo con una advertencia.  
  
- `FAILURE`: No se puede asociar al proceso.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
