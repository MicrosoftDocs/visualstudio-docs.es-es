---
title: POPDIRLISTFUNC ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52a0c16af0e142bda8527c5244a22e0830ced9e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702079"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Se trata de una función de devolución de llamada dada a la [función SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) para actualizar una colección de directorios y (opcionalmente) nombres de archivo para averiguar cuáles están bajo control de código fuente.

 La `POPDIRLISTFUNC` devolución de llamada debe llamarse solo para los directorios y nombres de archivo (en la lista dada a la `SccPopulateDirList` función) que realmente están bajo control de código fuente.

## <a name="signature"></a>Signature

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>Parámetros
 pvCallerData

[en] Valor de usuario dado a [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bCarpeta

[en] `TRUE` si el `lpDirectoryOrFileName` nombre en es un directorio; de lo contrario, el nombre es un nombre de archivo.

 lpDirectoryOrFileName

[en] Ruta de acceso local completa a un directorio o nombre de archivo que está bajo control de código fuente.

## <a name="return-value"></a>Valor devuelto
 El IDE devuelve un código de error adecuado:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Continúe el procesamiento.|
|SCC_I_OPERATIONCANCELED|Detiene el procesamiento.|
|SCC_E_xxx|Cualquier error de control de código fuente adecuado debe detener el procesamiento.|

## <a name="remarks"></a>Observaciones
 Si `fOptions` el parámetro `SccPopulateDirList` de `SCC_PDL_INCLUDEFILES` la función contiene la marca, la lista posiblemente contendrá nombres de archivo, así como nombres de directorio.

## <a name="see-also"></a>Vea también
- [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Códigos de error](../extensibility/error-codes.md)
