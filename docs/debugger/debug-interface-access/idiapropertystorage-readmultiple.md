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
ms.openlocfilehash: 0ec66de4feea1a59ca1ef71f48bae49ed5ac2232
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708815"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Lee especificado las propiedades desde el conjunto de propiedades actual.

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

[in] Recuento de las propiedades especificadas en el `rgpspec` matriz. Si es cero, el método no devuelve ninguna propiedad, pero devolver `S_OK` como un código correcto.

 `rgpspec`

[in] Una matriz de propiedades que se va a leer. Propiedades pueden especificarse un identificador de propiedad o un nombre de cadena opcional. No es necesario especificar las propiedades en ningún orden concreto de la matriz. La matriz puede contener propiedades duplicadas, lo que resulta en valores de propiedad duplicados en la devolución de propiedades sencillas. Las propiedades de la simple no deberían devolver ha denegado el acceso en un intento para abrirlos en una segunda vez. La matriz puede contener una combinación de identificadores de propiedad y los identificadores de cadena. Esta matriz debe tener al menos `cpspec` número de valores de propiedad.

 `rgvar`

[in, out] Una matriz de `PROPVARIANT` estructuras (en el espacio de nombres de ensamblados Microsoft.VisualStudio.OLE.Interop) que se rellena con los valores para cada propiedad. La matriz debe ser al menos `cpspec` elementos de tamaño. El llamador no necesita inicializar los valores de la matriz.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se encontraron una o varias de las propiedades. En caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Si una propiedad no se encontró, la entrada correspondiente en el `rgvar` matriz contiene un `VARIANT` con el tipo de `VT_EMPTY`.

## <a name="see-also"></a>Vea también
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)