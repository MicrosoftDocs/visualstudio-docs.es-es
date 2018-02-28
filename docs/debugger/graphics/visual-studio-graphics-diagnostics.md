---
title: "Diagnóstico de gráficos de Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 69965b35d919c4170c54cbfa1eed5d5a52dc8287
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnóstico de gráficos de Visual Studio
Visual Studio*diagnóstico de gráficos* es un conjunto de herramientas para grabar y analizar problemas de representación y rendimiento de aplicaciones de Direct3D. Diagnóstico de gráficos puede usarse con aplicaciones que se ejecutan localmente en su PC de Windows, en un emulador de dispositivos de Windows o en un dispositivo o equipo remoto.  
  
 El flujo de trabajo de Diagnóstico de gráficos comienza capturando un registro de cómo la aplicación usa Direct3D (en directo, mientras se ejecuta) por lo que el comportamiento se puede analizar inmediatamente, compartir o guardar para más tarde. Se pueden iniciar sesiones de captura y controlarlas manualmente desde Visual Studio o con la herramienta de captura de línea de comandos **dxcap.exe**. También se pueden iniciar sesiones de captura y controlarlas mediante programación con las API de captura de Diagnóstico de gráficos.  
  
 Después de una sesión de captura se ha registrado su contenido puede reproducirse en Visual Studio *analizador de gráficos* en cualquier momento, volver a crear los fotogramas capturados con exactamente los mismos recursos y comandos de representación que la aplicación usa. Luego, con las herramientas que se ofrecen en la ventana del Analizador de gráficos, se puede analizar en detalle cualquiera de los fotogramas capturados. Estas herramientas se pueden usar para examinar cualquier llamada API, recurso, objeto de estado de la canalización, fase de canalización de Direct3D o incluso el historial completo de cualquier píxel de un fotograma capturado. Con el uso conjunto de estas herramientas, un problema de representación se puede explorar de forma intuitiva, empezando por cómo aparece en un fotograma capturado y profundizando hasta su causa principal en el código, los sombreadores o los activos gráficos de origen de la aplicación.  
  
 Para diagnosticar problemas de rendimiento, se puede analizar un fotograma capturado mediante el uso de la *análisis de fotogramas* herramienta. Esta herramienta explora las posibles optimizaciones del rendimiento cambiando automáticamente la forma en que la aplicación usa Direct3D y realizando automáticamente pruebas comparativas de todas las variaciones. En el pasado, tendría que crear y realizar manualmente pruebas comparativas de este tipo de cambios solo para averiguar cuáles marcaban la diferencia. Con Análisis de fotogramas, solo es necesario que realice los cambios que ya sabe que se amortizarán.  
  
 Diagnóstico de gráficos ayuda a que su aplicación Direct3D con abundantes gráficos tenga mejor aspecto y se ejecute lo mejor posible.  
  
 Continuarán [Introducción](overview-of-visual-studio-graphics-diagnostics.md) para obtener más información sobre lo que ofrece el diagnóstico de gráficos de Visual Studio.  
  
