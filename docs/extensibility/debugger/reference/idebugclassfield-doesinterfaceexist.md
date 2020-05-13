---
title: IDebugClassField::DoesInterfaceExist ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba732b698f7372772142fda73e71d9e22aa443a6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734499"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Determina si se define una interfaz específica en la clase.

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
[en] Cadena que contiene el nombre de la interfaz que se va a buscar.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK, devuelve S_FALSE si la interfaz no existe; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método en efecto obtiene una enumeración de todas las interfaces y busca en la lista una interfaz coincidente.

## <a name="see-also"></a>Vea también
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
