---
title: LPTEXTOUTPROC | Microsoft Docs
description: Obtenga información sobre el puntero de función LPTEXTOUTPROC. El IDE Visual Studio implementa la función para mostrar el error y el estado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c313375efe8afd17dd5d76f55de4cdaf016bab40
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903104"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Cuando el usuario ejecuta una operación de control de código fuente desde dentro del entorno de desarrollo integrado (IDE), es posible que el complemento de control de código fuente quiera transmitir mensajes de error o de estado relacionados con la operación. El complemento puede mostrar sus propios cuadros de mensaje para este propósito. Sin embargo, para una integración más fluida, el complemento puede pasar cadenas al IDE, que luego las muestra en su forma nativa de mostrar información de estado. El mecanismo para esto es el puntero `LPTEXTOUTPROC` de función. El IDE implementa esta función (que se describe con más detalle a continuación) para mostrar el error y el estado.

El IDE pasa al complemento de control de código fuente un puntero de función a esta función, como parámetro, al llamar a `lpTextOutProc` [SccOpenProject](../extensibility/sccopenproject-function.md). Durante una operación SCC, por ejemplo, en medio de una llamada a [SccGet](../extensibility/sccget-function.md) que implica muchos archivos, el complemento puede llamar a la función y pasar periódicamente cadenas para `LPTEXTOUTPROC` mostrar. El IDE puede mostrar estas cadenas en una barra de estado, en una ventana de salida o en un cuadro de mensaje independiente, según corresponda. Opcionalmente, el IDE puede mostrar determinados mensajes con un **botón** Cancelar. Esto permite al usuario cancelar la operación y ofrece al IDE la capacidad de devolver esta información al complemento.

## <a name="signature"></a>Firma
 La función de salida del IDE tiene la firma siguiente:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Parámetros

display_string

Cadena de texto que se mostrará. Esta cadena no debe terminar con un retorno de carro o un avance de línea.

mesg_type

El tipo de mensaje. En la tabla siguiente se enumeran los valores admitidos para este parámetro.

|Valor|Descripción|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|El mensaje se considera Información, Advertencia o Error.|
|`SCC_MSG_STATUS`|El mensaje muestra el estado y se puede mostrar en la barra de estado.|
|`SCC_MSG_DOCANCEL`|Se envía sin cadena de mensaje.|
|`SCC_MSG_STARTCANCEL`|Comienza a mostrar un **botón** Cancelar.|
|`SCC_MSG_STOPCANCEL`|Deja de mostrar un **botón** Cancelar.|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Pregunta al IDE si se va a cancelar la operación en segundo plano: el IDE devuelve si se canceló `SCC_MSG_RTN_CANCEL` la operación; de lo contrario, devuelve `SCC_MSG_RTN_OK` . El `display_string` parámetro se convierte como una estructura [SccMsgDataIsCancelled,](#LinkSccMsgDataIsCancelled) proporcionada por el complemento de control de código fuente.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Indica al IDE un archivo antes de que se recupere del control de versiones. El parámetro se convierte como una estructura `display_string` [SccMsgDataOnBeforeGetFile,](#LinkSccMsgDataOnBeforeGetFile) proporcionada por el complemento de control de código fuente.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Indica al IDE un archivo después de que se haya recuperado del control de versiones. El `display_string` parámetro se convierte como una estructura [SccMsgDataOnAfterGetFile,](#LinkSccMsgDataOnAfterGetFile) proporcionada por el complemento de control de código fuente.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Indica al IDE el estado actual de una operación en segundo plano. El `display_string` parámetro se convierte como una estructura [SccMsgDataOnMessage,](#LinkSccMsgDataOnMessage) proporcionada por el complemento de control de código fuente.|

## <a name="return-value"></a>Valor devuelto

|Valor|Descripción|
|-----------|-----------------|
|SCC_MSG_RTN_OK|Se mostró la cadena o la operación se completó correctamente.|
|SCC_MSG_RTN_CANCEL|El usuario quiere cancelar la operación.|

## <a name="example"></a>Ejemplo
 Supongamos que el IDE llama a [SccGet con](../extensibility/sccget-function.md) veinte nombres de archivo. El complemento de control de código fuente quiere evitar la cancelación de la operación en medio de una operación get de archivo. Después de obtener cada archivo, llama a , le pasa la información de estado en cada archivo y envía un mensaje si `lpTextOutProc` no tiene ningún estado para `SCC_MSG_DOCANCEL` notificar. Si en cualquier momento el complemento recibe un valor devuelto de del IDE, cancela la operación get inmediatamente, de modo que no se `SCC_MSG_RTN_CANCEL` recuperen más archivos.

## <a name="structures"></a>Estructuras

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Esta estructura se envía con el `SCC_MSG_BACKGROUND_IS_CANCELLED` mensaje . Se usa para comunicar el identificador de la operación en segundo plano que se canceló.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Esta estructura se envía con el `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` mensaje . Se usa para comunicar el nombre del archivo que se va a recuperar y el identificador de la operación en segundo plano que está realizando la recuperación.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Esta estructura se envía con el `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` mensaje . Se usa para comunicar el resultado de recuperar el archivo especificado, así como el identificador de la operación en segundo plano que hizo la recuperación. Consulte los valores devueltos para [SccGet](../extensibility/sccget-function.md) para obtener información sobre lo que se puede dar como resultado.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Esta estructura se envía con el `SCC_MSG_BACKGROUND_ON_MESSAGE` mensaje . Se usa para comunicar el estado actual de una operación en segundo plano. El estado se expresa como una cadena que el IDE va a mostrar e indica la gravedad del mensaje ( para un mensaje de error; para una advertencia o para un mensaje `bIsError` `TRUE` `FALSE` informativo). También se proporciona el identificador de la operación en segundo plano que envía el estado.

## <a name="code-example"></a>Ejemplo de código
 Este es un breve ejemplo de llamada a para enviar el mensaje, en el que se `LPTEXTOUTPROC` muestra cómo convertir la estructura de la `SCC_MSG_BACKGROUND_ON_MESSAGE` llamada.

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

## <a name="see-also"></a>Consulta también
- [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
