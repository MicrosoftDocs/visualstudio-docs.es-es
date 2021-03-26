---
description: Obtiene una lista de los elementos secundarios seleccionados de una referencia.
title: 'IDebugReference2:: EnumChildren | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::EnumChildren
helpviewer_keywords:
- IDebugReference2::EnumChildren
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92f55f511a68cca6685579eeb6d686108bf70799
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071459"
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
Obtiene una lista de los elementos secundarios seleccionados de una referencia. Reservado para uso futuro.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumChildren ( 
   DEBUGREF_INFO_FLAGS        dwFields,
   DWORD                      dwRadix,
   DBG_ATTRIB_FLAGS           dwAttribFilter,
   LPCOLESTR                  pszNameFilter,
   DWORD                      dwTimeout,
   IEnumDebugReferenceInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGREF_INFO_FLAGS     dwFields,
   uint                         dwRadix,
   enum_DBG_ATTRIB_FLAGS        dwAttribFilter,
   string                       pszNameFilter,
   uint                         dwTimeout,
   out IEnumDebugReferenceInfo2 ppEnum
);
```

## <a name="parameters"></a>Parámetros
`dwFields`\
de Combinación de marcas de la enumeración [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) que especifica los campos de las estructuras de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) enumeradas que se van a rellenar.

`dwRadix`\
de La base que se va a utilizar para dar formato a cualquier información numérica.

`dwAttribFilter`\
de Combinación de marcas de la enumeración [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) que se utiliza como filtro en combinación con el `pszNameFilter` parámetro para seleccionar las estructuras que se van a enumerar.

`pszNameFilter`\
de Cadena que especifica un filtro, como "MyX", que se usa en combinación con el `dwAttribFilter` parámetro para seleccionar las estructuras que se van a enumerar.

`dwTimeout`\
de Tiempo máximo, en milisegundos, que se va a esperar antes de que se devuelva desde este método. Use `INFINITE` para esperar indefinidamente.

`ppEnum`\
enuncia Devuelve un objeto [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) que contiene una lista de las propiedades secundarias solicitadas.

## <a name="return-value"></a>Valor devuelto
 Siempre devuelve `E_NOTIMPL`.

## <a name="see-also"></a>Consulte también
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
