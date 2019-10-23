---
title: IDiaDataSource::openSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7dd6ab61db3e3bafd594298aa41d32bce64d4941
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744919"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Abre una sesión para consultar los símbolos.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT openSession ( 
   IDiaSession** ppSession
);
```

#### <a name="parameters"></a>Parámetros
ppSession

enuncia Devuelve un objeto [IDiaSession](../../debugger/debug-interface-access/idiasession.md) que representa la sesión abierta.

## <a name="return-value"></a>Valor devuelto
Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. En la tabla siguiente se muestran los posibles valores devueltos para este método.

|Valor|Descripción|
|-----------|-----------------|
|E_UNEXPECTED|El objeto [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) no se ha inicializado previamente con un origen de símbolos.|
|E_INVALIDARG|El parámetro `ppSession` no es válido.|
|E_OUTOFMEMORY|Memoria insuficiente para abrir la sesión.|

## <a name="remarks"></a>Comentarios
Este método abre un objeto [IDiaSession](../../debugger/debug-interface-access/idiasession.md) para un origen de datos.

`IDiaSession` objetos implementan consultas en el origen de datos. Una sesión administra un espacio de direcciones para cada conjunto de símbolos de depuración. Si el archivo. exe o. dll descrito por los símbolos del origen de datos está activo en varios intervalos de direcciones (por ejemplo, debido a que se han cargado varios procesos), se debe usar una sesión para cada intervalo de direcciones.

## <a name="example"></a>Ejemplo

```C++
IDiaSession* pSession;
HRESULT hr = pSource->openSession( &pSession );
if (FAILED(hr))
{
   // report error
}
```

## <a name="see-also"></a>Vea también
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [Información general](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
