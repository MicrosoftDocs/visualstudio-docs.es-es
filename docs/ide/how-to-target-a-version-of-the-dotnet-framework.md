---
title: Establecer una versión de .NET como destino
ms.date: 03/21/2019
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET [Visual Studio]
- .NET version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2c316610fc007e3e8642567c01a5172feb461bda
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747120"
---
# <a name="how-to-target-a-version-of-net"></a>Procedimiento Establecer una versión de .NET como destino

En este artículo se explica cómo establecer una versión concreta de .NET Framework como destino al crear un proyecto de .NET Framework. También se describe cómo cambiar la versión de destino en un proyecto existente de Visual Basic, C#, o F#.

> [!IMPORTANT]
> Para obtener información sobre cómo cambiar la versión de destino para los proyectos de C++, vea [Cómo: Modificar la plataforma de destino y el conjunto de herramientas de la plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="target-a-version-when-you-create-a-project"></a>Especificación de una versión de destino al crear un proyecto

Al crear un proyecto de .NET Framework, las versiones de .NET Framework disponibles dependen de las versiones instaladas y de la plantilla de proyecto seleccionada.

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

1. Seleccione una plantilla de .NET Framework para el tipo de proyecto que quiere crear.

1. En la lista desplegable **Plataforma** situada en la parte inferior del cuadro de diálogo, elija la versión de .NET Framework de destino que quiera especificar para el proyecto.

   En la lista de los plataformas se muestran solo aquellas versiones aplicables a la plantilla que eligió.

   > [!NOTE]
   > Algunos tipos de proyecto, como .NET Core, no muestran la lista desplegable **Marco**.

   ::: moniker range="vs-2017"

   ![Desplegable Marco en el cuadro de diálogo Nuevo proyecto de Visual Studio 2017](media/vside-newproject-framework.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Selector de marco de trabajo en VS 2019](media/vs-2019/configure-new-project-framework.png)

   ::: moniker-end

1. Continúe con [creación de proyectos](create-new-project.md).

## <a name="change-the-targeted-version"></a>Cambio de la versión de destino

Puede cambiar la versión de destino de .NET en un proyecto de Visual Basic, C# o F# si sigue este procedimiento.

1. En el **Explorador de soluciones**, abra el menú contextual del proyecto que quiere cambiar y después elija **Propiedades**.

    ![Propiedades del Explorador de soluciones de Visual Studio](../ide/media/vs_slnexplorer_properties.png)

1. En la columna izquierda de la ventana **Propiedades**, elija la pestaña **Aplicación**.

    ![Propiedades de aplicación de Visual Studio, pestaña Aplicación](../ide/media/vs_slnexplorer_properties_applicationtab.png)

    > [!NOTE]
    > Después de crear una aplicación para UWP, no puede cambiar la versión de destino de Windows ni de .NET.

1. En la lista **Plataforma de destino**, elija la versión que quiera.

1. En el cuadro de diálogo de comprobación que aparece, elija el botón **Sí**.

    Se descarga el proyecto. Cuando se vuelve a cargar, establece como destino la versión de .NET que acaba de elegir.

    > [!NOTE]
    > Si el código contiene referencias a una versión de .NET distinta a la indicada, pueden aparecer mensajes de error al compilar o ejecutar el código. Para resolver estos errores, deberá modificar las referencias. Vea [Solucionar problemas de versión de .NET Framework de destino](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Vea también

- [Información general sobre destinos de Framework](../ide/visual-studio-multi-targeting-overview.md)
- [Solucionar problemas de versión de .NET Framework de destino](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [Página de aplicación, Diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Página de aplicación, Diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Cómo: Modificar la plataforma de destino y el conjunto de herramientas de la plataforma (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)