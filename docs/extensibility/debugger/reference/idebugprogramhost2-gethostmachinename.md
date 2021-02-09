---
title: 'IDebugProgramHost2:: GetHostMachineName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramHost2::GetHostMachineName
ms.assetid: 4677ffe4-aa9b-4450-a63b-74cd3984d956
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 575481951ffb662452d5cb6635f91bfb11ea6432
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898761"
---
# <a name="idebugprogramhost2gethostmachinename"></a>IDebugProgramHost2::GetHostMachineName
Obtiene el nombre del equipo en el que se está ejecutando el proceso que hospeda este programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetHostMachineName( 
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName( 
   out string pbstrHostMachineName
);
```

## <a name="parameters"></a>Parámetros
`pbstrHostMachineName`\
enuncia Devuelve el nombre de la máquina.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
