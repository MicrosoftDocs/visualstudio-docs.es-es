---
title: Compilar y generar en Visual Studio
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 472fcda584db4bf6cd16c386fec4b3e668f44a9f
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341681"
---
# <a name="compile-and-build-in-visual-studio"></a>Compilar y generar en Visual Studio

La ejecución de una compilación crea ensamblados y aplicaciones ejecutables a partir del código fuente en cualquier momento durante un ciclo de desarrollo. En general, el proceso de compilación es muy parecido en numerosos tipos de proyectos diferentes, como Windows, ASP.NET, aplicaciones móviles y otros. El proceso de compilación también se parece mucho en lenguajes de programación como C#, Visual Basic, C++ y F#.

Al compilar el código con frecuencia, se pueden identificar rápidamente errores en tiempo de compilación, como sintaxis incorrecta, palabras clave mal escritas y errores de coincidencia de tipos. También es posible detectar y corregir rápidamente errores en tiempo de ejecución, como errores lógicos y errores semánticos, si se compilan y ejecutan con frecuencia versiones de depuración del código.

Una compilación correcta es básicamente una validación de que el código fuente de la aplicación contiene una sintaxis correcta y de que se han resuelto todas las referencias estáticas a bibliotecas, ensamblados y otros componentes. Esto genera un archivo ejecutable de aplicación que se puede probar para asegurarse de que funciona correctamente en un [entorno de depuración](../debugger/index.md) y en una serie de pruebas manuales y automatizadas para [validar la calidad del código](../test/improve-code-quality.md). Una vez haya probado por completo la aplicación, podrá compilar una versión e implementarla para sus clientes. Para una introducción a este proceso, vea [Tutorial: Compilar una aplicación](../ide/walkthrough-building-an-application.md).

En la familia de productos de Visual Studio, hay tres métodos que puede usar para compilar una aplicación: el IDE de Visual Studio, las herramientas de línea de comandos de MSBuild y Team Foundation Build en Visual Studio Team Services:

| Método de compilación | Ventajas |
| --- |--- | --- |
| IDE |- Crear compilaciones inmediatamente y probarlas en un depurador.<br />- Ejecutar compilaciones multiprocesador para proyectos de C++ y C#.<br />- Personalizar aspectos diferentes del sistema de compilación. |
| Línea de comandos de MSBuild| - Compilar proyectos sin instalar Visual Studio.<br />- Ejecutar compilaciones multiprocesador para todos los tipos de proyecto.<br />- Personalizar la mayoría de las áreas del sistema de compilación.|
| Team Foundation Build | - Automatizar el proceso de compilación como parte de una canalización de integración continua o entrega continua.<br />- Aplicar pruebas automatizadas con cada compilación.<br />- Emplear recursos basados en la nube prácticamente ilimitados para los procesos de compilación.<br />- Modificar el flujo de trabajo de compilación y crear actividades de compilación para realizar tareas muy personalizadas.|

La documentación de esta sección analiza en detalle el proceso de compilación basado en el IDE. Para obtener más información sobre los otros métodos, vea [MSBuild](../msbuild/msbuild.md) y [Continuous integration and deployment](/vsts/pipelines/index?view=vsts) (Integración e implementación continuas).

## <a name="overview-of-building-from-the-ide"></a>Introducción a la compilación desde el IDE

Cuando crea un proyecto, Visual Studio crea las configuraciones de compilación predeterminadas para el proyecto y la solución que contiene el proyecto.  Estas configuraciones definen cómo se compilan y se implementan las soluciones y los proyectos. Las configuraciones de proyecto, en concreto, son únicas para una plataforma de destino (por ejemplo, Windows o Linux) y para un tipo de compilación (por ejemplo, depuración o publicación). Puede editar estas configuraciones como quiera y también puede crear sus propias configuraciones según sea necesario.

Para obtener una primera introducción a la compilación dentro del IDE, vea [Tutorial: Compilar una aplicación](walkthrough-building-an-application.md).

Después, vea [Compilar y limpiar proyectos y soluciones en Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md) para obtener información sobre las diversas personalizaciones de aspectos que puede llevar a cabo en el proceso. Entre las personalizaciones se incluyen [cambiar los directorios de salida](how-to-change-the-build-output-directory.md), [especificar eventos de compilación personalizados](specifying-custom-build-events-in-visual-studio.md), [administrar dependencias del proyecto](how-to-create-and-remove-project-dependencies.md), [administrar archivos del registro de compilación](how-to-view-save-and-configure-build-log-files.md) y [suprimir las advertencias del compilador](how-to-suppress-compiler-warnings.md).

De ahí en adelante, puede explorar otras tareas:
- [Descripción de las configuraciones de compilación](understanding-build-configurations.md)
- [Descripción de las plataformas de compilación](understanding-build-platforms.md)
- [Administración de propiedades de soluciones y proyectos](managing-project-and-solution-properties.md)
- Especificar eventos de compilación en [C#](how-to-specify-build-events-csharp.md) y [Visual Basic](how-to-specify-build-events-visual-basic.md)
- [Establecer las opciones de compilación](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="see-also"></a>Vea también

- [Compilar proyectos de sitios web](http://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)
