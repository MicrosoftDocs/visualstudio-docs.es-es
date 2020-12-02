---
title: Procedimiento Visualización, guardado y configuración de archivos de registro de compilación | Microsoft Docs
description: Aprenda a ver, guardar y configurar archivos de registro de compilación. Estos archivos proporcionan información de utilidad para tareas como la solución de un error de compilación.
ms.custom: SEO-VS-2020
ms.date: 08/28/2019
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 02d26416357ec13b61232f2adb0bc3e5e3c67818
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970198"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Procedimiento Visualización, guardado y configuración de archivos de registro de compilación

Después de compilar un proyecto en el IDE de Visual Studio, puede ver información sobre la compilación en la ventana **Salida**. Con esta información puede, por ejemplo, solucionar un error de compilación.

- En el caso de los proyectos de C++, también puede ver la misma información en un archivo de registro que se crea y se guarda al compilar un proyecto. 

- En los proyectos de código administrado, puede hacer clic en la ventana de salida de la compilación y presionar **Ctrl**+**S**. Visual Studio le pregunta en qué ubicación quiere guardar la información de la ventana **Salida** en un archivo de registro.

También puede usar el IDE para especificar qué tipo de información quiere ver para cada compilación.

Si compila un proyecto mediante MSBuild, puede crear un archivo de registro para guardar la información de la compilación. Para obtener más información, vea [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-view-the-build-log-file-for-a-c-project"></a>Para ver el archivo de registro de compilación de un proyecto de C++

1. En **Explorador de Windows** o el **Explorador de archivos**, abra el siguiente archivo (relativo a la carpeta raíz del proyecto): *Versión*\\<ProjectName>\>.Log* o *Depurar\\<NombreProyecto\>.log*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Para crear un archivo de registro de compilación para un proyecto de código administrado

1. En la barra de menús, elija **Compilar** > **Compilar solución**.

2. En la ventana **Salida**, haga clic en cualquier parte del texto.

3. Presione **Ctrl**+**S**.

   Visual Studio le preguntará en qué ubicación guardar la salida de la compilación.

También puede generar registros mediante la ejecución directa de MSBuild desde la línea de comandos, con la opción de línea de comandos `-fileLogger` (`-fl`). Consulte [Obtener registros de compilación con MSBuild](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Para cambiar el volumen de información incluida en el registro de compilación

1. En la barra de menús, seleccione **Herramientas** > **Opciones**.

2. En la página **Proyectos y soluciones**, elija la página **Compilar y ejecutar**.

3. En la lista **Detalles de la salida de la compilación del proyecto de MSBuild**, seleccione uno de los valores siguientes y, después, elija el botón **Aceptar**.

    |Nivel de detalle|Descripción|
    | - |-----------------|
    |**Silencioso**|Muestra un resumen solo de la compilación.|
    |**Mínima**|Muestra un resumen de la compilación y los errores, las advertencias y los mensajes que están clasificados como muy importantes.|
    |**Normal**|Muestra un resumen de la compilación; los errores, las advertencias y los mensajes que están clasificados como muy importantes; y los pasos principales de la compilación. Este es el nivel de detalle que se usará con más frecuencia.|
    |**Detallado**|Muestra un resumen de la compilación; los errores, las advertencias y los mensajes que están clasificados como muy importantes; todos los pasos de la compilación; y los mensajes que están clasificados como de importancia normal.|
    |**Diagnóstico**|Muestra todos los datos que están disponibles para la compilación. Puede usar este nivel de detalle para ayudar a depurar problemas con los scripts de compilación personalizada y otros problemas de compilación.|

     Para obtener más información, vea [Cuadro de diálogo Opciones, Proyectos y soluciones, Compilar y ejecutar](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) y <xref:Microsoft.Build.Framework.LoggerVerbosity>.

    > [!IMPORTANT]
    > Debe recompilar el proyecto para que los cambios surtan efecto en la ventana **Salida** (todos los proyectos) y el archivo *\<ProjectName>.txt* (solo para proyectos de C++).

## <a name="use-binary-logs-to-make-it-easier-to-browse-large-log-files"></a>Uso de registros binarios para facilitar la exploración de archivos de registro de gran tamaño

Los registros binarios son una característica opcional de los proyectos .NET que permite tener una experiencia de exploración de registros más completa que puede facilitar la búsqueda de información en registros de gran tamaño. Para usar registros binarios, instale [Project System Tools](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools). Para más información, consulte [https://msbuildlog.com](https://msbuildlog.com) y [Registro binario](https://github.com/microsoft/msbuild/blob/master/documentation/wiki/Binary-Log.md).

## <a name="see-also"></a>Vea también

- [Compilar y limpiar proyectos y soluciones en Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Compilar y generar](../ide/compiling-and-building-in-visual-studio.md)
