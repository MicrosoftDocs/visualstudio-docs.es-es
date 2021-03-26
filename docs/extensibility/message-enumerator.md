---
title: Enumerador de mensajes | Microsoft Docs
description: Los miembros de este enumerador se usan para la función TEXTOUTPROC, que es una función de devolución de llamada que el IDE proporciona cuando llama a SccOpenProject.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 113f9fe8470b718a219e967b41bc92ecab2cf3c8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063999"
---
# <a name="message-enumerator"></a>Enumerador de mensajes
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
 SCC_MSG_RTN_CANCEL devolver de la devolución de llamada para indicar la cancelación.

 SCC_MSG_RTN_OK devolver de la devolución de llamada para continuar.

 SCC_MSG_INFO mensaje es informativo.

 SCC_MSG_WARNING mensaje es una advertencia.

 SCC_MSG_ERROR mensaje es un error.

 SCC_MSG_STATUS mensaje está pensado para la barra de estado.

 No SCC_MSG_DOCANCEL ningún texto; IDE devuelve `SCC_MSG_RTN_OK` o `SCC_MSG_RTN_CANCEL` .

 SCC_MSG_STARTCANCEL inicia un bucle CANCEL.

 SCC_MSG_STOPCANCEL detiene el bucle CANCEL.

## <a name="see-also"></a>Consulte también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
