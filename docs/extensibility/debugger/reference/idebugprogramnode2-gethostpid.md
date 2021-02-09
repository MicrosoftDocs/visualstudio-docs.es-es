---
title: 'IDebugProgramNode2:: GetHostPid | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostPid
helpviewer_keywords:
- IDebugProgramNode2::GetHostPid
ms.assetid: e65b4b15-46d8-4ca7-9456-2b4c078f7cf9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5dc11dbbe8845bac125942bc3825ecdf5dacdb00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898602"
---
# <a name="idebugprogramnode2gethostpid"></a>IDebugProgramNode2::GetHostPid
Obtiene el identificador de proceso del sistema para el proceso que hospeda el programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetHostPid ( 
   AD_PROCESS_ID * pdwHostPid
);
```

```csharp
int GetHostPid ( 
   out AD_PROCESS_ID pdwHostPid
);
```

## <a name="parameters"></a>Parámetros
`pdwHostPid`\
enuncia Devuelve el identificador de proceso del sistema para el proceso de hospedaje.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra cómo implementar este método para un `CProgram` objeto simple que implementa la interfaz [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) .

```cpp
HRESULT CProgram::GetHostPid(AD_PROCESS_ID* pdwHostPid) {
   // Check for valid argument.
   if (pdwHostPid == NULL)
     return E_INVALIDARG;

   // Get the process identifier of the calling process.
   pdwHostPid->ProcessIdType = AD_PROCESS_ID_SYSTEM;
   pdwHostPid->ProcessId.dwProcessId = GetCurrentProcessId();
   return S_OK;
}
```

## <a name="see-also"></a>Vea también
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
