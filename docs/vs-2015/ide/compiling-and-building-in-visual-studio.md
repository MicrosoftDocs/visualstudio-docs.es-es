---
title: Compilar y generar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bfee16abf522284471baf4c8dc8b3c47468a032e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701493"
---
# <a name="compiling-and-building-in-visual-studio"></a>Compilar y generar en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se puede utilizar Visual Studio para compilar aplicaciones y para crear ensamblados y programas ejecutables con frecuencia durante un ciclo de desarrollo. Al compilar el código con frecuencia, se pueden identificar antes errores en tiempo de compilación como sintaxis incorrecta, palabras clave mal escritas y errores de coincidencia de tipos. También es posible detectar y corregir errores en tiempo de ejecución, como errores lógicos y errores semánticos, si se compilan y ejecutan con frecuencia versiones de depuración del código.

 Cuando un proyecto o una solución se ha desarrollado totalmente y se ha depurado suficientemente, se pueden compilar sus componentes en una compilación de versión. De forma predeterminada, una compilación de versión está optimizada y diseñada para que sea menor y se ejecute más rápidamente que una versión de depuración. Para obtener más información, vea [Tutorial: Compilación de una aplicación](../ide/walkthrough-building-an-application.md).

## <a name="choosing-a-build-method"></a>Elegir un método de compilación
 Se puede compilar una aplicación mediante las opciones de compilación predeterminadas en el IDE, en un símbolo del sistema o mediante Team Foundation Build. Cada una de estas opciones utiliza MSBuild como tecnología subyacente y cada enfoque tiene ventajas concretas, como se muestra en la tabla siguiente.

|Método de compilación|Ventajas|Para obtener más información|
|------------------|--------------|--------------------------|
|Uso de el IDE|- Puede crear compilaciones más fácilmente y ejecutarlas de forma inmediata.<br />- Puede ejecutar compilaciones multiprocesador para proyectos de C# y C++.<br />- Puede personalizar algunos aspectos del sistema de compilación.|[Compilar y limpiar proyectos y soluciones en Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)|
|Ejecutar una línea de comandos de MSBuild|- Puede compilar proyectos sin instalar Visual Studio.<br />- Puede ejecutar compilaciones multiprocesador para todos los tipos de proyecto.<br />- Puede personalizar la mayoría de las áreas del sistema de compilación.|[MSBuild](../msbuild/msbuild.md)|
|Usar Team Foundation Build|- Puede automatizar el proceso de compilación. Por ejemplo, puede compilar uno o varios proyectos por la noche o cada vez que se proteja ese código. También puede compilar proyectos en servidores de compilación compartidos en lugar de hacerlo en el equipo de desarrollo.<br />- Puede especificar rápidamente el código que quiere compilar, las pruebas que quiere ejecutar y otras opciones frecuentes.<br />- Puede modificar el flujo de trabajo de compilación y, si es necesario, crear actividades de compilación para realizar tareas muy personalizadas.|[Compilar la aplicación](https://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)|

## <a name="building-from-the-ide"></a>Compilar desde el IDE
 Al crear un proyecto, se definen las configuraciones de compilación predeterminadas para el mismo y se le asigna una configuración de compilación de soluciones para proporcionar contexto para las compilaciones. Las configuraciones de soluciones definen cómo se compilan y se implementan los proyectos de las soluciones. Las configuraciones de proyecto son un conjunto de propiedades de proyecto que son únicas para una plataforma y un tipo de compilación (por ejemplo, Versión Win32). Es posible editar estas configuraciones predeterminadas y crear sus propias configuraciones. Para obtener más información, consulte [Introducción al diseñador de proyectos](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7) y [Cómo: Modificar las propiedades del proyecto y los valores de configuración](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67).

 Desde el IDE se pueden realizar las siguientes tareas adicionales:

- [Cambiar el directorio de salida de la compilación](../ide/how-to-change-the-build-output-directory.md).

- [Identificar los proyectos que dependen de la salida de otro proyecto para que se compilen correctamente](../ide/how-to-create-and-remove-project-dependencies.md).

- [Cambiar el volumen de información incluida en el registro de compilación o en la ventana de salida para las compilaciones](../ide/how-to-view-save-and-configure-build-log-files.md).

- [Ocultar determinadas advertencias del compilador para Visual C#, Visual C++ o Visual Basic](../ide/how-to-suppress-compiler-warnings.md).

- [Especificar acciones previas y posteriores a la compilación personalizadas para una compilación](../ide/specifying-custom-build-events-in-visual-studio.md).

- Mejorar el rendimiento de la compilación mediante compilaciones paralelas. Para obtener más información, vea [Compilar varios proyectos en paralelo con MSBuild](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) o la publicación del blog [Tuning C++ build parallelism](http://blogs.msdn.com/b/msbuild/archive/2010/03/08/tuning-c-build-parallelism-in-vs2010.aspx) (Ajustar el paralelismo de compilación de C++).

## <a name="see-also"></a>Vea también
 [Tutorial: Creación de una aplicación](../ide/walkthrough-building-an-application.md) [descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md) [descripción de las plataformas de compilación](../ide/understanding-build-platforms.md) [compilar proyectos de sitio Web (compilación)](https://msdn.microsoft.com/library/a9cbb88c-8fff-4c67-848b-98fbfd823193) [ Cómo: Creación y eliminación de dependencias del proyecto](../ide/how-to-create-and-remove-project-dependencies.md)
