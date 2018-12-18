---
title: Códigos de mensaje | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0464042c17a3ed0836b99183dacbe4918823c752
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724631"
---
# <a name="message-codes"></a>Códigos de mensaje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cada línea del mensaje se muestra en [vista mensajes](../debugger/messages-view.md) contiene "P", del,' del,' o 'R' código. Estos códigos tienen los significados siguientes:  
  
|Código|Significado|  
|----------|-------------|  
|P|Se expuso el mensaje a la cola con el **PostMessage** función. No hay disponible información sobre la distribución final del mensaje.|  
|S|Se envió el mensaje con el **SendMessage** función. Esto significa que el remitente no recuperar el control hasta que el receptor procesa y devuelve el mensaje. El receptor por lo tanto, puede pasar un valor devuelto al remitente.|  
|s|Se envió el mensaje, pero la seguridad impide el acceso al valor devuelto.|  
|R|De cada una ' línea tiene una línea 'R' (devolución) correspondiente que enumera el valor devuelto del mensaje. A veces llamadas de mensajes están anidadas, lo que significa que un controlador de mensajes envía otro mensaje.|



