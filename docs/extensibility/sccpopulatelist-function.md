---
title: Función SccPopulateList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a2cfdf5a617352d7ba0c2db00e7705343f1eb5e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720868"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList (Función)
Esta función actualiza una lista de archivos para un comando de control de código fuente determinado y proporciona el estado del control de código fuente en todos los archivos especificados.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccPopulateList (
   LPVOID          pvContext,
   enum SCCCOMMAND nCommand,
   LONG            nFiles,
   LPCSTR*         lpFileNames,
   POPLISTFUNC     pfnPopulate,
   LPVOID          pvCallerData,
   LPLONG          lpStatus,
   LONG            fOptions
);
```

#### <a name="parameters"></a>Parámetros
 pvContext

de Estructura de contexto del complemento de control de código fuente.

 nlínea

de Comando de control de código fuente que se aplicará a todos los archivos de la matriz de `lpFileNames` (vea el [código de comando](../extensibility/command-code-enumerator.md) para obtener una lista de los comandos posibles).

 N archivos

de Número de archivos de la matriz de `lpFileNames`.

 lpFileNames

de Matriz de nombres de archivo que conoce el IDE.

 pfnPopulate

de Función de devolución de llamada IDE a la que se llama para agregar y quitar archivos (vea [POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más información).

 pvCallerData

de Valor que se va a pasar sin cambiar a la función de devolución de llamada.

 lpStatus

[in, out] Una matriz para el complemento de control de código fuente para devolver las marcas de estado de cada archivo.

 Opciones

de Marcas de comandos (consulte la sección "PopulateList flag" de [marcadores que usan los comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) para obtener más detalles).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Correcto.|
|SCC_E_NONSPECIFICERROR|Error no específico.|

## <a name="remarks"></a>Comentarios
 Esta función examina la lista de archivos en busca de su estado actual. Usa la función de devolución de llamada `pfnPopulate` para notificar al autor de la llamada cuando un archivo no coincide con los criterios de la `nCommand`. Por ejemplo, si el comando se `SCC_COMMAND_CHECKIN` y no se desprotege un archivo de la lista, la devolución de llamada se usa para informar al llamador. En ocasiones, el complemento de control de código fuente puede encontrar otros archivos que pueden formar parte del comando y agregarlos. Esto permite, por ejemplo, que un usuario de Visual Basic desproteja un archivo. bmp utilizado por su proyecto, pero que no aparece en el archivo de proyecto de Visual Basic. Un usuario elige el comando **Get** en el IDE. El IDE mostrará una lista de todos los archivos que considera que el usuario puede obtener, pero antes de que se muestre la lista, se llama a la función `SccPopulateList` para asegurarse de que la lista que se va a mostrar está actualizada.

## <a name="example"></a>Ejemplo
 El IDE crea una lista de los archivos que considera que el usuario puede obtener. Antes de que se muestre esta lista, llama a la función `SccPopulateList`, lo que permite que el complemento de control de código fuente tenga la oportunidad de agregar y eliminar archivos de la lista. El complemento modifica la lista mediante una llamada a la función de devolución de llamada dada (vea [POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más detalles).

 El complemento sigue llamando a la función `pfnPopulate`, que agrega y elimina archivos, hasta que termina y, a continuación, vuelve de la función `SccPopulateList`. Después, el IDE puede mostrar la lista. La matriz de `lpStatus` representa todos los archivos de la lista original pasados por el IDE. El complemento rellena el estado de todos estos archivos, además de hacer uso de la función de devolución de llamada.

> [!NOTE]
> Un complemento de control de código fuente siempre tiene la opción de devolver inmediatamente desde esta función, lo que sale de la lista. Si un complemento implementa esta función, puede indicarlo estableciendo el indicador de bits de capacidad de `SCC_CAP_POPULATELIST` en la primera llamada a [SccInitialize](../extensibility/sccinitialize-function.md). De forma predeterminada, el complemento siempre debe suponer que todos los elementos que se pasan son archivos. Sin embargo, si el IDE establece la marca `SCC_PL_DIR` en el parámetro `fOptions`, todos los elementos que se pasan se consideran directorios. El complemento debe agregar todos los archivos que pertenecen a los directorios. El IDE nunca pasará una mezcla de archivos y directorios.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
- [Código de comando](../extensibility/command-code-enumerator.md)