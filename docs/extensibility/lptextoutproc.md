---
title: LPTEXTOUTPROC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 235d98ba6a5ca665857b8a18db5ca823ecc0c7c1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
Cuando el usuario ejecuta una operación de control de código fuente desde dentro del entorno de desarrollo integrado (IDE), el complemento de control de origen conviene transmitir mensajes de error o estado relativos a la operación. El complemento puede mostrar sus propios cuadros de mensaje para este propósito. Sin embargo, para la integración sin problemas más, el complemento puede pasar cadenas para el IDE, lo que, a continuación, se muestra de manera nativa de mostrar información de estado. El mecanismo para esto es el `LPTEXTOUTPROC` puntero de función. El IDE implementa esta función (que se describe con más detalle a continuación) para mostrar el error y estado.  
  
 El IDE pasa al control de código fuente complemento un puntero a función a esta función, como la `lpTextOutProc` parámetro, al llamar a la [SccOpenProject](../extensibility/sccopenproject-function.md). Durante una operación de control de código fuente, por ejemplo, en el medio de una llamada a la [SccGet](../extensibility/sccget-function.md) que implican muchos archivos, el complemento puede llamar a la `LPTEXTOUTPROC` función, periódicamente pasar cadenas para mostrarlas. El IDE puede mostrar estas cadenas en una barra de estado, en una ventana de salida, o en un cuadro de mensaje diferente, según corresponda. Si lo desea, el IDE puede mostrar determinados mensajes con un **cancelar** botón. Esto permite al usuario cancelar la operación, y proporciona el IDE de la capacidad de pasar esta información para el complemento.  
  
## <a name="signature"></a>Signatura  
 El IDE de salida de función tiene la siguiente firma:  
  
```cpp  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>Parámetros  
 display_string  
 Una cadena de texto para mostrar. Esta cadena no debe terminar con un valor devuelto o un avance de línea de carro.  
  
 mesg_type  
 El tipo de mensaje. En la tabla siguiente se enumera los valores admitidos para este parámetro.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|El mensaje se considera información, advertencia o Error.|  
|`SCC_MSG_STATUS`|El mensaje de estado muestra y se pueden mostrar en la barra de estado.|  
|`SCC_MSG_DOCANCEL`|Se envía con ninguna cadena de mensaje.|  
|`SCC_MSG_STARTCANCEL`|Comienza a mostrar un **cancelar** botón.|  
|`SCC_MSG_STOPCANCEL`|Deja de mostrar una **cancelar** botón.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Pide IDE si la operación en segundo plano es que debe cancelarse: IDE devuelve `SCC_MSG_RTN_CANCEL` si la operación se canceló; en caso contrario, devuelve `SCC_MSG_RTN_OK`. El `display_string` parámetro se convierte como un [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) estructura, que le ha suministrado el complemento de control de código fuente.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Indica el IDE acerca de un archivo antes de recuperarlos del control de versiones. El `display_string` parámetro se convierte como un [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) estructura, que le ha suministrado el complemento de control de código fuente.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Indica el IDE sobre un archivo después de que se ha recuperado del control de versiones. El `display_string` parámetro se convierte como un [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) estructura, que le ha suministrado el complemento de control de código fuente.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Indica el IDE del estado actual de una operación en segundo plano. El `display_string` parámetro se convierte como un [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) estructura, que le ha suministrado el complemento de control de código fuente.|  
  
## <a name="return-value"></a>Valor devuelto  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|Se muestra la cadena o la operación se completó correctamente.|  
|SCC_MSG_RTN_CANCEL|El usuario desea cancelar la operación.|  
  
## <a name="example"></a>Ejemplo  
 Suponga que las llamadas IDE la [SccGet](../extensibility/sccget-function.md) con veinte nombres de archivo. Para evitar la cancelación de la operación en el medio de una operación get archivo desea que el complemento de control de código fuente. Después de obtener cada archivo, llama a `lpTextOutProc`, pasar la información de estado en cada archivo y envía un `SCC_MSG_DOCANCEL` mensaje si no tiene ningún estado para notificar. Si en cualquier momento el complemento recibe un valor devuelto de `SCC_MSG_RTN_CANCEL` desde el IDE, cancela la operación get inmediatamente, por lo que no hay más archivos se recuperan.  
  
## <a name="structures"></a>Estructuras  
  
###  <a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 Esta estructura se envía con el `SCC_MSG_BACKGROUND_IS_CANCELLED` mensaje. Se utiliza para comunicarse el identificador de la operación en segundo plano que se ha cancelado.  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 Esta estructura se envía con el `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` mensaje. Se usa para comunicar el nombre del archivo que se va a recuperar y el identificador de la operación en segundo plano que realiza la recuperación.  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 Esta estructura se envía con el `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` mensaje. Se usa para comunicar el resultado de recuperar el archivo especificado, así como el identificador de la operación en segundo plano que hizo la recuperación. Ver los valores devueltos para el [SccGet](../extensibility/sccget-function.md) para lo que se puede dar como resultado.  
  
###  <a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 Esta estructura se envía con el `SCC_MSG_BACKGROUND_ON_MESSAGE` mensaje. Se usa para comunicar el estado actual de una operación en segundo plano. El estado se expresa como una cadena que va a mostrar el IDE y `bIsError` indica la gravedad del mensaje (`TRUE` para un mensaje de error; `FALSE` para una advertencia o un mensaje informativo). También se indica el identificador de la operación en segundo plano el estado de envío.  
  
## <a name="code-example"></a>Ejemplo de código  
 Este es un breve ejemplo de llamar al método `LPTEXTOUTPROC` para enviar el `SCC_MSG_BACKGROUND_ON_MESSAGE` mensaje, que muestra cómo convertir la estructura de la llamada.  
  
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
 [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)