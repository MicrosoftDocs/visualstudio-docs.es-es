---
title: IDebugProgramHost2::GetHostName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 45919c6c9fafceecca2cb53fa9c2c9f43b68e382
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707424"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Obtiene el título, el nombre descriptivo o el nombre de archivo del proceso de hospedaje de este programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetHostName( 
   DWORD dwType,
   BSTR* pbstrHostName
);
```

```csharp
int GetHostName( 
   uint dwType,
   out string pbstrHostName
);
```

#### <a name="parameters"></a>Parámetros
 `dwType`

 [in] Un valor de la [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) enumeración.

 `pbstrHostName`

 [out] Devuelve el nombre del proceso de hospedaje solicitado.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 En una implementación típica de este método, el `dwType` parámetro se omite y se devuelve un nombre descriptivo de la máquina host. Otra posible implementación consiste en pasar el `dwType` parámetro a una llamada a la [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) método para obtener el nombre.

## <a name="see-also"></a>Vea también
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)