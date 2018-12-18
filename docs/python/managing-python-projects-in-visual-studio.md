---
title: Administración de proyectos de aplicación de Python
description: El propósito de los proyectos de Visual Studio, cómo crear y administrar proyectos de código de Python y las diferentes plantillas de proyecto disponibles para Python.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 9f5612aa166f81bf1f42983989db5bdf5422a7ef
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220474"
---
# <a name="python-projects-in-visual-studio"></a>Proyectos de Python en Visual Studio

Las aplicaciones de Python suelen definirse usando solo carpetas y archivos, pero esta estructura se puede complicar a medida que aplicaciones se van haciendo cada vez más grandes y pueden llegar a afectar a los archivos generados automáticamente, a JavaScript para aplicaciones web, etc. Un proyecto de Visual Studio le ayuda a administrar esta complejidad. El proyecto (un archivo *.pyproj*) identifica todos los archivos de origen y de contenido asociados al proyecto, contiene información de compilación para cada archivo, mantiene la información para integrarse con sistemas de control de código fuente y le ayuda a organizar la aplicación en componentes lógicos.

![Proyecto de Python en el Explorador de soluciones](media/projects-solution-explorer.png)

Además, los proyectos siempre se administran dentro de una *solución* de Visual Studio, que puede contener cualquier número de proyectos que pueden hacerse referencia entre sí. Por ejemplo, un proyecto de Python puede hacer referencia a un proyecto de C++ que implementa un módulo de extensión. Con esta relación, Visual Studio genera automáticamente el proyecto de C++ (si es necesario) al iniciar la depuración del proyecto de Python. (Para obtener información general, consulte [Soluciones y proyectos en Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)).

