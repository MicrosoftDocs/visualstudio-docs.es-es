---
title: Cambio de la tecla de ayuda F1
description: Describe cómo volver a asignar o quitar la asignación de la tecla F1
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
robots: noindex,nofollow
manager: jmartens
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 30073b31fb98f604313c8de5d45687f3f768a374
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961695"
---
# <a name="change-the-f1-help-key-in-visual-studio"></a>Cambio de la tecla de ayuda F1 en Visual Studio

Si quiere usar la tecla F1 para una función distinta al servicio de ayuda F1, o si solo quiere deshabilitar la ayuda con F1, puede quitar o modificar la asignación de la tecla.

> [!IMPORTANT]
> Si quiere deshabilitar la ayuda F1 debido a problemas de rendimiento, se recomienda modificar temporalmente la asignación de la tecla para que pueda probar las mejoras del el servicio de ayuda F1 en las actualizaciones de Visual Studio. En la mayoría de los escenarios, F1 es una manera fácil de abrir páginas de referencia para las palabras clave del idioma y API desde el editor de código, o bien para abrir páginas de ayuda asociadas a elementos de Windows o de la interfaz de usuario en el IDE. Si la deshabilita, la deshabilitará para todos los usos dentro de Visual Studio.

**Para deshabilitar la ayuda F1:**

1. En Visual Studio, seleccione **Herramientas** > **Opciones** y, en **Entorno**, seleccione **Teclado**.

1. En el cuadro de texto **Mostrar los comandos que contengan**, escriba **Help.f1** para filtrar la vista de los comandos.

   ![Deshabilitación de la ayuda F1](../not-in-toc/media/disable-f1-help-key.png)

1. Seleccione **Quitar** para quitar la asignación de la tecla.

1. Seleccione el cuadro de texto **Presionar teclas de método abreviado**.

1. En el teclado, presione una tecla o una combinación de teclas nueva para la ayuda F1, como **Alt + F1**, seleccione **Asignar** y, luego, seleccione **Aceptar**.

Para más información sobre la configuración de los métodos abreviados de teclado, consulte [Identificar y personalizar métodos abreviados de teclado en Visual Studio](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
