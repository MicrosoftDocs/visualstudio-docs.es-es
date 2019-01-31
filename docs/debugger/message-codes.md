---
title: Códigos de mensaje | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3899da3b668406a701ce5c1c4935b531754d10e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55017089"
---
# <a name="message-codes"></a>Códigos de mensaje
Cada línea del mensaje se muestra en [vista mensajes](../debugger/messages-view.md) contiene "P", del,' del,' o 'R' código. Estos códigos tienen los significados siguientes:  
  
|Código|Significado|  
|----------|-------------|  
|P|Se expuso el mensaje a la cola con el **PostMessage** función. No hay disponible información sobre la distribución final del mensaje.|  
|S|Se envió el mensaje con el **SendMessage** función. Esto significa que el remitente no recuperar el control hasta que el receptor procesa y devuelve el mensaje. El receptor por lo tanto, puede pasar un valor devuelto al remitente.|  
|s|Se envió el mensaje, pero la seguridad impide el acceso al valor devuelto.|  
|R|De cada una ' línea tiene una línea 'R' (devolución) correspondiente que enumera el valor devuelto del mensaje. A veces llamadas de mensajes están anidadas, lo que significa que un controlador de mensajes envía otro mensaje.|