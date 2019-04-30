---
title: IPropertyProxyEESide::GetManagedViewerCreationData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd92f8a93427264966bb44bbf44d5e519cb9459a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62914210"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Recupera información sobre el Visor para este tipo de propiedad con el fin de crear una instancia de dicho visor.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
   out string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     className,
   out enum_ASSEMBLYLOCRESOLUTION alr,
   out int                        replacementOk
);
```

#### <a name="parameters"></a>Parámetros
 `assemName`

 [out] Devuelve el nombre del ensamblado que contiene este objeto.

 `assemBytes`

 [out] Devuelve un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto que contiene los bytes del ensamblado de este objeto (este es un valor nulo si ningún byte está disponible).

 `assemPdb`

 [out] Devuelve un `IEEDataStorage` objeto que contiene el símbolo de almacena información de este objeto (este es un valor nulo si ningún almacén de símbolos está disponible).

 `className`

 [out] Devuelve el nombre de clase que contiene este objeto.

 `alr`

 [out] Devuelve un valor de la [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) enumeración que indica la ubicación del ensamblado.

 `replacementOk`

 [out] Devuelve cero (`TRUE`) si se puede cambiar el valor de este objeto; cero (`FALSE`) si el objeto es de solo lectura.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método se usa por los visualizadores de tipo para crear instancias de un visor administrado.

## <a name="see-also"></a>Vea también
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)