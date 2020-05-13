---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3c0f6e66b6585eafde656cd7be88d0c76bbb3f37
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720707"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Obtiene una interfaz especificada a través de los límites del proceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT UnmarshalDebuggeeInterface(
   REFIID riid,
   void** ppvObject
);
```

```csharp
int UnmarshalDebuggeeInterface(
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Parámetros
`riid`\
[en] GUID de la interfaz que se debe obtener.

`ppvObject`\
[fuera] Devuelve el objeto que implementa la interfaz deseada. [C++] se puede convertir directamente al tipo de interfaz deseado. Utilice el <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> método para obtener la interfaz deseada.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método se utiliza cuando el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] motor de depuración se ejecuta en el espacio de proceso y el programa que se está depurando se ejecuta en su propio espacio de proceso.

## <a name="see-also"></a>Vea también
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
