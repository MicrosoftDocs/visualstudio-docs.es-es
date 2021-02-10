---
title: POPDIRLISTFUNC | Microsoft Docs
description: Obtenga información sobre la función de devolución de llamada POPDIRLISTFUNC, que se pasa a los directorios de actualización para averiguar cuáles están bajo control de código fuente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: da499ee9bbdcdff95456a4e4d5f5dc63f2acfb2c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967402"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Se trata de una función de devolución de llamada proporcionada a la función [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) para actualizar una colección de directorios y (opcionalmente) nombres de archivo para averiguar cuáles están bajo control de código fuente.

 `POPDIRLISTFUNC`Solo se debe llamar a la devolución de llamada para esos directorios y nombres de archivo (en la lista proporcionada a la `SccPopulateDirList` función) que realmente están bajo control de código fuente.

## <a name="signature"></a>Firma

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>Parámetros
 pvCallerData

de Valor de usuario dado a [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bFolder

[in] `TRUE` Si el nombre de `lpDirectoryOrFileName` es un directorio; de lo contrario, el nombre es un nombre de archivo.

 lpDirectoryOrFileName

de Ruta de acceso local completa a un directorio o nombre de archivo que se encuentra bajo control de código fuente.

## <a name="return-value"></a>Valor devuelto
 El IDE devuelve un código de error adecuado:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Continúe el procesamiento.|
|SCC_I_OPERATIONCANCELED|Detiene el procesamiento.|
|SCC_E_xxx|Cualquier error de control de código fuente adecuado debe detener el procesamiento.|

## <a name="remarks"></a>Notas
 Si el `fOptions` parámetro de la `SccPopulateDirList` función contiene la `SCC_PDL_INCLUDEFILES` marca, la lista posiblemente contendrá nombres de archivo y nombres de directorio.

## <a name="see-also"></a>Vea también
- [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Códigos de error](../extensibility/error-codes.md)
