---
description: Recupera información sobre el visor para este tipo de propiedad con el fin de crear instancias del visor.
title: 'IPropertyProxyEESide:: GetManagedViewerCreationData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f2d7d4ef3f35cb0ad00f91033213449af8cb7306
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224140"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Recupera información sobre el visor para este tipo de propiedad con el fin de crear instancias del visor.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
   out string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     className,
   out enum_ASSEMBLYLOCRESOLUTION alr,
   out int                        replacementOk
);
```

## <a name="parameters"></a>Parámetros
`assemName`\
enuncia Devuelve el nombre del ensamblado que contiene este objeto.

`assemBytes`\
enuncia Devuelve un objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que contiene los bytes de ensamblado de este objeto (es un valor NULL si no hay ningún byte disponible).

`assemPdb`\
enuncia Devuelve un `IEEDataStorage` objeto que contiene la información del almacén de símbolos para este objeto (es un valor NULL si no hay ningún almacén de símbolos disponible).

`className`\
enuncia Devuelve el nombre de clase que contiene este objeto.

`alr`\
enuncia Devuelve un valor de la enumeración [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) que indica la ubicación del ensamblado.

`replacementOk`\
enuncia Devuelve un valor distinto `TRUE` de cero () si el valor de este objeto se puede cambiar; cero ( `FALSE` ) si el objeto es de solo lectura.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Los visualizadores de tipos usan este método para crear instancias de un visor administrado.

## <a name="see-also"></a>Consulte también
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
