---
title: SccSetOption (función) | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf9d700facfedc83d9eb12e96b854de7d4e9c181
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338569"
---
# <a name="sccsetoption-function"></a>SccSetOption (Función)
Esta función establece las opciones que controlan el comportamiento del complemento de control de código fuente.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccSetOption(
   LPVOID pvContext,
   LONG   nOption,
   LONG   dwVal
);
```

#### <a name="parameters"></a>Parámetros
 pvContext

[in] La estructura de contexto de complemento de control de origen.

 nOption

[in] La opción que se va a establecer.

 dwVal

[in] Configuración de la opción.

## <a name="return-value"></a>Valor devuelto
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La opción se estableció correctamente.|
|SCC_I_SHARESUBPROJOK|Devuelve si `nOption` era `SCC_OPT_SHARESUBPROJ` y el complemento de control de código fuente permite que el IDE establecer la carpeta de destino.|
|SCC_E_OPNOTSUPPORTED|La opción no se estableció y no se debería confiar en.|

## <a name="remarks"></a>Comentarios
 El IDE llama a esta función para controlar el comportamiento del complemento de control de origen. El primer parámetro, `nOption`, indica el valor que se va a establecer, mientras que el segundo, `dwVal`, indica qué hacer con ese valor. El complemento almacena esta información asociada con un `pvContext``,` por lo que el IDE debe llamar a esta función después de llamar a la [SccInitialize](../extensibility/sccinitialize-function.md) (pero no necesariamente después de cada llamada a la [SccOpenProject](../extensibility/sccopenproject-function.md)).

 Resumen de las opciones y sus valores:

|`nOption`|`dwValue`|Descripción|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Habilita o deshabilita la puesta en cola eventos de fondo.|
|`SCC_OPT_USERDATA`|Valor arbitrario|Especifica un valor de usuario que se pasarán a la [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) función de devolución de llamada.|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Indica si el IDE actualmente admite la cancelación de una operación.|
|`SCC_OPT_NAMECHANGEPFN`|Puntero a la [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) callback (función)|Establece un puntero a una función de devolución de llamada de cambio de nombre.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Indica si el IDE permite la comprobación fuera de sus archivos de forma manual (a través de la interfaz de usuario del control de origen) o si deben desproteger únicamente a través del complemento de control de código fuente.|
|`SCC_OPT_SHARESUBPROJ`|N/D|Si el complemento de control de código fuente permite el IDE especificar la carpeta de proyecto local, el complemento devuelve `SCC_I_SHARESUBPROJOK`.|

## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE
 Si `nOption` es `SCC_OPT_EVENTQUEUE`, el IDE es deshabilitar (o volver a habilitar) procesamiento en segundo plano. Por ejemplo, durante una compilación, el IDE podría indicar que el complemento para detener el procesamiento en inactividad de cualquier tipo de control de origen. Después de la compilación, lo que permitiría volver a procesamiento en segundo plano para mantener actualizado de la cola de eventos del complemento. Correspondiente a la `SCC_OPT_EVENTQUEUE` valor `nOption`, hay dos valores posibles para `dwVal`, es decir, `SCC_OPT_EQ_ENABLE` y `SCC_OPT_EQ_DISABLE`.

## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE
 Si el valor de `nOption` es `SCC_OPT_HASCANCELMODE`, el IDE permite a los usuarios cancelar operaciones de larga duración. Establecer `dwVal` a `SCC_OPT_HCM_NO` (predeterminado) indica que el IDE no tiene ningún modo de cancelar. El complemento de control de origen debe ofrecer su propio botón Cancelar si desea que el usuario pueda cancelar. `SCC_OPT_HCM_YES` indica que el IDE proporciona la capacidad de cancelar una operación, por lo que no es necesario mostrar su propio botón Cancelar el complemento de SCC. Si establece el IDE `dwVal` a `SCC_OPT_HCM_YES`, ya está preparado para responder a `SCC_MSG_STATUS` y `DOCANCEL` los mensajes enviados a la `lpTextOutProc` función de devolución de llamada (consulte [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Si el IDE no establece esta variable, el complemento no debería enviar estos dos mensajes.

## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Si se establece nOption en `SCC_OPT_NAMECHANGEPFN`y tanto el origen de complemento de control y el IDE lo permiten, el complemento puede realmente cambiar el nombre o mover un archivo durante una operación de control de código fuente. El `dwVal` se establecerá en un puntero de función de tipo [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Durante una operación de control de código fuente, el complemento puede llamar a esta función, pasando tres parámetros. Estos son el nombre antiguo (con la ruta de acceso completa) de un archivo, el nuevo nombre (con la ruta de acceso completa) de ese archivo y un puntero a la información que tiene relevancia para el IDE. El IDE se envía en este último puntero mediante una llamada a `SccSetOption` con `nOption` establecido en `SCC_OPT_USERDATA`, con `dwVal` que apunta a los datos. Soporte técnico para esta función es opcional. Un enchufe VSSCI-que usa esta capacidad debe inicializar sus variables de datos de puntero y el usuario de función para `NULL`, y no debe llamar a una función de cambio de nombre a menos que se le han otorgado uno. También debe estar preparado para contener el valor que ha proporcionado o cambiarla en respuesta a una nueva llamada a `SccSetOption`. Esto no ocurre en el medio de una operación de comando de control de código fuente, pero puede ocurrir entre comandos.

## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Si se establece nOption en `SCC_OPT_SCCCHECKOUTONLY`, el IDE es que indica que los archivos en el proyecto abierto actualmente no deben nunca se desprotegen manualmente a través de la interfaz de usuario del sistema de control de origen. En su lugar, se deben desproteger los archivos solo mediante el complemento bajo el control IDE de control de código fuente. Si `dwValue` está establecido en `SCC_OPT_SCO_NO`, significa que los archivos se deben tratar normalmente por el complemento y se pueden comprobar a través de la interfaz de usuario de control de código fuente. Si `dwValue` está establecido en `SCC_OPT_SCO_YES`, a continuación, se permite solo el complemento para desproteger los archivos y no se debe invocar la interfaz de usuario del sistema de control de origen. Esto es para las situaciones donde el IDE puede tener "archivos pseudo de que tengan sentido para desproteger solo a través del IDE.

## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Si`nOption` está establecido en `SCC_OPT_SHARESUBPROJ`, el IDE va a probar si el complemento de control de origen puede usar una carpeta local especificada al agregar archivos de control de código fuente. El valor de la `dwVal` parámetro no es relevante en este caso. Si el complemento permite que el IDE especificar la carpeta de destino local donde se agregarán los archivos de origen de controlar cuándo el [SccAddFromScc](../extensibility/sccaddfromscc-function.md) se llama, a continuación, el complemento debe devolver `SCC_I_SHARESUBPROJOK` cuando el `SccSetOption` es la función se llama. El IDE, a continuación, usa el `lplpFileNames` parámetro de la `SccAddFromScc` función pasar en la carpeta de destino. El complemento usa la carpeta de destino para colocar los archivos agregados desde el control de código fuente. Si el complemento no devuelve `SCC_I_SHARESUBPROJOK` cuando el `SCC_OPT_SHARESUBPROJ` opción está activada, el IDE se da por supuesto que el complemento es capaz de agregar archivos únicamente en la carpeta local actual.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)