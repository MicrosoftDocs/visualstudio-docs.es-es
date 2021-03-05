---
description: Esta función establece las opciones que controlan el comportamiento del complemento de control de código fuente.
title: Función SccSetOption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e25647eb8d2e5796665f072af6df43b2f585c7b0
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221384"
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

de Estructura de contexto del complemento de control de código fuente.

 nOption

de Opción que se va a establecer.

 dwVal

de Configuración de la opción.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La opción se estableció correctamente.|
|SCC_I_SHARESUBPROJOK|Se devuelve si `nOption` era `SCC_OPT_SHARESUBPROJ` y el complemento de control de código fuente permite que el IDE establezca la carpeta de destino.|
|SCC_E_OPNOTSUPPORTED|No se ha establecido la opción y no se debe confiar en ella.|

## <a name="remarks"></a>Observaciones
 El IDE llama a esta función para controlar el comportamiento del complemento de control de código fuente. El primer parámetro, `nOption` , indica el valor que se va a establecer, mientras que el segundo, `dwVal` , indica qué hacer con ese valor. El complemento almacena esta información asociada a `pvContext``,` , por lo que el IDE debe llamar a esta función después de llamar a [SccInitialize](../extensibility/sccinitialize-function.md) (pero no necesariamente después de cada llamada a [SccOpenProject](../extensibility/sccopenproject-function.md)).

 Resumen de las opciones y sus valores:

|`nOption`|`dwValue`|Descripción|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Habilita o deshabilita la cola de eventos en segundo plano.|
|`SCC_OPT_USERDATA`|Valor arbitrario|Especifica un valor de usuario que se va a pasar a la función de devolución de llamada [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) .|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Indica si el IDE admite actualmente la cancelación de una operación.|
|`SCC_OPT_NAMECHANGEPFN`|Puntero a la función de devolución de llamada [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)|Establece un puntero a una función de devolución de llamada Name-Change.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Indica si el IDE permite la desprotección de sus archivos manualmente (a través de la interfaz de usuario del control de código fuente) o si deben desprotegerse solo a través del complemento de control de código fuente.|
|`SCC_OPT_SHARESUBPROJ`|N/D|Si el complemento de control de código fuente permite al IDE especificar la carpeta de proyecto local, el complemento devuelve `SCC_I_SHARESUBPROJOK` .|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 Si `nOption` es `SCC_OPT_EVENTQUEUE` , el IDE está deshabilitando (o volviendo a habilitar) el procesamiento en segundo plano. Por ejemplo, durante una compilación, el IDE podría indicar al complemento de control de código fuente que detenga el procesamiento en inactividad de cualquier tipo. Después de la compilación, volvería a habilitar el procesamiento en segundo plano para mantener actualizada la cola de eventos del complemento. Que corresponde al `SCC_OPT_EVENTQUEUE` valor de `nOption` , hay dos valores posibles para `dwVal` , es decir, `SCC_OPT_EQ_ENABLE` y `SCC_OPT_EQ_DISABLE` .

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 Si el valor de `nOption` es `SCC_OPT_HASCANCELMODE` , el IDE permite a los usuarios cancelar operaciones largas. Si se establece `dwVal` en `SCC_OPT_HCM_NO` (valor predeterminado), indica que el IDE no tiene el modo de cancelación. El complemento de control de código fuente debe ofrecer su propio botón Cancelar si desea que el usuario pueda cancelar. `SCC_OPT_HCM_YES` indica que el IDE proporciona la capacidad de cancelar una operación, por lo que el complemento SCC no necesita mostrar su propio botón Cancelar. Si el IDE establece `dwVal` en `SCC_OPT_HCM_YES` , está preparado para responder a los `SCC_MSG_STATUS` `DOCANCEL` mensajes y enviados a la `lpTextOutProc` función de devolución de llamada (vea [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Si el IDE no establece esta variable, el complemento no debe enviar estos dos mensajes.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Si nOption se establece en `SCC_OPT_NAMECHANGEPFN` y tanto el complemento de control de código fuente como el IDE lo permiten, el complemento puede cambiar el nombre de un archivo o moverlo en realidad durante una operación de control de código fuente. Se `dwVal` establecerá en un puntero de función de tipo [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Durante una operación de control de código fuente, el complemento puede llamar a esta función y pasar tres parámetros. Se trata del nombre anterior (con ruta de acceso completa) de un archivo, el nuevo nombre (con la ruta de acceso completa) de ese archivo y un puntero a la información que tiene relevancia para el IDE. El IDE envía en este último puntero mediante una llamada a `SccSetOption` con `nOption` establecido en `SCC_OPT_USERDATA` , que `dwVal` apunta a los datos. La compatibilidad con esta función es opcional. Un complemento VSSCI que usa esta capacidad debe inicializar el puntero de función y las variables de datos de usuario en `NULL` , y no debe llamar a una función de cambio de nombre a menos que se le haya proporcionado. También debe estar preparado para contener el valor que se le proporcionó o cambiarlo como respuesta a una nueva llamada a `SccSetOption` . Esto no ocurrirá en medio de una operación del comando de control de código fuente, pero puede ocurrir entre los comandos.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Si nOption se establece en `SCC_OPT_SCCCHECKOUTONLY` , el IDE indica que los archivos del proyecto actualmente abierto nunca deben desprotegerse manualmente a través de la interfaz de usuario del sistema de control de código fuente. En su lugar, los archivos deben desprotegerse solo a través del complemento de control de código fuente en control IDE. Si `dwValue` se establece en `SCC_OPT_SCO_NO` , significa que los archivos deben ser tratados normalmente por el complemento y se pueden desproteger a través de la interfaz de usuario del control de código fuente. Si `dwValue` está establecido en `SCC_OPT_SCO_YES` , solo se permite que el complemento desproteja los archivos y no se debe invocar la interfaz de usuario del sistema de control de código fuente. Esto se realiza en situaciones en las que el IDE podría tener "pseudo archivos" que tienen sentido desproteger solo a través del IDE.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Si `nOption` se establece en `SCC_OPT_SHARESUBPROJ` , el IDE está probando si el complemento de control de código fuente puede utilizar una carpeta local especificada al agregar archivos desde el control de código fuente. En este caso, el valor del parámetro no es `dwVal` relevante. Si el complemento permite al IDE especificar la carpeta de destino local a la que se agregarán los archivos desde el control de código fuente cuando se llama a [SccAddFromScc](../extensibility/sccaddfromscc-function.md) , el complemento debe devolver `SCC_I_SHARESUBPROJOK` cuando `SccSetOption` se llame a la función. A continuación, el IDE utiliza el `lplpFileNames` parámetro de la `SccAddFromScc` función que se va a pasar a la carpeta de destino. El complemento utiliza esa carpeta de destino para colocar los archivos agregados desde el control de código fuente. Si el complemento no devuelve `SCC_I_SHARESUBPROJOK` cuando `SCC_OPT_SHARESUBPROJ` se establece la opción, el IDE supone que el complemento solo puede Agregar archivos en la carpeta local actual.

## <a name="see-also"></a>Consulte también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
