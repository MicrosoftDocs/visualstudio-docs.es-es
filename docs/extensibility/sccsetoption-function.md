---
title: "Función SccSetOption | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccSetOption
helpviewer_keywords: SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a0bc7ab99c6bc3643ee61b403e4aa0c40c41a63a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="sccsetoption-function"></a>SccSetOption (función)
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
 [in] La estructura de contexto de complemento de control de código fuente.  
  
 nOption  
 [in] La opción que se va a establecer.  
  
 dwVal  
 [in] Configuración para la opción.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|La opción se estableció correctamente.|  
|SCC_I_SHARESUBPROJOK|Se devuelve si `nOption` era `SCC_OPT_SHARESUBPROJ` y el complemento de control de código fuente permite que el IDE establecer la carpeta de destino.|  
|SCC_E_OPNOTSUPPORTED|La opción no se ha establecido y no debe confiar en.|  
  
## <a name="remarks"></a>Comentarios  
 El IDE llama a esta función para controlar el comportamiento del complemento de control de código fuente. El primer parámetro, `nOption`, indica el valor que se está estableciendo, mientras que la segunda, `dwVal`, indica qué hacer con ese valor. El complemento almacena esta información asociada con un `pvContext``,` por lo que el IDE debe llamar a esta función después de llamar a la [SccInitialize](../extensibility/sccinitialize-function.md) (pero no necesariamente después de cada llamada a la [SccOpenProject](../extensibility/sccopenproject-function.md)).  
  
 Resumen de las opciones y sus valores:  
  
|`nOption`|`dwValue`|Descripción|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Habilita o deshabilita en segundo plano puesta en cola eventos.|  
|`SCC_OPT_USERDATA`|Valor arbitrario|Especifica un valor de usuario que se pasan a la [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) función de devolución de llamada.|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Indica si el IDE actualmente admite la cancelación de una operación.|  
|`SCC_OPT_NAMECHANGEPFN`|Puntero a la [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) callback (función)|Establece un puntero a una función de devolución de llamada de cambio de nombre.|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Indica si el IDE permite la comprobación fuera de sus archivos de forma manual (a través de la interfaz de usuario de control de código fuente) o si debe desproteger sólo mediante el complemento de control de código fuente.|  
|`SCC_OPT_SHARESUBPROJ`|N/D|Si el complemento de control de código fuente permite el IDE especificar la carpeta de proyecto local, el complemento devuelve `SCC_I_SHARESUBPROJOK`.|  
  
## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE  
 Si `nOption` es `SCC_OPT_EVENTQUEUE`, el IDE es deshabilitar (o volver a habilitar) procesamiento en segundo plano. Por ejemplo, durante una compilación, el IDE podría indicar que el complemento para detener el procesamiento en inactividad de cualquier tipo de control de código fuente. Después de la compilación, lo que permitiría volver a procesamiento en segundo plano para mantener actualizada de la cola de eventos del complemento. Correspondiente a la `SCC_OPT_EVENTQUEUE` valo `nOption`, hay dos valores posibles para `dwVal`, es decir, `SCC_OPT_EQ_ENABLE` y `SCC_OPT_EQ_DISABLE`.  
  
## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE  
 Si el valor de `nOption` es `SCC_OPT_HASCANCELMODE`, el IDE permite a los usuarios cancelar operaciones de larga duración. Establecer `dwVal` a `SCC_OPT_HCM_NO` (valor predeterminado) indica que el IDE no tiene ningún modo de cancelar. El complemento de control de código fuente debe ofrecer su propio botón Cancelar si desea que el usuario pueda cancelar. `SCC_OPT_HCM_YES`indica que el IDE proporciona la capacidad para cancelar una operación, por lo que no es necesario que el complemento de SCC mostrar su propio botón de cancelación. Si establece el IDE `dwVal` a `SCC_OPT_HCM_YES`, ya está preparado para responder a `SCC_MSG_STATUS` y `DOCANCEL` mensajes enviados a la `lpTextOutProc` función de devolución de llamada (vea [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Si no establece esta variable para el IDE, el complemento no debe enviar estos dos mensajes.  
  
## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN  
 Si se establece nOption en `SCC_OPT_NAMECHANGEPFN`y tanto el origen de complemento de control y el IDE permiten, el complemento puede realmente cambiar el nombre o mover un archivo durante una operación de control de código fuente. El `dwVal` se establecerá en un puntero a función de tipo [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Durante una operación de control de código fuente, el complemento puede llamar a esta función, pasando tres parámetros. Estas son el nombre antiguo (con la ruta de acceso completa) de un archivo, el nuevo nombre (con la ruta de acceso completa) de ese archivo y un puntero a la información que tenga importancia para el IDE. El IDE envía en este puntero del último mediante una llamada a `SccSetOption` con `nOption` establecido en `SCC_OPT_USERDATA`, con `dwVal` que apunta a los datos. Compatibilidad con esta función es opcional. Un enchufe VSSCI-que usa esta capacidad debe inicializar variables de datos de su puntero y del usuario de función para `NULL`, y no debe llamar a una función de cambio de nombre a menos que se le ha asignado uno. También debe prepararán para contener el valor que se especificó o cambian en respuesta a una nueva llamada a `SccSetOption`. Esto no se realizará en el medio de una operación de comando de control de código fuente, pero puede ocurrir entre los comandos.  
  
## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY  
 Si se establece nOption en `SCC_OPT_SCCCHECKOUTONLY`, el IDE es que indica que los archivos en el proyecto abierto actualmente no deben nunca se extraiga del repositorio manualmente a través de la interfaz de usuario del sistema de control de código fuente. En su lugar, se deben desproteger los archivos sólo mediante el complemento bajo el control IDE de control de código fuente. Si `dwValue` se establece en `SCC_OPT_SCO_NO`, significa que los archivos deben tratarse normalmente por el complemento y que se pueden comprobar mediante la interfaz de usuario de control de código fuente. Si `dwValue` se establece en `SCC_OPT_SCO_YES`, a continuación, se permite solo el complemento desproteger los archivos y no se debe invocar interfaz de usuario del sistema de control de origen. Esto es en situaciones donde el IDE podría tener "archivos pseudo" que tengan sentido para desproteger solo a través del IDE.  
  
## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ  
 Si`nOption` se establece en `SCC_OPT_SHARESUBPROJ`, el IDE se prueba si el complemento de control de código fuente puede usar una carpeta local especificada al agregar archivos de control de código fuente. El valor de la `dwVal` parámetro no es relevante en este caso. Si el complemento permite que el IDE especificar la carpeta de destino local donde se agregará los archivos de origen y controla cuándo el [SccAddFromScc](../extensibility/sccaddfromscc-function.md) se llama, a continuación, el complemento debe devolver `SCC_I_SHARESUBPROJOK` cuando el `SccSetOption` función es se llama. El IDE, a continuación, usa el `lplpFileNames` parámetro de la `SccAddFromScc` función pasar en la carpeta de destino. El complemento utiliza esa carpeta de destino para colocar los archivos agregados desde el control de código fuente. Si el complemento no devuelve `SCC_I_SHARESUBPROJOK` cuando el `SCC_OPT_SHARESUBPROJ` opción está activada, el IDE se da por supuesto que el complemento es capaz de agregar archivos en la carpeta local actual.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)