---
description: Obtiene una interfaz especificada a través de los límites del proceso.
title: 'IDebugProviderProgramNode2:: UnmarshalDebuggeeInterface | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42b51d93f9c0cec3a2ee74b2dfc0f4621c608c07
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083692"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Obtiene una interfaz especificada a través de los límites del proceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT UnmarshalDebuggeeInterface(
   REFIID riid,
   void** ppvObject
);
```

```csharp
int UnmarshalDebuggeeInterface(
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Parámetros
`riid`\
de GUID de la interfaz que se va a obtener.

`ppvObject`\
enuncia Devuelve el objeto que implementa la interfaz deseada. [C++] Esto se puede convertir directamente al tipo de interfaz deseado. [C#] Use el <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> método para obtener la interfaz deseada.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método se usa cuando el motor de depuración se está ejecutando en el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] espacio de proceso y el programa que se está depurando se ejecuta en su propio espacio de proceso.

## <a name="see-also"></a>Consulte también
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
