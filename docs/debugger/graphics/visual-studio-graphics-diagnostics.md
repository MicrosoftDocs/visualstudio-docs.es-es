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
ms.openlocfilehash: cbc3edfabe041804a632b919eff4e565be9cc5e3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703037"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnóstico de gráficos de Visual Studio
Visual Studio*diagnóstico de gráficos* es un conjunto de herramientas para grabar y, a continuación, analizar los problemas de representación y rendimiento en aplicaciones de Direct3D. Diagnóstico de gráficos puede usarse con aplicaciones que se ejecutan localmente en su PC Windows, en un emulador de dispositivos de Windows o en un dispositivo o equipo remoto.

 El flujo de trabajo de Diagnóstico de gráficos comienza capturando un registro de cómo la aplicación usa Direct3D (en directo, mientras se ejecuta) por lo que el comportamiento se puede analizar inmediatamente, compartir o guardar para más tarde. Se pueden iniciar sesiones de captura y controla manualmente desde Visual Studio o con la herramienta de línea de comandos de captura **dxcap.exe**. También se pueden iniciar sesiones de captura y controlar mediante programación utilizando las API de captura de diagnóstico de gráficos.

 Cuando una sesión de captura registra su contenido, puede reproducirse siempre que se quiera con el *Analizador de gráficos* de Visual Studio, volviendo a crear los fotogramas capturados con exactamente los mismos recursos y comandos de representación que usa la aplicación. A continuación, mediante las herramientas proporcionadas en la ventana del analizador de gráficos, cualquiera de los fotogramas capturados se pueden analizar en detalle. Estas herramientas se pueden usar para examinar cualquier llamada API, recurso, objeto de estado de la canalización, fase de canalización de Direct3D o incluso el historial completo de cualquier píxel de un fotograma capturado. Con el uso conjunto de estas herramientas, un problema de representación se puede explorar de forma intuitiva, empezando por cómo aparece en un fotograma capturado y profundizando hasta su causa principal en el código, los sombreadores o los activos gráficos de origen de la aplicación.

 Para diagnosticar problemas de rendimiento, un fotograma capturado se puede analizar con la herramienta *Análisis de fotogramas*. Esta herramienta explora las posibles optimizaciones del rendimiento cambiando automáticamente la forma en que la aplicación usa Direct3D y realizando automáticamente pruebas comparativas de todas las variaciones. En el pasado, tendría que crear y realizar manualmente pruebas comparativas de este tipo de cambios solo para averiguar cuáles marcaban la diferencia. Con Análisis de fotogramas, solo es necesario que realice los cambios que ya sabe que se amortizarán.

 Diagnóstico de gráficos ayuda a que su aplicación Direct3D con abundantes gráficos tenga mejor aspecto y se ejecute lo mejor posible.

 Seguir [Introducción](overview-of-visual-studio-graphics-diagnostics.md) para obtener más información sobre lo que ofrece el diagnóstico de gráficos de Visual Studio.

