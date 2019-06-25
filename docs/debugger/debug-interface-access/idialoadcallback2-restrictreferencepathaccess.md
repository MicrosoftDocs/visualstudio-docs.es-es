---
title: IDiaLoadCallback2::RestrictReferencePathAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictReferencePathAccess method
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a39186cfc8fb3f83986692ebf7c608b895aae7ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839737"
---
# <a name="idialoadcallback2restrictreferencepathaccess"></a>IDiaLoadCallback2::RestrictReferencePathAccess
Determina si se permite la búsqueda de un archivo .pdb en la ruta de acceso donde se encuentra el archivo .exe.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT RestrictReferencePathAccess();
```

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Cualquier código de retorno distinto `S_OK` para evitar que busca un archivo .pdb en la ruta de acceso donde se encuentra el archivo .exe.

## <a name="see-also"></a>Vea también
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)