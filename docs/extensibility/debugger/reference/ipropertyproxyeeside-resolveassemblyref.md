---
description: Determina la ubicación de la referencia de ensamblado administrado especificada.
title: 'IPropertyProxyEESide:: ResolveAssemblyRef | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 03df51a5c229f5fd3a5cc5ea8f35c8ecaa9e2da7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082389"
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
de Nombre del ensamblado que se va a resolver.

`assemBytes`\
enuncia Devuelve un objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que contiene los bytes de ensamblado asociados a la referencia.

`assemPdb`\
enuncia Devuelve un `IEEDataStorage` objeto que contiene los datos del almacén de símbolos asociados a esta referencia.

`assemLocation`\
enuncia Devuelve la ubicación de la ruta de acceso de esta referencia.

`alr`\
enuncia Devuelve un valor de la enumeración [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) que indica la ubicación del ensamblado de esta referencia.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Normalmente, el evaluador de expresiones personalizadas no implementa este método.

## <a name="see-also"></a>Consulte también
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
