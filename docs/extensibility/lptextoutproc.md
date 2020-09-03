---
title: LPTEXTOUTPROC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38c3e8263b9a30058c2de019e5e92160b716aa71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702789"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Cuando el usuario ejecuta una operación de control de código fuente desde dentro del entorno de desarrollo integrado (IDE), es posible que el complemento de control de código fuente desee transmitir mensajes de error o de estado relacionados con la operación. El complemento puede mostrar sus propios cuadros de mensaje para este fin. Sin embargo, para una integración más fluida, el complemento puede pasar cadenas al IDE, que después las muestra en su forma nativa de Mostrar información de estado. El mecanismo para este es el `LPTEXTOUTPROC` puntero de función. El IDE implementa esta función (se describe con más detalle a continuación) para mostrar los errores y el estado.

El IDE pasa al complemento de control de código fuente un puntero de función a esta función, como `lpTextOutProc` parámetro, al llamar a [SccOpenProject](../extensibility/sccopenproject-function.md). Durante una operación de SCC, por ejemplo, en el medio de una llamada a [SccGet](../extensibility/sccget-function.md) que implica muchos archivos, el complemento puede llamar a la `LPTEXTOUTPROC` función, pasando de forma periódica las cadenas que se van a mostrar. El IDE puede mostrar estas cadenas en una barra de estado, en una ventana de salida o en un cuadro de mensaje independiente, según corresponda. Opcionalmente, es posible que el IDE pueda mostrar determinados mensajes con un botón **Cancelar** . Esto permite al usuario cancelar la operación y proporciona al IDE la capacidad de volver a pasar esta información al complemento.

## <a name="signature"></a>Firma
 La función de salida del IDE tiene la siguiente firma:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Parámetros

display_string

Cadena de texto que se va a mostrar. Esta cadena no se debe terminar con un retorno de carro o un salto de línea.

mesg_type

El tipo de mensaje. En la tabla siguiente se enumeran los valores admitidos para este parámetro.

|Value|Descripción|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|El mensaje se considera información, ADVERTENCIA o error.|
|`SCC_MSG_STATUS`|El mensaje muestra el estado y se puede mostrar en la barra de estado.|
|`SCC_MSG_DOCANCEL`|Se envía sin cadena de mensaje.|
|`SCC_MSG_STARTCANCEL`|Comienza a mostrar un botón **Cancelar** .|
|`SCC_MSG_STOPCANCEL`|Deja de mostrar un botón **Cancelar** .|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Pregunta al IDE si se va a cancelar la operación en segundo plano: el IDE devuelve `SCC_MSG_RTN_CANCEL` si la operación se canceló; de lo contrario, devuelve `SCC_MSG_RTN_OK` . El `display_string` parámetro se convierte en una estructura [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) , proporcionada por el complemento de control de código fuente.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Indica al IDE sobre un archivo antes de que se recupere del control de versiones. El `display_string` parámetro se convierte en una estructura [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) , proporcionada por el complemento de control de código fuente.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Indica al IDE sobre un archivo una vez que se ha recuperado del control de versiones. El `display_string` parámetro se convierte en una estructura [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) , proporcionada por el complemento de control de código fuente.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Indica al IDE el estado actual de una operación en segundo plano. El `display_string` parámetro se convierte en una estructura [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) , proporcionada por el complemento de control de código fuente.|

## <a name="return-value"></a>Valor devuelto

|Value|Descripción|
|-----------|-----------------|
|SCC_MSG_RTN_OK|Se mostró la cadena o la operación se completó correctamente.|
|SCC_MSG_RTN_CANCEL|El usuario desea cancelar la operación.|

## <a name="example"></a>Ejemplo
 Supongamos que el IDE llama a [SccGet](../extensibility/sccget-function.md) con veinte nombres de archivo. El complemento de control de código fuente desea evitar que se cancele la operación en medio de un archivo get. Después de obtener cada archivo, llama a `lpTextOutProc` , pasándole la información de estado en cada archivo y envía un `SCC_MSG_DOCANCEL` mensaje si no tiene ningún Estado para notificar. Si en cualquier momento el complemento recibe un valor devuelto de `SCC_MSG_RTN_CANCEL` desde el IDE, cancela la operación Get inmediatamente, de modo que no se recuperen más archivos.

## <a name="structures"></a>Estructuras

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Esta estructura se envía con el `SCC_MSG_BACKGROUND_IS_CANCELLED` mensaje. Se utiliza para comunicar el identificador de la operación en segundo plano que se canceló.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Esta estructura se envía con el `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` mensaje. Se utiliza para comunicar el nombre del archivo que se va a recuperar y el ID. de la operación en segundo plano que realiza la recuperación.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Esta estructura se envía con el `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` mensaje. Se utiliza para comunicar el resultado de la recuperación del archivo especificado, así como el identificador de la operación en segundo plano que se recuperó. Vea los valores devueltos de [SccGet](../extensibility/sccget-function.md) para lo que se puede proporcionar como resultado.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Esta estructura se envía con el `SCC_MSG_BACKGROUND_ON_MESSAGE` mensaje. Se utiliza para comunicar el estado actual de una operación en segundo plano. El estado se expresa como una cadena que se va a mostrar en el IDE e `bIsError` indica la gravedad del mensaje ( `TRUE` para un mensaje de error; `FALSE` para una advertencia o para un mensaje informativo). También se proporciona el identificador de la operación en segundo plano que envía el estado.

## <a name="code-example"></a>Ejemplo de código
 Este es un breve ejemplo de llamada `LPTEXTOUTPROC` a para enviar el `SCC_MSG_BACKGROUND_ON_MESSAGE` mensaje, que muestra cómo convertir la estructura de la llamada.

```cpp
LONG SendStatusMessage(
    LPTEXTOUTPROC pTextOutProc,
    DWORD         dwBackgroundID,
    LPCTSTR       pStatusMsg,
    BOOL          bIsError)
{
    SccMsgDataOnMessage msgData = { 0 };
    LONG                result  = 0;

    msgData.dwBackgroundOperationID = dwBackgroundID;
    msgData.szMessage               = pStatusMsg;
    msgData.bIsError                = bIsError;

    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);
    return result;
}
```

## <a name="see-also"></a>Vea también
- [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
