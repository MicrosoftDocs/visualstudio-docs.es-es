---
description: Determina si una interfaz específica está definida en la clase.
title: IDebugClassField::D oesInterfaceExist | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60a9a64e408f182476d6f34b19fea45f6fe8ad48
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085031"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Determina si una interfaz específica está definida en la clase.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT DoesInterfaceExist( 
   LPCOLESTR pszInterfaceName
);
```

```csharp
int DoesInterfaceExist(
   [In] string pszInterfaceName
);
```

## <a name="parameters"></a>Parámetros
`pszInterfaceName`\
de Cadena que contiene el nombre de interfaz que se va a buscar.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, Devuelve S_OK, devuelve S_FALSE si la interfaz no existe; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método en vigor obtiene una enumeración de todas las interfaces y busca en la lista una interfaz coincidente.

## <a name="see-also"></a>Consulte también
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
