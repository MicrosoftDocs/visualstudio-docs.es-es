---
title: POPLISTFUNC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c5f8c1683a993915476ff23f1f5d5f2c2aba462
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702064"
---
# <a name="poplistfunc"></a>POPLISTFUNC
El IDE proporciona esta devolución de llamada al [SccPopulateList](../extensibility/sccpopulatelist-function.md) y la usa el complemento de control de código fuente para actualizar una lista de archivos o directorios (también proporcionados a la `SccPopulateList` función).

 Cuando un usuario elige el comando **Get** en el IDE, el IDE muestra un cuadro de lista de todos los archivos que el usuario puede obtener. Desafortunadamente, el IDE no conoce la lista exacta de todos los archivos que el usuario podría obtener; solo el complemento tiene esta lista. Si otros usuarios han agregado archivos al proyecto de control de código fuente, estos archivos deben aparecer en la lista, pero el IDE no los conoce. El IDE crea una lista de los archivos que considera que el usuario puede obtener. Antes de que muestre esta lista al usuario, llama a [SccPopulateList](../extensibility/sccpopulatelist-function.md) , lo que `,` le permite agregar y eliminar archivos de la lista.

## <a name="signature"></a>Firma
 El complemento de control de código fuente modifica la lista mediante una llamada a una función implementada por el IDE con el siguiente prototipo:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Parámetros
 pvCallerData el `pvCallerData` parámetro pasado por el llamador (el IDE) al [SccPopulateList](../extensibility/sccpopulatelist-function.md). El complemento de control de código fuente no debe suponer nada sobre el contenido de este parámetro.

 fAddRemove si `TRUE` `lpFileName` es un archivo que se debe agregar a la lista de archivos. Si `FALSE` `lpFileName` es, es un archivo que se debe eliminar de la lista de archivos.

 Estado de nStatus de `lpFileName` (una combinación de `SCC_STATUS` bits; consulte el [código de estado de archivo](../extensibility/file-status-code-enumerator.md) para obtener más detalles).

 lpFileName ruta de acceso completa del directorio del nombre de archivo que se va a agregar o eliminar de la lista.

## <a name="return-value"></a>Valor devuelto

|Value|Descripción|
|-----------|-----------------|
|`TRUE`|El complemento puede seguir llamando a esta función.|
|`FALSE`|Se ha producido un problema en el lado del IDE (por ejemplo, una situación de memoria insuficiente). El complemento debe detener la operación.|

## <a name="remarks"></a>Observaciones
 Para cada archivo que el complemento de control de código fuente desea agregar o eliminar de la lista de archivos, llama a esta función, pasando el `lpFileName` . La `fAddRemove` marca indica un nuevo archivo que se va a agregar a la lista o a un archivo anterior que se va a eliminar. El `nStatus` parámetro proporciona el estado del archivo. Cuando el complemento SCC ha terminado de agregar y eliminar archivos, vuelve de la llamada a [SccPopulateList](../extensibility/sccpopulatelist-function.md) .

> [!NOTE]
> El `SCC_CAP_POPULATELIST` bit de capacidad es necesario para Visual Studio.

## <a name="see-also"></a>Consulte también
- [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Código de estado del archivo](../extensibility/file-status-code-enumerator.md)
