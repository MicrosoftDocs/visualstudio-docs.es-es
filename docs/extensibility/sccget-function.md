---
description: Esta función recupera una copia de uno o varios archivos para verlos y compilarlos, pero no para editarlos.
title: SccGet Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 805c19b0c326e8389b4e1905edf370ad042aac92
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904557"
---
# <a name="sccget-function"></a>Función SccGet
Esta función recupera una copia de uno o varios archivos para verlos y compilarlos, pero no para editarlos. En la mayoría de los sistemas, los archivos se etiquetan como de solo lectura.

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

[in] Estructura de contexto del complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 nFiles

[in] Número de archivos especificados en la `lpFileNames` matriz.

 lpFileNames

[in] Matriz de nombres completos de archivos que se recuperarán.

 fOptions

[in] Marcas de comandos ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 pvOptions

[in] Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Operación get correcta.|
|SCC_E_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|
|SCC_E_FILEISCHECKEDOUT|No se puede obtener el archivo que el usuario ha desprotegiendo actualmente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NOSPECIFIEDVERSION|Se especificó una versión o fecha y hora no válidas.|
|SCC_E_NONSPECIFICERROR|Error no específico; el archivo no se sincronizó.|
|SCC_I_OPERATIONCANCELED|Operación cancelada antes de la finalización.|
|SCC_E_NOTAUTHORIZED|El usuario no está autorizado para realizar esta operación.|

## <a name="remarks"></a>Observaciones
 Se llama a esta función con un recuento y una matriz de nombres de los archivos que se recuperarán. Si el IDE pasa la marca , significa que los elementos de no son archivos, sino directorios, y que se recuperarán todos los archivos bajo control de código fuente de los `SCC_GET_ALL` `lpFileNames` directorios especificados.

 La marca se puede combinar con la marca para recuperar todos los archivos de `SCC_GET_ALL` `SCC_GET_RECURSIVE` los directorios y subdirectorios dados.

> [!NOTE]
> `SCC_GET_RECURSIVE` nunca se debe pasar sin `SCC_GET_ALL` . Además, tenga en cuenta que si los directorios *C:\A* y *C:\A\B* se pasan en una get recursiva, *C:\A\B* y todos sus subdirectorios se recuperarán realmente dos veces. Es responsabilidad del IDE (y no de los complementos de control de código fuente) asegurarse de que los duplicados como este se mantienen fuera de la matriz.

 Por último, incluso si un complemento de control de código fuente especificó la marca en la inicialización, lo que indica que no tiene una interfaz de usuario para un comando Get, el IDE todavía puede llamar a esta función para recuperar `SCC_CAP_GET_NOUI` archivos. La marca simplemente significa que el IDE no muestra un elemento de menú Obtener y que no se espera que el complemento proporcione ninguna interfaz de usuario.

## <a name="rename-files-and-sccget"></a>Cambiar el nombre de los archivos y SccGet
 Situación: un usuario comprueba un archivo, por ejemplo, *a.txt*, y lo modifica. Antes *dea.txt* se puede comprobar, un segundo usuario cambia el nombre de *a.txt* *ab.txt* en la base de datos de control de código fuente, comprueba *b.txt*, realiza algunas modificaciones en el archivo y comprueba el archivo. El primer usuario quiere que los cambios realizados por el segundo usuario cambien  el nombre de la versión local del archivo *a.txtb.txt* y realice una operación get en el archivo. Sin embargo, la caché local que realiza el seguimiento de los números de versión sigue pensando que la primera versión de *a.txt* se almacena localmente y, por tanto, el control de código fuente no puede resolver las diferencias.

 Hay dos maneras de resolver esta situación en la que la caché local de versiones de control de código fuente deja de estar sincronizada con la base de datos de control de código fuente:

1. No permita cambiar el nombre de un archivo en la base de datos de control de código fuente que está desprotegiendo actualmente.

2. Realice el equivalente de "delete old" seguido de "add new". El siguiente algoritmo es una manera de lograrlo.

    1. Llame a [la función SccQueryChanges](../extensibility/sccquerychanges-function.md) para  obtener información sobre el cambio dea.txtpara *b.txt* en la base de datos de control de código fuente.

    2. Cambie el nombre *dela.txt* local *ab.txt*.

    3. Llame a `SccGet` la función para *a.txt* y *b.txt*.

    4. Dado *a.txt* no existe en la base de datos de control de código fuente, la caché de versiones local se purga de la información de la versión *a.txt* existente.

    5. El *b.txt* que se está desprotegiendo se combina con el contenido del *archivo* b.txtlocal.

    6. Ahora se *puedeb.txt* archivo actualizado.

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags usados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
