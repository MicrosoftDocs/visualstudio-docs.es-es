---
title: IPropertyProxyEESide::InitSourceDataProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 05f5987037e63c3c81585ba51deed72f06fd3278
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461084"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
Inicializa los datos de origen para este objeto y devuelve un objeto que contiene los datos iniciales.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT InitSourceDataProvider(
   IEEDataStorage** dataOut
);
```

```csharp
int InitSourceDataProvider(
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parámetros
 `dataOut`\

 [out] Devuelve un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método no hace todo lo que es necesario para inicializar un objeto, por lo que puede devolver un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) interfaz en los datos del objeto. Esto permite que los datos del objeto se pueden ver y, si permite, puede cambiar por un visualizador de tipo.

## <a name="see-also"></a>Vea también
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)