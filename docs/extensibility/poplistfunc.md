---
title: POPLISTFUNC | Microsoft Docs
description: Obtenga información sobre la función de devolución de llamada POPLISTFUNC, que usa el complemento de control de código fuente para actualizar una lista de archivos o directorios.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b52ed40397793b44f8a9c7ed9c36aa5996ae0176
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900387"
---
# <a name="poplistfunc"></a>POPLISTFUNC
El IDE proporciona esta devolución de llamada a [SccPopulateList](../extensibility/sccpopulatelist-function.md) y la usa el complemento de control de código fuente para actualizar una lista de archivos o directorios (también proporcionados a la `SccPopulateList` función).

 Cuando un usuario elige el **comando Get** en el IDE, el IDE muestra un cuadro de lista de todos los archivos que el usuario puede obtener. Desafortunadamente, el IDE no conoce la lista exacta de todos los archivos que el usuario podría obtener. solo el complemento tiene esta lista. Si otros usuarios han agregado archivos al proyecto de control de código fuente, estos archivos deben aparecer en la lista, pero el IDE no los conoce. El IDE crea una lista de los archivos que cree que el usuario puede obtener. Antes de mostrar esta lista al usuario, llama a [SccPopulateList,](../extensibility/sccpopulatelist-function.md) lo que da al complemento de control de código fuente la oportunidad de agregar y eliminar archivos `,` de la lista.

## <a name="signature"></a>Firma
 El complemento de control de código fuente modifica la lista mediante una llamada a una función implementada por ide con el siguiente prototipo:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Parámetros
 pvCallerData El `pvCallerData` parámetro pasado por el autor de la llamada (el IDE) a [SccPopulateList](../extensibility/sccpopulatelist-function.md). El complemento de control de código fuente no debe suponer nada sobre el contenido de este parámetro.

 fAddRemove Si `TRUE` es , es un archivo que se debe agregar a la lista de `lpFileName` archivos. Si `FALSE` es , es un archivo que se debe eliminar de la lista de `lpFileName` archivos.

 nEstado de `lpFileName` estado de (una combinación de `SCC_STATUS` los bits; vea Código de estado [del archivo](../extensibility/file-status-code-enumerator.md) para obtener más información).

 lpFileName Ruta de acceso completa al directorio del nombre de archivo que se agregará o eliminará de la lista.

## <a name="return-value"></a>Valor devuelto

|Valor|Descripción|
|-----------|-----------------|
|`TRUE`|El complemento puede seguir llamando a esta función.|
|`FALSE`|Ha habido un problema en el lado del IDE (por ejemplo, una situación de memoria desaprobada). El complemento debe detener la operación.|

## <a name="remarks"></a>Observaciones
 Para cada archivo que el complemento de control de código fuente quiera agregar o eliminar de la lista de archivos, llama a esta función y pasa `lpFileName` . La `fAddRemove` marca indica un nuevo archivo que se agregará a la lista o un archivo antiguo que se eliminará. El `nStatus` parámetro proporciona el estado del archivo. Cuando el complemento SCC ha terminado de agregar y eliminar archivos, devuelve desde la [llamada a SccPopulateList.](../extensibility/sccpopulatelist-function.md)

> [!NOTE]
> El `SCC_CAP_POPULATELIST` bit de funcionalidad es necesario para Visual Studio.

## <a name="see-also"></a>Consulta también
- [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Código de estado del archivo](../extensibility/file-status-code-enumerator.md)
