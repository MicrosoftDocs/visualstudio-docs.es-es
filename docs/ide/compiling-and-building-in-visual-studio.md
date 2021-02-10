---
title: Compilación y generación
description: Aprenda a usar el método de compilación del IDE de Visual Studio, el método de compilación de las herramientas de línea de comandos de MSBuild o el método de compilación de Azure Pipelines para compilar una aplicación.
ms.custom: SEO-VS-2020
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 61abd28890fe92918c8ee2c9067820a781fac9c4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970899"
---
# <a name="compile-and-build-in-visual-studio"></a>Compilar y generar en Visual Studio

Para obtener una primera introducción a la compilación dentro del IDE, vea [Tutorial: Compilación de una aplicación](walkthrough-building-an-application.md).

Puede usar cualquiera de los siguientes métodos para compilar una aplicación: el IDE de Visual Studio, las herramienta de línea de comandos de MSBuild y Azure Pipelines:

| Método de compilación | Ventajas |
| --- |--- | --- |
| IDE |- Crear compilaciones inmediatamente y probarlas en un depurador.<br />- Ejecutar compilaciones multiprocesador para proyectos de C++ y C#.<br />- Personalizar aspectos diferentes del sistema de compilación. |
| CMake | - Compilar proyectos con la herramienta CMake<br />- Usar el mismo sistema de compilación en plataformas Windows y Linux. |
| Línea de comandos de MSBuild| - Compilar proyectos sin instalar Visual Studio.<br />- Ejecutar compilaciones multiprocesador para todos los tipos de proyecto.<br />- Personalizar la mayoría de las áreas del sistema de compilación.|
| Azure Pipelines | - Automatizar el proceso de compilación como parte de una canalización de integración continua o entrega continua.<br />- Aplicar pruebas automatizadas con cada compilación.<br />- Emplear recursos basados en la nube prácticamente ilimitados para los procesos de compilación.<br />- Modificar el flujo de trabajo de compilación y crear actividades de compilación para realizar tareas muy personalizadas.|

La documentación de esta sección analiza en detalle el proceso de compilación basado en el IDE. Para obtener más información sobre los otros métodos, vea [MSBuild](../msbuild/msbuild.md) y [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true) respectivamente.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Compilar y generar en Visual Studio para Mac](/visualstudio/mac/compiling-and-building).

## <a name="overview-of-building-from-the-ide"></a>Introducción a la compilación desde el IDE

Cuando crea un proyecto, Visual Studio crea las configuraciones de compilación predeterminadas para el proyecto y la solución que contiene el proyecto.  Estas configuraciones definen cómo se compilan y se implementan las soluciones y los proyectos. Las configuraciones de proyecto, en concreto, son únicas para una plataforma de destino (por ejemplo, Windows o Linux) y para un tipo de compilación (por ejemplo, depuración o publicación). Puede editar estas configuraciones como quiera y también puede crear sus propias configuraciones según sea necesario.

Para obtener una primera introducción a la compilación dentro del IDE, vea [Tutorial: Compilación de una aplicación](walkthrough-building-an-application.md).

Después, vea [Compilar y limpiar proyectos y soluciones en Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md) para obtener información sobre las diversas personalizaciones de aspectos que puede llevar a cabo en el proceso. Entre las personalizaciones se incluyen [cambiar los directorios de salida](how-to-change-the-build-output-directory.md), [especificar eventos de compilación personalizados](specifying-custom-build-events-in-visual-studio.md), [administrar dependencias del proyecto](how-to-create-and-remove-project-dependencies.md), [administrar archivos del registro de compilación](how-to-view-save-and-configure-build-log-files.md) y [suprimir las advertencias del compilador](how-to-suppress-compiler-warnings.md).

De ahí en adelante, puede explorar otras tareas:
- [Descripción de las configuraciones de compilación](understanding-build-configurations.md)
- [Descripción de las plataformas de compilación](understanding-build-platforms.md)
- [Administración de propiedades de soluciones y proyectos](managing-project-and-solution-properties.md)
- Especificar eventos de compilación en [C#](how-to-specify-build-events-csharp.md) y [Visual Basic](how-to-specify-build-events-visual-basic.md)
- [Establecer las opciones de compilación](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="see-also"></a>Consulta también

- [Compilar proyectos de sitios web](/previous-versions/hwxa5aha(v=vs.140))
- [Compilar y generar (Visual Studio para Mac)](/visualstudio/mac/compiling-and-building)
- [Proyectos de CMake en Visual Studio](/cpp/build/cmake-projects-in-visual-studio)