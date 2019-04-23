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
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab1a2dcbf39be6f8e0366dcdccdaea168ad37c87
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102606"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Cuando el usuario ejecuta una operación de control de código fuente desde dentro del entorno de desarrollo integrado (IDE), el complemento de control de código fuente que desee transmitir los mensajes de estado o error relacionados con la operación. El complemento puede mostrar sus propios cuadros de mensaje para este propósito. Sin embargo, una integración más, el complemento puede pasar cadenas para el IDE, que se muestra a continuación, en su forma nativa de mostrar información de estado. Es el mecanismo para ello la `LPTEXTOUTPROC` puntero de función. El IDE implementa esta función (que se describe más detalladamente a continuación) para mostrar el error y estado.

El IDE pasa el control de código fuente complemento un puntero de función a esta función, como el `lpTextOutProc` parámetro al llamar a la [SccOpenProject](../extensibility/sccopenproject-function.md). Durante una operación de control de código fuente, por ejemplo, en el medio de una llamada a la [SccGet](../extensibility/sccget-function.md) que implican muchos archivos, el complemento puede llamar a la `LPTEXTOUTPROC` función, pasando periódicamente las cadenas para mostrar. El IDE puede mostrar estas cadenas en una barra de estado en una ventana de salida o en un cuadro de mensaje separado, según corresponda. Opcionalmente, el IDE puede ser capaz de mostrar determinados mensajes con un **cancelar** botón. Esto permite al usuario cancelar la operación, y proporciona la capacidad para pasar esta información a la del complemento el IDE.

## <a name="signature"></a>Signatura
 El IDE de la salida de función tiene la firma siguiente:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Parámetros

display_string

Una cadena de texto para mostrar. Esta cadena no debe terminar con un valor devuelto o un salto de línea de carro.

mesg_type

El tipo de mensaje. En la tabla siguiente se enumera los valores admitidos para este parámetro.

|Valor|Descripción|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Se considera el mensaje de Error, advertencia o información.|
|`SCC_MSG_STATUS`|El mensaje muestra el estado y se puede mostrar en la barra de estado.|
|`SCC_MSG_DOCANCEL`|Se envía con ninguna cadena de mensaje.|
|`SCC_MSG_STARTCANCEL`|Comienza a mostrar un **cancelar** botón.|
|`SCC_MSG_STOPCANCEL`|Deja de mostrar un **cancelar** botón.|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Pide IDE si la operación en segundo plano es cancelar: Devuelve el IDE `SCC_MSG_RTN_CANCEL` si la operación se canceló; de lo contrario, devuelve `SCC_MSG_RTN_OK`. El `display_string` parámetro se convierte como un [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) estructura, que se ha proporcionado por el complemento de control de código fuente.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Indica al IDE acerca de un archivo antes de recuperarlos del control de versiones. El `display_string` parámetro se convierte como un [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) estructura, que se ha proporcionado por el complemento de control de código fuente.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Indica al IDE acerca de un archivo una vez recuperado del control de versiones. El `display_string` parámetro se convierte como un [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) estructura, que se ha proporcionado por el complemento de control de código fuente.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Indica al IDE del estado actual de una operación en segundo plano. El `display_string` parámetro se convierte como un [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) estructura, que se ha proporcionado por el complemento de control de código fuente.|

## <a name="return-value"></a>Valor devuelto

|Valor|Descripción|
|-----------|-----------------|
|SCC_MSG_RTN_OK|Se muestra la cadena o la operación se completó correctamente.|
|SCC_MSG_RTN_CANCEL|El usuario desea cancelar la operación.|

## <a name="example"></a>Ejemplo
 Suponga que las llamadas IDE el [SccGet](../extensibility/sccget-function.md) con veinte nombres de archivo. El complemento de control de código fuente desea evitar la cancelación de la operación get de un archivo en el medio. Después de obtener cada archivo, llama a `lpTextOutProc`, pasándole la información de estado en cada archivo y envía un `SCC_MSG_DOCANCEL` mensaje si no tiene ningún estado al informe. Si en cualquier momento el complemento recibe un valor devuelto de `SCC_MSG_RTN_CANCEL` desde el IDE, cancela la operación get inmediatamente, por lo que no hay más archivos se recuperan.

## <a name="structures"></a>Estructuras

### <a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Esta estructura se envía con el `SCC_MSG_BACKGROUND_IS_CANCELLED` mensaje. Sirve para comunicar el identificador de la operación en segundo plano que se ha cancelado.

### <a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Esta estructura se envía con el `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` mensaje. Sirve para comunicar el nombre del archivo que se va a recuperar y el identificador de la operación en segundo plano que realiza la recuperación.

### <a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Esta estructura se envía con el `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` mensaje. Sirve para comunicar el resultado de recuperar el archivo especificado, así como el identificador de la operación en segundo plano que realizó la recuperación. Vea los valores devueltos por la [SccGet](../extensibility/sccget-function.md) para lo que puede proporcionarse como resultado.

### <a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Esta estructura se envía con el `SCC_MSG_BACKGROUND_ON_MESSAGE` mensaje. Sirve para comunicar el estado actual de una operación en segundo plano. El estado se expresa como una cadena que va a mostrar el IDE, y `bIsError` indica la gravedad del mensaje (`TRUE` para un mensaje de error; `FALSE` para una advertencia o un mensaje informativo). También se proporciona el identificador de la operación en segundo plano el estado de envío.

## <a name="code-example"></a>Ejemplo de código
 Este es un breve ejemplo de llamar a `LPTEXTOUTPROC` para enviar el `SCC_MSG_BACKGROUND_ON_MESSAGE` mensaje, que muestra cómo convertir la estructura de la llamada.

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