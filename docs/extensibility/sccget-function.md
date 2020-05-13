---
title: Función SccGet (SccGet) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2d69308d2f569fc2e0d72dcf64c762687955d4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700900"
---
# <a name="sccget-function"></a>Función SccGet
Esta función recupera una copia de uno o más archivos para ver los archivos, pero no para editarlos. En la mayoría de los sistemas, los archivos se etiquetan como de solo lectura.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccGet(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parámetros
 pvContext

[en] La estructura de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 nArchivos

[en] Número de archivos especificados en la `lpFileNames` matriz.

 lpFileNames

[en] Matriz de nombres completos de los archivos que se van a recuperar.

 fOptions

[en] Indicadores`SCC_GET_ALL`de `SCC_GET_RECURSIVE`comando ( , ).

 pvOptions

[en] Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|El éxito de conseguir la operación.|
|SCC_E_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|
|SCC_E_FILEISCHECKEDOUT|No se puede obtener el archivo que el usuario ha traído actualmente.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NOSPECIFIEDVERSION|Se ha especificado una versión no válida o una fecha/hora.|
|SCC_E_NONSPECIFICERROR|Error inespecífico; archivo no se sincronizó.|
|SCC_I_OPERATIONCANCELED|Operación cancelada antes de la finalización.|
|SCC_E_NOTAUTHORIZED|El usuario no está autorizado para realizar esta operación.|

## <a name="remarks"></a>Observaciones
 Esta función se llama con un recuento y una matriz de nombres de los archivos que se van a recuperar. Si el IDE pasa `SCC_GET_ALL`la marca , `lpFileNames` esto significa que los elementos en no son archivos, sino directorios, y que se deben recuperar todos los archivos bajo control de código fuente en los directorios especificados.

 La `SCC_GET_ALL` marca se puede `SCC_GET_RECURSIVE` combinar con la marca para recuperar todos los archivos en los directorios dados y todos los subdirectorios también.

> [!NOTE]
> `SCC_GET_RECURSIVE`nunca debe `SCC_GET_ALL`pasarse sin . Además, tenga en cuenta que si los directorios *C:-A* y *C:-A-B* se pasan en un get recursivo, *C:-A-B* y todos sus subdirectorios se recuperarán realmente dos veces. Es responsabilidad del IDE, y no del complemento de control de código fuente, asegurarse de que los duplicados como este se mantengan fuera de la matriz.

 Por último, incluso si un complemento `SCC_CAP_GET_NOUI` de control de código fuente especificó la marca en la inicialización, lo que indica que no tiene una interfaz de usuario para un Get comando, esta función todavía puede ser llamada por el IDE para recuperar archivos. La marca simplemente significa que el IDE no muestra un get elemento de menú y que no se espera que el complemento proporcione ninguna interfaz de usuario.

## <a name="rename-files-and-sccget"></a>Cambiar el nombre de los archivos y SccGet
 Situación: un usuario desprotege un archivo, por ejemplo, *a.txt*, y lo modifica. Antes de que se pueda proteger *a.txt,* un segundo usuario cambia el nombre de *a.txt* a *b.txt* en la base de datos de control de código fuente, desprotege *b.txt*, realiza algunas modificaciones en el archivo y protege el archivo. El primer usuario desea los cambios realizados por el segundo usuario para que el primer usuario cambie el nombre de su versión local del archivo *a.txt* a *b.txt* y realice una obtención en el archivo. Sin embargo, la memoria caché local que realiza un seguimiento de los números de versión sigue pensando que la primera versión de *a.txt* se almacena localmente y, por lo tanto, el control de código fuente no puede resolver las diferencias.

 Hay dos maneras de resolver esta situación en la que la memoria caché local de las versiones de control de código fuente no está sincronizada con la base de datos de control de código fuente:

1. No permita cambiar el nombre de un archivo en la base de datos de control de código fuente que está actualmente desprotegida.

2. Haga el equivalente de "eliminar antiguo" seguido de "añadir nuevo". El siguiente algoritmo es una manera de lograr esto.

    1. Llame a la función [SccQueryChanges](../extensibility/sccquerychanges-function.md) para obtener información sobre el cambio de nombre de *a.txt* a *b.txt* en la base de datos de control de código fuente.

    2. Cambie el nombre del archivo local *a.txt* a *b.txt*.

    3. Llame `SccGet` a la función para *a.txt* y *b.txt*.

    4. Dado que *a.txt* no existe en la base de datos de control de código fuente, la caché de la versión local se purga de la información de versión *a.txt* que falta.

    5. El archivo *b.txt* que se desprotege se combina con el contenido del archivo *b.txt* local.

    6. El archivo *b.txt* actualizado ahora se puede registrar.

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
