---
title: Análisis del uso de bases de datos para proyectos de .NET Core | Microsoft Docs
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- database, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 0aeb2341d905be8f34d47c477f35861b8575dc69
ms.sourcegitcommit: 13cf7569f62c746708a6ced1187d8173eda7397c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352321"
---
# <a name="analyze-database-performance-using-the-database-tool"></a>Análisis del rendimiento de bases de datos con la herramienta Base de datos

Use la herramienta Base de datos para registrar las consultas de base de datos que la aplicación realiza durante una sesión de diagnóstico. Luego puede analizar la información sobre consultas individuales para buscar lugares con el fin de mejorar el rendimiento de la aplicación.

> [!NOTE]
> La herramienta Base de datos requiere la versión 16.3 de Visual Studio 2019 o posterior y un proyecto de .NET Core en Windows que use [ADO.NET]( https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) o [Entity Framework Core](/ef/core/).

## <a name="setup"></a>Programa de instalación

1. Seleccione **Alt + F2** para abrir el generador de perfiles de rendimiento en Visual Studio.

1. Active la casilla **Base de datos**.

   ![Herramienta Base de datos seleccionada](./media/db-launch.png "Herramienta Base de datos seleccionada")

   > [!NOTE]
   > Si la herramienta no está disponible para la selección, desactive la casilla de cada una de las otras herramientas, porque algunas herramientas se deben ejecutar de forma independiente. Para más información sobre cómo ejecutar herramientas en conjunto, consulte [Uso de las Herramientas de generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md).
   >
   > Si la herramienta todavía no está disponible, compruebe que el proyecto cumple los requisitos anteriores. Asegúrese de que el proyecto esté en modo de versión para capturar los datos más precisos.

1. Seleccione el botón **Iniciar** para ejecutar la herramienta.

1. Una vez que se inicie la ejecución de la herramienta, repase el escenario del que desea generar perfiles en su aplicación. A continuación, seleccione **Detener recopilación** o cierre la aplicación para ver los datos.

1. Una vez que la recopilación se detenga, verá una tabla de las consultas que se ejecutaron durante la sesión de generación de perfiles.

   ![Herramienta Base de datos detenida](./media/db-after.png "Herramienta Base de datos detenida")

Las consultas se organizan cronológicamente, pero puede ordenarlas por cualquiera de las columnas. Para mostrar más columnas, haga clic con el botón derecho en los títulos de las columnas. Al seleccionar la columna **Duración**, las consultas se ordenan de la más larga a la más corta.

Después de que encuentre una consulta que quiera investigar, haga clic con el botón derecho en la consulta. A continuación, seleccione **Ir al archivo de origen** para ver qué código es responsable de esa consulta.

![Ir a archivo de origen seleccionado](./media/db-gotosource.png "Ir a archivo de origen seleccionado")

Si selecciona un intervalo de tiempo en un gráfico, la tabla de consulta muestra solo las consultas que se produjeron durante ese intervalo de tiempo. Este comportamiento es especialmente útil cuando también se ejecuta la [herramienta Uso de CPU](./cpu-usage.md?view=vs-2019&preserve-view=true).

## <a name="see-also"></a>Vea también

- [Optimización de la configuración del generador de perfiles](../profiling/optimize-profiler-settings.md)