---
title: Recopilar datos de simultaneidad de subprocesos y procesos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 424675726dd91664923cde0a3a5ad5573d51b4d5
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34548344"
---
# <a name="collect-thread-and-process-concurrency-data"></a>Recopilar datos de simultaneidad de subprocesos y procesos

El método de generación de perfiles de simultaneidad de las Herramientas de generación de perfiles de Visual Studio permite recopilar datos de contención de recursos que incluyen información sobre cada evento de sincronización que hace que una función de la aplicación perfilada espere para obtener acceso a un recurso.

Puede especificar el método de generación de perfiles de simultaneidad mediante uno de los procedimientos siguientes:

- En la primera página del Asistente de generación de perfiles, haga clic en **Simultaneidad**
- En la página **General** del cuadro de diálogo de propiedades de la sesión de rendimiento, haga clic en **Simultaneidad**.
- En la barra de herramientas **Explorador de rendimiento**, en la lista **Método**, haga clic en **Simultaneidad**.

## <a name="common-tasks"></a>Tareas comunes

Puede especificar opciones adicionales en el cuadro de diálogo *Sesión de rendimiento***Páginas de propiedad** de la sesión de rendimiento. Para abrir este cuadro de diálogo:

- En el **Explorador de rendimiento**, haga clic con el botón secundario del mouse en el nombre de la sesión y, a continuación, haga clic en **Propiedades**.

Las tareas de la tabla siguiente describen las opciones que puede especificar en el cuadro de diálogo *Sesión de rendimiento***Páginas de propiedad* cuando genere perfiles mediante el método de simultaneidad.

|Tarea|Contenido relacionado|
|----------|---------------------|
|En la página **General** , especifique los detalles de nomenclatura del archivo de datos de generación de perfiles generado (.vsp).|- [Cómo: establecer opciones de nombre de archivo de datos de rendimiento](../profiling/how-to-set-performance-data-file-name-options.md)|
|En la página **Iniciar**, especifique la aplicación que quiere iniciar si tiene varios proyectos .exe en la solución de código.|- [Cómo: Especificar el binario de inicio](../profiling/how-to-specify-the-binary-to-start.md)|
|En la página **Interacción de capas** , agregue los datos de la llamada ADO.NET a la ejecución de la generación de perfiles.|- [Recopilación de datos de interacción de capas](../profiling/collecting-tier-interaction-data.md)|
|En la página **Contadores de Windows** , especifique uno o varios contadores de rendimiento de sistema operativo para agregar a los datos de generación de perfiles como marcas.|- [Cómo: Recopilar datos de contadores de Windows](../profiling/how-to-collect-windows-counter-data.md)|
|En la página **Avanzado**, especifique la versión del runtime de .NET Framework de la cual quiere generar el perfil si los módulos de aplicación utilizan varias versiones. De forma predeterminada, se genera el perfil de la primera versión cargada.|- [Cómo: Especificar runtime de .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|