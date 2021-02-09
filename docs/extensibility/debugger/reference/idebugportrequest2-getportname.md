---
title: 'IDebugPortRequest2:: GetPortName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 574ea2ecb69c944bdb47ff80d7b4e26db51933da
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887164"
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
enuncia Devuelve el nombre del puerto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 La interfaz [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) normalmente se pasa desde un paquete de depuración (el cliente) a un proveedor de puerto (el servidor) para obtener una conexión a un puerto. Tanto el paquete de depuración como el proveedor del puerto reconocen las posibles opciones para el puerto. Si una cadena simple puede describir el puerto, el `IDebugPortRequest2::GetPortName` método tiene información suficiente para establecer la conexión. De lo contrario, el cliente puede proporcionar otras interfaces, que puede obtener el servidor mediante `IDebugPortRequest2::QueryInterface` .

## <a name="see-also"></a>Vea también
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
