---
title: 'Inicio rápido: Apertura de una carpeta de código de Python'
description: En este inicio rápido, abrirá y ejecutará código de Python desde una carpeta sin usar un proyecto de Visual Studio (solo Visual Studio 2019).
ms.date: 03/12/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
monikerRange: '>= vs-2019'
ms.openlocfilehash: ab234d9482cf9cbab49c15167ea45aff9ac2c7e6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2020
ms.locfileid: "62431157"
---
# <a name="quickstart-open-and-run-python-code-in-a-folder"></a>Inicio rápido: Apertura y ejecución de código de Python en una carpeta

Una vez que haya [instalado la compatibilidad con Python en Visual Studio 2019](installing-python-support-in-visual-studio.md), es fácil ejecutar el código de Python existente en Visual Studio 2019 sin crear un proyecto de Visual Studio.

> [!Note]
> Visual Studio 2017 y las versiones anteriores requieren la creación de un proyecto de Visual Studio para ejecutar el código de Python, lo que se puede hacer fácilmente mediante una plantilla de proyecto integrada. Consulte [Inicio rápido: Creación de un proyecto de Python a partir del código existente](quickstart-01-python-in-visual-studio-project-from-existing-code.md)

1. En este tutorial, puede usar cualquier carpeta con código de Python que quiera. Para seguir con el ejemplo que se muestra aquí, clone el repositorio gregmalcolm/python_koans de GitHub en su equipo mediante el comando `git clone https://github.com/gregmalcolm/python_koans` en una carpeta adecuada.

1. Inicie Visual Studio 2019 y, en la ventana de inicio, seleccione **Abrir** en la parte inferior de la columna **Get started** (Empezar). De manera alternativa, si ya ejecuta Visual Studio, seleccione en su lugar el comando **Archivo** > **Abrir** > **Carpeta**.

    ![La pantalla Inicio de Visual Studio](media/quickstart-open-folder/01-open-local-folder.png)

1. Vaya a la carpeta que contiene el código de Python y elija **Seleccionar carpeta**. Si usa el código python_koans, asegúrese de seleccionar la carpeta `python3` dentro de la carpeta de clonación.

    ![Cuadro de diálogo Seleccionar carpeta desde el comando Abrir carpeta](media/quickstart-open-folder/02-select-folder.png)

1. Visual Studio muestra la carpeta en el **Explorador de soluciones** en lo que se conoce como **Vista de carpetas**. Puede expandir y contraer las carpetas con las flechas que aparecen en los bordes izquierdos de los nombres de las carpetas:

    ![Controles para expandir y contraer las carpetas en el Explorador de soluciones](media/quickstart-open-folder/03-expand-collapse-folders.png)

1. Cuando se abre una carpeta de Python, Visual Studio crea varias carpetas ocultas para administrar la configuración relacionada con el proyecto. Para ver estas carpetas (y cualquier otra carpeta o archivo oculto, como la carpeta *.git*), haga clic en el botón de la barra de herramientas **Mostrar todos los archivos**:

    ![Vista de las carpetas ocultas en el Explorador de soluciones](media/quickstart-open-folder/05-view-hidden-folders.png)