Visual Studio proporciona numerosas plantillas de proyecto de Python para configurar rápidamente una serie de estructuras de aplicación, incluida una plantilla para crear un proyecto a partir de un árbol de carpetas existente y una plantilla para crear un proyecto vacío y limpio. Consulte la sección [Plantillas de proyecto](#project-templates) para ver un índice.

<a name="lightweight-usage-project-free"></a>

> [!Tip]
> Incluso sin un proyecto, Visual Studio funciona bien con código de Python. Por ejemplo, puede abrir un archivo de Python por sí mismo y disfrutar de las funciones de autocompletar, IntelliSense y depuración. Para ello, haga clic con el botón derecho en el editor y seleccione **Iniciar con depurar**. Como dicho código siempre usa el entorno global predeterminado, puede ver finalizaciones incorrectas o errores si el código está pensado para un entorno diferente. Además, Visual Studio analiza todos los archivos y paquetes de la carpeta desde la que se abrió el archivo único, lo que podría consumir mucho tiempo de CPU.
>
> Se puede crear fácilmente un proyecto de Visual Studio a partir de código existente, como se describe en [Creación de un proyecto a partir de archivos existentes](#create-project-from-existing-files).

|   |   |
|---|---|
| ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo") | [Vea un vídeo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Getting-Python-Code-iLAv23LWE_3905918567) para obtener una introducción a los proyectos de Python (2 minutos 17 segundos). |
| ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo") | Consulte también el vídeo de Youtube.com (8 minutos y 55 segundos) [Deep Dive: Use source control with Python projects](https://youtu.be/Aq8eqApnugM) (Profundización: uso del control de código fuente con proyectos de Python). |

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Incorporación de archivos, asignación de un archivo de inicio y establecimiento de entornos

Al desarrollar la aplicación, normalmente necesita agregar nuevos archivos de distintos tipos al proyecto. La adición de dichos archivos se realiza fácilmente haciendo clic con el botón derecho en el proyecto y seleccionando **Agregar** > **Elemento existente**, lo que le permitirá buscar un archivo que quiere agregar, o mediante **Agregar** > **Nuevo elemento**, que abre un cuadro de diálogo con numerosas plantillas de elementos. Como se describe en la referencia sobre [plantillas de elemento](python-item-templates.md), las opciones incluyen archivos de Python vacíos, una clase de Python, una prueba unitaria y varios archivos relacionados con aplicaciones web. Puede explorar estas opciones con un proyecto de prueba para saber lo que está disponible en la versión de Visual Studio.

Cada proyecto de Python tiene un archivo de inicio asignado, que se muestra en negrita en el **Explorador de soluciones**. El archivo de inicio es el archivo que se ejecuta al iniciar la depuración (**F5** o **Depurar** > **Iniciar depuración**) o que ejecuta el proyecto en la ventana **interactiva** (**Mayús**+**Alt**+**F5** o **Depurar** > **Ejecutar proyecto en Python interactivo**). Para cambiarlo, haga clic con el botón derecho en el archivo nuevo y seleccione **Set as Startup File** (Establecer como archivo de inicio).

> [!Tip]
> Si quita el archivo de inicio seleccionado de un proyecto y no selecciona uno nuevo, Visual Studio no sabrá con que archivo de Python empezar al intentar ejecutar el proyecto. En este caso, Visual Studio 2017, versión 15.6 y posteriores, muestra un error; con las versiones anteriores, se abre una ventana de salida con el intérprete de Python en ejecución o verá la ventana de salida aparecer pero desaparecer a continuación casi de inmediato. Si se produce alguno de estos comportamientos, compruebe que tiene un archivo de inicio asignado.
>
> Si desea mantener abierta la ventana de salida por cualquier motivo, haga clic con el botón derecho en el proyecto, seleccione **Propiedades**, seleccione la pestaña **Depurar** y, después, agregue `-i` al campo **Argumentos del intérprete**. Este argumento hace que el intérprete entre en modo interactivo una vez que se haya finalizado un programa, con lo que la ventana se mantendrá abierta hasta que pulse **Ctrl**+**Z** > **Entrar** para salir.

Un proyecto nuevo siempre está asociado al entorno de Python global predeterminado. Para asociar el proyecto a otro entorno (incluidos los entornos virtuales), haga clic con el botón derecho en el nodo **Python Environments** (Entornos de Python) del proyecto, seleccione **Add/Remove Python Environments** (Agregar o quitar entornos de Python) y seleccione los que desee. Para cambiar el entorno activo, haga clic con el botón derecho en el entorno que quiera y seleccione **Activar entorno** como se muestra a continuación. Para más información, vea [Selección de un entorno para un proyecto](selecting-a-python-environment-for-a-project.md).

![Activación de un entorno para un proyecto de Python](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Plantillas de proyecto

Visual Studio ofrece varias maneras de configurar un proyecto de Python, desde cero o a partir de código existente. Para usar una plantilla, seleccione el comando de menú **Archivo** > **Nuevo** > **Proyecto** o haga clic con el botón derecho en la solución en el **Explorador de soluciones** y seleccione **Agregar** > **Nuevo proyecto**. Ambas acciones abrirán el cuadro de diálogo **Nuevo proyecto** que se muestra a continuación. Para ver plantillas específicas de Python, busque "Python" o seleccione el nodo **Instalado** > **Python**:

![Cuadro de diálogo Nuevo proyecto con plantillas de Python](media/projects-new-project-dialog.png)

En la tabla siguiente se muestra un resumen de las plantillas disponibles en Visual Studio 2017 (no todas las plantillas están disponibles en todas las versiones anteriores):

| Plantilla | Descripción |
| --- | --- |
| [**Desde código de Python existente**](#create-project-from-existing-files) | Crea un proyecto de Visual Studio a partir de código Python existente en una estructura de carpetas.  |
| **Aplicación de Python** | Estructura básica de proyecto para una nueva aplicación de Python con un solo archivo de origen vacío. De forma predeterminada, el proyecto se ejecuta en el intérprete de la consola del entorno global predeterminado, que se puede cambiar [asignando un entorno diferente](selecting-a-python-environment-for-a-project.md). |
| [**Servicio en la nube de Azure**](python-azure-cloud-service-project-template.md) | Proyecto para un servicio en la nube de Azure escrito en Python. |
| [**Proyectos web**](python-web-application-project-templates.md) | Proyectos para aplicaciones web basados en distintos marcos, incluidos Bottle, Django y Flask. |
| **Aplicación de IronPython** | Similar a la plantilla Python Application (Aplicación de Python), pero usa IronPython de forma predeterminada habilitando la interoperabilidad .NET y la depuración en modo mixto con lenguajes de. NET. |
| **Aplicación de WPF de IronPython** | Estructura de proyecto que usa IronPython con archivos XAML de Windows Presentation Foundation para la interfaz de usuario de la aplicación. Visual Studio proporciona un diseñador de IU XAML, el código subyacente se puede escribir en Python y la aplicación se ejecuta sin mostrar una consola. |
| **Página de IronPython y Silverlight** | Proyecto de IronPython que se ejecuta en un explorador mediante Silverlight. El código Python de la aplicación se incluye en la página web como un script. Una etiqueta de script reutilizable extrae código de JavaScript que inicializa IronPython ejecutándose dentro de Silverlight, desde donde el código Python puede interactuar con DOM. |
| **Aplicación de Windows Forms de IronPython** | Estructura de proyecto que usa IronPython con la interfaz de usuario creada mediante código con Windows Forms. La aplicación se ejecuta sin mostrar una consola. |
| **Aplicación en segundo plano (IoT)** | Admite la implementación de proyectos de Python para que se ejecuten como servicios en segundo plano en dispositivos. Visite el [Centro de desarrollo de Windows IoT](https://dev.windows.com/en-us/iot) para más información. |
| **Módulo de extensión de Python** | Esta plantilla aparece en Visual C++ si ha instalado las **herramientas de desarrollo nativo de Python** con la carga de trabajo de Python en Visual Studio 2017 (consulte [Instalación](installing-python-support-in-visual-studio.md)). Proporciona la estructura básica de un archivo DLL de extensión de C++, similar a lo que se describe en [Creación de una extensión de C++ para Python](working-with-c-cpp-python-in-visual-studio.md). |

> [!Note]
> Dado que Python es un lenguaje interpretado, los proyectos de Python en Visual Studio no producen un archivo ejecutable independiente al igual que otros proyectos de lenguaje compilado (C#, por ejemplo). Para obtener más información, consulte [Preguntas y respuestas](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Creación de un proyecto a partir de archivos existentes

> [!Important]
> El proceso que se describe aquí no mueve ni copia los archivos de código fuente originales. Si quiere trabajar con una copia, duplique primero la carpeta.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Archivos vinculados

Los archivos vinculados son archivos que se incorporan a un proyecto pero normalmente residen fuera de las carpetas de proyecto de la aplicación. Aparecen en el **Explorador de soluciones** como archivos normales con un icono de acceso directo superpuesto: ![Icono de archivo vinculado](media/projects-linked-file-icon.png)

Los archivos vinculados se especifican en el archivo *.pyproj* mediante el elemento `<Compile Include="...">`. Los archivos vinculados son implícitos si usan una ruta de acceso relativa fuera de la estructura de directorios o explícitos si usan rutas de acceso dentro del **Explorador de soluciones**:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Los archivos vinculados se omiten en cualquiera de las condiciones siguientes:

- El archivo vinculado contiene metadatos de vínculo y la ruta de acceso especificada en el atributo Include reside dentro del directorio del proyecto.
- El archivo vinculado duplica un archivo que existe dentro de la jerarquía del proyecto.
- El archivo vinculado contiene metadatos de vínculo y la ruta de acceso del vínculo es una ruta de acceso relativa fuera de la jerarquía del proyecto.
- La ruta de acceso del vínculo es raíz.

### <a name="work-with-linked-files"></a>Trabajar con archivos vinculados

Para agregar un elemento existente como un vínculo, haga clic con el botón derecho en la carpeta donde desea agregar el archivo, seleccione **Agregar** > **Elemento existente**. En el cuadro de diálogo que aparece, seleccione un archivo y pulse **Agregar como vínculo** en la lista desplegable del botón **Agregar**. Siempre que no haya ningún archivo en conflicto, este comando crea un vínculo en la carpeta seleccionada. Sin embargo, el vínculo no se agrega si ya existe un archivo con el mismo nombre o ya existe un vínculo a ese archivo en el proyecto.

Si intenta establecer el vínculo a un archivo que ya existe en las carpetas de proyecto, se agrega como un archivo normal y no como un vínculo. Para convertir un archivo en un vínculo, seleccione **Archivo** > **Guardar como** para guardar el archivo en una ubicación fuera de la jerarquía del proyecto; Visual Studio lo convierte automáticamente en un vínculo. De forma similar, se puede invertir la conversión de un vínculo mediante **Archivo** > **Guardar como** para guardar el archivo en algún lugar dentro de la jerarquía del proyecto. 

Si mueve un archivo vinculado en el **Explorador de soluciones**, dicho vínculo se mueve, pero el archivo real no se ve afectado. De manera similar, al eliminar un vínculo este se quita sin afectar al archivo.

El nombre de los archivos vinculados no se puede cambiar.

## <a name="references"></a>Referencias

Los proyectos de Visual Studio admiten la incorporación de referencias a proyectos y extensiones, que aparecen bajo el nodo **References** del **Explorador de soluciones**:

![Referencias de extensión en proyectos de Python](media/projects-extension-references.png)

Las referencias de extensión normalmente indican dependencias entre proyectos y se utilizan para proporcionar IntelliSense en tiempo de diseño o vinculación en tiempo de compilación. Los proyectos de Python usan referencias de manera similar pero, debido a la naturaleza dinámica de Python, se utilizan principalmente en tiempo de diseño para mejorar la funcionalidad IntelliSense. También se pueden utilizar para implementación en Microsoft Azure para instalar dependencias adicionales.

### <a name="extension-modules"></a>Módulos de extensión

Una referencia a un archivo *.pyd* habilita IntelliSense para el módulo generado. Visual Studio carga el archivo *.pyd* en el intérprete de Python y realiza introspecciones en sus tipos y funciones. También intenta analizar las cadenas de documento para que las funciones proporcionen ayuda para las firmas.

Si en cualquier momento el módulo de extensión se actualiza en el disco, Visual Studio vuelve a analizarlo en segundo plano. Esta acción no afecta al comportamiento en tiempo de ejecución, pero algunas finalizaciones no están disponibles hasta que se complete el análisis.

Puede que también necesite agregar una [ruta de acceso de búsqueda](search-paths.md) a la carpeta que contiene el módulo.

### <a name="net-projects"></a>Proyectos de .NET

Cuando trabaje con IronPython, puede agregar referencias a ensamblados de .NET para habilitar IntelliSense. Para los proyectos de .NET de la solución, haga clic con el botón derecho en el nodo **References** en el proyecto de Python, seleccione **Agregar referencia**, seleccione la pestaña **Proyectos** y vaya al proyecto que desee. Para archivos DLL que haya descargado por separado, seleccione la pestaña **Examinar** y vaya al archivo DLL que desee.

Dado que las referencias de IronPython no están disponibles hasta que se realiza una llamada a `clr.AddReference('<AssemblyName>')`, también necesita agregar una llamada `clr.AddReference` apropiada al ensamblado, normalmente al principio del código. Por ejemplo, el código creado por la plantilla de proyecto **IronPython Windows Forms Application** (Aplicación de Windows Forms en IronPython) de Visual Studio incluye dos llamadas en la parte superior del archivo:

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>Proyectos de WebPI

Puede agregar referencias a entradas de producto de WebPI para la implementación en Microsoft Azure Cloud Services donde puede instalar componentes adicionales a través de la fuente de WebPI. De manera predeterminada, la fuente que se muestra es específica de Python e incluye Django, CPython y otros componentes principales. También puede seleccionar su propia fuente tal como se muestra a continuación. Al publicar en Microsoft Azure, una tarea de configuración instala todos los productos a los que se hace referencia.

![Referencias de WebPI](media/projects-webPI-components.png)
