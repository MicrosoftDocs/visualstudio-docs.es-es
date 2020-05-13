---
title: LPTEXTOUTPROC ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702789"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Cuando el usuario ejecuta una operación de control de código fuente desde dentro del entorno de desarrollo integrado (IDE), es posible que el complemento de control de código fuente desee transmitir mensajes de error o de estado relacionados con la operación. El complemento puede mostrar sus propios cuadros de mensaje para este propósito. Sin embargo, para una integración más fluida, el complemento puede pasar cadenas al IDE, que, a continuación, las muestra en su forma nativa de mostrar información de estado. El mecanismo para `LPTEXTOUTPROC` esto es el puntero de función. El IDE implementa esta función (descrita con más detalle a continuación) para mostrar el error y el estado.

El IDE pasa al complemento de control de código fuente `lpTextOutProc` un puntero de función a esta función, como parámetro, al llamar a [sccOpenProject](../extensibility/sccopenproject-function.md). Durante una operación SCC, por ejemplo, en medio de una llamada a la [SccGet](../extensibility/sccget-function.md) que implica muchos archivos, el complemento puede llamar a la `LPTEXTOUTPROC` función, pasando periódicamente cadenas para mostrar. El IDE puede mostrar estas cadenas en una barra de estado, en una ventana de salida o en un cuadro de mensaje independiente, según corresponda. Opcionalmente, el IDE puede mostrar ciertos mensajes con un botón **Cancelar.** Esto permite al usuario cancelar la operación y proporciona al IDE la capacidad de pasar esta información al complemento.

## <a name="signature"></a>Signature
 La función de salida del IDE tiene la siguiente firma:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Parámetros

display_string

Una cadena de texto para mostrar. Esta cadena no debe terminarse con un retorno de carro o un avance de línea.

mesg_type

El tipo de mensaje. En la tabla siguiente se enumeran los valores admitidos para este parámetro.

|Value|Descripción|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|El mensaje se considera Información, Advertencia o Error.|
|`SCC_MSG_STATUS`|El mensaje muestra el estado y se puede mostrar en la barra de estado.|
|`SCC_MSG_DOCANCEL`|Enviado sin cadena de mensaje.|
|`SCC_MSG_STARTCANCEL`|Comienza a mostrar un botón **Cancelar.**|
|`SCC_MSG_STOPCANCEL`|Detiene la visualización de un botón **Cancelar.**|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Pregunta al IDE si se va a cancelar `SCC_MSG_RTN_CANCEL` la operación en segundo plano: IDE devuelve si se canceló la operación; de lo `SCC_MSG_RTN_OK`contrario, devuelve . El `display_string` parámetro se convierte como un [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) estructura, que se proporciona mediante el complemento de control de código fuente.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Indica al IDE acerca de un archivo antes de recuperarlo del control de versiones. El `display_string` parámetro se convierte como un [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) estructura, que se proporciona mediante el complemento de control de código fuente.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Indica al IDE acerca de un archivo después de que se ha recuperado del control de versiones. El `display_string` parámetro se convierte como un [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) estructura, que se proporciona mediante el complemento de control de código fuente.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Indica al IDE el estado actual de una operación en segundo plano. El `display_string` parámetro se convierte como un [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) estructura, que se proporciona mediante el complemento de control de código fuente.|

## <a name="return-value"></a>Valor devuelto

|Value|Descripción|
|-----------|-----------------|
|SCC_MSG_RTN_OK|La cadena se mostró o la operación se completó correctamente.|
|SCC_MSG_RTN_CANCEL|El usuario desea cancelar la operación.|

## <a name="example"></a>Ejemplo
 Supongamos que el IDE llama a [La SccGet](../extensibility/sccget-function.md) con veinte nombres de archivo. El complemento de control de código fuente desea evitar la cancelación de la operación en medio de un archivo get. Después de obtener `lpTextOutProc`cada archivo, llama, pasándole la `SCC_MSG_DOCANCEL` información de estado de cada archivo y envía un mensaje si no tiene ningún estado para informar. Si en algún momento el complemento recibe `SCC_MSG_RTN_CANCEL` un valor devuelto del IDE, cancela la operación get inmediatamente, de modo que no se recuperan más archivos.

## <a name="structures"></a>Estructuras

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Esta estructura se `SCC_MSG_BACKGROUND_IS_CANCELLED` envía con el mensaje. Se utiliza para comunicar el identificador de la operación en segundo plano que se canceló.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Esta estructura se `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` envía con el mensaje. Se utiliza para comunicar el nombre del archivo a punto de recuperarse y el identificador de la operación en segundo plano que realiza la recuperación.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Esta estructura se `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` envía con el mensaje. Se utiliza para comunicar el resultado de la recuperación del archivo especificado, así como el identificador de la operación en segundo plano que realizó la recuperación. Vea los valores devueltos para [el SccGet](../extensibility/sccget-function.md) para lo que se puede dar como resultado.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Esta estructura se `SCC_MSG_BACKGROUND_ON_MESSAGE` envía con el mensaje. Se utiliza para comunicar el estado actual de una operación en segundo plano. El estado se expresa como una cadena que se `bIsError` mostrará en el IDE`TRUE` e indica la gravedad del mensaje ( para un mensaje de error; `FALSE` para una advertencia o para un mensaje informativo). También se proporciona el identificador de la operación en segundo plano que envía el estado.

## <a name="code-example"></a>Ejemplo de código
 Este es un breve `LPTEXTOUTPROC` ejemplo `SCC_MSG_BACKGROUND_ON_MESSAGE` de llamada para enviar el mensaje, que muestra cómo convertir la estructura para la llamada.

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
