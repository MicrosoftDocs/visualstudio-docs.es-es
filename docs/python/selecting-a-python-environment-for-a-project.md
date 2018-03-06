---
title: "Selección de un entorno para un proyecto | Microsoft Docs"
description: "En el Explorador de soluciones de Visual Studio, puede asignar un intérprete de Python específico (entorno) para usarlo siempre en un proyecto determinado, sin considerar el entorno predeterminado. También puede crear y administrar los entornos virtuales."
ms.custom: 
ms.date: 02/20/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 6f422cc60638b7eed4a5b42516e7496c4a6f6209
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="selecting-a-python-interpreter-and-environment-for-use-in-a-project"></a>Selección de un entorno y un intérprete de Python para usarlo en un proyecto

Todo el código de un proyecto Python se ejecuta dentro del contexto de un entorno específico. Visual Studio también usa ese entorno para la depuración, las finalizaciones de importación y miembros, la comprobación de sintaxis y cualquier otra tarea que necesite un entorno.

Todos los proyectos Python nuevos en Visual Studio están configurados inicialmente para usar el entorno global predeterminado, que aparece en el nodo **Entornos de Python** en el Explorador de soluciones:

![Entorno de Python predeterminado global en el Explorador de soluciones](media/environments-project.png)

Puede hacer que haya otros entornos disponibles para el proyecto, incluidos los entornos virtuales. Solo se puede activar un entorno en un momento dado.

## <a name="using-global-environments"></a>Uso de los entornos globales

Para hacer que entornos globales específicos estén disponibles para el proyecto (incluidos los entornos de conda [identificados de manera manual](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment)), haga clic con el botón derecho en el nodo **Entornos de Python** y seleccione **Agregar o quitar entornos de Python...**. En la lista que aparece, seleccione los entornos deseados:

![Cuadro de diálogo Add/Remove Python Environments (Agregar o quitar entornos de Python)](media/environments-add-remove.png)

Una vez que seleccione **Aceptar**, todos los entornos seleccionados aparecen en el nodo **Entornos de Python**. El entorno activado actualmente aparece en negrita:

![Varios entornos de Python en el Explorador de soluciones](media/environments-project-multiple.png)

Para activar un entorno distinto, haga clic con el botón derecho en el nombre del entorno y seleccione **Activar entorno**. La opción se guarda con el proyecto y ese entorno se abrirá cada vez que abra el proyecto.

Si desactiva todas las opciones en el cuadro de diálogo **Agregar o quitar entornos de Python**, Visual Studio activa el entorno predeterminado global.

## <a name="using-virtual-environments"></a>Uso de los entornos virtuales

Un entorno virtual es una combinación única de un intérprete de Python específico y un conjunto de bibliotecas específico distinto de otros entornos globales y de conda. Por lo general, usa un entorno virtual cuando tiene necesidades específicas en un proyecto y no quiere modificar otros entornos para cumplir con esas necesidades.

Una vez que un entorno virtual se agrega al proyecto y aparece en la ventana **Python Environments** (Entornos de Python), puede activarlo como cualquier otro entorno y administrar sus paquetes.

Tenga en cuenta que un inconveniente de los entornos virtuales es que contienen rutas de acceso a archivos codificadas de forma rígida y, por tanto, no es fácil compartirlos o transportarlos a otros equipos de desarrollo. Afortunadamente, puede usar el archivo `requirements.txt` para permitir que los destinatarios del proyecto restauren fácilmente el entorno. Para más información, consulte [Managing required packages with requirements.txt](managing-required-packages-with-requirements-txt.md) (Administración de los paquetes requeridos con requirements.txt).

### <a name="activating-an-existing-virtual-environment"></a>Activación de un entorno virtual existente

Si ya creó un entorno virtual en otro lugar, puede activarlo para un proyecto como se indica a continuación:

1. Haga clic con el botón derecho en **Entornos de Python** en el Explorador de soluciones y seleccione **Agregar entorno virtual existente...**.

