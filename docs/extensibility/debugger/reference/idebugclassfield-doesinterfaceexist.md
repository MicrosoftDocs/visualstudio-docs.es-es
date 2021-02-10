---
title: IDebugClassField::D oesInterfaceExist | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b7116b9e675605863805fb413340ea8b45ec608
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947117"
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

## <a name="remarks"></a>Notas
 Este método en vigor obtiene una enumeración de todas las interfaces y busca en la lista una interfaz coincidente.

## <a name="see-also"></a>Vea también
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
