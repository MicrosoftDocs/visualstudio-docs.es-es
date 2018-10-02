---
title: Explorador de rendimiento | Microsoft Docs
ms.custom: ''
ms.date: 06/19/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance
- vs.performance.wizard.website
helpviewer_keywords:
- performance tools [Visual Studio ALM]
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 837c8d405245237962888a0a689fbdd17f6a0a92
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35669335"
---
# <a name="performance-explorer"></a>Explorador de rendimiento

Las Herramientas de generación de perfiles de Visual Studio permiten a los desarrolladores medir, evaluar y detectar los problemas relacionados con el rendimiento del código. Estas herramientas se integran totalmente en el IDE a fin de proporcionar al usuario una experiencia accesible y sin fisuras.

La generación de perfiles de una aplicación es bastante sencilla. Comienza por la creación de una nueva sesión de rendimiento. En Visual Studio Team System Development Edition, puede usar el Asistente para crear una nueva sesión de rendimiento. Una vez finalizada la sesión de rendimiento, los datos recopilados durante la generación de perfiles se guardan en un archivo .*vsp*. Puede ver el archivo .*vsp* desde el IDE. Existen varias vistas de informe que ayudan a ver y detectar los problemas de rendimiento a partir de los datos recopilados.

Las herramientas de generación de perfiles también pueden usarse desde la línea de comandos. Esto ofrece al usuario la flexibilidad de ejecutar estas herramientas desde la línea de comandos o usarlas para automatizar tareas que usan script.

Para obtener más información sobre temas actuales y avanzados relacionados con el rendimiento y la generación de perfiles, busque en los temas y blogs de Microsoft en Microsoft Developer Network. Utilice las palabras clave Enterprise Performance Tools Team.

## <a name="common-tasks"></a>Tareas comunes

|Tarea|Contenido relacionado|
|----------|---------------------|
|**Técnicas para Windows 8 y versiones posteriores**|[Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)|
|**Entender los conceptos de generación de perfiles:** proporciona información sobre los conceptos y los términos que utilizará para recopilar, ver y analizar el rendimiento del código mediante las herramientas de generación de perfiles.|[Información general](../profiling/overviews-performance-tools.md)|
|**Comenzar el aprendizaje:** proporciona información sobre los procedimientos básicos que utilizará al recopilar, ver y analizar el rendimiento del código mediante las herramientas de generación de perfiles. Pruébelo con un tutorial práctico.|[Introducción](../profiling/getting-started-with-performance-tools.md)|
|**Configurar una sesión de generación de perfiles:** proporciona información sobre cómo especificar los proyectos o binarios de los que se van a generar perfiles, seleccionar un método de generación de perfiles, elegir los datos de rendimiento que se van a recopilar y establecer otras opciones de la sesión de generación de perfiles.|[Configuración de sesiones de rendimiento](../profiling/configuring-performance-sessions.md)|
|**Controlar los datos que recopila el generador de perfiles:** proporciona información sobre cómo utilizar las propiedades de una sesión de rendimiento y los procedimientos interactivos para iniciar y detener la generación de perfiles, además de cómo limitar los datos de rendimiento que va a recopilar a la información estrictamente deseada.|[Control de la recopilación de datos](../profiling/controlling-data-collection.md)|
|**Buscar problemas de rendimiento:** proporciona información sobre cómo ver y analizar los datos de rendimiento recopilados en la ventana de la vista Informe de las herramientas de generación de perfiles.|[Análisis de datos de herramientas de rendimiento](../profiling/analyzing-performance-tools-data.md)|
|**Analizar cambios de rendimiento:** proporciona información sobre cómo comparar dos archivos de datos del generador de perfiles para analizar los cambios de rendimiento.|[Comparación de archivos de datos de rendimiento](../profiling/comparing-performance-data-files.md)|
|**Guardar y compartir los resultados:** proporciona información sobre cómo guardar datos de generación de perfiles para archivarlos o compartirlos.|[Guardar y exportar datos de herramientas de rendimiento](../profiling/saving-and-exporting-performance-tools-data.md)|
|**Generación automática de perfiles:** proporciona información sobre cómo utilizar las herramientas de generación de perfiles desde el símbolo del sistema.|[Generar perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)|
|**Controlar la generación de perfiles mediante programación:** proporciona información sobre cómo utilizar las API administradas y nativas de las herramientas de generación de perfiles para controlar la recolección de datos del código fuente directamente.|[API de herramientas de generación de perfiles](../profiling/profiling-tools-apis.md)|
|**Solucionar problemas de generación de perfiles**|[Solución de problemas de herramientas de rendimiento](../profiling/troubleshooting-performance-tools-issues.md)|

## <a name="see-also"></a>Vea también

[Primer vistazo a la generación de perfiles](../profiling/profiling-feature-tour.md)