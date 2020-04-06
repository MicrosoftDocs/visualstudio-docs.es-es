---
title: IDebugReference2::EnumChildren ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::EnumChildren
helpviewer_keywords:
- IDebugReference2::EnumChildren
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 96b2fec782ce88dfb2200df35f56b35b304beda5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720623"
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
Obtener una lista de los elementos secundarios seleccionados de una referencia. Reservado para uso futuro.

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
[en] Una combinación de indicadores de la [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) enumeración que especifica qué campos de las estructuras [de DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) enumeradas se deben rellenar.

`dwRadix`\
[en] El radio que se utilizará para dar formato a cualquier información numérica.

`dwAttribFilter`\
[en] Una combinación de indicadores de la [enumeración](../../../extensibility/debugger/reference/dbg-attrib-flags.md) DBG_ATTRIB_FLAGS `pszNameFilter` que se utiliza como filtro en combinación con el parámetro para seleccionar qué estructuras se van a enumerar.

`pszNameFilter`\
[en] Cadena que especifica un filtro, como "MyX", `dwAttribFilter` que se utiliza en combinación con el parámetro para seleccionar las estructuras que se van a enumerar.

`dwTimeout`\
[en] Tiempo máximo, en milisegundos, para esperar antes de volver de este método. Se `INFINITE` usa para esperar indefinidamente.

`ppEnum`\
[fuera] Devuelve un [objeto IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) que contiene una lista de las propiedades secundarias solicitadas.

## <a name="return-value"></a>Valor devuelto
 Siempre devuelve `E_NOTIMPL`.

## <a name="see-also"></a>Vea también
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
