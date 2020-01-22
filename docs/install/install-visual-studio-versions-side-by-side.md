---
title: Instalación de distintas versiones de Visual Studio en paralelo
ms.date: 03/05/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.openlocfilehash: 428c41a96de90494167d04ded8722d49c76afc71
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114645"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Instalación de distintas versiones de Visual Studio en paralelo

Puede instalar Visual Studio en un equipo que ya tenga instalada una versión anterior o posterior.

::: moniker range="vs-2017"

Antes de instalar versiones en paralelo, debe tener en cuenta los siguientes puntos:

* Si usa Visual Studio 2017 para abrir una solución creada en Visual Studio 2015, puede volver a abrir y modificar después la solución en la versión anterior, siempre y cuando no haya implementado ninguna de las características que son específicas de Visual Studio 2017.

* Si intenta usar Visual Studio 2017 para abrir una solución creada en Visual Studio 2015 o en una versión anterior, es posible que necesite modificar los proyectos y los archivos para que sean compatibles con Visual Studio 2017. Para obtener más información, consulte la página [Portar, migrar y actualizar proyectos de Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017).

::: moniker-end

::: moniker range=">= vs-2019"

Antes de instalar versiones en paralelo, debe tener en cuenta los siguientes puntos:

* Si usa Visual Studio 2019 para abrir una solución creada en Visual Studio 2017, puede volver a abrir y modificar después la solución en la versión anterior, siempre y cuando no haya implementado ninguna de las características que son específicas de Visual Studio 2019.

* Si intenta usar Visual Studio 2019 para abrir una solución creada en Visual Studio 2017 o en una versión anterior, es posible que necesite modificar los proyectos y los archivos para que sean compatibles con Visual Studio 2019. Para obtener más información, consulte la página [Portar, migrar y actualizar proyectos de Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

::: moniker-end

* Si se desinstala una versión de Visual Studio en un equipo que tenga más de una versión instalada, se quitarán las asociaciones de archivo de Visual Studio para todas las versiones.

* Visual Studio no actualiza automáticamente las extensiones porque no todas las extensiones son compatibles. Debe reinstalar las extensiones desde el [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o el editor de software.

## <a name="net-framework-versions-and-side-by-side-installations"></a>Versiones de .NET Framework e instalaciones en paralelo

Los proyectos de Visual Basic, Visual C# y Visual F# utilizan la opción **Plataforma de destino** del **Diseñador de proyectos** para especificar la versión de .NET Framework que utiliza un proyecto. En un proyecto de C++, se puede cambiar manualmente la versión de .NET Framework de destino si se modifica el archivo .vcxproj. Para obtener más información, consulte la página [Compatibilidad de versiones en .NET Framework](/dotnet/framework/migration-guide/version-compatibility).

Cuando se crea un proyecto, se puede especificar la versión de .NET Framework a la que se dirige el proyecto en la lista **.NET Framework** del cuadro de diálogo **Nuevo proyecto** .

Para obtener información específica del lenguaje, vea el tema correspondiente en la tabla siguiente.

::: moniker range="vs-2017"

| Lenguaje | Tema |
|--------------|-----------|
| Visual Basic | [Página de aplicación, Diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017) |
| Visual C# | [Página de aplicación, Diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017) |
| Visual F# | [Desarrollo con Visual F# en Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017) |
|C++ | [Cómo: Modificación de la plataforma de destino y el conjunto de herramientas de la plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalar Visual Studio](install-visual-studio.md?view=vs-2017)
* [Portar, migrar y actualizar proyectos de Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)
* [Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Lenguaje | Tema |
|--------------|-----------|
| Visual Basic | [Página de aplicación, Diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [Página de aplicación, Diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Desarrollo con Visual F# en Visual Studio](../ide/fsharp-visual-studio.md) |
| C++ | [Cómo: Modificación de la plataforma de destino y el conjunto de herramientas de la plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalar Visual Studio](install-visual-studio.md)
* [Portar, migrar y actualizar proyectos de Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end
