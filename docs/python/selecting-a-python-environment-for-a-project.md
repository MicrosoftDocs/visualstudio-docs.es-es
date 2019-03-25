---
title: Seleccionar un entorno y un intérprete de Python para un proyecto
description: En concreto, puede seleccionar un entorno de Python, incluido Anaconda y entornos virtuales, para aplicarlo a un proyecto específico.
ms.date: 03/18/2019
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 1bf1937c92f5da234ab72934c5acd52bc9cd0a6b
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194968"
---
# <a name="how-to-select-a-python-environment-for-a-project"></a>Cómo seleccionar un entorno de Python para un proyecto

Todo el código de un proyecto de Python se ejecuta dentro del contexto de un entorno concreto, como uno de Python global, de Anaconda, virtual o de Conda. Visual Studio también usa ese entorno para la depuración, las finalizaciones de importaciones y miembros, la comprobación de sintaxis y cualquier otra tarea que necesite servicios de lenguaje específicos de la versión de Python y un conjunto de paquetes instalados.

Todos los proyectos Python nuevos en Visual Studio están configurados inicialmente para usar el entorno global predeterminado, que aparece en el nodo **Entornos de Python** en el **Explorador de soluciones**:

![Entorno de Python predeterminado global en el Explorador de soluciones](media/environments/environments-project.png)

::: moniker range="vs-2017"
Para cambiar el entorno para un proyecto, haga clic en el nodo **Entornos de Python** y seleccione **Agregar o quitar entornos de Python**. En la lista mostrada, que incluye entornos globales, virtuales y de conda, seleccione todos los que desee que aparezca en el nodo **Entornos de Python**:

![Cuadro de diálogo Add/Remove Python Environments (Agregar o quitar entornos de Python)](media/environments/environments-add-remove.png)

Una vez que seleccione **Aceptar**, todos los entornos seleccionados aparecen en el nodo **Entornos de Python**. El entorno activado actualmente aparece en negrita:

![Varios entornos de Python en el Explorador de soluciones](media/environments/environments-project-multiple.png)

Para activar rápidamente un entorno distinto, haga clic con el botón derecho en el nombre de ese entorno y seleccione **Activar entorno**. La opción se guarda con el proyecto y ese entorno se abrirá cada vez que abra el proyecto. Si desactiva todas las opciones en el cuadro de diálogo **Agregar o quitar entornos de Python**, Visual Studio activa el entorno predeterminado global.

El menú contextual del nodo **Entornos de Python** también proporciona comandos adicionales:

