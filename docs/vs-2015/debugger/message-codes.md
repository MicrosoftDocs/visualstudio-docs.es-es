---
title: Códigos de mensaje | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d995a884b8d223a4415549739c9701fd72886a56
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47565870"
---
# <a name="message-codes"></a>Códigos de mensaje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [códigos de mensaje](https://docs.microsoft.com/visualstudio/debugger/message-codes).  
  
Cada línea del mensaje se muestra en [vista mensajes](../debugger/messages-view.md) contiene "P", del,' del,' o 'R' código. Estos códigos tienen los significados siguientes:  
  
|Código|Significado|  
|----------|-------------|  
|P|Se expuso el mensaje a la cola con el **PostMessage** función. No hay disponible información sobre la distribución final del mensaje.|  
|S|Se envió el mensaje con el **SendMessage** función. Esto significa que el remitente no recuperar el control hasta que el receptor procesa y devuelve el mensaje. El receptor por lo tanto, puede pasar un valor devuelto al remitente.|  
|s|Se envió el mensaje, pero la seguridad impide el acceso al valor devuelto.|  
|R|De cada una ' línea tiene una línea 'R' (devolución) correspondiente que enumera el valor devuelto del mensaje. A veces llamadas de mensajes están anidadas, lo que significa que un controlador de mensajes envía otro mensaje.|



