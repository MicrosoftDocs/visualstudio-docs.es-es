---
title: Enumerador de mensajes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37932ce6e64361692d659355e9ab6e88ee5462ed
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713183"
---
# <a name="message-enumerator"></a>Enumerador de mensajes
Las marcas siguientes se usan para la `TEXTOUTPROC` función, que es una función de devolución de llamada que el IDE proporciona cuando llama a la [SccOpenProject](../extensibility/sccopenproject-function.md) (consulte [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) para obtener más información sobre la devolución de llamada función).

 Si el IDE se pide a cancelar el proceso, puede obtener uno de los mensajes de cancelación. En este caso, el origen de control usa complemento `SCC_MSG_STARTCANCEL` para pedir el IDE para mostrar el **cancelar** botón. Una vez hecho esto, se puede enviar cualquier conjunto de mensajes normales. Si alguno de estos Devuelve `SCC_MSG_RTN_CANCEL`, a continuación, el complemento se cierra la operación y devuelve. El complemento también sondea `SCC_MSG_DOCANCEL` periódicamente para determinar si el usuario ha cancelado la operación. Cuando se realizan todas las operaciones, o si el usuario ha cancelado, envía el complemento `SCC_MSG_STOPCANCEL`. El `SCC_MSG_INFO`, SCC_MSG_WARNING, y los tipos SCC_MSG_ERROR se utilizan para los mensajes que se muestran en la lista desplazable de mensajes. `SCC_MSG_STATUS` es un tipo especial que indica que el texto debería aparecer en una barra de estado o el área de presentación temporal. No permanecen permanentemente en la lista.

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
 Devolver SCC_MSG_RTN_CANCEL de devolución de llamada para indicar la cancelación.

 SCC_MSG_RTN_OK devolver desde la devolución de llamada para continuar.

 SCC_MSG_INFO mensaje es informativo.

 Mensaje de SCC_MSG_WARNING es una advertencia.

 Mensaje SCC_MSG_ERROR es un error.

 Mensaje SCC_MSG_STATUS está pensada para la barra de estado.

 Texto sin SCC_MSG_DOCANCEL; Devuelve el IDE `SCC_MSG_RTN_OK` o `SCC_MSG_RTN_CANCEL`.

 SCC_MSG_STARTCANCEL inicia un cancelar un bucle.

 SCC_MSG_STOPCANCEL detiene el bucle de cancelación.

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)