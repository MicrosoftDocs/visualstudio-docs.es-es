---
title: Función SccSetOption (SccSetOption) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1adcbb47e9fce7037fe8942326e8836ade51e3eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700311"
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

[en] La estructura de contexto del complemento de control de código fuente.

 nOpción

[en] La opción que se está configurando.

 dwVal

[en] Configuración de la opción.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La opción se ha establecido correctamente.|
|SCC_I_SHARESUBPROJOK|Se `nOption` devuelve `SCC_OPT_SHARESUBPROJ` si lo fue y el complemento de control de código fuente permite que el IDE establezca la carpeta de destino.|
|SCC_E_OPNOTSUPPORTED|La opción no se estableció y no se debe confiar en ella.|

## <a name="remarks"></a>Observaciones
 El IDE llama a esta función para controlar el comportamiento del complemento de control de código fuente. El primer `nOption`parámetro, , indica el valor que se `dwVal`está establecer, mientras que el segundo, , indica qué hacer con ese valor. El complemento almacena esta información `pvContext``,` asociada a un por lo que el IDE debe llamar a esta función después de llamar a la [SccInitialize](../extensibility/sccinitialize-function.md) (pero no necesariamente después de cada llamada a la [SccOpenProject](../extensibility/sccopenproject-function.md)).

 Resumen de las opciones y sus valores:

|`nOption`|`dwValue`|Descripción|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Habilita/deshabilita la cola de eventos en segundo plano.|
|`SCC_OPT_USERDATA`|Valor arbitrario|Especifica un valor de usuario que se pasará a la función de devolución de llamada [OPTNAMECHANGEPFN.](../extensibility/optnamechangepfn.md)|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Indica si el IDE admite actualmente la cancelación de una operación.|
|`SCC_OPT_NAMECHANGEPFN`|Puntero a la función de devolución de llamada [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)|Establece un puntero a una función de devolución de llamada de cambio de nombre.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Indica si el IDE permite la desproteger sus archivos manualmente (a través de la interfaz de usuario del control de código fuente) o si solo se deben desproteger a través del complemento de control de código fuente.|
|`SCC_OPT_SHARESUBPROJ`|N/D|Si el complemento de control de código fuente permite que el IDE especifique la carpeta del proyecto local, el complemento devuelve `SCC_I_SHARESUBPROJOK`.|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 Si `nOption` `SCC_OPT_EVENTQUEUE`es , el IDE está deshabilitando (o volviendo a habilitar) el procesamiento en segundo plano. Por ejemplo, durante una compilación, el IDE podría indicar al complemento de control de código fuente que detenga el procesamiento en reposo de cualquier tipo. Después de la compilación, volvería a habilitar el procesamiento en segundo plano para mantener actualizada la cola de eventos del complemento. Correspondiente al `SCC_OPT_EVENTQUEUE` valor `nOption`de , hay `dwVal`dos valores `SCC_OPT_EQ_ENABLE` posibles `SCC_OPT_EQ_DISABLE`para , a saber, y .

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 Si el `nOption` valor `SCC_OPT_HASCANCELMODE`de es , el IDE permite a los usuarios cancelar operaciones largas. Establecer `dwVal` `SCC_OPT_HCM_NO` en (el valor predeterminado) indica que el IDE no tiene modo de cancelación. El complemento de control de código fuente debe ofrecer su propio botón Cancelar si desea que el usuario pueda cancelar. `SCC_OPT_HCM_YES`indica que el IDE proporciona la capacidad de cancelar una operación, por lo que el complemento SCC no necesita mostrar su propio botón Cancelar. Si el IDE se `dwVal` establece en `SCC_MSG_STATUS` `DOCANCEL` `lpTextOutProc` `SCC_OPT_HCM_YES`, está preparado para responder y los mensajes enviados a la función de devolución de llamada (consulte [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Si el IDE no establece esta variable, el complemento no debe enviar estos dos mensajes.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Si nOption está `SCC_OPT_NAMECHANGEPFN`establecido en , y tanto el complemento de control de código fuente como el IDE lo permiten, el complemento puede cambiar el nombre o mover un archivo durante una operación de control de código fuente. Se `dwVal` establecerá en un puntero de función de tipo [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Durante una operación de control de código fuente, el complemento puede llamar a esta función, pasando tres parámetros. Estos son el nombre antiguo (con ruta de acceso completa) de un archivo, el nuevo nombre (con ruta de acceso completa) de ese archivo y un puntero a la información que tiene relevancia para el IDE. El IDE envía este último `SccSetOption` `nOption` puntero `SCC_OPT_USERDATA`llamando `dwVal` a set a , con apuntar a los datos. La compatibilidad con esta función es opcional. Un complemento VSSCI que utiliza esta capacidad debe inicializar su `NULL`puntero de función y las variables de datos de usuario en , y no debe llamar a una función de cambio de nombre a menos que se le haya dado una. También debe estar preparado para mantener el valor que se le dio `SccSetOption`o para cambiarlo en respuesta a una nueva llamada a . Esto no sucederá en medio de una operación de comando de control de código fuente, pero puede suceder entre comandos.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Si nOption se `SCC_OPT_SCCCHECKOUTONLY`establece en , el IDE indica que los archivos del proyecto actualmente abierto nunca se deben desproteger manualmente a través de la interfaz de usuario del sistema de control de código fuente. En su lugar, los archivos deben desprotegerse solo a través del complemento de control de código fuente bajo control IDE. Si `dwValue` se `SCC_OPT_SCO_NO`establece en , significa que los archivos deben ser tratados normalmente por el complemento y se pueden desproteger a través de la interfaz de usuario del control de código fuente. Si `dwValue` se `SCC_OPT_SCO_YES`establece en , solo se permite que el complemento desproteger archivos y no se debe invocar la interfaz de usuario del sistema de control de código fuente. Esto es para situaciones en las que el IDE puede tener "pseudoarchivos" que tienen sentido para desproteger solo a través del IDE.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Si`nOption` se `SCC_OPT_SHARESUBPROJ`establece en , el IDE está probando si el complemento de control de código fuente puede usar una carpeta local especificada al agregar archivos desde el control de código fuente. El valor `dwVal` del parámetro no importa en este caso. Si el complemento permite que el IDE especifique la carpeta de destino local donde se agregarán los archivos desde el `SCC_I_SHARESUBPROJOK` control `SccSetOption` de código fuente cuando se llama [a SccAddFromScc,](../extensibility/sccaddfromscc-function.md) el complemento debe devolver cuando se llama a la función. A continuación, el `lplpFileNames` IDE `SccAddFromScc` utiliza el parámetro de la función para pasar en la carpeta de destino. El complemento utiliza esa carpeta de destino para colocar los archivos agregados desde el control de código fuente. Si el complemento no `SCC_I_SHARESUBPROJOK` vuelve `SCC_OPT_SHARESUBPROJ` cuando se establece la opción, el IDE asume que el complemento puede agregar archivos solo en la carpeta local actual.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