1. En el cuadro de diálogo **Examinar** que aparece, vaya a la carpeta que contiene el entorno virtual, selecciónela y, luego, seleccione **Aceptar**. Si Visual Studio detecta un archivo `requirements.txt` en ese entorno, preguntará si instalar esos paquetes.

1. Después de unos momentos, el entorno virtual aparece en el nodo **Entornos de Python** en el Explorador de soluciones. El entorno virtual no se activa de manera predeterminada, por lo que debe hacer clic con el botón derecho en él y seleccionar **Activar entorno**.

### <a name="creating-a-virtual-environment"></a>Creación de un entorno virtual

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

### <a name="remove-a-virtual-environment"></a>Eliminación de un entorno virtual

1. En el Explorador de soluciones, haga clic con el botón derecho en el entorno virtual y seleccione **Quitar**.

1. Visual Studio pregunta si desea quitar o eliminar el entorno virtual. Si selecciona **Quitar**, deja de estar disponible para el proyecto pero sigue en el sistema de archivos. Si selecciona **Eliminar**, se quita el entorno del proyecto y se elimina del sistema de archivos. El intérprete básico no se ve afectado.

## <a name="viewing-installed-packages"></a>Visualización de los paquetes instalados

En el Explorador de soluciones, expanda cualquier nodo específico del entorno para ver rápidamente los paquetes que están instalados en ese entorno (lo que significa que puede importar esos paquetes y usarlos en el código cuando el entorno está activo):

![Paquetes de Python para un entorno en el Explorador de soluciones](media/environments-installed-packages.png)

Para instalar paquetes nuevos, haga clic con el botón derecho en el entorno y seleccione **Instalar paquete de Python...** para cambiar a la pestaña **Paquetes** en la ventana **Entornos de Python**. Escriba un término de búsqueda (por lo general, el nombre del paquete) y Visual Studio mostrará los paquetes que coincidan.

Dentro de Visual Studio, los paquetes (y las dependencias) se descargan desde [Python Package Index (PyPI)](https://pypi.python.org/pypi) (Índice de paquetes de Python), donde también puede buscar los paquetes disponibles. La barra de estado y la ventana de salida de Visual Studio muestran información sobre la instalación. Para desinstalar un paquete, haga clic con el botón derecho en él y seleccione **Quitar**.

Tenga en cuenta que las entradas mostradas puede que no sean siempre precisas, y la instalación y desinstalación pueden no ser confiables o estar disponibles. Visual Studio usa el administrador de paquetes de pip si está disponible y lo descarga e instala cuando sea necesario. Visual Studio también puede usar el administrador de paquetes de easy_install. También se muestran los paquetes instalados con `pip` o `easy_install` desde la línea de comandos.

Tenga en cuenta también que Visual Studio no admite actualmente el uso de `conda` para instalar paquetes en un entorno de conda. En su lugar, use `conda` desde la línea de comandos.

> [!Tip]
> Una situación común donde pip no puede instalar un paquete es cuando este incluye código fuente para componentes nativos en archivos `*.pyd`. Sin la versión necesaria de Visual Studio instalada, pip no puede compilar estos componentes. El mensaje de error que se muestra en esta situación es `error: Unable to find vcvarsall.bat`. `easy_install` suele poder descargar los binarios previamente compilados, y el usuario puede descargar un compilador adecuado para versiones anteriores de Python de [http://aka.ms/VCPython27](http://aka.ms/VCPython27). Para más información, consulte [How to deal with the pain of "unable to find vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) (Cómo afrontar la dificultad de "no poder encontrar vcvarsallbat") en el blog del equipo de herramientas de Python.

## <a name="see-also"></a>Vea también

- [Administración de entornos de Python en Visual Studio](managing-python-environments-in-visual-studio.md)
- [Uso de requirements.txt para las dependencias](managing-required-packages-with-requirements-txt.md)
- [Rutas de acceso de búsqueda](search-paths.md)
- [Python Environments window reference](python-environments-window-tab-reference.md) (Referencia de ventana Entornos de Python)