1. Para ejecutar el código, en primer lugar debe identificar el archivo del programa principal o de inicio. En el ejemplo que se muestra aquí, el archivo de inicio es *contemplate-koans.py*. Haga clic con el botón derecho en ese archivo y seleccione **Establecer como elemento de inicio**.

    ![Establecimiento de un elemento de inicio en el Explorador de soluciones](media/quickstart-open-folder/06-set-as-startup-item-command.png)

    > [!Important]
    > Si el elemento de inicio no se encuentra en la raíz de la carpeta que abrió, también debe agregar una línea en el archivo JSON de configuración de inicio, tal como se describe en la sección [Establecimiento de un directorio de trabajo](#set-a-working-directory).

1. Para ejecutar el código, presione **Ctrl**+**F5** o seleccione **Depurar** > **Iniciar sin depurar**. También puede hacer clic en el botón de la barra de herramientas que muestra el elemento de inicio con un botón de reproducción, el que ejecuta el código en el depurador de Visual Studio. En todos los casos, Visual Studio detecta que el elemento de inicio es un archivo de Python, por lo que ejecuta automáticamente el código en el entorno de Python predeterminado. (Dicho entorno se muestra a la derecha del elemento de inicio en la barra de herramientas).

    ![Botón de la barra de herramientas para iniciar el depurador](media/quickstart-open-folder/07-start-debug-toolbar.png)

1. La salida del programa aparece en una ventana de comandos independiente:

    ![Ventana de salida para la ejecución del código de Python](media/quickstart-open-folder/08-result-window.png)

1. Para ejecutar el código en un entorno distinto, seleccione ese entorno desde el control desplegable en la barra de herramientas y vuelva a iniciar el elemento de inicio.

1. Para cerrar la carpeta en Visual Studio, seleccione el comando de menú **Archivo** > **Cerrar carpeta**.

## <a name="set-a-working-directory"></a>Establecimiento de un directorio de trabajo

De manera predeterminada, Visual Studio ejecuta un proyecto de Python abierto como una carpeta en la raíz de la misma carpeta. Sin embargo, el código de proyecto podría suponer que Python se está ejecutando en una subcarpeta. Por ejemplo, suponga que abre la carpeta raíz del repositorio python_koans y luego establece el archivo *python3/contemplate-koans.py* como elemento de inicio. Si luego ejecuta el código, verá un error que indica que no se encuentra el archivo *koans.txt*. Este error se produce porque *contemplate-koans.py* supone que Python se ejecuta en la carpeta *python3* en lugar de la raíz del repositorio.

En tales casos, también debe agregar una línea al archivo JSON de configuración de inicio para especificar el directorio de trabajo:

1. Haga clic con el botón derecho en el archivo de inicio de Python ( *.py*) en el **Explorador de soluciones** y seleccione **Configuración de depuración e inicio**.

    ![Comando Configuración de depuración e inicio de un archivo de Python](media/quickstart-open-folder/09-debug-launch-settings-menu-command.png)

1. En el cuadro de diálogo **Seleccionar depurador** que aparece, seleccione **Valor predeterminado** y elija **Seleccionar**.

    ![Comando Configuración de depuración e inicio de un archivo de Python](media/quickstart-open-folder/10-select-debugger.png)

    > [!Note]
    > Si **Valor predeterminado** no aparece como opción, asegúrese de haber hecho clic con el botón derecho en un archivo Python *.py* cuando seleccionó el comando **Configuración de depuración e inicio**. Visual Studio usa el tipo de archivo para determinar las opciones de depurador que se van a mostrar.

1. Visual Studio abre un archivo denominado *launch.vs.json*, que se encuentra en la carpeta oculta *.vs*. En este archivo se describe el contexto de depuración del proyecto. Para especificar un directorio de trabajo, agregue un valor para `"workingDirectory"`, como en `"workingDirectory": "python3"` en el ejemplo de python-koans:

    ```json
    {
      "version": "0.2.1",
      "defaults": {},
      "configurations": [
        {
          "type": "python",
          "interpreter": "(default)",
          "interpreterArguments": "",
          "scriptArguments": "",
          "env": {},
          "nativeDebug": false,
          "webBrowserUrl": "",
          "project": "python3\\contemplate_koans.py",
          "name": "contemplate_koans.py",
          "workingDirectory": "python3"
        }
      ]
    }
    ```

1. Guarde el archivo y vuelva a iniciar el programa, el que ahora se ejecuta en la carpeta especificada.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Tutorial: Uso de Python en Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Vea también

- [Inicio rápido: Creación de un proyecto de Python a partir del código existente](quickstart-01-python-in-visual-studio-project-from-existing-code.md)
- [Inicio rápido: Creación de un proyecto de Python a partir de un repositorio](quickstart-03-python-in-visual-studio-project-from-repository.md)
- [Manually identifying an existing Python interpreter](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment) (Identificación manual de un intérprete de Python existente)
