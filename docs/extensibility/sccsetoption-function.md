---
title: "SccSetOption (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccSetOption"
helpviewer_keywords: 
  - "SccSetOption (función)"
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccSetOption (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función establece opciones que controlan el comportamiento del complemento de control de código fuente.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### Parámetros  
 pvContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 nOption  
 \[in\] La opción que se va a establecer.  
  
 dwVal  
 \[in\] Configuración de la opción.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|La opción se estableció correctamente.|  
|SCC\_I\_SHARESUBPROJOK|Se devuelve si `nOption` era `SCC_OPT_SHARESUBPROJ` y el complemento de control de código fuente permite que el IDE establecer la carpeta de destino.|  
|SCC\_E\_OPNOTSUPPORTED|La opción no se ha establecido y no se debería confiar en.|  
  
## Comentarios  
 El IDE llama a esta función para controlar el comportamiento del complemento de control de origen. El primer parámetro, `nOption`, indica el valor que se va a establecer, mientras que el segundo, `dwVal`, indica qué hacer con ese valor. El complemento almacena esta información asociada con un `pvContext``,` para que el IDE debe llamar a esta función después de llamar a la [SccInitialize](../extensibility/sccinitialize-function.md) \(pero no necesariamente después de cada llamada a la [SccOpenProject](../extensibility/sccopenproject-function.md)\).  
  
 Resumen de las opciones y sus valores:  
  
|`nOption`|`dwValue`|Descripción|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Habilita o deshabilita en segundo plano la cola de eventos.|  
|`SCC_OPT_USERDATA`|Valor arbitrario|Especifica un valor de usuario que se pasan a la [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) función de devolución de llamada.|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Indica si el IDE actualmente admite la cancelación de una operación.|  
|`SCC_OPT_NAMECHANGEPFN`|Puntero a la [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) función de devolución de llamada|Establece un puntero a una función de devolución de llamada de cambio de nombre.|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Indica si el IDE permite la comprobación de sus archivos manualmente \(a través de la interfaz de usuario de control de código fuente\) o si deben desproteger sólo mediante el complemento de control de código fuente.|  
|`SCC_OPT_SHARESUBPROJ`|N\/D|Si el complemento de control de código fuente permite el IDE especificar la carpeta de proyecto local, el complemento devuelve `SCC_I_SHARESUBPROJOK`.|  
  
## SCC\_OPT\_EVENTQUEUE  
 Si `nOption` es `SCC_OPT_EVENTQUEUE`, el IDE es deshabilitar \(o volver a habilitar\) procesamiento en segundo plano. Por ejemplo, durante una compilación, el IDE podría indicar que el complemento para detener el procesamiento en inactividad de cualquier tipo de control de origen. Después de la compilación, lo que permitiría volver a procesamiento en segundo plano para mantener actualizados de la cola de eventos del complemento. Correspondiente a la `SCC_OPT_EVENTQUEUE` valor de `nOption`, hay dos posibles valores para `dwVal`, es decir, `SCC_OPT_EQ_ENABLE` y `SCC_OPT_EQ_DISABLE`.  
  
## SCC\_OPT\_HASCANCELMODE  
 Si el valor de `nOption` es `SCC_OPT_HASCANCELMODE`, el IDE permite a los usuarios cancelar operaciones de larga duración. Establecer `dwVal` a `SCC_OPT_HCM_NO` \(predeterminado\) indica que el IDE no tiene ningún modo de cancelar. El complemento de control de código fuente debe ofrecer su propio botón Cancelar si desea que el usuario pueda cancelar.`SCC_OPT_HCM_YES` indica que el IDE proporciona la capacidad de cancelar una operación, por lo que el complemento control de código fuente no es necesario mostrar su propio botón Cancelar. Si establece el IDE `dwVal` a `SCC_OPT_HCM_YES`, está preparado para responder a `SCC_MSG_STATUS` y `DOCANCEL` los mensajes enviados a la `lpTextOutProc` función de devolución de llamada \(consulte [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)\). Si no establece esta variable para el IDE, el complemento no debe enviar estos dos mensajes.  
  
## SCC\_OPT\_NAMECHANGEPFN  
 Si nOption se establece en `SCC_OPT_NAMECHANGEPFN`, y tanto el origen del complemento de control y el IDE lo permiten, el complemento puede realmente cambiar nombre o mover un archivo durante una operación de control de código fuente. El `dwVal` se establecerá en un puntero de función de tipo [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Durante una operación de control de código fuente, el complemento puede llamar a esta función, pasando tres parámetros. Estas son el nombre anterior \(con la ruta de acceso completa\) de un archivo, el nuevo nombre \(con la ruta de acceso completa\) de ese archivo y un puntero a la información que tiene relevancia en el IDE. El IDE envía este último puntero al llamar a `SccSetOption` con `nOption` establecido en `SCC_OPT_USERDATA`, con `dwVal` que apunta a los datos. Compatibilidad para esta función es opcional. Un conector VSSCI\-que usa esta capacidad debe inicializar sus variables de datos de puntero y el usuario de función en `NULL`, y no debe llamar a una función de cambio de nombre a menos que se ha proporcionado uno. También debe estar preparado para mantener el valor dado o cambie en respuesta a una nueva llamada a `SccSetOption`. Esto no se realizará en medio de una operación de comando de control de código fuente, pero se puede producir entre los comandos.  
  
## SCC\_OPT\_SCCCHECKOUTONLY  
 Si se establece nOption en `SCC_OPT_SCCCHECKOUTONLY`, el IDE indica que los archivos en el proyecto abierto nunca se comprobarán manualmente a través de la interfaz de usuario del sistema de control de código fuente. En su lugar, se deben desproteger los archivos sólo a través del control de código fuente bajo el control IDE. Si `dwValue` se establece en `SCC_OPT_SCO_NO`, significa que los archivos se deben tratar normalmente por el complemento y se pueden comprobar a través de la interfaz de usuario de control de código fuente. Si `dwValue` se establece en `SCC_OPT_SCO_YES`, a continuación, solo el complemento puede desproteger los archivos y no se debe invocar la interfaz de usuario del sistema de control de código fuente. Esto es para las situaciones donde el IDE puede tener "archivos pseudo" que tengan sentido para desproteger sólo a través del IDE.  
  
## SCC\_OPT\_SHARESUBPROJ  
 Si`nOption` se establece en `SCC_OPT_SHARESUBPROJ`, el IDE es comprobar si el complemento de control de código fuente puede usar una carpeta local especificada al agregar archivos de control de código fuente. El valor de la `dwVal` parámetro no importa en este caso. Si el complemento permite que el IDE especificar la carpeta de destino local donde se agregarán los archivos de origen para controlar cuándo el [SccAddFromScc](../extensibility/sccaddfromscc-function.md) se llama, a continuación, el complemento debe devolver `SCC_I_SHARESUBPROJOK` cuando el `SccSetOption` se llama la función. A continuación, utiliza el IDE de la `lplpFileNames` parámetro de la `SccAddFromScc` función pasar en la carpeta de destino. El complemento usa la carpeta de destino para colocar los archivos agregados desde el control de código fuente. Si el complemento no devuelve `SCC_I_SHARESUBPROJOK` cuando el `SCC_OPT_SHARESUBPROJ` opción está activada, el IDE se supone que el complemento es capaz de agregar archivos únicamente en la carpeta local actual.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)