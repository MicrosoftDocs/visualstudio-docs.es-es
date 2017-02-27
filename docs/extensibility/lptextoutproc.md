---
title: "LPTEXTOUTPROC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LPTEXTOUTPROC"
helpviewer_keywords: 
  - "SccMsgDataOnMessage (estructura)"
  - "SccMsgDataOnBeforeGetFile (estructura)"
  - "SccMsgDataIsCancelled (estructura)"
  - "Función de devolución de llamada LPTEXTOUTPROC"
  - "SccMsgDataOnAfterGetFile (estructura)"
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# LPTEXTOUTPROC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando el usuario ejecuta una operación de control de código fuente desde dentro del entorno de desarrollo integrado \(IDE\), el complemento de control de código fuente puede transmitir los mensajes de error o estado relativos a la operación. El complemento puede mostrar sus propios cuadros de mensaje para este propósito. Sin embargo, una integración más, el complemento puede pasar cadenas en el IDE, que se muestran a continuación, en su forma nativa de mostrar información de estado. Este mecanismo es el `LPTEXTOUTPROC` puntero de función. El IDE implementa esta función \(que se describe en más detalle a continuación\) para mostrar el error y estado.  
  
 El IDE pasa el control de código fuente complemento un puntero de función a esta función, como la `lpTextOutProc` parámetro al llamar a la [SccOpenProject](../extensibility/sccopenproject-function.md). Durante una operación de control de código fuente, por ejemplo, en medio de una llamada a la [SccGet](../extensibility/sccget-function.md) que implican muchos archivos, el complemento puede llamar a la `LPTEXTOUTPROC` función, periódicamente para pasar las cadenas para mostrar. El IDE puede mostrar estas cadenas en una barra de estado en una ventana o en un cuadro de mensaje independiente, según corresponda. Opcionalmente, el IDE puede mostrar determinados mensajes con un **Cancelar** botón. Esto permite al usuario cancelar la operación y le ofrece el IDE de la capacidad de pasar esta información al complemento.  
  
## Signature  
 Salida del IDE de la función tiene la firma siguiente:  
  
```cpp#  
typedef LONG (*LPTEXTOUTPROC) ( LPSTR display_string, LONG mesg_type );  
```  
  
## Parámetros  
 display\_string  
 Una cadena de texto para mostrar. Esta cadena no debe finalizar con un valor devuelto o un salto de línea de carro.  
  
 mesg\_type  
 El tipo de mensaje. La tabla siguiente enumeran los valores admitidos para este parámetro.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Se considera el mensaje de Error, advertencia o información.|  
|`SCC_MSG_STATUS`|El mensaje muestra el estado y puede mostrarse en la barra de estado.|  
|`SCC_MSG_DOCANCEL`|Se envía con ninguna cadena de mensaje.|  
|`SCC_MSG_STARTCANCEL`|Comienza a mostrar un **Cancelar** botón.|  
|`SCC_MSG_STOPCANCEL`|Deja de mostrar una **Cancelar** botón.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Solicita el IDE si la operación en segundo plano es cancelar: IDE devuelve `SCC_MSG_RTN_CANCEL` Si la operación se canceló; en caso contrario, devuelve `SCC_MSG_RTN_OK`. El `display_string` parámetro se convierte como un [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) estructura, que es proporcionado por el complemento de control de código fuente.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Indica al IDE acerca de un archivo antes de recuperarlos del control de versiones. El `display_string` parámetro se convierte como un [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) estructura, que es proporcionado por el complemento de control de código fuente.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Indica al IDE acerca de un archivo una vez recuperado del control de versiones. El `display_string` parámetro se convierte como un [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) estructura, que es proporcionado por el complemento de control de código fuente.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Indica al IDE del estado actual de una operación en segundo plano. El `display_string` parámetro se convierte como un [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) estructura, que es proporcionado por el complemento de control de código fuente.|  
  
## Valor devuelto  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_MSG\_RTN\_OK|Se muestra la cadena o la operación se completó correctamente.|  
|SCC\_MSG\_RTN\_CANCEL|El usuario desea cancelar la operación.|  
  
## Ejemplo  
 Suponga que las llamadas IDE la [SccGet](../extensibility/sccget-function.md) con veinte nombres de archivo. El complemento de control de código fuente desea evitar la cancelación de la operación en el medio de un archivo obtener. Después de obtener cada archivo, llama a `lpTextOutProc`, pasando la información de estado en cada archivo y envía una `SCC_MSG_DOCANCEL` mensaje si no tiene ningún estado al informe. Si en cualquier momento el complemento recibe un valor devuelto de `SCC_MSG_RTN_CANCEL` desde el IDE, cancela la operación get inmediatamente, por lo que no hay más archivos se recuperan.  
  
## Estructuras  
  
###  <a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled  
  
```cpp#  
typedef struct { DWORD dwBackgroundOperationID; } SccMsgDataIsCancelled;  
```  
  
 Esta estructura se envía con el `SCC_MSG_BACKGROUND_IS_CANCELLED` mensaje. Se utiliza para comunicar el identificador de la operación en segundo plano que se ha cancelado.  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile  
  
```cpp#  
typedef struct { DWORD dwBackgroundOperationID; PCSTR szFile; } SccMsgDataOnBeforeGetFile;  
```  
  
 Esta estructura se envía con el `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` mensaje. Se utiliza para comunicar el nombre del archivo que se va a recuperar y el identificador de la operación en segundo plano que realiza la recuperación.  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile  
  
```cpp#  
typedef struct { DWORD dwBackgroundOperationID; PCSTR szFile; SCCRTN sResult; } SccMsgDataOnAfterGetFile;  
```  
  
 Esta estructura se envía con el `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` mensaje. Se utiliza para comunicar el resultado de recuperar el archivo especificado, así como el identificador de la operación en segundo plano que hizo la recuperación. Consulte los valores devueltos por la [SccGet](../extensibility/sccget-function.md) para lo que puede dar como resultado.  
  
###  <a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage  
 \[C\+\+\]  
  
```  
typedef struct { DWORD dwBackgroundOperationID; PCSTR szMessage; BOOL bIsError; } SccMsgDataOnMessage;  
```  
  
 Esta estructura se envía con el `SCC_MSG_BACKGROUND_ON_MESSAGE` mensaje. Se utiliza para comunicar el estado actual de una operación en segundo plano. El estado se expresa como una cadena que va a mostrar el IDE y `bIsError` indica la gravedad del mensaje \(`TRUE` para un mensaje de error `FALSE` para un mensaje informativo o advertencia\). También se indica el identificador de la operación en segundo plano el estado de envío.  
  
## Ejemplo de código  
 Este es un ejemplo breve de la llamada a `LPTEXTOUTPROC` para enviar el `SCC_MSG_BACKGROUND_ON_MESSAGE` mensaje, que muestra cómo convertir la estructura de la llamada.  
  
```cpp#  
LONG SendStatusMessage( LPTEXTOUTPROC pTextOutProc, DWORD         dwBackgroundID, LPCTSTR       pStatusMsg, BOOL          bIsError) { SccMsgDataOnMessage msgData = { 0 }; LONG                result  = 0; msgData.dwBackgroundOperationID = dwBackgroundID; msgData.szMessage               = pStatusMsg; msgData.bIsError                = bIsError; result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE); return result; }  
```  
  
## Vea también  
 [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)