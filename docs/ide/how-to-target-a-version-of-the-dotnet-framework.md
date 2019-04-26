---
title: Uso de una versión de .NET Framework como destino
ms.date: 03/21/2019
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- .NET Framework version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ba8bdcade321c3660e89ab6b7cf6e0b79471b393
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548665"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Procedimiento Uso de una versión de .NET Framework como destino

En este artículo se describe usar una versión de .NET Framework como destino al crear un proyecto. También se describe cómo cambiar la versión de destino en un proyecto existente de Visual Basic, C#, o F#.

> [!IMPORTANT]
> Para obtener información sobre cómo cambiar la versión de destino para los proyectos de C++, vea [Cómo: Modificar la plataforma de destino y el conjunto de herramientas de la plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="target-a-version-when-you-create-a-project"></a>Especificación de una versión de destino al crear un proyecto

Al crear un proyecto, las versiones de .NET Framework disponibles dependen de las versiones que están instaladas y de la plantilla de proyecto seleccionada.

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

1. Elija una plantilla para el tipo de proyecto que quiere crear. Escriba un nombre para el proyecto.

1. En la lista desplegable **Plataforma** situada en la parte inferior del cuadro de diálogo, elija la versión de .NET Framework de destino que quiera especificar para el proyecto.

   En la lista de los plataformas se muestran solo aquellas versiones aplicables a la plantilla que eligió. Algunos tipos de proyecto, como .NET Core, no requieren .NET Framework. En tales casos, la lista desplegable **Plataforma** se mantiene oculta.

   ::: moniker range="vs-2017"

   ![Desplegable Plataforma en el cuadro de diálogo Nuevo proyecto](media/vside-newproject-framework.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Selector de marco de trabajo en VS 2019](media/vs-2019/configure-new-project-framework.png)

   ::: moniker-end

1. Continúe con [creación de proyectos](create-new-project.md).

## <a name="change-the-targeted-version"></a>Cambio de la versión de destino

Puede cambiar la versión de .NET Framework de destino en un proyecto de Visual Basic, C# o F# si sigue este procedimiento.

1. En el **Explorador de soluciones**, abra el menú contextual del proyecto que quiere cambiar y después elija **Propiedades**.

    ![Propiedades del Explorador de soluciones de Visual Studio](../ide/media/vs_slnexplorer_properties.png)

1. En la columna izquierda de la ventana **Propiedades**, elija la pestaña **Aplicación**.

    ![Propiedades de aplicación de Visual Studio, pestaña Aplicación](../ide/media/vs_slnexplorer_properties_applicationtab.png)

    > [!NOTE]
    > Después de crear una aplicación para UWP, no puede cambiar la versión de destino de Windows ni de .NET Framework.

1. En la lista **Plataforma de destino**, elija la versión que quiera.

1. En el cuadro de diálogo de comprobación que aparece, elija el botón **Sí**.

    Se descarga el proyecto. Cuando se vuelva a cargar, la versión de .NET Framework de destino será la que acaba de elegir.

    > [!NOTE]
    > Si el código contiene referencias a una versión de .NET Framework distinta de la que indicó, pueden aparecer mensajes de error al compilar o ejecutar el código. Para resolver estos errores, deberá modificar las referencias. Consulte [Solucionar problemas de versión de .NET Framework de destino](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Vea también

- [Información general sobre la compatibilidad con múltiples versiones de Visual Studio](../ide/visual-studio-multi-targeting-overview.md)
- [Solucionar problemas de versión de .NET Framework de destino](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [Página de aplicación, Diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Página de aplicación, Diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Cómo: Modificar la plataforma de destino y el conjunto de herramientas de la plataforma (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)