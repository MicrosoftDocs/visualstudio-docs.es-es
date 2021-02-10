---
title: Función SccGet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 50281ffdd233debd3c10672868e9debd4b1f395f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965218"
---
# <a name="sccget-function"></a>SccGet función)
Esta función recupera una copia de uno o más archivos para ver y compilar, pero no para editar. En la mayoría de los sistemas, los archivos se etiquetan como de solo lectura.

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

de La estructura de contexto del complemento de control de código fuente.

 hWnd

de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.

 N archivos

de Número de archivos especificados en la `lpFileNames` matriz.

 lpFileNames

de Matriz de los nombres completos de los archivos que se van a recuperar.

 Opciones

de Marcas de comandos ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 pvOptions

de Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Operación Get correcta.|
|SCC_E_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|
|SCC_E_FILEISCHECKEDOUT|No se puede obtener el archivo que el usuario ha desprotegido actualmente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|
|SCC_E_NOSPECIFIEDVERSION|Especificó una versión o fecha/hora no válida.|
|SCC_E_NONSPECIFICERROR|Error no específico; no se sincronizó el archivo.|
|SCC_I_OPERATIONCANCELED|Operación cancelada antes de la finalización.|
|SCC_E_NOTAUTHORIZED|El usuario no está autorizado para realizar esta operación.|

## <a name="remarks"></a>Notas
 Se llama a esta función con un recuento y una matriz de nombres de los archivos que se van a recuperar. Si el IDE pasa la marca `SCC_GET_ALL` , esto significa que los elementos de `lpFileNames` no son archivos sino directorios y que se recuperarán todos los archivos bajo control de código fuente en los directorios especificados.

 La `SCC_GET_ALL` marca se puede combinar con la `SCC_GET_RECURSIVE` marca para recuperar también todos los archivos de los directorios especificados y todos los subdirectorios.

> [!NOTE]
> `SCC_GET_RECURSIVE` nunca debe pasarse sin `SCC_GET_ALL` . Además, tenga en cuenta que si los directorios *C:\a* y *C:\A\B* se pasan en una Get recursiva, *C:\A\B* y todos sus subdirectorios se recuperarán dos veces. Es responsabilidad del IDE (y no del complemento de control de código fuente) asegurarse de que los duplicados, como esto, se mantienen fuera de la matriz.

 Por último, incluso si un complemento de control de código fuente especifica la `SCC_CAP_GET_NOUI` marca en la inicialización, lo que indica que no tiene una interfaz de usuario para un comando get, es posible que el IDE siga llamando a esta función para recuperar archivos. La marca simplemente significa que el IDE no muestra un elemento de menú Get y que no se espera que el complemento proporcione ninguna interfaz de usuario.

## <a name="rename-files-and-sccget"></a>Cambiar el nombre de los archivos y SccGet
 Situación: un usuario desprotege un archivo, por ejemplo, *a.txt* y lo modifica. Antes de que se pueda proteger *a.txt* , un segundo usuario cambia el nombre *a.txt* a *b.txt* en la base de datos de control de código fuente, desprotege *b.txt*, realiza algunas modificaciones en el archivo y comprueba el archivo. El primer usuario desea los cambios realizados por el segundo usuario, por lo que el primer usuario cambia el nombre de su versión local de *a.txt* archivo a *b.txt* y realiza una obtención en el archivo. Sin embargo, la memoria caché local que realiza un seguimiento de los números de versión sigue pensando en que la primera versión de *a.txt* se almacena localmente y, por tanto, el control de código fuente no puede resolver las diferencias.

 Hay dos maneras de resolver esta situación en la que la caché local de las versiones de control de código fuente deja de estar sincronizada con la base de datos de control de código fuente:

1. No permite cambiar el nombre de un archivo en la base de datos de control de código fuente que está desprotegido actualmente.

2. Realice el equivalente a "eliminar anterior" seguido de "Agregar nuevo". El siguiente algoritmo es una manera de lograrlo.

    1. Llame a la función [SccQueryChanges](../extensibility/sccquerychanges-function.md) para obtener información sobre cómo cambiar el nombre de *a.txt* a *b.txt* en la base de datos de control de código fuente.

    2. Cambie el nombre del *a.txt* local a *b.txt*.

    3. Llame a la `SccGet` función para *a.txt* y *b.txt*.

    4. Dado que *a.txt* no existe en la base de datos de control de código fuente, la memoria caché de la versión local se purga de la información de versión de *a.txt* que falta.

    5. El archivo *b.txt* que se va a desproteger se combina con el contenido del archivo *b.txt* local.

    6. Ahora se puede proteger el archivo de *b.txt* actualizado.

## <a name="see-also"></a>Vea también
- [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Marcadores usado por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
