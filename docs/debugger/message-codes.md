---
title: Códigos de mensaje | Microsoft Docs
description: Obtenga información sobre los significados de los códigos de mensaje que se muestran en cada línea de mensaje en la vista Mensajes.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e4b836a5d4c1faad6b4c0375e2ec51d759816889
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903615"
---
# <a name="message-codes"></a>Códigos de mensaje
Cada línea de mensaje que se muestra en la [vista Mensajes](../debugger/messages-view.md) contiene un código "P", "S", "s" o "R". Estos códigos tienen los siguientes significados:

|Código|Significado|
|----------|-------------|
|P|El mensaje se ha enviado a la cola con la función **PostMessage**. No hay información disponible relativa a la disposición final del mensaje.|
|S|El mensaje se ha enviado con la función **SendMessage**. Esto significa que el remitente no recupera el control hasta que el receptor procesa y devuelve el mensaje. Por tanto, el receptor puede pasar un valor devuelto al remitente.|
|s|El mensaje se ha enviado, pero la seguridad impide el acceso al valor devuelto.|
|R|La línea "S" tiene una línea "R" (valor devuelto) correspondiente en la que se muestra el valor devuelto del mensaje. En ocasiones, las llamadas a mensajes están anidadas, lo que significa que un controlador de mensajes envía otro mensaje.|