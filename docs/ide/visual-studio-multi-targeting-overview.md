---
title: Marcos .NET Framework de destino
ms.date: 02/06/2018
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: cb7af190ac7fc5d4d5ce547029689f6c902a6e4f
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747620"
---
# <a name="framework-targeting-overview"></a>Información general sobre destinos de Framework

En Visual Studio, puede especificar la versión de .NET a la que quiere que vaya destinado el proyecto. Para que las aplicaciones de .NET Framework se ejecuten en otro equipo, la versión del marco de destino de la aplicación debe ser compatible con la versión del marco instalada en el equipo.

Para obtener más información sobre los marcos de destino, vea [Versiones de .NET Framework de destino](/dotnet/standard/frameworks).

También puede crear una solución que contenga proyectos destinados a otras versiones de .NET. La elección del marco de destino ayuda a garantizar que la aplicación use solo la funcionalidad que está disponible en la versión especificada del marco.

> [!TIP]
> También puede dirigir aplicaciones a distintas plataformas. Para obtener más información, consulte [Compatibilidad con múltiples versiones (multi-targeting)](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Características de la elección de la plataforma de destino

La elección del marco de destino incluye las siguientes características:

- Si abre un proyecto que tiene como destino una versión anterior del marco, Visual Studio puede actualizarlo de forma automática o mantener el destino tal cual.

- Al crear un proyecto de .NET Framework, puede especificar la versión de .NET Framework que quiere establecer como destino.

- También puede [establecer varios marcos de destino](/dotnet/standard/frameworks#how-to-specify-target-frameworks) en un solo proyecto.

- Puede elegir como destino otra versión de .NET en cada uno de los proyectos de la misma solución.

- Puede cambiar la versión de .NET que tiene como destino un proyecto existente.

   Si cambia la versión de .NET de destino de un proyecto, Visual Studio realiza los cambios necesarios en las referencias y los archivos de configuración.

Si trabaja en un proyecto que tiene como destino una versión anterior del marco, Visual Studio cambia de forma dinámica el entorno de desarrollo, de la siguiente forma:

- Filtra los elementos de los cuadros de diálogo **Agregar nuevo elemento**, **Agregar nueva referencia** y **Agregar referencia de servicio** para omitir las opciones que no están disponibles en la versión de destino.

- Filtra los controles personalizados del **Cuadro de herramientas** para quitar los que no están disponibles en la versión de destino y para mostrar solo los controles más actualizados cuando hay varios disponibles.

- Filtra **IntelliSense** para omitir características de lenguaje que no están disponibles en la versión de destino.

- Filtra propiedades de la ventana **Propiedades** para omitir aquellas que no están disponibles en la versión de destino.

- Filtra opciones de menú para omitir aquellas que no están disponibles en la versión de destino.

- Para las compilaciones, usa la versión y las opciones del compilador que son adecuadas para la versión de destino.

> [!NOTE]
> - La elección del marco de destino no garantiza que la aplicación se ejecute correctamente. Debe probar la aplicación para asegurarse de que se ejecuta en la versión de destino.
> - No puede establecer como destino versiones de .NET Framework anteriores a la versión 2.0.

## <a name="select-a-target-framework-version"></a>Seleccionar una versión de la plataforma de destino

Al crear un proyecto de .NET Framework, seleccione la versión de destino de .NET Framework después de seleccionar una plantilla de proyecto. La lista de las plataformas disponibles incluye las versiones de las plataformas instaladas que son aplicables al tipo de plantilla seleccionada. En el caso de plantillas de proyecto que no son de .NET Framework, por ejemplo, las plantillas de .NET Core, la lista desplegable **Marco** no aparece.

::: moniker range="vs-2017"

![Lista desplegable de la plataforma en VS 2017](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Lista desplegable de la plataforma en VS 2019](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

En un proyecto existente, puede cambiar la versión de .NET de destino en el cuadro de diálogo de propiedades del proyecto. Para obtener más información, vea [Cómo: Establecer una versión de .NET como destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="resolve-system-and-user-assembly-references"></a>Resolver referencias de ensamblado de usuario y sistema

Para establecer como destino una versión de .NET, primero debe instalar las referencias de ensamblado adecuadas. Puede descargar los paquetes de desarrollador de distintas versiones de .NET en la página [Descargas de .NET](https://www.microsoft.com/net/download/windows).

En los proyectos de .NET Framework, el cuadro de diálogo **Agregar referencia** deshabilita los ensamblados del sistema que no pertenecen a la versión de .NET Framework de destino para evitar que se agreguen a un proyecto de forma involuntaria. (Los ensamblados del sistema son archivos *.dll* que se incluyen en una versión de .NET Framework). No se resuelven las referencias que pertenecen a una versión del marco posterior a la versión de destino y no se pueden agregar controles que dependan de este tipo de referencia. Si quiere habilitar este tipo de referencia, restablezca el .NET Framework de destino del proyecto a otro que incluya la referencia. Para obtener más información, vea [Cómo: Establecer una versión de Framework como destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

Para obtener más información sobre las referencias de ensamblado, consulte [Resolver ensamblados en tiempo de diseño](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>Habilitar LINQ

Si elige como destino .NET Framework 3.5 o una versión posterior, se agregan de forma automática una referencia a **System.Core** y una importación de nivel de proyecto para <xref:System.Linq> (solo en Visual Basic). Si quiere usar características de LINQ, también debe activar `Option Infer` (solo en Visual Basic). La referencia y la importación se quitan de forma automática si cambia el destino a una versión anterior de .NET Framework. Para obtener más información, vea [Trabajar con LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Vea también

- [Marcos de trabajo de destino](/dotnet/standard/frameworks)
- [Compatibilidad con múltiples versiones (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Cómo: Modificar la plataforma de destino y el conjunto de herramientas de la plataforma (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)