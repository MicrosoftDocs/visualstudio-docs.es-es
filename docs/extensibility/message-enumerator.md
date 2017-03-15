---
title: "Enumerador de mensajes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "enumerador de mensajes"
  - "origen control complementos, enumeración de mensaje"
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Enumerador de mensajes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las marcas siguientes se utilizan para la `TEXTOUTPROC` función, que es una función de devolución de llamada que el IDE proporciona al llamar a la [SccOpenProject](../extensibility/sccopenproject-function.md) \(consulte [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) para obtener más información sobre la función de devolución de llamada\).  
  
 Si se solicita el IDE para cancelar el proceso, puede obtener uno de los mensajes de cancelación. En este caso, el origen de control complemento `SCC_MSG_STARTCANCEL` para solicitar el IDE para mostrar el **Cancelar** botón. Después de esto, se puede enviar cualquier conjunto de mensajes normales. Si alguno de estos Devuelve `SCC_MSG_RTN_CANCEL`, a continuación, el complemento se cierra la operación y devuelve. El complemento también sondea `SCC_MSG_DOCANCEL` periódicamente para determinar si el usuario ha cancelado la operación. Cuando se realizan todas las operaciones o si el usuario ha cancelado, envía el complemento `SCC_MSG_STOPCANCEL`. El `SCC_MSG_INFO`, SCC\_MSG\_WARNING, y los tipos SCC\_MSG\_ERROR se utilizan para los mensajes que se muestran en la lista desplegable de mensajes.`SCC_MSG_STATUS` es un tipo especial que indica que el texto debería aparecer en una barra de estado o el área de visualización temporal. No permanecen permanentemente en la lista.  
  
## Sintaxis  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## Miembros  
 SCC\_MSG\_RTN\_CANCEL  
 Devolver desde la devolución de llamada para indicar la cancelación.  
  
 SCC\_MSG\_RTN\_OK  
 Devolver desde la devolución de llamada para continuar.  
  
 SCC\_MSG\_INFO  
 Mensaje es informativo.  
  
 SCC\_MSG\_WARNING  
 Mensaje es una advertencia.  
  
 SCC\_MSG\_ERROR  
 Mensaje es un error.  
  
 SCC\_MSG\_STATUS  
 Mensaje está destinado a la barra de estado.  
  
 SCC\_MSG\_DOCANCEL  
 No hay texto; IDE devuelve `SCC_MSG_RTN_OK` o `SCC_MSG_RTN_CANCEL`.  
  
 SCC\_MSG\_STARTCANCEL  
 Inicia un bucle de cancelación.  
  
 SCC\_MSG\_STOPCANCEL  
 Detiene el bucle de cancelación.  
  
## Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)