---
description: Esta función actualiza una lista de archivos para un comando de control de código fuente determinado y proporciona el estado de control de código fuente en todos los archivos dados.
title: SccPopulateList (Función) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b386c576b48e14b6118f62d451c42ac20f048b45
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902350"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList (Función)
Esta función actualiza una lista de archivos para un comando de control de código fuente determinado y proporciona el estado de control de código fuente en todos los archivos dados.

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

[in] Estructura de contexto del complemento de control de código fuente.

 nCommand

[in] El comando de control de código fuente que se aplicará a todos los archivos de la matriz `lpFileNames` (vea [Código de comando](../extensibility/command-code-enumerator.md) para obtener una lista de posibles comandos).

 nFiles

[in] Número de archivos de la `lpFileNames` matriz.

 lpFileNames

[in] Matriz de nombres de archivo conocidos por el IDE.

 pfnPopulate

[in] Función de devolución de llamada ide para llamar a para agregar y quitar archivos [(vea POPLISTFUNC para](../extensibility/poplistfunc.md) obtener más información).

 pvCallerData

[in] Valor que se va a pasar sin cambios a la función de devolución de llamada.

 lpStatus

[in, out] Matriz para que el complemento de control de código fuente devuelva las marcas de estado de cada archivo.

 fOptions

[in] Marcas de comandos (consulte la sección "Marca populateList" de [Marcas de bits usadas](../extensibility/bitflags-used-by-specific-commands.md) por comandos específicos para obtener más información).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Correcto.|
|SCC_E_NONSPECIFICERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 Esta función examina la lista de archivos para ver su estado actual. Usa la función de devolución de llamada para notificar al autor de la llamada cuando un `pfnPopulate` archivo no coincide con los criterios de `nCommand` . Por ejemplo, si el comando es y no se desprotegía un archivo de la lista, la devolución de llamada `SCC_COMMAND_CHECKIN` se usa para informar al autor de la llamada. En ocasiones, el complemento de control de código fuente puede encontrar otros archivos que podrían formar parte del comando y agregarlos. Esto permite, por ejemplo, que un usuario de Visual Basic compruebe un archivo .bmp que usa su proyecto, pero que no aparece en el archivo Visual Basic proyecto. Un usuario elige el **comando Get** en el IDE. El IDE mostrará una lista de todos los archivos que cree que el usuario puede obtener, pero antes de mostrar la lista, se llama a la función para asegurarse de que la lista que se va a mostrar esté `SccPopulateList` actualizada.

## <a name="example"></a>Ejemplo
 El IDE crea una lista de archivos que cree que el usuario puede obtener. Antes de mostrar esta lista, llama a la función , lo que ofrece al complemento de control de código fuente la oportunidad de agregar y `SccPopulateList` eliminar archivos de la lista. El complemento modifica la lista llamando a la función de devolución de llamada determinada [(vea POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más detalles).

 El complemento sigue llamada a la función , que agrega y elimina archivos, hasta que finaliza y, a `pfnPopulate` continuación, vuelve de la `SccPopulateList` función. A continuación, el IDE puede mostrar su lista. La `lpStatus` matriz representa todos los archivos de la lista original que pasa el IDE. El complemento rellena el estado de todos estos archivos además de usar la función de devolución de llamada.

> [!NOTE]
> Un complemento de control de código fuente siempre tiene la opción de simplemente volver inmediatamente de esta función, dejando la lista tal como está. Si un complemento implementa esta función, puede indicarlo estableciendo la característica bitflag en la primera llamada `SCC_CAP_POPULATELIST` a [SccInitialize.](../extensibility/sccinitialize-function.md) De forma predeterminada, el complemento siempre debe suponer que todos los elementos que se pasan son archivos. Sin embargo, si el IDE establece la marca en el parámetro , todos los elementos que se pasan se `SCC_PL_DIR` `fOptions` considerarán directorios. El complemento debe agregar todos los archivos que pertenecen a los directorios. El IDE nunca pasará una combinación de archivos y directorios.

## <a name="see-also"></a>Consulta también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
- [Código de comando](../extensibility/command-code-enumerator.md)
