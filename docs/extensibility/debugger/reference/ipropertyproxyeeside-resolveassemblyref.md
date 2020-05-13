---
title: IPropertyProxyEESide::ResolveAssemblyRef ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c54945b0c89fb9608fab6aa70dcc63a7c6ae42df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714885"
---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
Determina la ubicación de la referencia de ensamblado administrado especificada.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT ResolveAssemblyRef(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  assemLocation,
   ASSEMBLYLOCRESOLUTION* alr
);
```

```csharp
int ResolveAssemblyRef(
   ref string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     assemLocation,
   out enum_ASSEMBLYLOCRESOLUTION alr
);
```

## <a name="parameters"></a>Parámetros
`assemName`\
[en] Nombre del ensamblado que se ha de resolver.

`assemBytes`\
[fuera] Devuelve un objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que contiene los bytes de ensamblado asociados a la referencia.

`assemPdb`\
[fuera] Devuelve `IEEDataStorage` un objeto que contiene los datos del almacén de símbolos asociados a esta referencia.

`assemLocation`\
[fuera] Devuelve la ubicación de la ruta de acceso de esta referencia.

`alr`\
[fuera] Devuelve un valor de la [assemblyLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) enumeración que indica la ubicación del ensamblado de esta referencia.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método normalmente no lo implementa un evaluador de expresiones personalizado.

## <a name="see-also"></a>Vea también
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
