---
title: Compilar y generar
description: En este artículo se explica cómo compilar y generar proyectos y soluciones en Visual Studio para Mac
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/03/2021
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: a24c57907afedb4f02068a071d2c9f81eb8962bb
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2021
ms.locfileid: "108640979"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Compilar y generar en Visual Studio para Mac

Visual Studio para Mac se puede usar para compilar aplicaciones y crear ensamblados durante el desarrollo del proyecto. Es importante compilar el código a menudo para que pueda identificar rápidamente los errores de coincidencia de tipos, la sintaxis errónea, las palabras clave mal escritas y otros errores en tiempo de compilación. Al compilarlo después la depuración, también puede buscar y corregir errores en tiempo de ejecución, como errores de lógica, E/S y división por cero.

Una compilación correcta significa que el código fuente contiene la sintaxis adecuada y que todas las referencias estáticas a bibliotecas, ensamblados y otros componentes se pueden resolver. El proceso de compilación genera un archivo ejecutable de la aplicación. Este archivo ejecutable se puede probar luego través de la depuración y diferentes tipos de pruebas manuales y automatizadas para validar la calidad del código. Después de que la aplicación se ha probado por completo, es posible compilar una versión e implementarla para los clientes.

En el equipo Mac, puede usar cualquiera de los métodos siguientes para compilar la aplicación: Visual Studio para Mac, herramientas de línea de comandos de MSBuild o Azure Pipelines.

| Método de compilación | Ventajas |
| --- |--- | --- |
| Visual Studio para Mac |- Crear compilaciones inmediatamente y probarlas en un depurador.<br />- Ejecutar compilaciones multiprocesador para proyectos de C#.<br />- Personalizar aspectos diferentes del sistema de compilación. |
| Línea de comandos de MSBuild| - Compilar proyectos sin instalar Visual Studio para Mac.<br />- Ejecutar compilaciones multiprocesador para todos los tipos de proyecto.<br />- Personalizar la mayoría de las áreas del sistema de compilación.|
| Azure Pipelines | - Automatizar el proceso de compilación como parte de una canalización de integración continua o entrega continua.<br />- Aplicar pruebas automatizadas con cada compilación.<br />- Emplear recursos basados en la nube prácticamente ilimitados para los procesos de compilación.<br />- Modificar el flujo de trabajo de compilación y crear actividades de compilación para realizar tareas muy personalizadas.|

La documentación de esta sección analiza en detalle el proceso de compilación basado en el IDE. Para compilar aplicaciones desde la línea de comandos sin instalar Visual Studio para Mac, puede instalar la versión más reciente del [SDK de .NET Core](https://dotnet.microsoft.com/download). Para más información sobre la creación de aplicaciones mediante la línea de comandos, consulte [MSBuild](/visualstudio/msbuild/msbuild). Para más información sobre la creación de aplicaciones con Azure Pipelines, consulte [Azure Pipelines](/azure/devops/pipelines).


> [!NOTE]
> Este tema se aplica a Visual Studio para Mac. En el caso de Visual Studio en Windows, consulte [Compilar y generar en Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio).


## <a name="building-from-the-ide"></a>Compilar desde el IDE

Visual Studio para Mac le permite crear y ejecutar compilaciones de forma inmediata sin perder el control sobre la funcionalidad de compilación. Al crear un proyecto, Visual Studio para Mac define una configuración de compilación predeterminada que establece el contexto de las compilaciones. Puede editar las configuraciones de compilación predeterminadas y también crear las suyas propias. Al crear o modificar estas configuraciones se actualiza automáticamente el archivo de proyecto que luego usa MSBuild para compilar el proyecto.

Para más información sobre cómo compilar proyectos y soluciones en el IDE, vea la guía [Compilar y limpiar proyectos y soluciones](building-and-cleaning-projects-and-solutions.md).

Visual Studio para Mac también se puede usar para lo siguiente:

* Cambiar la ruta de acceso de la salida. Se edita en las opciones del proyecto:

    ![Cambio de la ruta de acceso de la salida](media/compiling-and-building-image4.png)

* Cambiar el nivel de detalle de la salida de compilación:

    ![Cambio del nivel de detalle de la compilación](media/compiling-and-building-image5.png)

* Agregar comandos personalizados antes, durante o después de compilar o limpiar:

    ![adición de comandos personalizados](media/compiling-and-building-image6.png)


## <a name="see-also"></a>Vea también

- [Compilar y generar (Visual Studio en Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)
