---
description: Esta función establece opciones que controlan el comportamiento del complemento de control de código fuente.
title: Función SccSetOption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 18e33cbb8dbee9b332456826ed33e46e4d2e76de
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904105"
---
# <a name="sccsetoption-function"></a>SccSetOption (Función)
Esta función establece opciones que controlan el comportamiento del complemento de control de código fuente.

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

[in] Estructura de contexto del complemento de control de código fuente.

 nOption

[in] Opción que se establece.

 dwVal

[in] Configuración de la opción.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La opción se estableció correctamente.|
|SCC_I_SHARESUBPROJOK|Se devuelve si era y el complemento `nOption` de control de código fuente permite al IDE establecer la carpeta de `SCC_OPT_SHARESUBPROJ` destino.|
|SCC_E_OPNOTSUPPORTED|No se estableció la opción y no se debe confiar en ella.|

## <a name="remarks"></a>Observaciones
 El IDE llama a esta función para controlar el comportamiento del complemento de control de código fuente. El primer parámetro, , indica el valor que se establece, mientras que el segundo, , indica qué hacer `nOption` `dwVal` con ese valor. El complemento almacena esta información asociada a un , por lo que el IDE debe llamar a esta función después de llamar a `pvContext``,` [SccInitialize](../extensibility/sccinitialize-function.md) (pero no necesariamente después de cada llamada a [SccOpenProject](../extensibility/sccopenproject-function.md)).

 Resumen de las opciones y sus valores:

|`nOption`|`dwValue`|Descripción|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Habilita o deshabilita la cola de eventos en segundo plano.|
|`SCC_OPT_USERDATA`|Valor arbitrario|Especifica un valor de usuario que se va a pasar a la función de devolución de llamada [OPTNAMECHANGEPFN.](../extensibility/optnamechangepfn.md)|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Indica si el IDE admite actualmente la cancelación de una operación.|
|`SCC_OPT_NAMECHANGEPFN`|Puntero a la [función de devolución de llamada OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)|Establece un puntero a una función de devolución de llamada de cambio de nombre.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Indica si el IDE permite la desprotecciones manuales de sus archivos (a través de la interfaz de usuario del control de código fuente) o si solo se deben desprotegiendo a través del complemento de control de código fuente.|
|`SCC_OPT_SHARESUBPROJ`|N/D|Si el complemento de control de código fuente permite que el IDE especifique la carpeta del proyecto local, el complemento devuelve `SCC_I_SHARESUBPROJOK` .|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 Si es , el IDE deshabilita (o vuelve a habilitar) el procesamiento `nOption` `SCC_OPT_EVENTQUEUE` en segundo plano. Por ejemplo, durante una compilación, el IDE podría indicar al complemento de control de código fuente que detenga el procesamiento inactivo de cualquier tipo. Después de la compilación, se habilitaría de nuevo el procesamiento en segundo plano para mantener actualizada la cola de eventos del complemento. Correspondiente al `SCC_OPT_EVENTQUEUE` valor de , hay dos valores `nOption` posibles para , es `dwVal` decir, y `SCC_OPT_EQ_ENABLE` `SCC_OPT_EQ_DISABLE` .

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 Si el valor de `nOption` es , el IDE permite a los usuarios cancelar operaciones `SCC_OPT_HASCANCELMODE` largas. Establecer `dwVal` en `SCC_OPT_HCM_NO` (valor predeterminado) indica que el IDE no tiene ningún modo de cancelación. El complemento de control de código fuente debe ofrecer su propio botón Cancelar si quiere que el usuario pueda cancelar. `SCC_OPT_HCM_YES` indica que el IDE proporciona la capacidad de cancelar una operación, por lo que el complemento SCC no necesita mostrar su propio botón Cancelar. Si el IDE establece en , está preparado para responder a los mensajes y enviados a la función de devolución de llamada `dwVal` `SCC_OPT_HCM_YES` `SCC_MSG_STATUS` `DOCANCEL` `lpTextOutProc` [(vea LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Si el IDE no establece esta variable, el complemento no debe enviar estos dos mensajes.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Si nOption está establecido en y tanto el complemento de control de código fuente como el IDE lo permiten, el complemento puede cambiar realmente el nombre o mover un archivo durante una operación de `SCC_OPT_NAMECHANGEPFN` control de código fuente. se `dwVal` establecerá en un puntero de función de tipo [OPTNAMECHANGEPFN.](../extensibility/optnamechangepfn.md) Durante una operación de control de código fuente, el complemento puede llamar a esta función, pasando tres parámetros. Estos son el nombre antiguo (con ruta de acceso completa) de un archivo, el nuevo nombre (con ruta de acceso completa) de ese archivo y un puntero a la información que tiene relevancia para el IDE. El IDE envía este último puntero mediante una llamada `SccSetOption` a con establecido en , con que apunta a los `nOption` `SCC_OPT_USERDATA` `dwVal` datos. La compatibilidad con esta función es opcional. Un complemento VSSCI que usa esta capacidad debe inicializar su puntero de función y las variables de datos de usuario en y no debe llamar a una función rename a menos que se le `NULL` haya dado una. También debe estar preparado para contener el valor que se le ha dado o para cambiarlo en respuesta a una nueva llamada a `SccSetOption` . Esto no ocurrirá en medio de una operación de comando de control de código fuente, pero puede ocurrir entre comandos.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Si nOption está establecido en , el IDE indica que los archivos del proyecto abierto actualmente nunca se deben desprotegiendo manualmente a través de la interfaz de usuario del sistema de `SCC_OPT_SCCCHECKOUTONLY` control de código fuente. En su lugar, los archivos solo se deben desprotegiendo a través del complemento de control de código fuente bajo control IDE. Si se establece en , significa que el complemento debe tratar los archivos con normalidad y se pueden desprotegiendo a través de la interfaz de usuario `dwValue` del control de código `SCC_OPT_SCO_NO` fuente. Si se establece en , solo se permite que el complemento desalme los archivos y no se invoque la interfaz de usuario del sistema `dwValue` de control de código `SCC_OPT_SCO_YES` fuente. Esto es para situaciones en las que el IDE podría tener "pseudo-archivos" que tienen sentido desatrase solo a través del IDE.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Si se establece en , el IDE está probando si el complemento de control de código fuente puede usar una carpeta local especificada al agregar archivos `nOption` desde el control de código `SCC_OPT_SHARESUBPROJ` fuente. El valor del `dwVal` parámetro no importa en este caso. Si el complemento permite que el IDE especifique la carpeta de destino local donde se agregarán los archivos desde el control de código fuente cuando se llame a [SccAddFromScc,](../extensibility/sccaddfromscc-function.md) el complemento debe devolver cuando se llame a la `SCC_I_SHARESUBPROJOK` `SccSetOption` función. A continuación, el IDE `lplpFileNames` usa el parámetro de la función para pasar la carpeta de `SccAddFromScc` destino. El complemento usa esa carpeta de destino para colocar los archivos agregados desde el control de código fuente. Si el complemento no devuelve cuando se establece la opción , el IDE asume que el complemento solo puede agregar archivos en la `SCC_I_SHARESUBPROJOK` `SCC_OPT_SHARESUBPROJ` carpeta local actual.

## <a name="see-also"></a>Consulta también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
