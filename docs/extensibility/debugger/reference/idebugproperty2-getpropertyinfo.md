---
description: Obtiene la estructura de DEBUG_PROPERTY_INFO que describe una propiedad.
title: 'IDebugProperty2:: GetPropertyInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetPropertyInfo
helpviewer_keywords:
- IDebugProperty2::GetPropertyInfo
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: deb8dbe5b055f42f21c087dcb2cc7a14e16858f9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166781"
---
# <a name="idebugproperty2getpropertyinfo"></a>IDebugProperty2::GetPropertyInfo
Obtiene la estructura de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) que describe una propiedad.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPropertyInfo ( 
   DEBUGPROP_INFO_FLAGS dwFields,
   DWORD                nRadix,
   DWORD                dwTimeout,
   IDebugReference2**   rgpArgs,
   DWORD                dwArgCount,
   DEBUG_PROPERTY_INFO* pPropertyInfo
);
```

```cpp
int GetPropertyInfo ( 
   enum_DEBUGPROP_INFO_FLAGS dwFields,
   uint                      nRadix,
   uint                      dwTimeout,
   IDebugReference2[]        rgpArgs,
   uint                      dwArgCount,
   DEBUG_PROPERTY_INFO[]     pPropertyInfo
);
```

## <a name="parameters"></a>Parámetros
`dwFields`\
de Combinación de valores de la enumeración [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) que especifica los campos que se van a rellenar en la `pPropertyInfo` estructura.

`nRadix`\
de Base que se va a utilizar para dar formato a cualquier información numérica.

`dwTimeout`\
de Especifica el tiempo máximo, en milisegundos, que se va a esperar antes de que se devuelva desde este método. Use `INFINITE` para esperar indefinidamente.

`rgpArgs`\
[in, out] Reservado para uso futuro; establecer en un valor null.

`dwArgCount`\
de Reservado para uso futuro; se establece en cero.

`pPropertyInfo`\
enuncia [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estructura que se rellena con la descripción de la propiedad.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error.

## <a name="see-also"></a>Consulte también
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
