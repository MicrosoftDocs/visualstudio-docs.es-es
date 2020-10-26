---
title: Procedimiento Compilación de varias configuraciones
description: Aprenda a compilar la mayoría de los tipos de proyectos con varias o incluso todas sus configuraciones de compilación con una acción del IDE.
ms.custom: SEO-VS-2020
ms.date: 05/13/2020
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cc5963ed3a16ffba16a52bfcde7425fb1f10cba
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136984"
---
# <a name="how-to-build-multiple-configurations-in-a-single-build-request"></a>Procedimiento Compilación de varias configuraciones en una única solicitud de compilación

Puede compilar la mayoría de los tipos de proyectos con varias o incluso todas sus configuraciones de compilación con una acción de IDE mediante el cuadro de diálogo **Compilación por lotes** . Sin embargo, no puede compilar los siguientes tipos de proyectos en varias configuraciones de compilación al mismo tiempo:

1. Aplicaciones de [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] compiladas para Windows mediante JavaScript.

2. Todos los proyectos de Visual Basic.

3. Proyectos de CMake.

Si una solución contiene cualquier proyecto de estos dos tipos de proyecto, **Compilación por lotes** no está disponible para esa solución. En ese caso, el comando no aparece en el menú **Compilar** .

   Para más información sobre las configuraciones de compilación, vea [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Para compilar un proyecto en varias configuraciones de compilación

1. En la barra de menús, elija **Compilar** > **Compilación por lotes** . O bien, presione **Ctrl**+**Q** para abrir el cuadro de búsqueda y busque `Batch Build`.

2. En la columna **Compilar** , seleccione las casillas de las configuraciones en las que quiere compilar un proyecto.

    > [!TIP]
    > Para editar o crear una configuración de compilación para una solución, en la barra de menús elija **Compilar** > **Administrador de configuración** para abrir el cuadro de diálogo **Administrador de configuración** . Después de editar una configuración de compilación para una solución, en el cuadro de diálogo **Compilación por lotes** , elija el botón **Recompilar** para actualizar todas las configuraciones para los proyectos de la solución.

3. Elija los botones **Compilar** o **Recompilar** para compilar el proyecto con las configuraciones que especificó.

## <a name="see-also"></a>Vea también

- [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md)
- [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md)
- [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)