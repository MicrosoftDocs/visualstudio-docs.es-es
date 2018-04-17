---
title: Códigos de mensaje | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96f980570bcbee7a26bf742556379899c0a88436
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="message-codes"></a>Códigos de mensaje
Cada línea de mensaje que aparece en [vista mensajes](../debugger/messages-view.md) contiene una "P", del,' del,' o 'R' código. Estos códigos tienen los significados siguientes:  
  
|Código|Significado|  
|----------|-------------|  
|P|El mensaje se envió a la cola con la **PostMessage** función. No hay información disponible relativa al procesamiento definitivo del mensaje.|  
|S|El mensaje se envió con el **SendMessage** función. Esto significa que el remitente no retomar el control hasta que el receptor procesa y devuelve el mensaje. El receptor por lo tanto, puede pasar un valor devuelto al remitente.|  
|s|Se envió el mensaje, pero seguridad impide el acceso al valor devuelto.|  
|R|De cada uno de ellos ' línea tiene una línea 'R' (devolución) correspondiente que enumera el valor devuelto del mensaje. En ocasiones llamadas de mensajes están anidadas, lo que significa que un controlador de mensajes envía otro mensaje.|