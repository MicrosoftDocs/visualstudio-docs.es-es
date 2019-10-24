---
title: IDiaStackWalkHelper::pdataForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d51736a80021847881db164c9e176a010124638
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741400"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Devuelve el bloque de datos de PDATA asociado a la dirección virtual.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT pdataForVA( 
   ULONGLONG  va,
   DWORD      cbData,
   DWORD*     pcbData,
   BYTE*      pbData
);
```

#### <a name="parameters"></a>Parámetros
 `va`

de Especifica la dirección virtual de los datos que se van a obtener.

 `cbData`

de Tamaño de los datos en bytes que se van a obtener.

 `pcbData`

enuncia Devuelve el tamaño real de los datos en bytes obtenidos.

 `pbData`

[in, out] Búfer que se rellena con los datos solicitados. El valor no puede ser `NULL`.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no hay ningún PDATA para la dirección especificada. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 PDATA (la sección denominada ". PDATA") de una operación de compilación contiene información sobre el control de excepciones para las funciones.

 El autor de la llamada sabe cuántos datos se van a devolver, por lo que el autor de la llamada no tiene necesidad de solicitar la cantidad de datos disponibles. Por lo tanto, es aceptable que una implementación de este método devuelva un error si el parámetro `pbData` es `NULL`.

## <a name="see-also"></a>Vea también
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)