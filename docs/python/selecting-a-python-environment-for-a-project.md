---
title: Selección de un entorno para un proyecto
description: En el Explorador de soluciones de Visual Studio, puede asignar un intérprete de Python específico (entorno) para usarlo siempre en un proyecto determinado, sin considerar el entorno predeterminado. También puede crear y administrar los entornos virtuales.
ms.date: 03/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 72f07115aa323db15dd5680575871b8d4c4b20b4
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="selecting-a-python-interpreter-and-environment-for-use-in-a-project"></a>Selección de un entorno y un intérprete de Python para usarlo en un proyecto

Todo el código de un proyecto Python se ejecuta dentro del contexto de un entorno específico. Visual Studio también usa ese entorno para la depuración, las finalizaciones de importación y miembros, la comprobación de sintaxis y cualquier otra tarea que necesite un entorno.

Todos los proyectos Python nuevos en Visual Studio están configurados inicialmente para usar el entorno global predeterminado, que aparece en el nodo **Entornos de Python** en el Explorador de soluciones:

![Entorno de Python predeterminado global en el Explorador de soluciones](media/environments-project.png)

Para cambiar el entorno para un proyecto, haga clic en el nodo **Entornos de Python** y seleccione **Agregar o quitar entornos de Python...** . En la lista mostrada, que incluye entornos globales, virtuales y de conda, seleccione todos los que desee que aparezca en el nodo **Entornos de Python**:

![Cuadro de diálogo Add/Remove Python Environments (Agregar o quitar entornos de Python)](media/environments-add-remove.png)

Una vez que seleccione **Aceptar**, todos los entornos seleccionados aparecen en el nodo **Entornos de Python**. El entorno activado actualmente aparece en negrita:

![Varios entornos de Python en el Explorador de soluciones](media/environments-project-multiple.png)

Para activar rápidamente un entorno distinto, haga clic con el botón derecho en el nombre de ese entorno y seleccione **Activar entorno**. La opción se guarda con el proyecto y ese entorno se abrirá cada vez que abra el proyecto. Si desactiva todas las opciones en el cuadro de diálogo **Agregar o quitar entornos de Python**, Visual Studio activa el entorno predeterminado global.

El menú contextual del nodo **Entornos de Python** también proporciona comandos adicionales:

