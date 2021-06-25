---
title: Enumeración de mensajes | Microsoft Docs
description: Los miembros de este enumerador se usan para la función TEXTOUTPROC, que es una función de devolución de llamada que proporciona el IDE cuando llama a SccOpenProject.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77c49f79ccdcfc4aa0325b89dfb38f3f8d4da721
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902597"
---
# <a name="message-enumerator"></a>Enumerador de mensajes
Las marcas siguientes se usan para la función , que es una función de devolución de llamada que proporciona el IDE cuando llama `TEXTOUTPROC` a [SccOpenProject](../extensibility/sccopenproject-function.md) (vea [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) para obtener más información sobre la función de devolución de llamada).

 Si se solicita al IDE que cancele el proceso, puede obtener uno de los mensajes de cancelación. En este caso, el complemento de control de código fuente usa `SCC_MSG_STARTCANCEL` para pedir al IDE que muestre el **botón** Cancelar. Después de esto, se puede enviar cualquier conjunto de mensajes normales. Si alguno de estos devuelve , el complemento sale de `SCC_MSG_RTN_CANCEL` la operación y devuelve . El complemento también sondea `SCC_MSG_DOCANCEL` periódicamente para determinar si el usuario ha cancelado la operación. Cuando se realizan todas las operaciones o si el usuario ha cancelado, el complemento envía `SCC_MSG_STOPCANCEL` . Los tipos , SCC_MSG_WARNING y SCC_MSG_ERROR se usan para los mensajes que se muestran en la `SCC_MSG_INFO` lista de desplazamiento de mensajes. `SCC_MSG_STATUS` es un tipo especial que indica que el texto debe aparecer en una barra de estado o en un área de presentación temporal. No permanece permanentemente en la lista.

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
 SCC_MSG_RTN_CANCEL de devolución de llamada para indicar la cancelación.

 SCC_MSG_RTN_OK de devolución de llamada para continuar.

 SCC_MSG_INFO message es informativo.

 SCC_MSG_WARNING message es una advertencia.

 SCC_MSG_ERROR mensaje es un error.

 SCC_MSG_STATUS message está pensado para la barra de estado.

 SCC_MSG_DOCANCEL texto; EL IDE devuelve `SCC_MSG_RTN_OK` o `SCC_MSG_RTN_CANCEL` .

 SCC_MSG_STARTCANCEL inicia un bucle de cancelación.

 SCC_MSG_STOPCANCEL detiene el bucle de cancelación.

## <a name="see-also"></a>Consulta también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
