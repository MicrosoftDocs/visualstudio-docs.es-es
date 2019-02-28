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
ms.openlocfilehash: 6315032a36369eff7a5d43241ae4968a64ad42cc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685462"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Devuelve el bloque de datos PDATA asociado con la dirección virtual.

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

[in] Especifica la dirección virtual de los datos que se va a obtener.

 `cbData`

[in] El tamaño de datos en bytes para obtener.

 `pcbData`

[out] Devuelve el tamaño real de los datos en bytes que se obtuvo.

 `pbData`

[in, out] Un búfer que se rellena con los datos solicitados. El valor no puede ser `NULL`.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no hay ningún PDATA para la dirección especificada. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 PDATA (la sección denominada ".pdata") de una operación de compilación contiene información sobre el control de excepciones de funciones.

 El autor sabe es la cantidad de datos que se devuelve por lo que el llamador no tiene ninguna necesidad de solicitar la cantidad de datos está disponible. Por lo tanto, es aceptable para una implementación de este método para devolver un error si el `pbData` parámetro es `NULL`.

## <a name="see-also"></a>Vea también
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)