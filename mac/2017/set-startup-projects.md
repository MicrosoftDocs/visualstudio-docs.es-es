---
title: Establecimiento de varios proyectos de inicio en Visual Studio para Mac
description: En este artículo se describe cómo configurar varios proyectos para que se inicien al ejecutar o depurar.
author: sayedihashimi
ms.author: sayedha
ms.date: 02/21/2019
ms.topic: conceptual
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: a4a4f2f4fd4ce6cd88d11979a21e4e9184adfca8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62988471"
---
# <a name="how-to-set-multiple-startup-projects"></a>Procedimiento Establecimiento de varios proyectos de inicio

Visual Studio para Mac permite especificar el inicio de más de un proyecto al depurar o ejecutar la solución.

## <a name="to-set-multiple-startup-projects"></a>Para establecer varios proyectos de inicio

1. En el **Panel de solución**, seleccione la solución (el nodo superior).

2. Seleccione el menú contextual del nodo de la solución (con el botón derecho) y, después, pulse **Establecer proyectos de inicio...**

   ![Menú contextual de Establecer proyectos de inicio](media/startup-proj-ctx-menu.png)

3. Aparece el cuadro de diálogo **Crear configuración de ejecución de la solución**. Este cuadro de diálogo creará una nueva configuración de ejecución para su solución. El nombre predeterminado es `Multiple Projects`, pero puede asignarle el nombre que quiera.

   ![Cuadro de diálogo Crear configuración de ejecución de la solución](media/create-sln-run-config.png)

4. Haga clic en **Crear configuración de ejecución**. El cuadro de diálogo **Opciones de la solución** se abre con la nueva configuración de ejecución de la solución seleccionada.

   ![Cuadro de diálogo Opciones de la solución](media/sln-options-run-config-multi-projects.png)

5. Seleccione los proyectos que quiera iniciar al depurar o ejecutar la aplicación desde Visual Studio para Mac.

   ![Cuadro de diálogo Opciones de la solución con la configuración de ejecución](media/sln-options-run-config-multi-projects-configured.png)

6. Haga clic en **Aceptar**. El cuadro de diálogo se descartará y la nueva configuración de ejecución de la solución se activará.

   ![Solución con varios proyectos configurados para iniciarse al depurar o ejecutar](media/startup-project-configured.png) Puede ver que los dos proyectos están configurados para iniciarse porque ambos están en **negrita** en el **Panel de solución**. En la barra de herramientas, la nueva configuración de ejecución se establece como la configuración de ejecución de la solución actual.

## <a name="next-steps"></a>Pasos siguientes

- [Compilar y generar en Visual Studio para Mac](compiling-and-building.md)
- [Descripción de las configuraciones de compilación](configurations.md)