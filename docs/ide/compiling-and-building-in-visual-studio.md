---
title: Compilación y generación
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe8528b9e6ad302319f1fb1ebb010c7f55b93932
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416596"
---
# <a name="compile-and-build-in-visual-studio"></a>Compilar y generar en Visual Studio

Al compilar código fuente, el motor de compilación crea ensamblados y aplicaciones ejecutables. En general, el proceso de compilación es muy parecido en numerosos tipos de proyectos diferentes, como Windows, ASP.NET, aplicaciones móviles y otros. El proceso de compilación también se parece en lenguajes de programación como C#, Visual Basic, C++ y F#.

Al compilar el código con frecuencia, se pueden identificar rápidamente errores en tiempo de compilación, como sintaxis incorrecta, palabras clave mal escritas y errores de coincidencia de tipos. También es posible detectar y corregir errores en tiempo de ejecución, como errores lógicos y semánticos, al compilar y ejecutar versiones de depuración del código.

Una compilación correcta valida que el código fuente de la aplicación contenga una sintaxis correcta y que se puedan resolver todas las referencias estáticas a bibliotecas, ensamblados y otros componentes. Se genera un archivo ejecutable de aplicación que se puede probar para asegurarse de que funciona correctamente en un [entorno de depuración](../debugger/index.md) y en una serie de pruebas manuales y automatizadas para [validar la calidad del código](../test/improve-code-quality.md). Una vez que se ha probado por completo la aplicación, es posible compilar una versión e implementarla para los clientes. Para obtener una introducción a este proceso, vea [Tutorial: Compilación de una aplicación](../ide/walkthrough-building-an-application.md).

Puede usar cualquiera de los siguientes métodos para compilar una aplicación: el IDE de Visual Studio, las herramienta de línea de comandos de MSBuild y Azure Pipelines:

| Método de compilación | Ventajas |
| --- |--- | --- |
| IDE |- Crear compilaciones inmediatamente y probarlas en un depurador.<br />- Ejecutar compilaciones multiprocesador para proyectos de C++ y C#.<br />- Personalizar aspectos diferentes del sistema de compilación. |
| Línea de comandos de MSBuild| - Compilar proyectos sin instalar Visual Studio.<br />- Ejecutar compilaciones multiprocesador para todos los tipos de proyecto.<br />- Personalizar la mayoría de las áreas del sistema de compilación.|
| Azure Pipelines | - Automatizar el proceso de compilación como parte de una canalización de integración continua o entrega continua.<br />- Aplicar pruebas automatizadas con cada compilación.<br />- Emplear recursos basados en la nube prácticamente ilimitados para los procesos de compilación.<br />- Modificar el flujo de trabajo de compilación y crear actividades de compilación para realizar tareas muy personalizadas.|

La documentación de esta sección analiza en detalle el proceso de compilación basado en el IDE. Para obtener más información sobre los otros métodos, vea [MSBuild](../msbuild/msbuild.md) y [Azure Pipelines](/azure/devops/pipelines/index?view=vsts) respectivamente.

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

## <a name="see-also"></a>Vea también

- [Compilar proyectos de sitios web](https://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)
- [Compilar y generar (Visual Studio para Mac)](/visualstudio/mac/compiling-and-building)