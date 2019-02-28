---
title: IDiaLoadCallback2::RestrictOriginalPathAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26539d4217682b4d5357f13e9f9368c81297da78
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635753"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Determina si es correcto buscar un archivo .pdb en el directorio de depuración original.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT RestrictOriginalPathAccess ();
```

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Cualquier código de retorno distinto `S_OK` impide que busca un archivo .pdb en el directorio de depuración original. El directorio de depuración original es la ruta de acceso para el archivo de símbolos que se compilan en el archivo ejecutable cuando se activa la depuración. Esta ruta de acceso no es necesariamente el mismo que la ruta de acceso donde existe el archivo ejecutable.

## <a name="see-also"></a>Vea también
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)