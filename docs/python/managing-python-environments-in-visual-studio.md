---
title: Administración de entornos e intérpretes de Python
description: Use la ventana Entornos de Python para administrar entornos globales, virtuales y de conda, instalar paquetes e intérpretes de Python y asignar entornos a proyectos de Visual Studio.
ms.date: 08/06/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: f331c794c50d6b6573ad9708da6d153c77f4d77c
ms.sourcegitcommit: 13cf7569f62c746708a6ced1187d8173eda7397c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352354"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Creación y administración de entornos de Python en Visual Studio

Un **entorno de Python** es un contexto en el que se ejecuta el código de Python e incluye los entornos globales, virtuales y de Conda. Un entorno consta de un intérprete, una biblioteca (normalmente la biblioteca estándar de Python) y un conjunto de paquetes instalados. Todos estos componentes determinan qué construcciones de lenguaje y sintaxis son válidas, a qué función de sistema operativo puede acceder y qué paquetes puede usar.

En Visual Studio en Windows, se usa la ventana **Entornos de Python**, como se explica en este artículo, para administrar entornos y seleccionar uno como valor predeterminado para los proyectos nuevos. En los siguientes artículos se indican otros aspectos de los entornos:

- En cualquier proyecto puede [seleccionar un entorno concreto](selecting-a-python-environment-for-a-project.md) en lugar de usar el predeterminado.

