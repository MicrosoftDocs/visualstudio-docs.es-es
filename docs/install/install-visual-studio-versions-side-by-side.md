---
title: Instalación de distintas versiones de Visual Studio en paralelo
ms.date: 07/24/2019
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
ms.openlocfilehash: 717a9cd3f4157c276ce7d0dd5c41cac625581ba6
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250255"
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

## <a name="install-minor-visual-studio-versions-side-by-side"></a>Instalación de distintas versiones secundarias de Visual Studio en paralelo

Al actualizar de una versión secundaria de Visual Studio a la siguiente, el instalador de Visual Studio actualizará la instalación actual a la siguiente versión de ese canal de forma predeterminada. Por ejemplo, al instalar la versión preliminar de 16.6.4, el instalador intentará reemplazar la instalación actual de la versión preliminar de 16.6.3, ya que ambas están en el canal de versión preliminar de 16.6. Esto ayuda a garantizar que las versiones anteriores de Visual Studio no ocupen espacio en el equipo. En algunos casos concretos, puede resultar útil instalar versiones secundarias en paralelo. En nuestro ejemplo, esto conllevaría tener tanto la versión 16.6.3 como la 16.6.4 en el mismo equipo.

1. Descargue el [archivo de programa previo de Visual Studio](https://docs.microsoft.com/visualstudio/releases/2019/history#installing-an-earlier-release) para la versión secundaria que quiere instalar en paralelo con las versiones existentes de Visual Studio.
2. Abra el símbolo del sistema en modo de administrador. Para ello, abra el menú Inicio de Windows, escriba "cmd", haga clic con el botón derecho en el resultado de la búsqueda del símbolo del sistema y seleccione **Ejecutar como administrador**. En el símbolo del sistema, cambie el directorio a la carpeta donde se encuentra el archivo de programa previo de Visual Studio.
3. Ejecute el siguiente comando, pero especifique una nueva ruta de acceso para la carpeta de la ubicación de la instalación y reemplace el nombre del archivo .exe por el nombre del programa previo correspondiente a la versión de Visual Studio que está instalando. El nombre del archivo .exe debe ser igual o ser parecido a uno de los siguientes nombres de archivo:
   * vs_community.exe para Visual Studio Community
   * vs_professional.exe para Visual Studio Professional
   * vs_enterprise.exe para Visual Studio Enterprise

   ```
   vs_Enterprise.exe --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<2019 AddNewPath>"
   ```

4. Siga los cuadros de diálogo del instalador para seleccionar los componentes que necesita para la instalación. Para obtener más información, consulte [Instalación de Visual Studio](install-visual-studio.md#step-4---choose-workloads).

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
