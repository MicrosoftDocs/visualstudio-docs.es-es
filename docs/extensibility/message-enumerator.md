---
title: Enumerador de mensajes | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 000b853c1f25d8b68ccdda87e6c0496aeeaaca0e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="message-enumerator"></a>Enumerador de mensajes
Las marcas siguientes se usan para la `TEXTOUTPROC` función, que es una función de devolución de llamada que el IDE proporciona cuando llama a la [SccOpenProject](../extensibility/sccopenproject-function.md) (consulte [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) para obtener más información sobre la devolución de llamada función).  
  
 Si se solicita el IDE para cancelar el proceso, puede obtener uno de los mensajes de cancelación. En este caso, el origen de control utiliza complemento `SCC_MSG_STARTCANCEL` para solicitar el IDE para mostrar el **cancelar** botón. Después de esto, se puede enviar cualquier conjunto de mensajes normales. Si alguno de estos Devuelve `SCC_MSG_RTN_CANCEL`, a continuación, se cierra la operación y devuelve el complemento. El complemento también sondea `SCC_MSG_DOCANCEL` periódicamente para determinar si el usuario ha cancelado la operación. Cuando se realizan todas las operaciones, o si el usuario ha cancelado, envía el complemento `SCC_MSG_STOPCANCEL`. El `SCC_MSG_INFO`, SCC_MSG_WARNING, y se utilizan los tipos SCC_MSG_ERROR para los mensajes que se muestren en la lista desplazable de mensajes. `SCC_MSG_STATUS`es un tipo especial que indica que el texto debería aparecer en una barra de estado o el área de presentación temporal. No permanecen permanentemente en la lista.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
## <a name="members"></a>Miembros  
 SCC_MSG_RTN_CANCEL  
 Se devuelve de devolución de llamada para indicar la cancelación.  
  
 SCC_MSG_RTN_OK  
 Se devuelve de devolución de llamada para continuar.  
  
 SCC_MSG_INFO  
 Mensaje es informativo.  
  
 SCC_MSG_WARNING  
 Mensaje es una advertencia.  
  
 SCC_MSG_ERROR  
 Mensaje es un error.  
  
 SCC_MSG_STATUS  
 Mensaje está destinado a la barra de estado.  
  
 SCC_MSG_DOCANCEL  
 Ningún texto; Devuelve el IDE `SCC_MSG_RTN_OK` o `SCC_MSG_RTN_CANCEL`.  
  
 SCC_MSG_STARTCANCEL  
 Inicia un bucle de cancelación.  
  
 SCC_MSG_STOPCANCEL  
 Detiene el bucle de cancelación.  
  
## <a name="see-also"></a>Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)