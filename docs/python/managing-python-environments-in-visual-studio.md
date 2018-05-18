---
title: Administración de entornos e intérpretes de Python
description: Use la ventana Entornos de Python para administrar entornos globales, virtuales y de conda, instalar paquetes e intérpretes de Python y asignar entornos a proyectos de Visual Studio.
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 1ba3902fde77e297148c2006f89dd61bca1e902b
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Creación y administración de entornos de Python en Visual Studio

Un *entorno* de Python es un contexto en el que se ejecuta el código de Python e incluye los entornos globales, virtuales y de conda. Un entorno consta de un intérprete, una biblioteca (normalmente la biblioteca estándar de Python) y un conjunto de paquetes instalados. Todos estos componentes determinan qué construcciones de lenguaje y sintaxis son válidas, a qué función de sistema operativo puede acceder y qué paquetes puede usar.

En Visual Studio en Windows, es en la ventana de [entornos de Python](#the-python-environments-window), tal como se describe en este artículo, donde administra estos entornos y selecciona uno como el valor predeterminado para los proyectos nuevos. Para un proyecto dado, también puede seleccionar un entorno específico en lugar de usar el valor predeterminado.

**Nota**: Si no está familiarizado con Python en Visual Studio, vea los siguientes artículos para obtener los conocimientos necesarios:

- [Uso de Python en Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Instalación de la compatibilidad con Python en Visual Studio](installing-python-support-in-visual-studio.md)

También debe tener en cuenta que no puede administrar los entornos para el código de Python que se abre solo como carpeta con el comando **Archivo** > **Abrir** > **Carpeta**. En su lugar, [cree un proyecto de Python a partir del código existente](quickstart-01-python-in-visual-studio-project-from-existing-code.md) para disfrutar de las características del entorno de Visual Studio.

Si desea instalar paquetes en un entorno, consulte la [pestaña Paquetes](python-environments-window-tab-reference.md#packages-tab).

## <a name="types-of-environments"></a>Tipos de entornos

### <a name="global-environments"></a>Entornos globales

Cada instalación de Python (por ejemplo, Python 2.7, Python 3.6, Anaconda 4.4.0, etc., consulte el artículo sobre la [selección e instalación de los intérpretes de Python](installing-python-interpreters.md)) mantiene su propio entorno global. Cada entorno está formado por el intérprete de Python determinado, su biblioteca estándar y un conjunto de paquetes instalados previamente. Al instalar un paquete en un entorno global, este pasa a estar disponible para todos los proyectos que usan ese entorno. Si el entorno está ubicado en una área protegida del sistema de archivos (dentro de `c:\program files`, por ejemplo), la instalación de paquetes requiere privilegios de administrador.

Los entornos globales están disponibles para todos los proyectos del equipo. En Visual Studio, debe seleccionar un entorno global como predeterminado, que será el que se utilice para todos los proyectos (a menos que elija específicamente otro diferente para un proyecto). Para obtener más información, consulte [Selección de un entorno para un proyecto](selecting-a-python-environment-for-a-project.md).

### <a name="virtual-environments"></a>Entornos virtuales

Debido a que los paquetes instalados en un entorno global están disponibles para todos los proyectos que lo usan, puede haber conflictos cuando dos proyectos requieren paquetes incompatibles o versiones diferentes del mismo paquete. Los entornos virtuales evitan estos conflictos utilizando el intérprete y la biblioteca estándar de un entorno global pero manteniendo sus propios almacenes de paquetes en carpetas aisladas.

En Visual Studio, puede crear un entorno virtual para un proyecto específico, que se almacena en una subcarpeta en el proyecto. Visual Studio proporciona un comando para generar un archivo `requirements.txt` desde el entorno virtual, lo que facilita volver a crear el entorno en otros equipos. Para más información, consulte [Uso de los entornos virtuales](selecting-a-python-environment-for-a-project.md#using-virtual-environments).

### <a name="conda-environments"></a>Entornos de coda

Un entorno de Conda es el creado mediante la herramienta `conda` o con la administración de Conda integrada en Visual Studio 2017, versión 15.7 y versiones posterior. [Requiere Anaconda o Miniconda; Anaconda está disponible a través del instalador de Visual Studio, vea [Installation - Visual Studio 2017](installing-python-support-in-visual-studio.md#visual-studio-2017)(Instalación de Visual Studio 2017)].

> [!Note]
> Para obtener mejores resultados con entornos de Conda, use Conda 4.4.8 o posterior (las versiones de Conda son diferentes de las versiones de Anaconda). Instalar Anaconda 5.1 desde el instalador de Visual Studio de 2017

Para ver la versión de conda, donde se almacenan los entornos de Conda, y otra información, ejecute `conda info` en un símbolo del sistema de Anaconda (es decir, un símbolo del sistema donde Anaconda está en la ruta de acceso):

```bash
conda info
```
Las carpetas de entorno de Conda tienen el siguiente aspecto:

```output
       envs directories : c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
                          C:\Users\user\.conda\envs
```

Debido a que los entornos de Conda no se almacenan con un proyecto, actúan de forma similar a los entornos globales. Por ejemplo, al instalar un paquete nuevo en un entorno de conda, ese paquete pasa a estar disponible para todos los proyectos que usan ese entorno.

Para Visual Studio 2017, versión 15.6 y anteriores, puede usar entornos de Conda apuntando a ellos de forma manual tal como se describe en [Manually identify an existing environment](#manually-identify-an-existing-environment) (Identificar de forma manual un entorno existente).

Visual Studio 2017, versión 15.7 y posteriores, detecta automáticamente los entornos de Conda y los muestra en la ventana **Entornos de Python**, tal y como se describe en la sección siguiente.

## <a name="the-python-environments-window"></a>La ventana Entornos de Python

Los entornos que Visual Studio conoce aparecen en la ventana **Entornos de Python**. Para abrir la ventana, use uno de los métodos siguientes:

- Seleccione el comando de menú **Vista** > **Otras ventanas** > **Entornos de Python** .
- Haga clic con el botón derecho en el nodo **Entornos de Python** de un proyecto en el Explorador de soluciones y seleccione **View All Python Environments** (Ver todos los entornos de Python):

    ![Comando Ver todos los entornos del Explorador de soluciones](media/environments-view-all.png)

En cualquier caso, la ventana **Entornos de Python** aparece como una pestaña del mismo nivel que el Explorador de soluciones:

![Ventana Python Environments (Entornos de Python)](media/environments-default-view.png)

El entorno predeterminado en negrita es Python 3.6, que Visual Studio usa para los nuevos proyectos. Se puede usar cualquier entorno de la lista, de cualquier tipo, como el valor predeterminado.

Los comandos que aparecen en la parte inferior de la ventana se aplican al intérprete seleccionado que, como puede ver, es la instalación específica en `C:\Python36-32` (el entorno predeterminado en negrita es parte de una instalación de Anaconda). Si no ve un entorno que espera, consulte [Identificación manual de un entorno existente](#manually-identify-an-existing-environment).

A la derecha de cada entorno de la lista figura un control que abre una ventana interactiva para ese entorno. En Visual Studio 2017, versión 15.5 y anteriores, aparece otro control que actualiza la base de datos de IntelliSense para ese entorno. Vea [Environments window reference](python-environments-window-tab-reference.md#intellisense-tab) (Referencia de la ventana de entornos) para obtener más información acerca de la base de datos.

Debajo de la lista de entornos hay un selector desplegable para las opciones **Introducción**, **Paquetes** e **IntelliSense** que se describen en el artículo sobre la [referencia de pestaña de la ventana Entornos de Python](python-environments-window-tab-reference.md). Además, si expande la ventana **Entornos de Python** con un ancho suficiente, estas opciones se muestran como pestañas, lo cual puede resultarle más cómodo:

![Vista de la ventana Python Environments (Entornos de Python) expandida](media/environments-expanded-view.png)

En la imagen anterior puede ver la lista completa de los entornos en este equipo en particular, junto con los comandos adicionales para crear entornos.

> [!Note]
> Aunque Visual Studio respeta la opción de paquetes de sitio de sistema, no ofrece una forma de cambiarla desde dentro de Visual Studio.

|   |   |
|---|---|
| ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo") | [Vea un vídeo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) sobre los entornos de Python en Visual Studio (2 minutos 35 segundos).|

### <a name="what-if-no-environments-appear"></a>¿Qué ocurre si no aparece ningún entorno?

Si no aparece ningún entorno, significa que Visual Studio no pudo detectar ninguna instalación de Python en las ubicaciones estándar. Por ejemplo, es posible que haya instalado Visual Studio 2017 pero también que haya borrado todas las opciones de intérprete en las opciones del instalador de la carga de trabajo de Python. De manera similar, es posible que haya instalado Visual Studio 2015 o una versión anterior, pero que no haya instalado un intérprete de manera manual (consulte [Instalación de intérpretes de Python](installing-python-interpreters.md)).

Si sabe que tiene un intérprete de Python en el equipo pero Visual Studio (cualquier versión) no lo detectó, use el comando **+ Personalizado...** para especificar manualmente la ubicación. Consulte la sección siguiente, [Identificación manual de un entorno existente](#manually-identify-an-existing-environment).

> [!Tip]
> Visual Studio detecta las actualizaciones de un intérprete existente, como actualizar Python 2.7.11 a 2.7.14 mediante los instaladores de python.org. Durante el proceso de instalación, el entorno anterior desaparece de la lista de **entornos de Python** antes de que aparezca la actualización en su lugar.
>
> Sin embargo, si mueve manualmente un intérprete y su entorno con el sistema de archivos, Visual Studio no sabrá cuál es la ubicación nueva. Para más información, consulte la sección sobre cómo [mover un intérprete](installing-python-interpreters.md#moving-an-interpreter).

<a name="manually-identifying-an-existing-environment></a>

## <a name="manually-identify-an-existing-environment"></a>Identificación manual de un entorno existente

Use los pasos siguientes para identificar un entorno instalado en una ubicación no estándar, como los entornos de Conda en Visual Studio 2017, versión 15.6 y anteriores:

1. Seleccione **+ Personalizado** en la ventana **Entornos de Python**, lo que abre la pestaña **Configurar**:

    ![Vista predeterminada para un nuevo entorno personalizado](media/environments-custom-1.png)

1. Escriba un nombre para el entorno en el campo **Descripción**.

1. Escriba o busque (con **...***) la ruta de acceso del intérprete en el campo **Ruta de acceso de prefijo**.

1. Si Visual Studio detecta un intérprete de Python en esa ubicación (como la ruta de acceso que aparece a continuación para un entorno de conda), habilita el comando **Detección automática**. Cuando selecciona **Detección automática*, se completan los campos restantes. También puede completar estos campos de manera manual.

    ![Habilitación del comando Detección automática](media/environments-custom-2.png)

    ![Campos de entorno completados después de usar Detección automática](media/environments-custom-3.png)

1. Una vez que los campos contienen los valores que desea, seleccione **Aplicar** para guardar la configuración. Ahora puede usar el entorno como cualquier otro dentro de Visual Studio.

1. Si necesita quitar un entorno identificado manualmente, seleccione el comando **Quitar** en la pestaña **Configurar**. Los entornos detectados automáticamente no proporcionan esta opción. Para más información, consulte la sección sobre la [pestaña de configuración](python-environments-window-tab-reference.md#configure-tab).

## <a name="create-a-conda-environment"></a>Crear un entorno de Conda

*Visual Studio 2017, versión 15.7 y posteriores*

1. Seleccione **+ Crear entorno de Conda** en la ventana **Entornos de Python**, que abre una pestaña **Crear nuevo entorno de Conda**:

    ![Crear pestaña para un nuevo entorno de Conda](media/environments-conda-1.png)

1. Escriba un nombre para el entorno en el campo **Nombre**, luego seleccione un intérprete de Python base en el campo **Python** y, después, seleccione **Crear**.

1. La ventana **Salida** muestra el progreso del nuevo entorno, con algunas instrucciones de CLI cuando se completa la creación:

    ![Creación correcta de un entorno de Conda](media/environments-conda-2.png)

1. En Visual Studio, puede activar un entorno de Conda para un proyecto de la misma forma que con cualquier otro entorno, tal como se describe en [Selecting an environment for a project](selecting-a-python-environment-for-a-project.md) (Seleccionar un entorno para un proyecto).

1. Para instalar paquetes en el entorno, use la [pestaña Paquetes](python-environments-window-tab-reference.md#packages-tab).

## <a name="see-also"></a>Vea también

- [Instalación de intérpretes de Python](installing-python-interpreters.md)
- [Selección de un intérprete para un proyecto](selecting-a-python-environment-for-a-project.md)
- [Uso de requirements.txt para las dependencias](managing-required-packages-with-requirements-txt.md)
- [Rutas de acceso de búsqueda](search-paths.md)
- [Referencia de ventana Entornos de Python](python-environments-window-tab-reference.md)