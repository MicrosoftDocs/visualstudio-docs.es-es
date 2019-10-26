---
title: Diagnóstico de gráficos | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 875c2578d5f8cc1aa68cc624adc0a6e2a1713472
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911364"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnóstico de gráficos de Visual Studio
Visual Studio*diagnóstico de gráficos* es un conjunto de herramientas para grabar y analizar los problemas de representación y rendimiento en las aplicaciones de Direct3D. Diagnóstico de gráficos puede usarse con aplicaciones que se ejecutan localmente en su PC Windows, en un emulador de dispositivos de Windows o en un dispositivo o equipo remoto.

 El flujo de trabajo de Diagnóstico de gráficos comienza capturando un registro de cómo la aplicación usa Direct3D (en directo, mientras se ejecuta) por lo que el comportamiento se puede analizar inmediatamente, compartir o guardar para más tarde. Las sesiones de captura se pueden iniciar y controlar manualmente desde Visual Studio o con la herramienta de captura de línea de comandos **dxcap. exe**. Las sesiones de captura también se pueden iniciar y controlar mediante programación con las API de captura de Diagnóstico de gráficos.

 Cuando una sesión de captura registra su contenido, puede reproducirse siempre que se quiera con el *Analizador de gráficos* de Visual Studio, volviendo a crear los fotogramas capturados con exactamente los mismos recursos y comandos de representación que usa la aplicación. A continuación, con las herramientas proporcionadas en la ventana del analizador de gráficos, se puede analizar en detalle cualquiera de los fotogramas capturados. Estas herramientas se pueden usar para examinar cualquier llamada API, recurso, objeto de estado de la canalización, fase de canalización de Direct3D o incluso el historial completo de cualquier píxel de un fotograma capturado. Con el uso conjunto de estas herramientas, un problema de representación se puede explorar de forma intuitiva, empezando por cómo aparece en un fotograma capturado y profundizando hasta su causa principal en el código, los sombreadores o los activos gráficos de origen de la aplicación.

 Para diagnosticar problemas de rendimiento, un fotograma capturado se puede analizar con la herramienta *Análisis de fotogramas*. Esta herramienta explora las posibles optimizaciones del rendimiento cambiando automáticamente la forma en que la aplicación usa Direct3D y realizando automáticamente pruebas comparativas de todas las variaciones. En el pasado, tendría que crear y realizar manualmente pruebas comparativas de este tipo de cambios solo para averiguar cuáles marcaban la diferencia. Con Análisis de fotogramas, solo es necesario que realice los cambios que ya sabe que se amortizarán.

 Diagnóstico de gráficos ayuda a que su aplicación Direct3D con abundantes gráficos tenga mejor aspecto y se ejecute lo mejor posible.

 Continúe con la [información general](overview-of-visual-studio-graphics-diagnostics.md) para obtener más información sobre lo que ofrece Visual Studio diagnóstico de gráficos.

