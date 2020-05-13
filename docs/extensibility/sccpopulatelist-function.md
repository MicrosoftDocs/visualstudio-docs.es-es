---
title: Función SccPopulateList (SccPopulateList) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f518413adba1546bcff4f7cf2e62b4563cf1bcc7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700528"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList (Función)
Esta función actualiza una lista de archivos para un comando de control de código fuente determinado y proporciona el estado de control de código fuente en todos los archivos determinados.

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

[en] La estructura de contexto del complemento de control de código fuente.

 nCommand

[en] El comando de control de código fuente `lpFileNames` que se aplicará a todos los archivos de la matriz (consulte Código de [comandos](../extensibility/command-code-enumerator.md) para obtener una lista de posibles comandos).

 nArchivos

[en] Número de archivos `lpFileNames` de la matriz.

 lpFileNames

[en] Matriz de nombres de archivo conocidos por el IDE.

 pfnPopulate

[en] La función de devolución de llamada IDE para llamar para agregar y quitar archivos (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más información).

 pvCallerData

[en] Valor que se va a pasar sin cambios a la función de devolución de llamada.

 lpStatus

[adentro, fuera] Matriz para que el complemento de control de código fuente devuelva los indicadores de estado de cada archivo.

 fOptions

[en] Indicadores de comando (consulte la sección "PopulateList flag" de [Bitflags Used by Specific Commands](../extensibility/bitflags-used-by-specific-commands.md) para obtener más información).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Correcto.|
|SCC_E_NONSPECIFICERROR|Fallo inespecífico.|

## <a name="remarks"></a>Observaciones
 Esta función examina la lista de archivos para su estado actual. Utiliza la `pfnPopulate` función de devolución de llamada para notificar `nCommand`al autor de la llamada cuando un archivo no coincide con los criterios para el archivo . Por ejemplo, si `SCC_COMMAND_CHECKIN` el comando es y un archivo de la lista no está desprotegido, la devolución de llamada se utiliza para informar al autor de la llamada. Ocasionalmente, el complemento de control de código fuente puede encontrar otros archivos que podrían formar parte del comando y agregarlos. Esto permite, por ejemplo, que un usuario de Visual Basic desproteger un archivo .bmp que usa su proyecto pero no aparece en el archivo de proyecto de Visual Basic. Un usuario elige el **comando Get** en el IDE. El IDE mostrará una lista de todos los archivos que cree que el `SccPopulateList` usuario puede obtener, pero antes de que se muestre la lista, se llama a la función para asegurarse de que la lista que se va a mostrar está actualizada.

## <a name="example"></a>Ejemplo
 El IDE crea una lista de archivos que cree que el usuario puede obtener. Antes de que muestre esta `SccPopulateList` lista, llama a la función, dando al complemento de control de código fuente la oportunidad de agregar y eliminar archivos de la lista. El complemento modifica la lista llamando a la función de devolución de llamada dada (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más detalles).

 El complemento continúa llamando a `pfnPopulate` la función, que agrega y elimina archivos, hasta `SccPopulateList` que finaliza y, a continuación, vuelve de la función. A continuación, el IDE puede mostrar su lista. La `lpStatus` matriz representa todos los archivos de la lista original que pasa el IDE. El complemento rellena el estado de todos estos archivos además de hacer uso de la función de devolución de llamada.

> [!NOTE]
> Un complemento de control de código fuente siempre tiene la opción de simplemente volver inmediatamente desde esta función, dejando la lista tal como está. Si un complemento implementa esta función, puede indicarlo estableciendo el `SCC_CAP_POPULATELIST` bitflag de capacidad en la primera llamada a [SccInitialize](../extensibility/sccinitialize-function.md). De forma predeterminada, el complemento siempre debe suponer que todos los elementos que se pasan son archivos. Sin embargo, si `SCC_PL_DIR` el IDE establece la marca en el `fOptions` parámetro, todos los elementos que se pasan deben considerarse directorios. El complemento debe agregar todos los archivos que pertenecen a los directorios. El IDE nunca pasará una mezcla de archivos y directorios.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
- [Código de comando](../extensibility/command-code-enumerator.md)
