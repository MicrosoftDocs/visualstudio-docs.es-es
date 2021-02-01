---
title: Especificar opciones de instrumentación adicionales | Microsoft Docs
description: Obtenga más información sobre cómo puede instrumentar archivos binarios mediante el IDE de Visual Studio o con las herramientas de la línea de comandos.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: aaa6a222ca320ff9e8e3d117c2218e170d67d683
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721858"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Procedimiento Especificar opciones de instrumentación adicionales

Puede instrumentar archivos binarios mediante el IDE de Visual Studio o con las herramientas de la línea de comandos. Si instrumenta un binario desde el IDE, puede controlar el volumen de datos que se recopila. Para ello, especifique opciones de instrumentación adicionales a la herramienta [VSInstr](../profiling/vsinstr.md). Estas opciones están disponibles por sesión o por destino. Por ejemplo, para incluir o excluir funciones concretas durante el proceso de instrumentación, utilice la opción de instrumentación adicional en el nivel de destino.

> [!IMPORTANT]
> Cada análisis que se inserta modifica ligeramente el comportamiento del programa original. Esta modificación provoca una sobrecarga durante el análisis. Aunque se resta una aproximación de esta sobrecarga, afecta sutilmente al control del tiempo en las aplicaciones multiproceso. Las opciones de la herramienta [VSInstr](../profiling/vsinstr.md) ayudan a controlar la recolección de datos durante la generación de perfiles.

## <a name="to-specify-additional-instrumentation-option"></a>Para especificar la opción de instrumentación adicional

1. En el **Explorador de rendimiento**, seleccione la **Sesión de rendimiento** y después haga clic con el botón derecho y seleccione **Propiedades**.

2. En las **Páginas de propiedades**, haga clic en las propiedades **Avanzadas**.

3. Escriba las opciones en el cuadro **Opciones de instrumentación adicionales**.

     Por ejemplo, utilice /CONTROL:THREAD para especificar el nivel de generación de perfiles. Para obtener una lista completa de opciones, consulte [VSInstr](../profiling/vsinstr.md).

4. Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también

[Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)
[Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)
