---
title: Clonación de un repositorio
description: Aprenda a usar Visual Studio Tools for AI para clonar un repositorio de código de Python y crear un proyecto a partir de él.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 303c410bf519561844d95cc13fa036534ddb2aa7
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726623"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Clonar un repositorio de código de Python en Visual Studio

Después de [instalar Visual Studio Tools para IA](installation.md), puede clonar fácilmente un repositorio de código de Python y crear un proyecto a partir de él.

1. Para conectarse a repositorios de GitHub, ejecute el instalador de Visual Studio, haga clic en **Modificar** y en la pestaña **Componentes individuales**. Desplácese hacia abajo hasta la sección **Herramientas de código**, seleccione **Extensión de GitHub para Visual Studio** y haga clic en **Modificar**.

    ![Selección de la extensión GitHub en el instalador de Visual Studio](media/create-project-repo/installation-github-extension.png)

2. Inicia Visual Studio.

3. Seleccione **Ver > Team Explorer** para abrir la ventana **Team Explorer** desde la que puede conectarse a GitHub o a Azure DevOps, o bien clonar un repositorio.

    ![Ventana de Team Explorer en la que se muestra Azure DevOps, GitHub y la clonación de un repositorio](media/create-project-repo/team-explorer-devops.png)

4. En el campo de dirección URL en **Repositorios GIT locales**, escriba `https://github.com/Microsoft/samples-for-ai`, especifique una carpeta para los archivos clonados y haga clic en **Clonar**.

    > [!Tip]
    > La carpeta que especifique en Team Explorer es la carpeta específica para recibir los archivos clonados. A diferencia del comando `git clone`, al crear un clon en Team Explorer no se crea automáticamente una subcarpeta con el nombre del repositorio.

5. Al finalizar la clonación, haga doble clic en la carpeta del repositorio en la parte inferior de Team Explorer para ir al panel de repositorio. En **Soluciones**, seleccione **Nuevo**.

    ![Ventana de Team Explorer, con la creación de un proyecto nuevo a partir de un clon](media/create-project-repo/team-explorer-new-project.png)

6. En el cuadro de diálogo **Nuevo proyecto** que se muestra, seleccione "**Desde código de Python existente**", especifique un nombre para el proyecto, establezca **Ubicación** en la misma carpeta que el repositorio y haga clic en **Aceptar**. En el asistente que aparece, seleccione **Finalizar**.

7. Seleccione **Vista > Explorador de soluciones** en el menú.

8. En el Explorador de soluciones, expanda el nodo `TensorFlow Examples> MNIST`, haga clic con el botón derecho en `convolutional.py` y seleccione **Establecer como archivo de inicio**. Este paso indica a Visual Studio qué archivo debe utilizar al ejecutar el proyecto.

9. Presione **Ctrl**+**F5** o seleccione **Depurar > Iniciar sin depurar** para ejecutar el programa. Si se muestra un error, vuelva a comprobar la configuración del directorio de trabajo en el paso anterior.

10. Cuando el programa se ejecute correctamente, verá que empieza a descargar el conjunto de datos de aprendizaje y pruebas, después entrena el modelo y muestra la tasa de errores. El objetivo es que la tasa de errores se reduzca con el tiempo

    ![Primera salida del programa MNIST de Python](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > Si usa Anaconda y obtiene un error que indica que falta numpy, es posible que tenga que [cambiar el entorno de Python para usar Anaconda](../python/selecting-a-python-environment-for-a-project.md).

11. Puede ver el progreso con TensorBoard. Haga clic con el botón derecho en el proyecto, haga clic en **Ejecutar TensorBoard** y, después, seleccione el directorio de los registros de TensorBoard de salida.

   ![Captura de pantalla del Explorador de soluciones de Visual Studio con el proyecto MNIST seleccionado y la opción Run TensorBoard (Ejecutar TensorBoard) seleccionada en el menú contextual.](media/create-project-repo/run-tensorboard.png)

12. Observe que el error disminuye con el tiempo, lo que significa que la calidad va mejorando.

   ![Captura de pantalla de la ventana principal de TensorBoard, en la que aparecen cuatro gráficos que muestran los datos de los registros de TensorBoard.](media/create-project-repo/tensorboard.png)
