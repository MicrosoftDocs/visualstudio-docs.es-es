---
title: Códigos de mensaje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 92cc911b0217a406302553b3d913c032fc915b4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182962"
---
# <a name="message-codes"></a>Códigos de mensaje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cada línea de mensaje que se muestra en la [vista Mensajes](../debugger/messages-view.md) contiene un código "P", "S", "s" o "R". Estos códigos tienen los siguientes significados:  
  
|Código|Significado|  
|----------|-------------|  
|P|El mensaje se ha enviado a la cola con la función **PostMessage**. No hay información disponible relativa a la disposición final del mensaje.|  
|S|El mensaje se ha enviado con la función **SendMessage**. Esto significa que el remitente no recupera el control hasta que el receptor procesa y devuelve el mensaje. Por tanto, el receptor puede pasar un valor devuelto al remitente.|  
|s|El mensaje se ha enviado, pero la seguridad impide el acceso al valor devuelto.|  
|R|La línea "S" tiene una línea "R" (valor devuelto) correspondiente en la que se muestra el valor devuelto del mensaje. En ocasiones, las llamadas a mensajes están anidadas, lo que significa que un controlador de mensajes envía otro mensaje.|
