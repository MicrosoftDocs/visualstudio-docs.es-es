---
title: Introducción a las herramientas de rendimiento | Microsoft Docs
description: Obtenga información sobre las distintas formas que ofrece Visual Studio para recopilar, ver y analizar los datos de rendimiento del código.
ms.custom: SEO-VS-2020
ms.date: 11/04/2018
ms.topic: conceptual
helpviewer_keywords:
- getting started, performance
- getting started, profiling tools
ms.assetid: 02085214-a8e4-40fd-9b26-32391a7a7082
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1eb65e3cb8273f36cd9255bc0a3a2f8e91689f39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907370"
---
# <a name="getting-started-with-performance-tools"></a>Introducción a las herramientas de rendimiento

Visual Studio ofrece varias maneras de recopilar, ver y analizar los datos de rendimiento del código. En muchos casos, el mejor modo de empezar a usar las herramientas de rendimiento es usar los valores predeterminados del **Asistente para rendimiento**. El asistente recopila estadísticas de aplicación que pueden indicar problemas de rendimiento en el código.

- En la ventana **Lista de errores** de Visual Studio aparecen advertencias de rendimiento que notifican problemas de codificación comunes. Puede navegar desde la advertencia al código fuente y a temas detallados de la Ayuda que le ayudarán a escribir código más eficaz.

- Los informes de rendimiento proporcionan vistas de diferentes niveles de la estructura, las líneas de código fuente y los procesos de la aplicación. Los informes de rendimiento muestran datos de ejecución de la aplicación, desde las funciones que realizan llamadas y a las que se llama de una función específica en el árbol de llamadas de toda la aplicación.

Para generar rápidamente el perfil de un proyecto, una aplicación o un sitio web de ASP.NET, seleccione **Depurar** > **Generador de perfiles de rendimiento** y elija **Asistente de rendimiento**. Para obtener instrucciones detalladas, vea [Guía para principiantes para el muestreo de la CPU](../profiling/beginners-guide-to-cpu-sampling.md) y [Recopilación de datos de rendimiento de un sitio web](../profiling/how-to-collect-performance-data-for-a-web-site.md).

Para especificar y configurar una sesión de generación de perfiles de rendimiento manualmente, seleccione **Depurar** > **Generador de perfiles** > **Explorador de rendimiento**. Use la carpeta **Destinos** y las páginas **Propiedades** en el **Explorador de rendimiento** para configurar las sesiones. Para obtener instrucciones, vea [Cómo: Crear manualmente sesiones de rendimiento](../profiling/how-to-manually-create-performance-sessions.md).

**Vea también:**

- [Información general (herramientas de rendimiento)](../profiling/overviews-performance-tools.md)
- [Analizar datos de herramientas de rendimiento](../profiling/analyzing-performance-tools-data.md)
- [Usar reglas de rendimiento para analizar datos](../profiling/using-performance-rules-to-analyze-data.md)
- [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)