| Comando | Description |
| --- | --- |
| Agregar entorno virtual... | Inicia el proceso de creación de un nuevo entorno virtual en el proyecto. Consulte [Creación de un entorno virtual](#create-a-virtual-environment). |
| Agregar entorno virtual existente... | Le pide que seleccione una carpeta que contenga un entorno virtual y lo agrega a la lista bajo **Entornos de Python**, pero no lo activa. Consulte [Activación de un entorno virtual existente](#activate-an-existing-virtual-environment). |
| Crear entorno de Conda... | Cambia a la *ventana* **Entornos de Python** en la que se escribe un nombre para el entorno y se especifica su intérprete básico. |

## <a name="using-virtual-environments"></a>Uso de los entornos virtuales

Un entorno virtual es una combinación única de un intérprete de Python específico y un conjunto de bibliotecas específico distinto de otros entornos globales y de conda. Un entorno virtual es específico a un proyecto y se mantiene en una carpeta de proyecto. Esta carpeta contiene las bibliotecas instaladas del entorno junto con un archivo `pyvenv.cfg` que especifica la ruta de acceso al *intérprete básico* de ese entorno en otra parte del sistema de archivos. (Es decir, un entorno virtual no contiene una copia del intérprete, solo un vínculo a él). 

Una ventaja de usar un entorno virtual es que a medida que el proyecto se desarrolla a lo largo del tiempo, el entorno virtual siempre refleja las dependencias exactas del proyecto. (Por otra parte, un entorno global compartido, contiene cualquier número de bibliotecas independientemente de si se usan en el proyecto o no). A continuación, puede crear fácilmente un archivo `requirements.txt` desde el entorno virtual, que después se usa para volver a instalar esas dependencias en otro equipo de desarrollo o producción. Para más información, consulte [Managing required packages with requirements.txt](managing-required-packages-with-requirements-txt.md) (Administración de los paquetes requeridos con requirements.txt).

Cuando abre un proyecto en Visual Studio que contiene un archivo `requirements.txt`, Visual Studio automáticamente le ofrece la opción de volver a crear el entorno virtual. En equipos donde no está instalado Visual Studio, como Azure App Service, puede usar `pip install -r requirements.txt` para restaurar los paquetes (este proceso se describe en [Administrar Python en Azure App Service](managing-python-on-azure-app-service.md)).

Dado que un entorno virtual contiene una ruta de acceso codificada de forma rígida al intérprete básico y que puede volver a crear el entorno mediante `requirements.txt`, normalmente se omite toda la carpeta del entorno virtual del control de código fuente.

En las siguientes secciones se explica cómo activar un entorno virtual existente en un proyecto y cómo crear un nuevo entorno virtual.

En Visual Studio, se puede activar un entorno virtual para un proyecto como cualquier otro a través del nodo **Entornos de Python** en el **Explorador de soluciones**.

Una vez que un entorno virtual se agrega al proyecto, aparece en la ventana **Entornos de Python**. Puede activarlo después al igual que cualquier otro entorno así como administrar sus paquetes.

### <a name="create-a-virtual-environment"></a>Creación de un entorno virtual

Puede crear un entorno virtual directamente desde Visual Studio como se indica a continuación:

1. Haga clic con el botón derecho en **Entornos de Python** en el Explorador de soluciones y seleccione **Agrega entorno virtual...**, con lo que se mostrará el cuadro de diálogo siguiente:

    ![Creación de un entorno virtual](media/environments-add-virtual-1.png)

1. En el campo **Ubicación del entorno virtual**, especifique una ruta de acceso para el entorno virtual. Si especifica solo un nombre, el entorno virtual se crea dentro del proyecto actual en una subcarpeta con ese nombre.

1. Seleccione un entorno como el intérprete base y seleccione **Crear**. Visual Studio muestra una barra de progreso mientras se configura el entorno y descarga los paquetes necesarios. En este punto, el entorno virtual aparece en la ventana **Entornos de Python** para el proyecto contenedor.

1. El entorno virtual no se activa de manera predeterminada. Si desea activarlo para el proyecto, haga clic con el botón derecho en él y seleccione **Activar entorno**.

> [!Note]
> Si la ruta de acceso de la ubicación identifica un entorno virtual existente, Visual Studio detecta de manera automática el intérprete básico (con el archivo `orig-prefix.txt` en el directorio `lib` del entorno) y cambia el botón Crear a **Agregar**.
>
> Si existe un archivo `requirements.txt` cuando se agrega un entorno virtual, el cuadro de diálogo **Agregar entorno virtual** muestra una opción para instalar los paquetes de manera automática, lo que facilita volver a crear un entorno en otro equipo:
>
> ![Creación de un entorno virtual con requirements.txt](media/environments-requirements-txt.png)
>
> En cualquier caso, el resultado es el mismo que si se usara el comando **Agregar entorno virtual existente...**.

### <a name="activate-an-existing-virtual-environment"></a>Activación de un entorno virtual existente

Si ya creó un entorno virtual en otro lugar, puede activarlo para un proyecto como se indica a continuación:

1. Haga clic con el botón derecho en **Entornos de Python** en el Explorador de soluciones y seleccione **Agregar entorno virtual existente...**.

1. En el cuadro de diálogo **Examinar** que aparece, vaya a la carpeta que contiene el entorno virtual, selecciónela y, luego, seleccione **Aceptar**. Si Visual Studio detecta un archivo `requirements.txt` en ese entorno, preguntará si instalar esos paquetes.

1. Después de unos momentos, el entorno virtual aparece en el nodo **Entornos de Python** en el Explorador de soluciones. El entorno virtual no se activa de manera predeterminada, por lo que debe hacer clic con el botón derecho en él y seleccionar **Activar entorno**.

### <a name="remove-a-virtual-environment"></a>Eliminación de un entorno virtual

1. En el Explorador de soluciones, haga clic con el botón derecho en el entorno virtual y seleccione **Quitar**.

1. Visual Studio pregunta si desea quitar o eliminar el entorno virtual. Si selecciona **Quitar**, deja de estar disponible para el proyecto pero sigue en el sistema de archivos. Si selecciona **Eliminar**, se quita el entorno del proyecto y se elimina del sistema de archivos. El intérprete básico no se ve afectado.

## <a name="view-installed-packages"></a>Visualización de los paquetes instalados

En el Explorador de soluciones, expanda cualquier nodo específico del entorno para ver rápidamente los paquetes que están instalados en ese entorno (lo que significa que puede importar esos paquetes y usarlos en el código cuando el entorno está activo):

![Paquetes de Python para un entorno en el Explorador de soluciones](media/environments-installed-packages.png)

Para instalar paquetes nuevos, haga clic con el botón derecho en el entorno y seleccione **Instalar paquete de Python...** para cambiar a la pestaña **Paquetes** en la ventana **Entornos de Python**. Escriba un término de búsqueda (por lo general, el nombre del paquete) y Visual Studio mostrará los paquetes que coincidan.

Dentro de Visual Studio, los paquetes (y las dependencias) se descargan desde [Python Package Index (PyPI)](https://pypi.org) (Índice de paquetes de Python), donde también puede buscar los paquetes disponibles. La barra de estado y la ventana de salida de Visual Studio muestran información sobre la instalación. Para desinstalar un paquete, haga clic con el botón derecho en él y seleccione **Quitar**.

Tenga en cuenta que las entradas mostradas puede que no sean siempre precisas, y la instalación y desinstalación pueden no ser confiables o estar disponibles. Visual Studio usa el administrador de paquetes de pip si está disponible y lo descarga e instala cuando sea necesario. Visual Studio también puede usar el administrador de paquetes de easy_install. También se muestran los paquetes instalados con `pip` o `easy_install` desde la línea de comandos.

Tenga en cuenta también que Visual Studio no admite actualmente el uso de `conda` para instalar paquetes en un entorno de conda. En su lugar, use `conda` desde la línea de comandos.

> [!Tip]
> Una situación común donde pip no puede instalar un paquete es cuando este incluye código fuente para componentes nativos en archivos `*.pyd`. Sin la versión necesaria de Visual Studio instalada, pip no puede compilar estos componentes. El mensaje de error que se muestra en esta situación es `error: Unable to find vcvarsall.bat`. `easy_install` suele poder descargar los binarios previamente compilados, y el usuario puede descargar un compilador adecuado para versiones anteriores de Python de [http://aka.ms/VCPython27](http://aka.ms/VCPython27). Para más información, consulte [How to deal with the pain of "unable to find vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) (Cómo afrontar la dificultad de "no poder encontrar vcvarsallbat") en el blog del equipo de herramientas de Python.

## <a name="see-also"></a>Vea también

- [Administración de entornos de Python en Visual Studio](managing-python-environments-in-visual-studio.md)
- [Uso de requirements.txt para las dependencias](managing-required-packages-with-requirements-txt.md)
- [Rutas de acceso de búsqueda](search-paths.md)
- [Referencia de ventana Entornos de Python](python-environments-window-tab-reference.md)