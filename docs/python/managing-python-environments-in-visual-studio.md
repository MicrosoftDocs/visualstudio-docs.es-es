---
title: "Administración de intérpretes y entornos de Python en Visual Studio | Microsoft Docs"
description: "Se describe cómo usar la ventana Entornos de Python en Visual Studio para administrar entornos globales y virtuales, configurar entornos personalizados, instalar intérpretes de Python, instalar paquetes, establecer rutas de búsqueda y administrar entornos para proyectos de Visual Studio."
ms.custom: 
ms.date: 03/05/2018
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
ms.openlocfilehash: 558ce58461b27bc9a86906278602d00d96377c63
ms.sourcegitcommit: 3285243d6c0521266053340fe06505885d12178b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/09/2018
---
# <a name="managing-python-environments-in-visual-studio"></a>Administración de entornos de Python en Visual Studio

Un *entorno* de Python es un contexto en el que se ejecuta el código de Python e incluye los entornos globales, virtuales y de conda. Un entorno consta de un intérprete, una biblioteca (normalmente la biblioteca estándar de Python) y un conjunto de paquetes instalados. Todos estos componentes determinan qué construcciones de lenguaje y sintaxis son válidas, a qué función de sistema operativo puede acceder y qué paquetes puede usar.

En Visual Studio en Windows, es en la ventana [Entornos de Python](#managing-python-environments-in-visual-studio), tal como se describe en este artículo, donde administra estos entornos y selecciona uno como el valor predeterminado para los proyectos nuevos. Para un proyecto dado, también puede seleccionar un entorno específico en lugar de usar el valor predeterminado.

**Nota**: Si no está familiarizado con Python en Visual Studio, vea los siguientes artículos para obtener los conocimientos necesarios:

- [Uso de Python en Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Instalación de la compatibilidad con Python en Visual Studio](installing-python-support-in-visual-studio.md)

También debe tener en cuenta que no puede administrar los entornos para el código de Python que se abre solo como carpeta con el comando **Archivo > Abrir > Carpeta**. En su lugar, [cree un proyecto de Python a partir del código existente](quickstart-01-python-in-visual-studio-project-from-existing-code.md) para disfrutar de las características del entorno de Visual Studio.

## <a name="types-of-environments"></a>Tipos de entornos

### <a name="global-environments"></a>Entornos globales

Cada instalación de Python (por ejemplo, Python 2.7, Python 3.6, Anaconda 4.4.0, etc., consulte el artículo sobre la [selección e instalación de los intérpretes de Python](installing-python-interpreters.md)) mantiene su propio entorno global. Cada entorno está formado por el intérprete de Python determinado, su biblioteca estándar y un conjunto de paquetes instalados previamente. Al instalar un paquete en un entorno global, este pasa a estar disponible para todos los proyectos que usan ese entorno. Si el entorno está ubicado en una área protegida del sistema de archivos (dentro de `c:\program files`, por ejemplo), la instalación de paquetes requiere privilegios de administrador.

Los entornos globales están disponibles para todos los proyectos del equipo. En Visual Studio, debe seleccionar un entorno global como predeterminado, que será el que se utilice para todos los proyectos (a menos que elija específicamente otro diferente para un proyecto). Para obtener más información, consulte [Selección de un entorno para un proyecto](selecting-a-python-environment-for-a-project.md).

### <a name="virtual-environments"></a>Entornos virtuales

Debido a que los paquetes instalados en un entorno global están disponibles para todos los proyectos que lo usan, puede haber conflictos cuando dos proyectos requieren paquetes incompatibles o versiones diferentes del mismo paquete. Los entornos virtuales evitan estos conflictos utilizando el intérprete y la biblioteca estándar de un entorno global pero manteniendo sus propios almacenes de paquetes en carpetas aisladas.

En Visual Studio, puede crear un entorno virtual para un proyecto específico, que se almacena en una subcarpeta en el proyecto (consulte [Creating virtual environments](selecting-a-python-environment-for-a-project.md#creating-a-virtual-environment) [Creación de entornos virtuales]). El archivo del proyecto también identifica el entorno virtual. Visual Studio también registra todos los paquetes que instale en ese entorno virtual en el archivo `requirements.txt` del proyecto. Si luego comparte el proyecto y otros desarrolladores lo abren en sus equipo, Visual Studio ofrece la opción de volver a crear el entorno virtual.

### <a name="conda-environments"></a>Entornos de coda

Un entorno de conda es un entorno que se crea con la herramienta `conda`. Por lo general, los entornos de conda se almacenan en la carpeta `envs` dentro de una instalación de Anaconda y, por lo tanto, actúan de manera similar a los entornos globales. Por ejemplo, al instalar un paquete nuevo en un entorno de conda, ese paquete pasa a estar disponible para todos los proyectos que usan ese entorno.

Actualmente, Visual Studio no detecta de manera automático los entornos de conda, pero es posible indicarle que lo haga manualmente. Consulte [Identificación manual de un entorno existente](#manually-identifying-an-existing-environment).

## <a name="the-python-environments-window"></a>La ventana Entornos de Python

Los entornos que Visual Studio conoce aparecen en la ventana **Entornos de Python**. Para abrir la ventana, use uno de los métodos siguientes:

- Seleccione el comando de menú **Vista > Otras ventanas > Entornos de Python (Entornos de Python)**.
- Haga clic con el botón derecho en el nodo **Entornos de Python** de un proyecto en el Explorador de soluciones y seleccione **View All Python Environments** (Ver todos los entornos de Python):

    ![Comando Ver todos los entornos del Explorador de soluciones](media/environments-view-all.png)

En cualquier caso, la ventana **Entornos de Python** aparece como una pestaña del mismo nivel que el Explorador de soluciones:

![Ventana Python Environments (Entornos de Python)](media/environments-default-view.png)

La imagen anterior muestra que Visual Studio detectó dos instalaciones de Python 3.6 (32 bits) junto con Anaconda 5.0.0.

El entorno predeterminado en negrita es Python 3.6 (en este caso, parte de una instalación de Anaconda), que Visual Studio usa para todos los proyectos nuevos. Los comandos que aparecen en la parte inferior de la ventana se aplican al intérprete seleccionado de Python 3.6 que, como puede ver, es la instalación específica en `C:\Python36-32`. Si no ve uno de los entornos que espera, consulte [Identificación manual de un entorno existente](#manually-identifying-an-existing-environment).

A la derecha de cada entorno de la lista figura un control que abre una ventana interactiva para ese entorno. Puede aparecer otro control que actualiza la base de datos de IntelliSense para ese entorno (vea [Referencia de pestañas de la ventana Entorno de Python](python-environments-window-tab-reference.md#intellisense-tab) para obtener más información acerca de la base de datos).

Debajo de la lista de entornos hay un selector desplegable para las opciones **Introducción**, **Paquetes** e **IntelliSense** que se describen en el artículo sobre la [referencia de pestaña de la ventana Entornos de Python](python-environments-window-tab-reference.md). Además, si expande la ventana **Entornos de Python** con un ancho suficiente, estas opciones se muestran como pestañas, lo cual puede resultarle más cómodo:

![Vista de la ventana Python Environments (Entornos de Python) expandida](media/environments-expanded-view.png)

> [!Note]
> Aunque Visual Studio respeta la opción de paquetes de sitio de sistema, no ofrece una forma de cambiarla desde dentro de Visual Studio.

|   |   |
|---|---|
| ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo") | [Vea un vídeo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) sobre los entornos de Python en Visual Studio (2 minutos 35 segundos).|

### <a name="what-if-no-environments-appear"></a>¿Qué ocurre si no aparece ningún entorno?

Si no aparece ningún entorno, significa que Visual Studio no pudo detectar ninguna instalación de Python en las ubicaciones estándar. Por ejemplo, es posible que haya instalado Visual Studio 2017 pero también que haya borrado todas las opciones de intérprete en las opciones del instalador de la carga de trabajo de Python. De manera similar, es posible que haya instalado Visual Studio 2015 o una versión anterior, pero que no haya instalado un intérprete de manera manual (consulte [Selección e instalación de los intérpretes de Python](installing-python-interpreters.md)).

Si sabe que tiene un intérprete de Python en el equipo pero Visual Studio (cualquier versión) no lo detectó, use el comando **+ Personalizado...** para especificar manualmente la ubicación. Consulte la sección siguiente, [Identificación manual de un entorno existente](#manually-identifying-an-existing-environment).

> [!Tip]
> Visual Studio detecta las actualizaciones de un intérprete existente, como actualizar Python 2.7.11 a 2.7.14 mediante los instaladores de python.org. Durante el proceso de instalación, el entorno anterior desaparece de la lista de **entornos de Python** antes de que aparezca la actualización en su lugar.
>
> Sin embargo, si mueve manualmente un intérprete y su entorno con el sistema de archivos, Visual Studio no sabrá cuál es la ubicación nueva. Para más información, consulte la sección sobre cómo [mover un intérprete](installing-python-interpreters.md#moving-an-interpreter).

## <a name="manually-identifying-an-existing-environment"></a>Identificación manual de un entorno existente

Use los pasos siguientes para identificar un entorno instalado en una ubicación no estándar, incluidos los entornos de conda:

1. Seleccione **+ Personalizado...** en la ventana **Entornos de Python**, lo que abre la pestaña **Configurar**:

    ![Vista predeterminada para un nuevo entorno personalizado](media/environments-custom-1.png)

1. Escriba un nombre para el entorno en el campo **Descripción**.

1. Escriba o busque (con **...***) la ruta de acceso del intérprete en el campo **Ruta de acceso de prefijo**.

1. Si Visual Studio detecta un intérprete de Python en esa ubicación (como la ruta de acceso que aparece a continuación para un entorno de conda), habilita el comando **Detección automática**. Cuando selecciona **Detección automática*, se completan los campos restantes. También puede completar estos campos de manera manual.

    ![Habilitación del comando Detección automática](media/environments-custom-2.png)

    ![Campos de entorno completados después de usar Detección automática](media/environments-custom-3.png)

1. Una vez que los campos contienen los valores que desea, seleccione **Aplicar** para guardar la configuración. Ahora puede usar el entorno como cualquier otro dentro de Visual Studio.

1. Si necesita quitar un entorno identificado manualmente, seleccione el comando **Quitar** en la pestaña **Configurar**. Los entornos detectados automáticamente no proporcionan esta opción. Para más información, consulte la sección sobre la [pestaña de configuración](python-environments-window-tab-reference.md#configure-tab).

## <a name="see-also"></a>Vea también

- [Instalación de intérpretes de Python](installing-python-interpreters.md)
- [Selección de un intérprete para un proyecto](selecting-a-python-environment-for-a-project.md)
- [Uso de requirements.txt para las dependencias](managing-required-packages-with-requirements-txt.md)
- [Rutas de acceso de búsqueda](search-paths.md)
- [Referencia de ventana Entornos de Python](python-environments-window-tab-reference.md)