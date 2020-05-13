---
title: POPLISTFUNC ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702064"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Esta devolución de llamada se proporciona a la [SccPopulateList](../extensibility/sccpopulatelist-function.md) por el IDE y se utiliza el complemento `SccPopulateList` de control de código fuente para actualizar una lista de archivos o directorios (también se proporciona a la función).

 Cuando un usuario elige el **get** comando en el IDE, el IDE muestra un cuadro de lista de todos los archivos que el usuario puede obtener. Desafortunadamente, el IDE no conoce la lista exacta de todos los archivos que el usuario puede obtener; solo el plug-in tiene esta lista. Si otros usuarios han agregado archivos al proyecto de control de código fuente, estos archivos deben aparecer en la lista, pero el IDE no conoce acerca de ellos. El IDE crea una lista de los archivos que cree que el usuario puede obtener. Antes de que muestre esta lista al usuario, llama a la [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` dando al complemento de control de código fuente la oportunidad de agregar y eliminar archivos de la lista.

## <a name="signature"></a>Signature
 El complemento de control de código fuente modifica la lista llamando a una función implementada por IDE con el siguiente prototipo:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Parámetros
 pvCallerData `pvCallerData` El parámetro pasado por el llamador (el IDE) a [SccPopulateList](../extensibility/sccpopulatelist-function.md). El complemento de control de código fuente debe asumir nada sobre el contenido de este parámetro.

 fAddRemove `TRUE`If `lpFileName` , es un archivo que se debe agregar a la lista de archivos. Si `FALSE` `lpFileName` , es un archivo que se debe eliminar de la lista de archivos.

 nEstado Estado `lpFileName` de (una `SCC_STATUS` combinación de los bits; consulte Código de [estado](../extensibility/file-status-code-enumerator.md) de archivo para obtener más información).

 lpFileName Ruta de acceso de directorio completa del nombre de archivo que se va a agregar o eliminar de la lista.

## <a name="return-value"></a>Valor devuelto

|Value|Descripción|
|-----------|-----------------|
|`TRUE`|El complemento puede seguir llamando a esta función.|
|`FALSE`|Ha habido un problema en el lado IDE (como una situación de memoria insuficiente). El plug-in debe detener el funcionamiento.|

## <a name="remarks"></a>Observaciones
 Para cada archivo que el complemento de control de código fuente desea agregar o eliminar `lpFileName`de la lista de archivos, llama a esta función, pasando el archivo . La `fAddRemove` marca indica un nuevo archivo para agregar a la lista o un archivo antiguo para eliminar. El `nStatus` parámetro proporciona el estado del archivo. Cuando el complemento SCC ha terminado de agregar y eliminar archivos, vuelve de la llamada [SccPopulateList.](../extensibility/sccpopulatelist-function.md)

> [!NOTE]
> El `SCC_CAP_POPULATELIST` bit de funcionalidad es necesario para Visual Studio.

## <a name="see-also"></a>Vea también
- [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Código de estado del archivo](../extensibility/file-status-code-enumerator.md)
