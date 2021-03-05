---
description: Obtiene el título, el nombre descriptivo o el nombre de archivo del proceso de hospedaje de este programa.
title: 'IDebugProgramHost2:: GetHostName (| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4574bee7fb5a7f3ed125a73361de6fc9c3bcbfc2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149527"
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

## <a name="parameters"></a>Parámetros
`dwType`\
de Un valor de la enumeración [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) .

`pbstrHostName`\
enuncia Devuelve el nombre solicitado del proceso de hospedaje.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 En una implementación típica de este método, el `dwType` parámetro se omite y se devuelve un nombre descriptivo del equipo host. Otra posible implementación es pasar el `dwType` parámetro a una llamada al método [GetHostName (](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) para obtener el nombre.

## <a name="see-also"></a>Consulte también
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
