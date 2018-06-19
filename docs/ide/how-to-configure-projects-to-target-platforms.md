---
title: 'Cómo: Configurar proyectos para plataformas de destino'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f5f5552cb87f1c8b4501930f23765143a9e9399
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946694"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Cómo: Configurar proyectos para plataformas de destino

Visual Studio permite configurar las aplicaciones para distintas plataformas de destino, incluidas las de 64 bits. Para más información sobre la compatibilidad con plataformas de 64 bits en Visual Studio, vea [Aplicaciones de 64 bits](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).

## <a name="target-platforms-with-the-configuration-manager"></a>Configurar plataformas de destino con el Administrador de configuración

El **Administrador de configuración** proporciona una forma de agregar rápidamente nuevas plataformas de destino para el proyecto. Si selecciona una de las plataformas que se incluyen con Visual Studio, las propiedades del proyecto se modifican a fin de compilarlo para esa plataforma.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Para configurar un proyecto para una plataforma de destino de 64 bits

1.  En la barra de menús, elija **Compilar** > **Administrador de configuración**.

2.  En la lista **Plataforma de soluciones activas**, elija una plataforma de 64 bits para la solución de destino y luego elija el botón **Cerrar**.

    1.  Si la plataforma que quiere no aparece en la lista **Plataforma de soluciones activas**, seleccione **Nueva**.

         Aparecerá el cuadro de diálogo **Nueva plataforma de solución**.

    2.  En la lista **Escriba o seleccione la nueva plataforma**, elija **x64**.

        > [!NOTE]
        >  Si asigna un nuevo nombre a la configuración, es posible que tenga que modificar la configuración del **Diseñador de proyectos** para seleccionar la plataforma correcta como destino.

    3.  Si quiere copiar la configuración de una configuración de plataforma actual, selecciónela y luego elija el botón **Aceptar**.

Se actualizarán las propiedades de todos los proyectos que tienen como destino la plataforma de 64 bits y la próxima compilación del proyecto se optimizará para plataformas de 64 bits.

## <a name="target-platforms-in-the-project-designer"></a>Configurar plataformas de destino en el Diseñador de proyectos

El **Diseñador de proyectos** también proporciona una forma de configurar distintas plataformas para el proyecto de destino. Si la selección de una de las plataformas incluidas en la lista del cuadro de diálogo **Nueva plataforma de solución** no funciona para la solución, puede crear un nombre de configuración personalizado y modificar la configuración en el **Diseñador de proyectos** a fin de configurar el proyecto para la plataforma de destino apropiada.

La realización de esta tarea varía según el lenguaje de programación utilizado. Para obtener más información, vea los siguientes vínculos:

-   Para proyectos de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], vea [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

-   Para proyectos de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], vea [Compilar (Página, Diseñador de proyectos) (C#)](../ide/reference/build-page-project-designer-csharp.md).

-   Para proyectos de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], vea [/clr (Compilación de Common Language Runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="see-also"></a>Vea también

- [Descripción de las plataformas de compilación](../ide/understanding-build-platforms.md)
- [/platform (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [Aplicaciones de 64 bits](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)
- [Compatibilidad de 64 bits del IDE de Visual Studio](../ide/visual-studio-ide-64-bit-support.md)
