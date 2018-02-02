---
title: "Cómo: habilitar y deshabilitar el análisis de la solución completa para código administrado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 64b541093aaf1a710976c0f53a3214b5d2a47e0d
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Cómo: habilitar y deshabilitar el análisis de la solución completa para código administrado

*Completa el análisis de la solución* es una característica de Visual Studio que le permite ver los problemas de análisis de código sólo en los archivos abiertos de Visual C# o Visual Basic en la solución, o también en el código los archivos que están cerrados. De forma predeterminada, los análisis de la solución completa se habilita para Visual Basic y se deshabilita para Visual C#.

Aunque es útil poder ver todos los problemas en todos los archivos, puede resultar confuso. Puede también lenta Visual Studio hacia abajo si la solución es muy grande o tiene una gran cantidad de archivos. Para limitar el número de problemas que se muestra y mejorar el rendimiento de Visual Studio, puede deshabilitar el análisis de la solución completa. Fácilmente puede volver a habilitar esta característica si es necesario.

## <a name="to-toggle-full-solution-analysis"></a>Para activar o desactivar el análisis de la solución completa

1. Para abrir el **opciones** elegir cuadro de diálogo, en la barra de menús de Visual Studio **herramientas** > **opciones**.

1. En el **opciones** diálogo cuadro, elija **Editor de texto** > **C#** o **básica**  >   **Advanced**.

1. Seleccione el **Habilitar análisis de la solución completa** casilla de verificación para habilitar el análisis de la solución completa, o desactive la casilla para deshabilitarlo. Elija la **Aceptar** botón cuando haya terminado.

    ![Habilitar la casilla de verificación de análisis de la solución completa. ] (../code-quality/media/fsa_toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Resultados de habilitar y deshabilitar el análisis de la solución completa

En la siguiente captura de pantalla, puede ver los resultados cuando se habilita el análisis de la solución completa. Todos los errores y problemas de análisis de código en *todos los* de los archivos de la solución aparecen, independientemente de si los archivos están abiertos.

![Análisis de la solución completa habilitada. ] (../code-quality/media/fsa_enabled.png "FSA_Enabled")

Captura de pantalla siguiente muestra los resultados de la misma solución después de deshabilitar el análisis de la solución completa. Solo los errores y problemas de análisis de código en abren solución archivos aparecen en la lista de errores.

![Análisis de la solución completa deshabilitado. ] (../code-quality/media/fsa_disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>Deshabilitar automáticamente el análisis de la solución completa

Si Visual Studio detecta que 200MB o menos de memoria del sistema está disponible en él, deshabilita automáticamente análisis de la solución completa (así como otras características) si está habilitado. Si esto ocurre, aparece una alerta que le informa de este. Un botón le permite volver a habilitar el análisis de la solución completa si lo desea.

![Texto de alerta suspender el análisis de la solución completa](../code-quality/media/fsa_alert.png "FSA_Alert")