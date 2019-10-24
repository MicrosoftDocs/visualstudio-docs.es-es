---
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f554485ae56a9d5f190c749879545165d299531c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742870"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Recupera los nombres de cadena correspondientes para los identificadores de propiedad especificados.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT ReadPropertyNames (
   ULONG         cpropid,
   PROPID const* rgpropid,
   BSTR*         rglpwstrName
);
```

#### <a name="parameters"></a>Parámetros
 `cpropid`

de Número de identificadores de propiedad en `rgpropid`.

 `rgpropid`

de Matriz de identificadores de propiedad para los que se van a obtener los nombres (`PROPID` se define en WTypes. h como `ULONG`).

 `rglpwstrName`

[in, out] Matriz de nombres de propiedad para los identificadores de propiedad especificados. La matriz debe estar asignada previamente para contener el número solicitado de nombres de propiedad y debe poder contener al menos `cpropid``BSTR` cadenas.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Los nombres de propiedad devueltos deben liberarse (llamando a la función `SysFreeString`) cuando ya no se necesiten.

## <a name="see-also"></a>Vea también
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)