---
title: Enumerador de mensajes ( Message Enumerator) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e09b72bd228839268cffc228dd0dc503cc82bd9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702509"
---
# <a name="message-enumerator"></a>Enumerador de mensajes
Los siguientes indicadores `TEXTOUTPROC` se utilizan para la función, que es una función de devolución de llamada que el IDE proporciona cuando llama a la [SccOpenProject](../extensibility/sccopenproject-function.md) (consulte [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) para obtener más información sobre la función de devolución de llamada).

 Si se pide al IDE que cancele el proceso, puede recibir uno de los mensajes de cancelación. En este caso, el complemento `SCC_MSG_STARTCANCEL` de control de código fuente se usa para pedir al IDE que muestre el botón **Cancelar.** Después de esto, se puede enviar cualquier conjunto de mensajes normales. Si cualquiera de `SCC_MSG_RTN_CANCEL`estas devuelve , el complemento cierra la operación y devuelve. El complemento también sondea `SCC_MSG_DOCANCEL` periódicamente para determinar si el usuario ha cancelado la operación. Cuando se realizan todas las operaciones, o si el `SCC_MSG_STOPCANCEL`usuario ha cancelado, el complemento envía . Los `SCC_MSG_INFO`tipos , SCC_MSG_WARNING y SCC_MSG_ERROR se usan para los mensajes que se muestran en la lista de mensajes de desplazamiento. `SCC_MSG_STATUS`es un tipo especial que indica que el texto debe aparecer en una barra de estado o un área de visualización temporal. No permanece permanentemente en la lista.

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
 SCC_MSG_RTN_CANCEL Devolver de devolución de llamada para indicar la cancelación.

 SCC_MSG_RTN_OK Devolver de la devolución de llamada para continuar.

 SCC_MSG_INFO mensaje es informativo.

 SCC_MSG_WARNING mensaje es una advertencia.

 SCC_MSG_ERROR mensaje es un error.

 SCC_MSG_STATUS Mensaje está destinado a la barra de estado.

 SCC_MSG_DOCANCEL Sin texto; IDE `SCC_MSG_RTN_OK` devuelve `SCC_MSG_RTN_CANCEL`o .

 SCC_MSG_STARTCANCEL Inicia un bucle de cancelación.

 SCC_MSG_STOPCANCEL Detiene el bucle de cancelación.

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