## <a name="in-this-section"></a>En esta sección
 [Información general sobre](overview-of-visual-studio-graphics-diagnostics.md) presenta las herramientas y flujo de trabajo de diagnóstico de gráficos.

 [Introducción a](getting-started-with-visual-studio-graphics-diagnostics.md) en esta sección, aprenderá cómo instalar diagnóstico de gráficos de Visual Studio y cómo empezar a usar diagnóstico de gráficos con la aplicación Direct3D.

 [Capturar información de gráficos](capturing-graphics-information.md) para usar diagnóstico de gráficos para examinar un problema de representación en la aplicación, primero debe registrar información acerca de cómo la aplicación utiliza DirectX. Durante la sesión de registro, durante la cual su aplicación se ejecuta con normalidad, debe *capturar* (es decir, seleccionar) los fotogramas de su interés. Las capturas contienen información detallada sobre cómo se presentan los fotogramas. Puede guardar la información capturada como un documento de registro de gráficos para examinarlo más adelante o compartirlo con otros miembros de su equipo.

 [Uso de GPU](gpu-usage.md) para usar diagnóstico de gráficos para generar perfiles de la aplicación, use la herramienta uso de GPU. Uso de GPU puede utilizarse junto con otras herramientas de generación de perfiles, como Uso de CPU, para correlacionar la actividad de CPU y GPU que pueda contribuir a problemas de rendimiento en su aplicación.

 [Documento de registro de gráficos](graphics-log-document.md) para iniciar el examen de un registro de gráficos registrado, utilice la ventana de documento de registro de gráficos para seleccionar un fotograma capturado, o incluso un píxel concreto, para que pueda examinar detalladamente el *eventos* (que es, las llamadas de API de DirectX) que le afecta.

 [Análisis de fotogramas](graphics-frame-analysis.md) después de seleccionar un fotograma, utilice el análisis de fotogramas de gráficos para examinar y adaptar el rendimiento de presentación.

 [Lista de eventos](graphics-event-list.md) después de seleccionar un fotograma, utilice el **lista de eventos gráficos** para examinar sus eventos para determinar si están relacionadas con el problema de presentación.

 [Estado](graphics-state.md) ventana de estado le ayudará a comprender el estado de los gráficos que está activo en el momento del evento actual.

 [Etapas de canalización](graphics-pipeline-stages.md) en el **etapas de canalización de gráficos** ventana, investigar cómo se procesa el evento seleccionado actualmente en cada etapa de la canalización de gráficos para que pueda identificar dónde el problema de presentación primera aparece. Examinar las etapas de canalización es especialmente útil cuando un proyecto no aparece por una transformación incorrecta o cuando una de las etapas produce un resultado que no coincide con lo que espera la etapa siguiente.

 [Pila de llamadas de eventos](graphics-event-call-stack.md) usas el **pila de llamadas de eventos de gráficos** para examinar la pila de llamadas del evento seleccionado actualmente para que pueda ir al código de aplicación que está relacionado con el problema de presentación.

 [Historial de píxeles](graphics-pixel-history.md) utilizando el **historial de píxeles** ventana para analizar cómo afectan el píxel seleccionado actualmente por los eventos que han influido en él, puede identificar el evento o combinación de eventos que provocan ciertos tipos de problemas de representación. El historial de píxeles es especialmente útil cuando un objeto está presentado incorrectamente porque el resultado del sombreador de píxeles es incorrecto o se ha combinado incorrectamente con el búfer del fotograma, o bien cuando un objeto no llega a aparecer porque sus píxeles se han descartado antes de llegar al búfer del fotograma.

 [Tabla de objetos](graphics-object-table.md) usas el **tabla de objetos gráficos** para examinar las propiedades y el contenido de los objetos de Direct3D específicos y los recursos que están en vigor para el evento seleccionado actualmente. La tabla de objetos puede ayudarle a determinar el contexto de dispositivo gráfico que está activo durante un evento y a examinar el contenido de recursos gráficos, como los búferes de constantes, los búferes de vértices y las texturas.

 [Depurador de HLSL](hlsl-shader-debugger.md) para examinar cómo el código del sombreador para el evento seleccionado actualmente y los gráficos de la etapa de canalización se comporta, usa el **depurador de HLSL** para recorrer el código, examinar el contenido de las variables y realizar otras tareas de depuración habituales. También puede utilizar el depurador HLSL para examinar el código del sombreador de cálculo, independientemente de si la canalización de gráficos sigue procesando los resultados o su aplicación tan solo los lee.

 [Herramienta de captura de línea de comandos](command-line-capture-tool.md) usar la herramienta de línea de comandos de captura para capturar y reproducir información de gráficos sin usar Visual Studio o la captura mediante programación rápidamente. En particular, puede usar la herramienta de captura de línea de comandos para la automatización o en un entorno de prueba.

 [Ejemplos](graphics-diagnostics-examples.md) varios ejemplos que demuestran cómo usar las herramientas de diagnóstico de gráficos juntos para diagnosticar diferentes tipos de problemas de representación.

## <a name="related-sections"></a>Secciones relacionadas

| Title | Descripción |
| - | - |
| [Guía de características del depurador](/visualstudio/debugger/debugger-feature-tour) | Introduce la función de depuración en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| [Gráficos de DirectX y juegos](http://go.microsoft.com/fwlink/?LinkId=256498) | Ofrece artículos sobre las tecnologías de gráficos DirectX. |
