---
title: IDiaDataSource::get_lastError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34954cd32b350a7c5f9c176deffd9943f8e05100
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554201"
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
Recupera el nombre de archivo para el último error de carga.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 pRetVal

[out] Devuelve una cadena que contiene el nombre del archivo .pdb asociado con el último error de carga.

## <a name="return-value"></a>Valor devuelto
 Devuelve el último código de error causado por una operación de carga. Devuelve `E_INVALIDARG` si el `pRetVal` parámetro es `NULL`.

## <a name="example"></a>Ejemplo

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>Vea también
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)