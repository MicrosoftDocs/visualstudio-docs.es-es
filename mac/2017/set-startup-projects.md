---
title: Establecimiento de varios proyectos de inicio
description: En este artículo se describe cómo configurar varios proyectos para que se inicien al ejecutar o depurar.
author: sayedihashimi
ms.author: sayedha
ms.date: 02/21/2019
ms.topic: how-to
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: 1b015d9009dc813c50ef891a4a523ba497c254c2
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950555"
---
# <a name="set-multiple-startup-projects"></a>Establecimiento de varios proyectos de inicio

Visual Studio para Mac permite especificar el inicio de más de un proyecto al depurar o ejecutar la solución.

## <a name="to-set-multiple-startup-projects"></a>Para establecer varios proyectos de inicio

1. En el Panel de solución, seleccione la solución (el nodo superior).

2. Haga clic con el botón derecho en la solución y luego seleccione **Establecer proyectos de inicio**:

   ![Selección de Establecer proyectos de inicio](media/startup-proj-ctx-menu.png)

3. Aparece el cuadro de diálogo **Crear configuración de ejecución de la solución**. Este cuadro de diálogo permite crear una nueva configuración de ejecución para su solución. Puede utilizar el nombre que desee. El nombre predeterminado es `Multiple Projects`.

   ![Cuadro de diálogo Crear configuración de ejecución de la solución](media/create-sln-run-config.png)

4. Seleccione **Crear configuración de ejecución**. El cuadro de diálogo **Opciones de la solución** se abre con la nueva configuración de ejecución de la solución seleccionada:

   ![Cuadro de diálogo Opciones de la solución](media/sln-options-run-config-multi-projects.png)

5. Seleccione los proyectos que quiera iniciar al depurar o ejecutar la aplicación desde Visual Studio para Mac:

   ![Cuadro de diálogo Opciones de la solución con proyectos seleccionados](media/sln-options-run-config-multi-projects-configured.png)

6. Seleccione **Aceptar**. El nuevo cuadro de diálogo Crear configuración de ejecución de la solución se establece como la configuración de ejecución activa:

   ![Solución con varios proyectos configurados para iniciar la depuración o la ejecución](media/startup-project-configured.png)

   Puede ver que los dos proyectos están configurados para iniciarse porque ambos proyectos están en **negrita** en el Panel de solución. En la barra de herramientas, la nueva configuración de ejecución se establece como la configuración de ejecución de la solución actual.

## <a name="next-steps"></a>Pasos siguientes

- [Compilar y generar en Visual Studio para Mac](compiling-and-building.md)
- [Descripción de las configuraciones de compilación](configurations.md)
