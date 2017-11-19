---
title: "Códigos de mensaje | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a1e724c5c328c86398c43263b19980b5f464a39
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="message-codes"></a>Códigos de mensaje
Cada línea de mensaje que aparece en [vista mensajes](../debugger/messages-view.md) contiene una "P", del,' del,' o 'R' código. Estos códigos tienen los significados siguientes:  
  
|Código|Significado|  
|----------|-------------|  
|P|El mensaje se envió a la cola con la **PostMessage** función. No hay información disponible relativa al procesamiento definitivo del mensaje.|  
|S|El mensaje se envió con el **SendMessage** función. Esto significa que el remitente no retomar el control hasta que el receptor procesa y devuelve el mensaje. El receptor por lo tanto, puede pasar un valor devuelto al remitente.|  
|s|Se envió el mensaje, pero seguridad impide el acceso al valor devuelto.|  
|R|De cada uno de ellos ' línea tiene una línea 'R' (devolución) correspondiente que enumera el valor devuelto del mensaje. En ocasiones llamadas de mensajes están anidadas, lo que significa que un controlador de mensajes envía otro mensaje.|