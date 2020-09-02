---
title: Enumerador de mensajes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6bd42c825cd45068e13178856e524268b426ec53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194339"
---
# <a name="message-enumerator"></a>Enumerador de mensaje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las marcas siguientes se usan para la `TEXTOUTPROC` función, que es una función de devolución de llamada que el IDE proporciona cuando llama a [SccOpenProject](../extensibility/sccopenproject-function.md) (vea [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) para obtener más información sobre la función de devolución de llamada).  
  
 Si se pide al IDE que cancele el proceso, puede obtener uno de los mensajes de cancelación. En este caso, el complemento de control de código fuente utiliza `SCC_MSG_STARTCANCEL` para pedir al IDE que muestre el botón **Cancelar** . Después, se puede enviar cualquier conjunto de mensajes normales. Si cualquiera de estos devuelven `SCC_MSG_RTN_CANCEL` , el complemento sale de la operación y devuelve. El complemento también sondea `SCC_MSG_DOCANCEL` periódicamente para determinar si el usuario ha cancelado la operación. Cuando se realizan todas las operaciones, o si el usuario se ha cancelado, el complemento envía `SCC_MSG_STOPCANCEL` . Los `SCC_MSG_INFO` tipos, SCC_MSG_WARNING y SCC_MSG_ERROR se utilizan para los mensajes que se muestran en la lista de desplazamiento de mensajes. `SCC_MSG_STATUS` es un tipo especial que indica que el texto debe aparecer en una barra de estado o en un área de presentación temporal. No se mantiene de forma permanente en la lista.  
  
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
 Vuelva de la devolución de llamada para indicar la cancelación.  
  
 SCC_MSG_RTN_OK  
 Vuelva de la devolución de llamada para continuar.  
  
 SCC_MSG_INFO  
 El mensaje es informativo.  
  
 SCC_MSG_WARNING  
 El mensaje es una advertencia.  
  
 SCC_MSG_ERROR  
 El mensaje es un error.  
  
 SCC_MSG_STATUS  
 El mensaje está pensado para la barra de estado.  
  
 SCC_MSG_DOCANCEL  
 Sin texto; IDE devuelve `SCC_MSG_RTN_OK` o `SCC_MSG_RTN_CANCEL` .  
  
 SCC_MSG_STARTCANCEL  
 Inicia un bucle de cancelación.  
  
 SCC_MSG_STOPCANCEL  
 Detiene el bucle CANCEL.  
  
## <a name="see-also"></a>Consulte también  
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
