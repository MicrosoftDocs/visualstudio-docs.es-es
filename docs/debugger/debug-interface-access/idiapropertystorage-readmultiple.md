---
title: IDiaPropertyStorage::ReadMultiple | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cd1e419e1d08120274fc627a672eb52331ca50f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742884"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Lee las propiedades especificadas del conjunto de propiedades actual.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT ReadMultiple( 
   ULONG          cpspec,
   PROPSPEC const rgpspec,
   PROPVARIANT    rgvar
);
```

#### <a name="parameters"></a>Parámetros
 `cpspec`

de Recuento de propiedades especificadas en la matriz de `rgpspec`. Si es cero, el método no devuelve ninguna propiedad, pero devuelve `S_OK` como un código de operación correcta.

 `rgpspec`

de Matriz de propiedades que se van a leer. Las propiedades se pueden especificar mediante un identificador de propiedad o un nombre de cadena opcional. No es necesario especificar propiedades en ningún orden concreto de la matriz. La matriz puede contener propiedades duplicadas, por lo que los valores de propiedad duplicados se devuelven para propiedades simples. Las propiedades no simples deben devolver acceso denegado al intentar abrirlas una segunda vez. La matriz puede contener una combinación de identificadores de propiedad y de cadena. Esta matriz debe tener al menos `cpspec` número de valores de propiedad.

 `rgvar`

[in, out] Matriz de estructuras `PROPVARIANT` (en el espacio de nombres Microsoft. VisualStudio. OLE. Interop) que se va a rellenar con valores para cada propiedad. La matriz debe ser al menos `cpspec` elementos de tamaño. El autor de la llamada no necesita inicializar los valores de la matriz.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se encontró una o varias de las propiedades. En caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Si no se encuentra una propiedad, la entrada correspondiente en la matriz de `rgvar` contiene un `VARIANT` con el tipo de `VT_EMPTY`.

## <a name="see-also"></a>Vea también
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)