---
title: Salida (Pestaña), Opciones de mensaje (Cuadro de diálogo) | Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905080"
---
# <a name="output-tab-message-options-dialog-box"></a>Pestaña Salida (Cuadro de diálogo Opciones de mensaje)
Use la pestaña **Salida** para especificar qué datos de cada mensaje se van a mostrar en la [Vista Mensajes](../debugger/messages-view.md). Para mostrar el [cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md), elija **Mensajes de registro** en el menú de **Spy**.

 En la pestaña **Salida** están disponibles los valores siguientes:

 **Números de línea** Muestra los números de línea.

 **Nivel de anidamiento del mensaje** Antepone un punto por nivel a los mensajes anidados.

 **Parámetros de mensaje originales** Muestra los valores hexadecimales **wParam** e **lParam**.

 **Parámetros de mensaje descodificados** Muestra los resultados de la descodificación específica de un mensaje de los valores **wParam** e **lParam**.

 **Valores devueltos originales** Muestra el valor hexadecimal **lResult** devuelto.

 **Valores devueltos descodificados** Muestra los resultados de la descodificación específica de un mensaje del valor devuelto **lResult**.

 **Hora de origen del mensaje** Tiempo transcurrido desde que se inició el sistema Windows (solo para mensajes publicados).

 **Posición del mouse en el mensaje** Coordenadas de pantalla del mouse cuando se publicó el mensaje (solo para mensajes publicados).

 **Líneas como máximo** Limita el número de líneas que se conservan en la vista Mensajes seleccionada.

 **Registrar también mensajes en archivo** Especifica un archivo de salida para el registro de mensajes. Este archivo de salida se escribe simultáneamente con la ventana de registro de mensajes.

 **Guardar la configuración como predeterminada** Guarda la configuración anterior para las nuevas ventanas de flujo de mensajes. Esta configuración se guarda al salir de Spy++.