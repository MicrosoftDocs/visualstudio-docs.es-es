---
title: Compilar soluciones de proyectos limpios
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.BuildProjectPicker
- vs.batchbuild
helpviewer_keywords:
- Clean Solution command
- builds [Visual Studio], managing
- solution build configurations, starting
- Build Solution command
- project build configurations, starting
- build configurations, starting
- project build configurations, dependencies
- Rebuild Solution command
- solution build configurations, build order
- builds [Visual Studio], preparing
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 15f2817b6fd0aee312ff41af218d01ad80bc785e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72620556"
---
# <a name="building-and-cleaning-projects-and-solutions-in-visual-studio"></a>Compilar y limpiar proyectos y soluciones en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mediante los procedimientos indicados en este tema, puede compilar, recompilar o limpiar todos o algunos de los proyectos o elementos de proyecto de una solución. Para obtener un tutorial paso a paso, vea [Tutorial: compilar una aplicación](../ide/walkthrough-building-an-application.md).

> [!NOTE]
> La interfaz de usuario de su edición de Visual Studio podría diferir de lo que se describe en este tema, en función de su configuración activa. Para cambiar la configuración, abra el menú **Herramientas** y elija **Importar y exportar configuraciones**. Para obtener más información, consulte [Personalizar la configuración de desarrollo de Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Para compilar, recompilar o limpiar toda la solución

1. En el **Explorador de soluciones**, seleccione o abra la solución.

2. En la barra de menús, seleccione **Compilar** y, después, elija uno de los comandos siguientes:

    - Seleccione **Compilar** o **Compilar solución** para compilar solo los archivos de proyecto y los componentes que han cambiado desde la compilación más reciente.

        > [!NOTE]
        > El comando **Compilar** se convierte en **Compilar solución** cuando una solución incluye más de un proyecto.

    - Seleccione **Recompilar solución** para "limpiar" la solución y, después, compilar todos los archivos de proyecto y los componentes.

    - Seleccione **Limpiar solución** para eliminar los archivos intermedios y de salida. Cuando solo quedan los archivos de proyecto y componente, se pueden compilar nuevas instancias de archivos intermedios y de salida.

## <a name="to-build-or-rebuild-a-single-project"></a>Para compilar o recompilar un solo proyecto

1. En el **Explorador de soluciones**, seleccione o abra el proyecto.

2. En la barra de menús, seleccione **Compilar** y, después, elija **Compilar** _NombreDelProyecto_ o **Recompilar** _NombreDelProyecto_.

    - Seleccione **Compilar** _NombreDelProyecto_ para compilar solo los componentes del proyecto que han cambiado desde la compilación más reciente.

    - Seleccione **Recompilar** _NombreDelProyecto_ para "limpiar" el proyecto y, después, compilar los archivos de proyecto y todos los componentes del proyecto.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Para compilar solo el proyecto de inicio y sus dependencias

1. En la barra de menús, elija **herramientas**, **Opciones**.

2. En el cuadro de diálogo **Opciones**, expanda el nodo **Proyectos y soluciones** y, después, seleccione la página **Compilar y ejecutar**.

    Se abre el cuadro de diálogo **Compilar y ejecutar, Proyectos y soluciones, Opciones**.

3. Active la casilla **Compilar proyectos de inicio y dependencias únicamente al ejecutar**.

    Cuando activa esta casilla, solo se compilan el proyecto inicial actual y sus dependencias cuando se lleva a cabo alguno de los pasos siguientes:

   - En la barra de menús, elija **depurar**  >  **iniciar depuración** (F5).

   - En la barra de menús, elija **compilar**  >  **compilar solución** (Ctrl + Mayús + B).

     Cuando esta casilla está desactivada, todos los proyectos, sus dependencias y los archivos de solución se compilan cuando se ejecuta alguno de los comandos anteriores. De forma predeterminada, esta casilla de verificación está desactivada.

## <a name="to-build-only-the-selected-visual-c-project"></a>Para compilar solo el proyecto de Visual C++ seleccionado

1. Seleccione un proyecto de [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] y, después, en la barra de menús, elija **Compilar**, **Solo el proyecto** y uno de los comandos siguientes:

   - **Compilar solo** *NombreDelProyecto*

   - **Recompilar solo** *NombreDelProyecto*

   - **Limpiar solo** *NombreDelProyecto*

   - **Vincular solo** *NombreDelProyecto*

     Estos comandos solo se aplican al proyecto de [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] que elija, sin compilar, recompilar, limpiar o vincular dependencias del proyecto o archivos de solución. En función de la versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que tenga, el submenú **Solo el proyecto** podría contener más comandos.

## <a name="to-compile-multiple-c-project-items"></a>Para compilar varios elementos de proyecto de C++

1. En el **Explorador de soluciones**, seleccione varios archivos, que pueden ser acciones compiladas, abra el menú contextual de uno de esos archivos y, después, seleccione **Compilar**.

     Si los archivos tienen dependencias, se compilarán en orden de dependencia. Se producirá un error en la operación de compilación si los archivos requieren un encabezado precompilado que no está disponible al compilar. La operación de compilación usa la configuración de la solución activa actual.

## <a name="to-stop-a-build"></a>Para detener una compilación

1. Realice uno de estos pasos:

    - En la barra de menús, seleccione **Compilar**, **Cancelar**.

    - Presione las teclas Ctrl+Interrumpir.

## <a name="see-also"></a>Consulte también
 [Cómo: ver, guardar y configurar archivos de registro de compilación](../ide/how-to-view-save-and-configure-build-log-files.md) [obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md) [compilar y crear](../ide/compiling-and-building-in-visual-studio.md) [Descripción de las configuraciones](../ide/understanding-build-configurations.md) [de compilación depurar y liberar configuraciones de proyecto](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) de [C/C++ generación de referencia](https://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d) de la línea de comandos de [devenv cambiar](../ide/reference/devenv-command-line-switches.md) [soluciones y proyectos](../ide/solutions-and-projects-in-visual-studio.md)
