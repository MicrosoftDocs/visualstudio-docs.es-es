---
title: Destino de .NET Framework
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
# <a name="framework-targeting-overview"></a>Plataforma de destino de la información general

En Visual Studio, puede especificar la versión de .NET que desea que el proyecto de destino. Para aplicaciones de .NET Framework puedan ejecutarse en otro equipo, la versión de framework que se destina la aplicación debe ser compatible con la versión de framework que está instalada en el equipo.

Para obtener más información sobre plataformas de destino, vea [plataformas de destino](/dotnet/standard/frameworks).

También puede crear una solución que contenga proyectos destinados a versiones diferentes de. NET. Compatibilidad de Framework ayuda a garantizar que la aplicación use solo la funcionalidad que está disponible en la versión del marco especificado.

> [!TIP]
> También puede dirigir aplicaciones a distintas plataformas. Para obtener más información, consulte [Compatibilidad con múltiples versiones (multi-targeting)](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Características de la elección de la plataforma de destino

La elección del marco de destino incluye las siguientes características:

- Al abrir un proyecto que tenga como destino una versión anterior de framework, Visual Studio puede actualizar el proyecto o deje el destino como automáticamente-es.

- Al crear un proyecto de .NET Framework, puede especificar la versión de .NET Framework que desea tener como destino.

- También puede [varias plataformas de destino](/dotnet/standard/frameworks#how-to-specify-target-frameworks) en un solo proyecto.

- Se puede tener como destino una versión diferente de .NET en cada uno de varios proyectos en la misma solución.

- Puede cambiar la versión de .NET que un proyecto existente destinos.

   Al cambiar la versión de .NET que hace necesario cualquier destino de un proyecto, Visual Studio cambia a las referencias y archivos de configuración.

Cuando se trabaja en un proyecto que tiene como destino una versión anterior de framework, Visual Studio de forma dinámica, cambia el entorno de desarrollo, como sigue:

- Filtra los elementos de los cuadros de diálogo **Agregar nuevo elemento**, **Agregar nueva referencia** y **Agregar referencia de servicio** para omitir las opciones que no están disponibles en la versión de destino.

- Filtra los controles personalizados del **Cuadro de herramientas** para quitar los que no están disponibles en la versión de destino y para mostrar solo los controles más actualizados cuando hay varios disponibles.

- Filtra **IntelliSense** para omitir características del lenguaje que no están disponibles en la versión de destino.

- Filtra las propiedades en el **propiedades** ventana para omitirlas que no están disponibles en la versión de destino.

- Filtra las opciones de menú para omitir las opciones que no están disponibles en la versión de destino.

- Para las compilaciones, usa la versión y las opciones del compilador que son adecuadas para la versión de destino.

> [!NOTE]
> - La elección del marco de destino no garantiza que la aplicación se ejecute correctamente. Debe probar la aplicación para asegurarse de que se ejecuta en la versión de destino.
> - No puede tener como destino versiones anteriores de framework a .NET Framework 2.0.

## <a name="select-a-target-framework-version"></a>Seleccionar una versión de la plataforma de destino

Al crear un proyecto de .NET Framework, puede seleccionar la versión de .NET Framework de destino después de seleccionar una plantilla de proyecto. La lista de las plataformas disponibles incluye las versiones de las plataformas instaladas que son aplicables al tipo de plantilla seleccionada. Para las plantillas de proyecto que no sean .NET Framework, por ejemplo las plantillas de .NET Core, el **Framework** no aparece la lista desplegable.

::: moniker range="vs-2017"

![Lista desplegable de la plataforma en VS 2017](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Lista desplegable de la plataforma en VS 2019](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

En un proyecto existente, puede cambiar la versión de .NET de destino en el cuadro de diálogo de propiedades de proyecto. Para obtener más información, vea [Cómo: Tener como destino una versión de .NET](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="resolve-system-and-user-assembly-references"></a>Resolver referencias de ensamblado de usuario y sistema

Para tener como destino una versión. NET, primero debe instalar las referencias de ensamblado adecuado. Puede descargar paquetes de desarrollador para distintas versiones de .NET en el [descargas de .NET](https://www.microsoft.com/net/download/windows) página.

Para los proyectos de .NET Framework, el **Agregar referencia** deshabilita el cuadro de diálogo ensamblados del sistema que no pertenecen a la versión de .NET Framework de destino para que no se agreguen accidentalmente a un proyecto. (Los ensamblados del sistema son archivos *.dll* que se incluyen en una versión de .NET Framework). No se resolverán las referencias que pertenecen a una versión de framework que es mayor que la versión de destino, y no se puede agregar controles que dependan de este tipo de referencia. Si quiere habilitar este tipo de referencia, restablezca el .NET Framework de destino del proyecto a otro que incluya la referencia. Para obtener más información, vea [Cómo: Tener como destino una versión de framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

Para obtener más información sobre las referencias de ensamblado, consulte [Resolver ensamblados en tiempo de diseño](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>Habilitar LINQ

Si elige como destino .NET Framework 3.5 o una versión posterior, se agregan de forma automática una referencia a **System.Core** y una importación de nivel de proyecto para <xref:System.Linq> (solo en Visual Basic). Si quiere usar características de LINQ, también debe activar `Option Infer` (solo en Visual Basic). La referencia y la importación se quitan de forma automática si cambia el destino a una versión anterior de .NET Framework. Para obtener más información, vea [Trabajar con LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Vea también

- [Marcos de trabajo de destino](/dotnet/standard/frameworks)
- [Compatibilidad con múltiples versiones (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Cómo: Modificar la plataforma de destino y el conjunto de herramientas de la plataforma (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)