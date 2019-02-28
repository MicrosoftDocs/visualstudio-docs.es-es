---
title: Salida (pestaña), cuadro de diálogo Opciones de mensaje | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Output
ms.assetid: 22dd48c2-6d17-41b1-b84c-9ddeaef68411
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63268fdbc320e78a697c181112dbeaaf8ad161ab
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690557"
---
# <a name="output-tab-message-options-dialog-box"></a>Pestaña Salida (Cuadro de diálogo Opciones de mensaje)
Use la **salida** tab para especificar qué datos de cada mensaje a la lista en [vista mensajes](../debugger/messages-view.md). Para mostrar el [cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md), elija **los mensajes de registro** desde el **Spy** menú.

 Las siguientes opciones están disponibles en el **salida** pestaña:

 **Números de línea** mostrar números de línea.

 **Nivel de anidamiento de mensaje** mensajes anidados con un punto por nivel de prefijo.

 **Parámetros de mensaje sin formato** mostrar hexadecimal **wParam** y **lParam** valores.

 **Descodificar mensaje parámetros** mostrar los resultados de la descodificación de mensaje específico de la **wParam** y **lParam** valores.

 **Sin procesar de los valores devueltos** mostrar hexadecimal **lResult** valor devuelto.

 **Descodifica los valores devueltos por** mostrar los resultados de la descodificación de mensaje específico de la **lResult** valor devuelto.

 **Hora de origen del mensaje** el tiempo transcurrido desde que se inició el sistema de Windows (sólo para mensajes expuestos).

 **Posición del Mouse del mensaje** las coordenadas de pantalla del puntero del mouse cuando se expuso el mensaje (sólo para mensajes expuestos).

 **Líneas como máximo** limitar el número de líneas que se conservan en la vista mensajes actualmente seleccionada.

 **También los mensajes de registro al archivo** especificar un archivo de salida para el registro de mensajes. Este archivo de salida se escribe simultáneamente con la ventana de registro de mensajes.

 **Guardar configuración como predeterminada** guardar la configuración anterior para las nuevas ventanas de flujo de mensajes. Esta configuración se guarda al salir de Spy ++.