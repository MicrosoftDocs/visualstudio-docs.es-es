---
title: Diagnóstico de gráficos | Microsoft Docs
description: Diagnóstico de gráficos de Visual Studio es un conjunto de herramientas para el registro y el análisis de la actividad de Direct3D. Úselas para solucionar los problemas de representación y rendimiento.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 679b9464ef10f121bbe38f486291b135872fb36b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861509"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnóstico de gráficos de Visual Studio
>[!NOTE]
> Visual Studio recomienda PIX en Windows para juegos de DirectX 12. [PIX en Windows](https://aka.ms/PIXonWindows) es una herramienta de optimización y depuración del rendimiento que es totalmente compatible con DirectX 12. [Obtenga más información](visual-studio-graphics-diagnostics-directx-12.md) o [descárguelo aquí](https://aka.ms/downloadPIX).

El *Diagnóstico de gráficos* de Visual Studio es un conjunto de herramientas para grabar y analizar problemas de representación y rendimiento de las aplicaciones de Direct3D. Diagnóstico de gráficos puede usarse con aplicaciones que se ejecutan localmente en su PC Windows, en un emulador de dispositivos de Windows o en un dispositivo o equipo remoto.

 El flujo de trabajo de Diagnóstico de gráficos comienza capturando un registro de cómo la aplicación usa Direct3D (en directo, mientras se ejecuta) por lo que el comportamiento se puede analizar inmediatamente, compartir o guardar para más tarde. Se pueden iniciar sesiones de captura y controlarlas manualmente desde Visual Studio o con la herramienta de captura de línea de comandos **dxcap.exe**. También se pueden iniciar sesiones de captura y controlarlas mediante programación con las API de captura de Diagnóstico de gráficos.

 Cuando una sesión de captura registra su contenido, puede reproducirse siempre que se quiera con el *Analizador de gráficos* de Visual Studio, volviendo a crear los fotogramas capturados con exactamente los mismos recursos y comandos de representación que usa la aplicación. Luego, con las herramientas que se ofrecen en la ventana del Analizador de gráficos, se puede analizar en detalle cualquiera de los fotogramas capturados. Estas herramientas se pueden usar para examinar cualquier llamada API, recurso, objeto de estado de la canalización, fase de canalización de Direct3D o incluso el historial completo de cualquier píxel de un fotograma capturado. Con el uso conjunto de estas herramientas, un problema de representación se puede explorar de forma intuitiva, empezando por cómo aparece en un fotograma capturado y profundizando hasta su causa principal en el código, los sombreadores o los activos gráficos de origen de la aplicación.

 Para diagnosticar problemas de rendimiento, un fotograma capturado se puede analizar con la herramienta *Análisis de fotogramas*. Esta herramienta explora las posibles optimizaciones del rendimiento cambiando automáticamente la forma en que la aplicación usa Direct3D y realizando automáticamente pruebas comparativas de todas las variaciones. En el pasado, tendría que crear y realizar manualmente pruebas comparativas de este tipo de cambios solo para averiguar cuáles marcaban la diferencia. Con Análisis de fotogramas, solo es necesario que realice los cambios que ya sabe que se amortizarán.

 Diagnóstico de gráficos ayuda a que su aplicación Direct3D con abundantes gráficos tenga mejor aspecto y se ejecute lo mejor posible.

 Vaya a [Información general](overview-of-visual-studio-graphics-diagnostics.md) para obtener más información sobre lo que ofrece Diagnóstico de gráficos de Visual Studio.

## <a name="in-this-section"></a>En esta sección
 [Información general](overview-of-visual-studio-graphics-diagnostics.md) Se presenta el flujo de trabajo y las herramientas de Diagnóstico de gráficos.

 [Introducción](getting-started-with-visual-studio-graphics-diagnostics.md) En esta sección, obtendrá información sobre cómo instalar Diagnóstico de gráficos de Visual Studio y cómo empezar a usarlo con la aplicación Direct3D.

 [Captura de información de gráficos](capturing-graphics-information.md) Para usar Diagnóstico de gráficos a fin de examinar un problema de presentación en la aplicación, primero debe registrar información sobre cómo se usa DirectX en la aplicación. Durante la sesión de registro, durante la cual su aplicación se ejecuta con normalidad, debe *capturar* (es decir, seleccionar) los fotogramas de su interés. Las capturas contienen información detallada sobre cómo se presentan los fotogramas. Puede guardar la información capturada como un documento de registro de gráficos para examinarlo más adelante o compartirlo con otros miembros de su equipo.

 [Uso de GPU](../../profiling/gpu-usage.md) Para usar Diagnóstico de gráficos a fin de generar perfiles de la aplicación, utilice la herramienta Uso de GPU. Uso de GPU puede utilizarse junto con otras herramientas de generación de perfiles, como Uso de CPU, para correlacionar la actividad de CPU y GPU que pueda contribuir a problemas de rendimiento en su aplicación.

 [Documento de registro de gráficos](graphics-log-document.md) Para iniciar el examen de un registro de gráficos registrado, use la ventana del documento Registro de gráficos para seleccionar un fotograma capturado (o incluso un píxel concreto) para que pueda examinar con detalle los *eventos* (es decir, las llamadas de la API DirectX) que le afectan.

 [Análisis de fotogramas](graphics-frame-analysis.md) Después de seleccionar un fotograma, use el Análisis de fotogramas de gráficos para examinar y adaptar el rendimiento de la presentación.

 [Lista de eventos](graphics-event-list.md) Después de seleccionar un fotograma, use la **Lista de eventos de gráficos** para examinar sus eventos y determinar si están relacionados con el problema de representación.

 [Estado](graphics-state.md) La ventana de estado le ayuda a comprender el estado de los gráficos que está activo en el momento del evento actual.

 [Etapas de canalización](graphics-pipeline-stages.md) En la ventana **Etapas de canalización de gráficos**, puede investigar cómo se procesa el evento seleccionado actualmente en cada etapa de la canalización de gráficos para identificar dónde aparece por primera vez el problema de representación. Examinar las etapas de canalización es especialmente útil cuando un proyecto no aparece por una transformación incorrecta o cuando una de las etapas produce un resultado que no coincide con lo que espera la etapa siguiente.

 [Pila de llamadas de eventos](graphics-event-call-stack.md) Use la **Pila de llamadas de eventos gráficos** para examinar la pila de llamadas del evento seleccionado actualmente para que pueda navegar hasta código de la aplicación relacionado con el problema de representación.

 [Historial de píxeles](graphics-pixel-history.md) Si usa la ventana **Historial de píxeles de gráfico** para analizar cómo los eventos que han influido en él afectan al píxel seleccionado actualmente, puede identificar el evento o combinación de eventos que causa ciertos tipos de problemas de representación. El historial de píxeles es especialmente útil cuando un objeto está presentado incorrectamente porque el resultado del sombreador de píxeles es incorrecto o se ha combinado incorrectamente con el búfer del fotograma, o bien cuando un objeto no llega a aparecer porque sus píxeles se han descartado antes de llegar al búfer del fotograma.

 [Tabla de objetos](graphics-object-table.md) La **Tabla de objetos gráficos** se usa para examinar las propiedades y el contenido de objetos y recursos de Direct3D específicos que están en vigor para el evento seleccionado actualmente. La tabla de objetos puede ayudarle a determinar el contexto de dispositivo gráfico que está activo durante un evento y a examinar el contenido de recursos gráficos, como los búferes de constantes, los búferes de vértices y las texturas.

 [Depurador HLSL](hlsl-shader-debugger.md) Para examinar cómo se comporta el código del sombreador para el evento seleccionado actualmente y la etapa de canalización de gráficos, use el **Depurador HLSL** para examinar el código, examinar los contenidos de las variables y realizar otras tareas de depuración habituales. También puede utilizar el depurador HLSL para examinar el código del sombreador de cálculo, independientemente de si la canalización de gráficos sigue procesando los resultados o su aplicación tan solo los lee.

 [Herramienta de captura de línea de comandos](command-line-capture-tool.md) Use la herramienta de captura de línea de comandos para capturar y reproducir rápidamente información de gráficos sin usar Visual Studio ni capturas mediante programación. En particular, puede usar la herramienta de captura de línea de comandos para la automatización o en un entorno de prueba.

 [Ejemplos](graphics-diagnostics-examples.md) Hay varios ejemplos que demuestran cómo usar las herramientas de Diagnóstico de gráficos para diagnosticar diferentes tipos de problemas de presentación.

## <a name="related-sections"></a>Secciones relacionadas

| Title | Descripción |
| - | - |
| [Guía de características del depurador](../debugger-feature-tour.md) | Introduce la función de depuración en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| [Gráficos y juegos de DirectX](/windows/win32/directx) | Ofrece artículos sobre las tecnologías de gráficos DirectX. |
| [Compatibilidad de DirectX 12 con Visual Studio](visual-studio-graphics-diagnostics-directx-12.md) | Más información sobre la compatibilidad de DirectX 12 con Visual Studio |