| Comando | Descripción |
| --- | --- |
| **Agregar entorno virtual** | Inicia el proceso de creación de un nuevo entorno virtual en el proyecto. Consulte [Creación de un entorno virtual](#create-a-virtual-environment). |
| **Agregar entorno virtual existente** | Le pide que seleccione una carpeta que contenga un entorno virtual y lo agrega a la lista bajo **Entornos de Python**, pero no lo activa. Consulte [Activación de un entorno virtual existente](#activate-an-existing-virtual-environment). |
| **Crear entorno de Conda** | Cambia a la *ventana* **Entornos de Python** en la que se escribe un nombre para el entorno y se especifica su intérprete básico. Vea [Entornos de Conda](managing-python-environments-in-visual-studio.md#conda-environments). |
::: moniker-end

::: moniker range=">=vs-2019"
Para cambiar el entorno de un proyecto, haga clic con el botón derecho en el nodo **Entornos de Python** y seleccione **Agregar entorno**, o bien seleccione **Agregar entorno** en el menú desplegable de entornos de la barra de herramientas de Python.

Una vez en el cuadro de diálogo **Agregar entorno**, seleccione la pestaña **Entorno existente** y elija un entorno nuevo en la lista desplegable **Entorno**:

![Selección de un entorno de proyecto en el cuadro de diálogo Agregar entornos](media/environments/environments-project-2019.png)

Si ya agregó un entorno distinto del valor predeterminado global a un proyecto, es posible que tenga que activar un entorno recién agregado. Haga clic con el botón derecho en ese entorno en el nodo **Entornos de Python** y seleccione **Activar entorno**. Para quitar un entorno del proyecto, seleccione **Quitar**.

![Activación y eliminación de un entorno de proyecto](media/environments/environments-project-add-remove-2019.png)
::: moniker-end

## <a name="use-virtual-environments"></a>Uso de entornos virtuales

Un entorno virtual es una combinación única de un intérprete de Python específico y un conjunto de bibliotecas específico distinto de otros entornos globales y de conda. Un entorno virtual es específico a un proyecto y se mantiene en una carpeta de proyecto. Esta carpeta contiene las bibliotecas instaladas del entorno junto con un archivo *pyvenv.cfg* que especifica la ruta de acceso al *intérprete básico* de ese entorno en otra parte del sistema de archivos. (Es decir, un entorno virtual no contiene una copia del intérprete, solo un vínculo a él).

Una ventaja de usar un entorno virtual es que a medida que el proyecto se desarrolla a lo largo del tiempo, el entorno virtual siempre refleja las dependencias exactas del proyecto. (Por otra parte, un entorno global compartido, contiene cualquier número de bibliotecas independientemente de si se usan en el proyecto o no). A continuación, puede crear fácilmente un archivo *requirements.txt* desde el entorno virtual, que después se usa para volver a instalar esas dependencias en otro equipo de desarrollo o producción. Para más información, consulte [Administración de los paquetes necesarios con requirements.txt](managing-required-packages-with-requirements-txt.md).

Cuando abre un proyecto en Visual Studio que contiene un archivo *requirements.txt*, Visual Studio automáticamente le ofrece la opción de volver a crear el entorno virtual. En los equipos donde no está instalado Visual Studio, puede usar `pip install -r requirements.txt` para restaurar los paquetes.

Dado que un entorno virtual contiene una ruta de acceso codificada de forma rígida al intérprete básico y que puede volver a crear el entorno mediante *requirements.txt*, normalmente se omite toda la carpeta del entorno virtual del control de código fuente.

En las siguientes secciones se explica cómo activar un entorno virtual existente en un proyecto y cómo crear un nuevo entorno virtual.

En Visual Studio, se puede activar un entorno virtual para un proyecto como cualquier otro a través del nodo **Entornos de Python** en el **Explorador de soluciones**.

Una vez que un entorno virtual se agrega al proyecto, aparece en la ventana **Entornos de Python**. Puede activarlo después al igual que cualquier otro entorno así como administrar sus paquetes.

::: moniker range="vs-2017"
### <a name="create-a-virtual-environment"></a>Creación de un entorno virtual

Puede crear un entorno virtual directamente en Visual Studio como se indica a continuación:

1. Haga clic con el botón derecho en **Entornos de Python** en el **Explorador de soluciones** y seleccione **Agregar entorno virtual**, con lo que se mostrará el cuadro de diálogo siguiente:

    ![Creación de un entorno virtual](media/environments/environments-add-virtual-1.png)

1. En el campo **Ubicación del entorno virtual**, especifique una ruta de acceso para el entorno virtual. Si especifica solo un nombre, el entorno virtual se crea dentro del proyecto actual en una subcarpeta con ese nombre.

1. Seleccione un entorno como el intérprete base y seleccione **Crear**. Visual Studio muestra una barra de progreso mientras se configura el entorno y descarga los paquetes necesarios. Una vez finalizado, el entorno virtual aparece en la ventana **Entornos de Python** para el proyecto contenedor.

1. El entorno virtual no se activa de manera predeterminada. Si desea activarlo para el proyecto, haga clic con el botón derecho en él y seleccione **Activar entorno**.

> [!Note]
> Si la ruta de acceso de la ubicación identifica un entorno virtual existente, Visual Studio detecta de manera automática el intérprete básico (con el archivo *orig-prefix.txt* en el directorio *lib* del entorno) y cambia el botón **Crear** a **Agregar**.
>
> Si existe un archivo *requirements.txt* cuando se agrega un entorno virtual, el cuadro de diálogo **Agregar entorno virtual** muestra una opción para instalar los paquetes de manera automática, lo que facilita volver a crear un entorno en otro equipo:
>
> ![Creación de un entorno virtual con requirements.txt](media/environments/environments-requirements-txt.png)
>
> En cualquier caso, el resultado es el mismo que si se usara el comando **Agregar entorno virtual existente**.

### <a name="activate-an-existing-virtual-environment"></a>Activación de un entorno virtual existente

Si ya creó un entorno virtual en otro lugar, puede activarlo para un proyecto como se indica a continuación:

1. Haga clic con el botón derecho en **Entornos de Python** en el **Explorador de soluciones** y seleccione **Agregar entorno virtual existente**.

1. En el cuadro de diálogo **Examinar** que aparece, vaya a la carpeta que contiene el entorno virtual, selecciónela y, luego, seleccione **Aceptar**. Si Visual Studio detecta un archivo *requirements.txt* en ese entorno, preguntará si instalar esos paquetes.

1. Después de unos momentos, el entorno virtual aparece en el nodo **Entornos de Python** en el **Explorador de soluciones**. El entorno virtual no se activa de manera predeterminada, por lo que debe hacer clic con el botón derecho en él y seleccionar **Activar entorno**.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="create-a-virtual-environment"></a>Creación de un entorno virtual

Puede crear un entorno virtual directamente en Visual Studio como se indica a continuación:

1. Haga clic con el botón derecho en **Entornos de Python** en el **Explorador de soluciones** y seleccione **Agregar entorno**, o bien seleccione **Agregar entorno** en la lista desplegable de entornos de la barra de herramientas de Python. En el cuadro de diálogo **Agregar entorno** que aparece, seleccione la pestaña **Entorno virtual**:

    ![Pestaña Entorno virtual del cuadro de diálogo Agregar entorno](media/environments/environments-add-virtual-1-2019.png)

1. Especifique un nombre para el entorno virtual, seleccione un intérprete básico y compruebe su ubicación. En **Install packages from file** (Instalar paquetes desde archivo), proporcione la ruta de acceso a un archivo *requirements.txt* si lo desea.

1. Revise las otras opciones del cuadro de diálogo:

    | Opción | Descripción |
    | --- | --- |
    | Establecer como entorno actual | Activa el entorno nuevo en el proyecto seleccionado una vez que se crea el entorno. |
    | Establecer como entorno predeterminado para los nuevos proyectos | Establecer y activa automáticamente el entorno virtual en los nuevos proyectos creados en Visual Studio. Cuando se usa esta opción, el entorno virtual debe estar en una ubicación fuera de un proyecto específico.  |
    | Ver en la ventana de entornos de Python | Especifica si abrir la ventana **Entornos de Python** después de crear el entorno. |
    | Poner el entorno a disposición globalmente | Especifica si el entorno virtual también sirve como entorno global. Cuando se usa esta opción, el entorno virtual debe estar en una ubicación fuera de un proyecto específico. |

1. Seleccione **Crear** para finalizar el entorno virtual. Visual Studio muestra una barra de progreso mientras se configura el entorno y descarga los paquetes necesarios. Una vez finalizado, el entorno virtual se activa y aparece en el nodo **Entornos de Python** del **Explorador de soluciones** y la ventana **Entornos de Python** del proyecto contenedor.

### <a name="activate-an-existing-virtual-environment"></a>Activación de un entorno virtual existente

Si ya creó un entorno virtual en otro lugar, puede activarlo para un proyecto como se indica a continuación:

1. Haga clic con el botón derecho en **Entornos de Python** en el **Explorador de soluciones** y seleccione **Agregar entorno**.

1. En el cuadro de diálogo **Examinar** que aparece, vaya a la carpeta que contiene el entorno virtual, selecciónela y, luego, seleccione **Aceptar**. Si Visual Studio detecta un archivo *requirements.txt* en ese entorno, preguntará si instalar esos paquetes.

1. Después de unos momentos, el entorno virtual aparece en el nodo **Entornos de Python** en el **Explorador de soluciones**. El entorno virtual no se activa de manera predeterminada, por lo que debe hacer clic con el botón derecho en él y seleccionar **Activar entorno**.
::: moniker-end

### <a name="remove-a-virtual-environment"></a>Eliminación de un entorno virtual

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el entorno virtual y seleccione **Quitar**.

1. Visual Studio pregunta si desea quitar o eliminar el entorno virtual. Si selecciona **Quitar**, deja de estar disponible para el proyecto pero sigue en el sistema de archivos. Si selecciona **Eliminar**, se quita el entorno del proyecto y se elimina del sistema de archivos. El intérprete básico no se ve afectado.

## <a name="view-installed-packages"></a>Visualización de los paquetes instalados

En el Explorador de soluciones, expanda cualquier nodo específico del entorno para ver rápidamente los paquetes que están instalados en ese entorno (lo que significa que puede importar esos paquetes y usarlos en el código cuando el entorno está activo):

![Paquetes de Python para un entorno en el Explorador de soluciones](media/environments/environments-installed-packages.png)

::: moniker range="vs-2017"
Para instalar paquetes nuevos, haga clic con el botón derecho en el entorno y seleccione **Instalar paquete de Python** para cambiar a la pestaña **Paquetes** correspondiente en la ventana **Entornos de Python**. Escriba un término de búsqueda (por lo general, el nombre del paquete) y Visual Studio mostrará los paquetes que coincidan.
::: moniker-end
::: moniker range=">=vs-2019"
Para instalar paquetes nuevos, haga clic con el botón derecho en el entorno y seleccione **Administrar paquetes de Python** (o use el botón de paquete de la barra de herramientas de Python) para cambiar a la pestaña **Paquetes** correspondiente en la ventana **Entornos de Python**. En la pestaña **Paquetes**, escriba un término de búsqueda (por lo general, el nombre del paquete) y Visual Studio mostrará los paquetes que coincidan.
::: moniker-end

Dentro de Visual Studio, los paquetes (y las dependencias) de la mayoría de los entornos se descargan desde [Python Package Index (PyPI)](https://pypi.org) (Índice de paquetes de Python), donde también puede buscar los paquetes disponibles. La barra de estado y la ventana de salida de Visual Studio muestran información sobre la instalación. Para desinstalar un paquete, haga clic con el botón derecho en él y seleccione **Quitar**.

Por lo general, el administrador de paquetes de Conda usa `https://repo.continuum.io/pkgs/` como el canal predeterminado, pero hay otros canales disponibles. Para más información, consulte [Administrar canales](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html) (docs.conda.io).

Tenga en cuenta que las entradas mostradas puede que no sean siempre precisas, y la instalación y desinstalación pueden no ser confiables o estar disponibles. Visual Studio usa el administrador de paquetes de pip si está disponible y lo descarga e instala cuando sea necesario. Visual Studio también puede usar el administrador de paquetes de easy_install. También se muestran los paquetes instalados con `pip` o `easy_install` desde la línea de comandos.

Tenga en cuenta también que Visual Studio no admite actualmente el uso de `conda` para instalar paquetes en un entorno de conda. En su lugar, use `conda` desde la línea de comandos.

> [!Tip]
> Una situación común donde pip no puede instalar un paquete es cuando este incluye código fuente para componentes nativos en archivos *\*.pyd*. Sin la versión necesaria de Visual Studio instalada, pip no puede compilar estos componentes. El mensaje de error que se muestra en esta situación es **error: Unable to find vcvarsall.bat** (Error: no se encuentra vcvarsall.bat). `easy_install` suele poder descargar los binarios previamente compilados, y el usuario puede descargar un compilador adecuado para versiones anteriores de Python de [https://aka.ms/VCPython27](https://aka.ms/VCPython27). Para más información, consulte [How to deal with the pain of "unable to find vcvarsallbat"](https://devblogs.microsoft.com/python/unable-to-find-vcvarsall-bat/) (Cómo afrontar la dificultad de "no poder encontrar vcvarsallbat") en el blog del equipo de herramientas de Python.

## <a name="see-also"></a>Vea también

- [Creación y administración de entornos de Python en Visual Studio](managing-python-environments-in-visual-studio.md)
- [Uso de requirements.txt para las dependencias](managing-required-packages-with-requirements-txt.md)
- [Rutas de acceso de búsqueda](search-paths.md)
- [Referencia de ventana Entornos de Python](python-environments-window-tab-reference.md)
