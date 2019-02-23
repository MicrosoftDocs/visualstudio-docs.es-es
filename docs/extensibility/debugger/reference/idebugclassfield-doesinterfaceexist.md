---
title: IDebugClassField::DoesInterfaceExist | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7884bff62321ed07c3a11a6db65855b1edea0adc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688412"
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

#### <a name="parameters"></a>Parámetros
 `pszInterfaceName`

 [in] Una cadena que contiene el nombre de la interfaz que se busca.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK, devuelve S_FALSE si no existe la interfaz; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 En efecto, este método obtiene una enumeración de todas las interfaces y busca en la lista para una interfaz de búsqueda de coincidencias.

## <a name="see-also"></a>Vea también
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)