- Para obtener detalles sobre la creación y el empleo de entornos virtuales para proyectos de Python, vea [Uso de entornos virtuales](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Si quiere instalar paquetes en un entorno, vea la referencia de la [pestaña Paquetes](python-environments-window-tab-reference.md#packages-tab).

- Para instalar otro intérprete de Python, vea [Instalación de intérpretes de Python](installing-python-interpreters.md). En general, si descarga y ejecuta el instalador de una distribución principal de Python, Visual Studio detecta esa nueva instalación y el entorno aparece en la ventana **Entornos de Python** y se puede seleccionar para los proyectos.

Si no está familiarizado con Python en Visual Studio, los siguientes artículos también proporcionan un contexto general:

- [Uso de Python en Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Instalación de la compatibilidad con Python en Visual Studio](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> No puede administrar entornos de código de Python abiertos como carpeta con el comando **Archivo** > **Abrir** > **Carpeta**. En su lugar, [cree un proyecto de Python a partir del código existente](quickstart-01-python-in-visual-studio-project-from-existing-code.md) para disfrutar de las características del entorno de Visual Studio.
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Los entornos de código de Python abiertos como una carpeta se pueden administrar con el comando **Archivo** > **Abrir** > **Carpeta**. La barra de herramientas de Python permite alternar entre todos los entornos detectados y, también, agregar un entorno nuevo. La información del entorno se almacena en el archivo PythonSettings.json, en la carpeta .vs del área de trabajo.
::: moniker-end

## <a name="the-python-environments-window"></a>La ventana Entornos de Python

Los entornos que Visual Studio conoce aparecen en la ventana **Entornos de Python**. Para abrir la ventana, use uno de los métodos siguientes:

- Seleccione el comando de menú **Vista** > **Otras ventanas** > **Entornos de Python**.
- Haga clic con el botón derecho en el nodo **Entornos de Python** de un proyecto en el **Explorador de soluciones** y seleccione **View All Python Environments** (Ver todos los entornos de Python):

    ::: moniker range="vs-2017"
    ![Comando Ver todos los entornos del Explorador de soluciones](media/environments/environments-view-all.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Comando Ver todos los entornos del Explorador de soluciones](media/environments/environments-view-all-2019.png)
    ::: moniker-end

En cualquier caso, la ventana **Entornos de Python** aparece junto al **Explorador de soluciones**:

::: moniker range="vs-2017"
![Ventana Python Environments (Entornos de Python)](media/environments/environments-default-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Ventana Python Environments (Entornos de Python)](media/environments/environments-default-view-2019.png)
::: moniker-end

Visual Studio busca entornos globales instalados mediante el Registro (tras [PEP 514](https://www.python.org/dev/peps/pep-0514/)), junto con entornos virtuales y entornos de Conda (vea [Tipos de entornos](#types-of-environments)). Si no ve un entorno previsto en la lista, vea [Identificación manual de un entorno existente](#manually-identify-an-existing-environment).

Al seleccionar un entorno de la lista, Visual Studio muestra distintas propiedades y comandos de ese entorno en la pestaña **Información general**. Por ejemplo, en la imagen anterior puede ver que la ubicación del intérprete es *C:\Python36-32*. Los cuatro comandos en la parte inferior de la pestaña **Información general** abren un símbolo del sistema con el intérprete en ejecución. Para obtener más información, vea [Referencia de pestañas de la ventana Entorno de Python: Información general](python-environments-window-tab-reference.md#overview-tab).

Use la lista desplegable situada debajo de la lista de entornos para cambiar de pestañas, como **Paquetes** o **IntelliSense**. Estas pestañas también se describen en la [Referencia de pestañas de la ventana Entornos de Python](python-environments-window-tab-reference.md).

La selección de un entorno no cambia su relación con los proyectos. El entorno predeterminado, que aparece en negrita en la lista, es el que usa Visual Studio para los proyectos nuevos. Para usar otro entorno con los proyectos nuevos, use el comando **Convertir este entorno en el predeterminado para nuevos proyectos**. En el contexto de un proyecto siempre puede seleccionar un entorno concreto. Para más información, vea [Selección de un entorno para un proyecto](selecting-a-python-environment-for-a-project.md).

A la derecha de cada entorno de la lista figura un control que abre una ventana **interactiva** para ese entorno. (En Visual Studio 2017, versión 15.5 y anteriores, aparece otro control que actualiza la base de datos de IntelliSense para ese entorno. Vea [Referencia de pestañas de la ventana Entornos de Python](python-environments-window-tab-reference.md) para obtener información detallada sobre la base de datos).

::: moniker range="vs-2017"
> [!Tip]
> Si expande la ventana **Entornos de Python** con un ancho suficiente, obtendrá una vista más completa de los entornos con la que podrá trabajar de una manera más cómoda.
>
> ![Vista de la ventana Python Environments (Entornos de Python) expandida](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Tip]
> Si expande la ventana **Entornos de Python** con un ancho suficiente, obtendrá una vista más completa de los entornos con la que podrá trabajar de una manera más cómoda.
>
> ![Vista de la ventana Python Environments (Entornos de Python) expandida](media/environments/environments-expanded-view-2019.png)
::: moniker-end

> [!Note]
> Aunque Visual Studio respeta la opción de paquetes de sitio de sistema, no ofrece una forma de cambiarla desde dentro de Visual Studio.

### <a name="what-if-no-environments-appear"></a>¿Qué ocurre si no aparece ningún entorno?

Si no aparece ningún entorno, significa que Visual Studio no pudo detectar ninguna instalación de Python en las ubicaciones estándar. Por ejemplo, es posible que haya instalado Visual Studio 2017 o una versión posterior, pero también que haya borrado todas las opciones de intérprete en las opciones del instalador de la carga de trabajo de Python. De manera similar, es posible que haya instalado Visual Studio 2015 o una versión anterior, pero que no haya instalado un intérprete de manera manual (vea [Instalación de intérpretes de Python](installing-python-interpreters.md)).

Si sabe que tiene un intérprete de Python en el equipo pero Visual Studio (cualquier versión) no lo detectó, use el comando **+ Personalizado** para especificar manualmente la ubicación. Consulte la sección siguiente, [Identificación manual de un entorno existente](#manually-identify-an-existing-environment).

> [!Tip]
> Visual Studio detecta las actualizaciones de un intérprete existente, como actualizar Python 2.7.11 a 2.7.14 mediante los instaladores de python.org. Durante el proceso de instalación, el entorno anterior desaparece de la lista de **entornos de Python** antes de que aparezca la actualización en su lugar.
>
> Sin embargo, si mueve manualmente un intérprete y su entorno con el sistema de archivos, Visual Studio no sabrá cuál es la ubicación nueva. Para obtener más información, vea la sección sobre cómo [mover un intérprete](installing-python-interpreters.md#move-an-interpreter).

### <a name="types-of-environments"></a>Tipos de entornos

Visual Studio puede trabajar con entornos globales, virtuales y de Conda.

#### <a name="global-environments"></a>Entornos globales

Cada instalación de Python (por ejemplo, Python 2.7, Python 3.6, Python 3.7, Anaconda 4.4.0, etc., vea [Instalación de intérpretes de Python](installing-python-interpreters.md)) mantiene su propio *entorno global*. Cada entorno está formado por el intérprete de Python correspondiente, su biblioteca estándar, un conjunto de paquetes preinstalados y cualquier paquete adicional que instale mientras ese entorno está activado. Al instalar un paquete en un entorno global, este pasa a estar disponible para todos los proyectos que usan ese entorno. Si el entorno se encuentra en un área protegida del sistema de archivos (dentro de *c:\archivos de programa*, por ejemplo), la instalación de paquetes requiere privilegios de administrador.

Los entornos globales están disponibles para todos los proyectos del equipo. En Visual Studio, debe seleccionar un entorno global como predeterminado, que será el que se utilice para todos los proyectos (a menos que elija específicamente otro diferente para un proyecto). Para más información, vea [Selección de un entorno para un proyecto](selecting-a-python-environment-for-a-project.md).

#### <a name="virtual-environments"></a>Entornos virtuales

Aunque trabajar en un entorno global es una forma sencilla de empezar, con el tiempo, ese entorno se llena de muchos paquetes diferentes que se han instalado para distintos proyectos. Tal desorden dificulta probar exhaustivamente una aplicación en un conjunto específico de paquetes con versiones conocidas, que es exactamente el tipo de entorno que se configuraría en un servidor web o de compilación. También pueden producirse conflictos si dos proyectos necesitan paquetes no compatibles o versiones diferentes del mismo paquete.

Por este motivo, los desarrolladores suelen crear un *entorno virtual* para un proyecto. Un entorno virtual es una subcarpeta de un proyecto que contiene una copia de un intérprete determinado. Al activar el entorno virtual, los paquetes que instale se instalan solo en la subcarpeta de ese entorno. Si luego ejecuta un programa de Python en ese entorno, sabe que se está ejecutando solo en esos paquetes específicos.

Visual Studio permite crear directamente un entorno virtual para un proyecto. Por ejemplo, si abre un proyecto que contiene un archivo *requirements.txt* o crea un proyecto a partir de una plantilla que incluye ese archivo, Visual Studio le pide que cree automáticamente un entorno virtual e instale esas dependencias.

En un proyecto abierto puede crear un nuevo entorno virtual en cualquier momento. En el **Explorador de soluciones**, expanda el nodo del proyecto, haga clic con el botón derecho en **Entornos de Python** y seleccione "Agregar entorno virtual". Para obtener más información, vea [Creación de un entorno virtual](./selecting-a-python-environment-for-a-project.md?view=vs-2019&preserve-view=true#create-a-virtual-environment-1).

Visual Studio además proporciona un comando para generar un archivo *requirements.txt* desde un entorno virtual, con lo que resulta sencillo volver a crear el entorno en otros equipos. Para obtener más información, vea [Use virtual environments](selecting-a-python-environment-for-a-project.md#use-virtual-environments) (Usar entornos virtuales).

#### <a name="conda-environments"></a>Entornos de coda

Un entorno de Conda es el creado mediante la herramienta `conda` o con la administración de Conda integrada en Visual Studio 2017, versión 15.7 y versiones posterior. (Requiere Anaconda o Miniconda, que están disponibles a través del instalador de Visual Studio; vea [Instalación](installing-python-support-in-visual-studio.md#visual-studio-2019-and-visual-studio-2017)).

::: moniker range="vs-2017"

1. Seleccione **+ Crear entorno de Conda** en la ventana **Entornos de Python**, que abre una pestaña **Crear nuevo entorno de Conda**:

    ![Crear pestaña para un nuevo entorno de Conda](media/environments/environments-conda-1.png)

1. Escriba un nombre para el entorno en el campo **Nombre**, luego seleccione un intérprete de Python base en el campo **Python** y, después, seleccione **Crear**.

1. La ventana **Salida** muestra el progreso del nuevo entorno, con algunas instrucciones de CLI cuando se completa la creación:

    ![Creación correcta de un entorno de Conda](media/environments/environments-conda-2.png)

1. En Visual Studio, puede activar un entorno de Conda para un proyecto de la misma forma que con cualquier otro entorno, tal como se describe en [Cómo asignar el entorno de Python que se usa en un proyecto](selecting-a-python-environment-for-a-project.md).

1. Para instalar paquetes en el entorno, use la [pestaña Paquetes](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

::: moniker range=">=vs-2019"

1. Seleccione **+ Agregar entorno** en la ventana **Entornos de Python** (o desde la barra de herramientas de Python), con lo que se abre el cuadro de diálogo **Agregar entorno**. En ese cuadro de diálogo, seleccione la pestaña **Entorno de Conda**:

    ![Pestaña Entorno de Conda en el cuadro de diálogo Agregar entorno](media/environments/environments-conda-1-2019.png)

1. Configure los campos siguientes:

    | Campo | Descripción |
    | --- | --- |
    | Proyecto | Proyecto en el que se creará el entorno (si tiene varios proyectos en la misma solución de Visual Studio). |
    | NOMBRE | Nombre del entorno de Conda. |
    | Agregar paquetes desde | Elija **Archivo de entorno** si tiene un archivo *environment.yml* que describe las dependencias o elija **One or more Anaconda package names** (Uno o más nombres de paquetes de Anaconda) y muestre al menos un paquete de Python o una versión de Python en el campo a continuación. La lista de paquetes indica a Conda que cree un entorno de Python. Para instalar la versión más reciente de Python, use `python`; para instalar una versión específica, use `python=,major>.<minor>` como en `python=3.7`. También puede usar el botón del paquete para seleccionar las versiones de Python y los paquetes comunes en una serie de menús. |
    | Establecer como entorno actual | Activa el entorno nuevo en el proyecto seleccionado una vez que se crea el entorno. |
    | Establecer como entorno predeterminado para los nuevos proyectos | Establecer y activa automáticamente el entorno de Conda en los nuevos proyectos creados en Visual Studio. Esta opción es igual que usar el comando **Convertir este entorno en el predeterminado para nuevos proyectos** en la ventana **Entornos de Python**. |
    | Ver en la ventana de entornos de Python | Especifica si mostrar la ventana **Entornos de Python** después de crear el entorno. |

    > [!Important]
    > Cuando cree un entorno de Conda, asegúrese de especificar al menos una versión de Python o un paquete de Python con `environments.yml` o con la lista de paquetes, lo que garantiza que el entorno contiene un runtime de Python. En caso contrario, Visual Studio omite el entorno: el entorno no aparece en ninguna parte de la ventana **Entornos de Python**, no se establece como el entorno actual de ningún proyecto ni tampoco está disponible como entorno global.
    >
    > Si crea un entorno de Conda sin una versión de Python, use el comando `conda info` para ver las ubicaciones de las carpetas del entorno de Conda y luego quite manualmente la subcarpeta del entorno de esa ubicación.

1. Seleccione **Crear** y observe el progreso en la ventana **Salida**. La salida incluye unas cuantas instrucciones de la CLI una vez que se completa la creación:

    ![Creación correcta de un entorno de Conda](media/environments/environments-conda-2-2019.png)

1. En Visual Studio, puede activar un entorno de Conda para un proyecto de la misma forma que con cualquier otro entorno, tal como se describe en [Cómo asignar el entorno de Python que se usa en un proyecto](selecting-a-python-environment-for-a-project.md).

1. Para instalar paquetes adicionales en el entorno, use la [pestaña Paquetes](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

> [!Note]
> Para obtener mejores resultados con entornos de Conda, use Conda 4.4.8 o posterior (las versiones de Conda son diferentes de las versiones de Anaconda). Puede instalar las versiones adecuadas de Miniconda (Visual Studio 2019) y Anaconda (Visual Studio 2017) mediante el instalador de Visual Studio.

Para ver la versión de conda, donde se almacenan los entornos de Conda, y otra información, ejecute `conda info` en un símbolo del sistema de Anaconda (es decir, un símbolo del sistema donde Anaconda está en la ruta de acceso):

```cli
conda info
```

Las carpetas de entorno de Conda tienen el siguiente aspecto:

```output
       envs directories : C:\Users\user\.conda\envs
                          c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
```

Debido a que los entornos de Conda no se almacenan con un proyecto, actúan de forma similar a los entornos globales. Por ejemplo, al instalar un paquete nuevo en un entorno de conda, ese paquete pasa a estar disponible para todos los proyectos que usan ese entorno.

Para Visual Studio 2017, versión 15.6 y anteriores, puede usar entornos de Conda apuntando a ellos de forma manual tal como se describe en [Manually identify an existing environment](#manually-identify-an-existing-environment) (Identificar de forma manual un entorno existente).

Visual Studio 2017, versión 15.7 y posteriores, detecta automáticamente los entornos de Conda y los muestra en la ventana **Entornos de Python**, tal y como se describe en la sección siguiente.

## <a name="manually-identify-an-existing-environment"></a>Identificación manual de un entorno existente

Use los pasos siguientes para identificar un entorno instalado en una ubicación no estándar, como los entornos de Conda en Visual Studio 2017, versión 15.6 y anteriores:

::: moniker range="vs-2017"

1. Seleccione **+ Personalizado** en la ventana **Entornos de Python**, lo que abre la pestaña **Configurar**:

    ![Vista predeterminada para un nuevo entorno personalizado](media/environments/environments-custom-1.png)

1. Escriba un nombre para el entorno en el campo **Descripción**.

1. Escriba o busque (con **...** ) la ruta de acceso del intérprete en el campo **Ruta de acceso de prefijo**.

1. Si Visual Studio detecta un intérprete de Python en esa ubicación (como la ruta de acceso que aparece a continuación para un entorno de conda), habilita el comando **Detección automática**. Cuando selecciona **Detección automática**, se completan los campos restantes. También puede completar estos campos de manera manual.

    ![Habilitación del comando Detección automática](media/environments/environments-custom-2.png)

    ![Campos de entorno completados después de usar Detección automática](media/environments/environments-custom-3.png)

1. Una vez que los campos contienen los valores que desea, seleccione **Aplicar** para guardar la configuración. Ahora puede usar el entorno como cualquier otro dentro de Visual Studio.

1. Si necesita quitar un entorno identificado manualmente, seleccione el comando **Quitar** en la pestaña **Configurar**. Los entornos detectados automáticamente no proporcionan esta opción. Para más información, consulte la sección sobre la [pestaña de configuración](python-environments-window-tab-reference.md#configure-tab).

::: moniker-end

::: moniker range=">=vs-2019"

1. Seleccione **+ Agregar entorno** en la ventana **Entornos de Python** (o desde la barra de herramientas de Python), con lo que se abre el cuadro de diálogo **Agregar entorno**. En ese cuadro de diálogo, seleccione la pestaña **Entorno existente**:

    ![Pestaña Entorno existente en el cuadro de diálogo Agregar entorno](media/environments/environments-custom-1-2019.png)

1. Seleccione el menú desplegable **Entorno** y seleccione **Personalizado**:

    ![Opción de entorno personalizado en el cuadro de diálogo Agregar entorno](media/environments/environments-custom-2-2019.png)

1. En los campos que se proporcionan en el cuadro de diálogo, escriba o busque (con **...** ) la ruta de acceso del intérprete en **Ruta de acceso del prefijo**, que se rellena en la mayoría de los otros campos. Después de revisar esos valores y modificarlos según sea necesario, seleccione **Agregar**.

    ![Campos para especificar detalles de la opción de un entorno personalizado en el cuadro de diálogo Agregar entorno](media/environments/environments-custom-3-2019.png)

1. Los detalles del entorno se pueden revisar y modificar en cualquier momento en la ventana **Entornos de Python**. En esa ventana, seleccione el entorno y luego, la pestaña **Configurar**. Después de hacer cambios, seleccione el comando **Aplicar**. También puede quitar el entorno con el comando **Quitar** (que no está disponible en entornos detectados automáticamente). Para más información, consulte la sección sobre la [pestaña de configuración](python-environments-window-tab-reference.md#configure-tab).
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>Corrección o eliminación de entornos no válidos

Si Visual Studio encuentra entradas del Registro de un entorno, pero la ruta de acceso para el intérprete no es válida, la ventana **Entornos de Python** mostrará el nombre con una fuente tachada:

::: moniker range="vs-2017"
![Ventana Entornos de Python en la que se muestra un entorno no válido](media/environments/environments-invalid-entry.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Ventana Entornos de Python en la que se muestra un entorno no válido](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

Para corregir un entorno que quiera mantener, en primer lugar intente usar el proceso **Reparar** del instalador. Los instaladores de la versión estándar de Python 3.x, por ejemplo, incluyen esa opción.

Para corregir un entorno sin opción de reparación o quitar un entorno no válido, siga estos pasos para modificar el Registro directamente. Visual Studio actualiza automáticamente la ventana **Entornos de Python** al realizar cambios en el Registro.

1. Ejecute *regedit.exe*.
1. Vaya a **HKEY_LOCAL_MACHINE\SOFTWARE\Python** o a **HKEY_CURRENT_USER\SOFTWARE\Python**. Para IronPython, busque **IronPython**.
1. Expanda el nodo que coincida con la distribución, como **Python Core** para CPython o **ContinuumAnalytics** para Anaconda. Para IronPython, expanda el nodo de número de versión.
1. Inspeccione los valores del nodo **InstallPath**:

    ![Entradas del Registro de una instalación típica de CPython](media/environments/environments-registry-entries.png)

    - Si el entorno todavía figura en el equipo, cambie el valor de **ExecutablePath** a la ubicación adecuada. Corrija también los valores **(Predeterminado)** y **WindowedExecutablePath** según sea necesario.
    - Si el entorno ya no figura en el equipo y quiere eliminarlo de la ventana **Entornos de Python**, elimine el nodo primario de **InstallPath**, como, por ejemplo, **3.6** en la imagen anterior.
    - La configuración no válida en **HKEY_CURRENT_USER\SOFTWARE\Python** reemplaza la configuración en **HKEY_LOCAL_MACHINE\SOFTWARE\Python**

## <a name="see-also"></a>Vea también

- [Instalación de intérpretes de Python](installing-python-interpreters.md)
- [Selección de un intérprete para un proyecto](selecting-a-python-environment-for-a-project.md)
- [Uso de requirements.txt para las dependencias](managing-required-packages-with-requirements-txt.md)
- [Rutas de acceso de búsqueda](search-paths.md)
- [Referencia de ventana Entornos de Python](python-environments-window-tab-reference.md)