## <a name="in-this-section"></a>En esta sección
 [Información general](overview-of-visual-studio-graphics-diagnostics.md) Presenta el Diagnóstico de gráficos el flujo de trabajo y las herramientas.

 [Introducción](getting-started-with-visual-studio-graphics-diagnostics.md) En esta sección, aprenderá a instalar Visual Studio Diagnóstico de gráficos y cómo empezar a usar Diagnóstico de gráficos con la aplicación Direct3D.

 [Capturar información de gráficos](capturing-graphics-information.md) Para usar Diagnóstico de gráficos para examinar un problema de representación en la aplicación, primero debe registrar información sobre cómo la aplicación usa DirectX. Durante la sesión de registro, durante la cual su aplicación se ejecuta con normalidad, debe *capturar* (es decir, seleccionar) los fotogramas de su interés. Las capturas contienen información detallada sobre cómo se presentan los fotogramas. Puede guardar la información capturada como un documento de registro de gráficos para examinarlo más adelante o compartirlo con otros miembros de su equipo.

 [Uso de GPU](gpu-usage.md) Para usar Diagnóstico de gráficos para generar perfiles de la aplicación, use la herramienta uso de GPU. Uso de GPU puede utilizarse junto con otras herramientas de generación de perfiles, como Uso de CPU, para correlacionar la actividad de CPU y GPU que pueda contribuir a problemas de rendimiento en su aplicación.

 [Documento de registro de gráficos](graphics-log-document.md) Para iniciar el examen de un registro de gráficos grabado, use la ventana de documento de registro de gráficos para seleccionar un fotograma capturado, o incluso un píxel específico, para que pueda examinar en detalle los *eventos* (es decir, las llamadas de la API de DirectX) que lo afecten.

 [Análisis de fotogramas](graphics-frame-analysis.md) Después de seleccionar un fotograma, utilice Análisis de fotogramas de gráficos para examinar y ajustar el rendimiento de la representación.

 [Lista de eventos](graphics-event-list.md) Después de seleccionar un fotograma, utilice la **lista de eventos gráficos** para examinar sus eventos y determinar si están relacionados con el problema de representación.

 [Estado](graphics-state.md) de La ventana Estado le ayuda a comprender el estado de los gráficos que está activo en el momento del evento actual.

 [Fases de canalización](graphics-pipeline-stages.md) En la ventana **etapas de canalización de gráficos** , investigue cómo se procesa el evento seleccionado actualmente en cada fase de la canalización de gráficos para que pueda identificar dónde aparece por primera vez el problema de representación. Examinar las etapas de canalización es especialmente útil cuando un proyecto no aparece por una transformación incorrecta o cuando una de las etapas produce un resultado que no coincide con lo que espera la etapa siguiente.

 [Pila de llamadas de eventos](graphics-event-call-stack.md) Use la **pila de llamadas de eventos gráficos** para examinar la pila de llamadas del evento seleccionado actualmente para poder navegar al código de la aplicación relacionado con el problema de representación.

 [Historial de píxeles](graphics-pixel-history.md) Mediante el uso de la ventana **historial de píxeles de gráfico** para analizar cómo afecta el píxel seleccionado actualmente a los eventos que lo influyen, puede identificar el evento o la combinación de eventos que causan ciertos tipos de problemas de representación. El historial de píxeles es especialmente útil cuando un objeto está presentado incorrectamente porque el resultado del sombreador de píxeles es incorrecto o se ha combinado incorrectamente con el búfer del fotograma, o bien cuando un objeto no llega a aparecer porque sus píxeles se han descartado antes de llegar al búfer del fotograma.

 [Tabla de objetos](graphics-object-table.md) La tabla de **objetos gráficos** se utiliza para examinar las propiedades y el contenido de objetos y recursos de Direct3D específicos que están en vigor para el evento seleccionado actualmente. La tabla de objetos puede ayudarle a determinar el contexto de dispositivo gráfico que está activo durante un evento y a examinar el contenido de recursos gráficos, como los búferes de constantes, los búferes de vértices y las texturas.

 [Depurador de HLSL](hlsl-shader-debugger.md) Para examinar cómo se comporta el código del sombreador para la fase de canalización de gráficos y eventos seleccionados actualmente, use el **depurador de HLSL** para recorrer el código, examinar el contenido de las variables y realizar otras tareas de depuración típicas. También puede utilizar el depurador HLSL para examinar el código del sombreador de cálculo, independientemente de si la canalización de gráficos sigue procesando los resultados o su aplicación tan solo los lee.

 [Herramienta de captura de línea de comandos](command-line-capture-tool.md) Use la herramienta de captura de línea de comandos para capturar y reproducir rápidamente información de gráficos sin usar Visual Studio ni la captura mediante programación. En particular, puede usar la herramienta de captura de línea de comandos para la automatización o en un entorno de prueba.

 [Ejemplos](graphics-diagnostics-examples.md) de Varios ejemplos muestran cómo usar las herramientas de Diagnóstico de gráficos juntas para diagnosticar diferentes tipos de problemas de representación.

## <a name="related-sections"></a>Secciones relacionadas

| Title | Descripción |
| - | - |
| [Guía de características del depurador](/visualstudio/debugger/debugger-feature-tour) | Introduce la función de depuración en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| [Gráficos y juegos de DirectX](/windows/win32/directx) | Ofrece artículos sobre las tecnologías de gráficos DirectX. |
