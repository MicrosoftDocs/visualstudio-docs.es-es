---
title: IDiaSession::findFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9751127007b4e7823cf6d2ae35ed2fe80cb83b8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742279"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Recupera los archivos de código fuente mediante la operación de compilación y nombre.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT findFile ( 
   IDiaSymbol*           pCompiland,
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSourceFiles** ppResult
);
```

#### <a name="parameters"></a>Parámetros
 `pCompiland`

de Objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa la operación de compilación que se va a usar como contexto de la búsqueda. Establezca este parámetro en `NULL` para buscar archivos de código fuente en todos los compilandos.

 `name`

de Especifica el nombre del archivo de código fuente que se va a recuperar. Establezca este parámetro en `NULL` para todos los archivos de origen que se van a recuperar.

 `option`

de Especifica las opciones de comparación aplicadas a la búsqueda de nombres. Los valores de la enumeración [namesearchoptions (](../../debugger/debug-interface-access/namesearchoptions.md) se pueden usar solos o en combinación.

 `ppResult`

enuncia Devuelve un objeto [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) que contiene una lista de los archivos de código fuente recuperados.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo

```C++
IDiaEnumSourceFiles* pEnum;
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );
```

## <a name="see-also"></a>Vea también
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeración NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)