## <a name="in-this-section"></a>En esta sección  
 [Información general](overview-of-visual-studio-graphics-diagnostics.md)  
 Introduce el flujo de trabajo y las herramientas de Diagnóstico de gráficos.  
  
 [Introducción](getting-started-with-visual-studio-graphics-diagnostics.md)  
 En esta sección, obtendrá información sobre cómo instalar Diagnóstico de gráficos de Visual Studio y cómo empezar a usar Diagnóstico de gráficos con su aplicación Direct3D.  
  
 [Capturing Graphics Information](capturing-graphics-information.md)  
 Para utilizar Diagnóstico de gráficos para examinar un problema de presentación en su aplicación, primero debe registrar información sobre cómo la aplicación utiliza DirectX. Durante la sesión de grabación, como la aplicación se ejecuta con normalidad, se *capturar* (es decir, seleccionar) los fotogramas que le interesa. Las capturas contienen información detallada sobre cómo se presentan los fotogramas. Puede guardar la información capturada como un documento de registro de gráficos para examinarlo más adelante o compartirlo con otros miembros de su equipo.  
  
 [Uso de GPU](gpu-usage.md)  
 Para usar Diagnóstico de gráficos a fin de generar perfiles de la aplicación, utilice la herramienta Uso de GPU. Uso de GPU puede utilizarse junto con otras herramientas de generación de perfiles, como Uso de CPU, para correlacionar la actividad de CPU y GPU que pueda contribuir a problemas de rendimiento en su aplicación.  
  
 [Documento de registro de gráficos](graphics-log-document.md)  
 Para iniciar el examen de un registro de gráficos registrado, utilice la ventana de documento de registro de gráficos para seleccionar un fotograma capturado, o incluso un píxel concreto, para que se puede examinar con detalle la *eventos* (es decir, la API DirectX llama) que le afectan .  
  
 [Análisis de fotogramas](graphics-frame-analysis.md)  
 Después de seleccionar un fotograma, utilice el Análisis de Fotograma Gráficos para examinar y adaptar el rendimiento de presentación.  
  
 [Lista de eventos](graphics-event-list.md)  
 Después de seleccionar un fotograma, utilice la **lista de eventos gráficos** para examinar sus eventos para determinar si están relacionados con el problema de presentación.  
  
 [Estado](graphics-state.md)  
 La ventana de estado le ayuda a comprender el estado de los gráficos que está activo en el momento del evento actual.  
  
 [Etapas de canalización](graphics-pipeline-stages.md)  
 En el **etapas de canalización de gráficos** ventana, investigar cómo se procesa el evento seleccionado actualmente por cada fase de la canalización de gráficos para que pueda identificar dónde aparece en primer lugar el problema de presentación. Examinar las etapas de canalización es especialmente útil cuando un proyecto no aparece por una transformación incorrecta o cuando una de las etapas produce un resultado que no coincide con lo que espera la etapa siguiente.  
  
 [Pila de llamadas de eventos](graphics-event-call-stack.md)  
 Usa el **pila de llamadas de eventos de gráficos** para examinar la pila de llamadas del evento seleccionado actualmente para que pueda ir al código de aplicación que está relacionado con el problema de presentación.  
  
 [Historial de píxeles](graphics-pixel-history.md)  
 Mediante el uso de la **historial de píxeles** ventana para analizar cómo se ve afectado el píxel seleccionado actualmente por los eventos que han influido en él, puede identificar el evento o combinación de eventos que causa ciertos tipos de problemas de representación. El historial de píxeles es especialmente útil cuando un objeto está presentado incorrectamente porque el resultado del sombreador de píxeles es incorrecto o se ha combinado incorrectamente con el búfer del fotograma, o bien cuando un objeto no llega a aparecer porque sus píxeles se han descartado antes de llegar al búfer del fotograma.  
  
 [Tabla de objetos](graphics-object-table.md)  
 Usa el **tabla de objetos gráficos** para examinar las propiedades y el contenido de los objetos de Direct3D específicos y recursos que están en vigor para el evento seleccionado actualmente. La tabla de objetos puede ayudarle a determinar el contexto de dispositivo gráfico que está activo durante un evento y a examinar el contenido de recursos gráficos, como los búferes de constantes, los búferes de vértices y las texturas.  
  
 [Depurador de HLSL](hlsl-shader-debugger.md)  
 Para examinar cómo el código del sombreador para el evento seleccionado actualmente y los gráficos de la etapa de canalización se comporta, utilice la **depurador de HLSL** para recorrer el código, examinar el contenido de las variables y realizar otras tareas de depuración habituales. También puede utilizar el depurador HLSL para examinar el código del sombreador de cálculo, independientemente de si la canalización de gráficos sigue procesando los resultados o su aplicación tan solo los lee.  
  
 [Herramienta de captura de línea de comandos](command-line-capture-tool.md)  
 Use la herramienta de captura de línea de comandos para capturar y reproducir rápidamente información de gráficos sin usar Visual Studio ni la captura mediante programación. En particular, puede usar la herramienta de captura de línea de comandos para la automatización o en un entorno de prueba.  
  
 [Ejemplos](graphics-diagnostics-examples.md)  
 Hay varios ejemplos que demuestran cómo utilizar las herramientas de Diagnóstico de gráficos para diagnosticar diferentes tipos de problemas de presentación.  
  
## <a name="related-sections"></a>Secciones relacionadas  
  
|Title|Descripción|  
|-----------|-----------------|  
|[Guía de características del depurador](../debugging-in-visual-studio.md)|Introduce la función de depuración en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].|  
|[Gráficos de DirectX y juegos](http://go.microsoft.com/fwlink/?LinkId=256498)|Ofrece artículos sobre las tecnologías de gráficos DirectX.|