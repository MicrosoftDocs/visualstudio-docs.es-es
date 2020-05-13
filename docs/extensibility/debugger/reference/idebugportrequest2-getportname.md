---
title: IDebugPortRequest2::GetPortName ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67121e98f2d506aa16c2b4dc3fff2ad5128fb93b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724811"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Obtiene el nombre del puerto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPortName( 
   BSTR* pbstrPortName
);
```

```csharp
int GetPortName( 
   out string pbstrPortName
);
```

## <a name="parameters"></a>Parámetros
`pbstrPortName`\
[fuera] Devuelve el nombre del puerto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) interfaz normalmente se pasa de un paquete de depuración (el cliente) a un proveedor de puertos (el servidor) para obtener una conexión a un puerto. Tanto el paquete de depuración como el proveedor de puertos son conscientes de las opciones posibles para el puerto. Si una cadena simple puede describir `IDebugPortRequest2::GetPortName` el puerto, el método tiene suficiente información para realizar la conexión. De lo contrario, el cliente puede proporcionar interfaces adicionales, `IDebugPortRequest2::QueryInterface`que pueden obtener el servidor mediante .

## <a name="see-also"></a>Vea también
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
