---
title: Proyectos de Python en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9c53f76-d0ef-4095-8b39-b7eb9bb33aba
caps.latest.revision: "11"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 3ce10862b3d71be43a86c1a98a9edf822ac9baf6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="python-projects"></a>Proyectos de Python

Las aplicaciones de Python suelen definirse usando solo carpetas y archivos, pero esta estructura se puede complicar a medida que aplicaciones se van haciendo cada vez más grandes y pueden llegar a afectar a los archivos generados automáticamente, a JavaScript para aplicaciones web, etc. Para ayudar a administrar esta complejidad, puede crear proyectos de Visual Studio para aplicaciones de Python. Un proyecto de Python (un archivo `.pyproj`) identifica todos los archivos de origen y de contenido asociados al proyecto, contiene información de compilación para cada archivo, mantiene la información para integrarse con sistemas de control de código fuente y ayuda a organizar la aplicación en componentes lógicos.

Además, los proyectos siempre se administran dentro de una *solución* de Visual Studio, que puede contener cualquier número de proyectos que pueden hacerse referencia entre sí. Por ejemplo, un proyecto de Python puede hacer referencia a un proyecto de C++ para un módulo de extensión, de modo que Visual Studio compila automáticamente el proyecto de C++ (si es necesario) al iniciar la depuración del proyecto de Python. (Para obtener información general, consulte [Soluciones y proyectos en Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)).

![Proyecto de Python en el Explorador de soluciones](media/projects-solution-explorer.png)

Visual Studio proporciona numerosas plantillas de proyecto de Python para configurar rápidamente una serie de estructuras de aplicación, incluida una plantilla para crear un proyecto a partir de un árbol de carpetas existente y una plantilla para crear un proyecto vacío y limpio. Consulte la sección [Plantillas de proyecto](#project-templates) a continuación para un índice.

En este tema:

- [Incorporación de archivos, asignación de un archivo de inicio y establecimiento de entornos](#adding-files-assigning-a-startup-file-and-setting-environments)
- [Plantillas de proyecto](#project-templates)
- [Archivos vinculados](#linked-files)
- [Referencias](#references)

<a name="lightweight-usage-project-free"</a>
> [!Tip]
> Incluso sin un proyecto, Visual Studio funciona bien con código Python, ya que puede abrir un archivo de Python por sí mismo y disfrutar de las funciones de autocompletar, IntellSense y depuración (haciendo clic con el botón derecho en el editor y seleccionando **Iniciar [con | sin] depurar**). Como dicho código siempre usa el entorno global predeterminado, puede ver finalizaciones incorrectas o errores si el código está pensado para un entorno diferente. Además, Visual Studio analiza todos los archivos y paquetes de la carpeta desde la que se abrió el archivo único, lo que podría consumir mucho tiempo de CPU.
>
> Se puede crear fácilmente un proyecto de Visual Studio a partir de código existente, como se describe a continuación en [Creación de un proyecto a partir de archivos existentes](#creating-a-project-from-existing-files).

Para ver una introducción a los proyectos de Python en Visual Studio, eche un vistazo al vídeo [Getting Python Code](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=iLAv23LWE_3905918567) (Obtener código de Python) de Microsoft Virtual Academy (2 minutos y 17 segundos).

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Getting-Python-Code-iLAv23LWE_3905918567]

Vea también el vídeo más antiguo de youtube.com (8 minutos y 55 segundos) [Deep Dive: Using source control with Python projects](https://youtu.be/Aq8eqApnugM) (Profundización: uso del control de código fuente con proyectos de Python).

## <a name="adding-files-assigning-a-startup-file-and-setting-environments"></a>Incorporación de archivos, asignación de un archivo de inicio y establecimiento de entornos

Al desarrollar la aplicación, normalmente necesita agregar nuevos archivos de distintos tipos al proyecto. Agregar dichos archivos se realiza fácilmente haciendo clic con el botón derecho en el proyecto y seleccionando **Agregar > Elemento existente...** , lo que le permitirá buscar un archivo que quiere agregar, o mediante **Agregar > Nuevo elemento...** , que abre un cuadro de diálogo con numerosas plantillas de elementos que incluyen archivos de Python vacíos, una clase de Python, una prueba unitaria y varios archivos relacionados con aplicaciones web. Le recomendamos que explore estas opciones con un proyecto de prueba para saber lo que está disponible en la versión de Visual Studio.

Cada proyecto de Python tiene un archivo de inicio asignado, que se muestra en negrita en el Explorador de soluciones. El archivo de inicio es el archivo que se ejecuta al iniciar la depuración (F5 o **Depurar > Iniciar depuración**) o que ejecuta el proyecto en la ventana interactiva (Alt+Mayús+F5 o **Depurar > Ejecutar proyecto en Python interactivo**). Para cambiarlo, haga clic con el botón derecho en el archivo nuevo y seleccione **Set as Startup File** (Establecer como archivo de inicio).

> [!Tip]
> Si quita de un proyecto el archivo de inicio seleccionado y no selecciona uno nuevo, cuando intente ejecutar el proyecto aparece una ventana de salida de Python que desaparecerá casi de inmediato. Si se produce este comportamiento, compruebe que tiene un archivo de inicio asignado. Además, para mantener abierta la ventana de salida en estos casos, haga clic con el botón derecho en el proyecto, seleccione **Propiedades**, seleccione la pestaña **Depurar** y, después, agregue `-i` al campo **Argumentos del intérprete**. Este argumento hace que el intérprete entre en modo interactivo una vez que ha finalizado un programa, con lo que la ventana se mantendrá abierta hasta que pulse Ctrl+Z, Entrar para salir.

Un proyecto nuevo siempre está asociado al entorno de Python global predeterminado. Para asociar el proyecto a otro entorno (incluidos los entornos virtuales), haga clic con el botón derecho en el nodo **Python Environments** (Entornos de Python) del proyecto, seleccione **Add/Remove Python Environments** (Agregar o quitar entornos de Python) y seleccione los que desee. Para cambiar el entorno activo, haga clic con el botón derecho en el entorno que quiera y seleccione **Activar entorno** como se muestra a continuación. Para más información, consulte [Entornos de Python](python-environments.md#project-specific-environments).

![Activación de un entorno para un proyecto de Python](media/projects-activate-environment.png)

<a name="project-types"</a>
## <a name="project-templates"></a>Plantillas de proyecto

Visual Studio ofrece varias maneras de configurar un proyecto de Python, desde cero o a partir de código existente. Para usar una plantilla, seleccione el comando de menú **Archivo > Nuevo > Proyecto...**  o haga clic con el botón secundario en la solución en el Explorador de soluciones y seleccione **Agregar > Nuevo proyecto...** . Ambas acciones abrirán el cuadro de diálogo **Nuevo proyecto** que se muestra a continuación. Para ver plantillas específicas de Python, busque "Python" o seleccione el nodo **Plantillas > Other Languages (Otros lenguajes) > Python**:

![Cuadro de diálogo Nuevo proyecto con plantillas de Python](media/projects-new-project-dialog.png)

En la tabla siguiente se muestra un resumen de las plantillas disponibles en Visual Studio 2017 (no todas las plantillas están disponibles en todas las versiones anteriores):

| Plantilla | Descripción | 
| --- | --- |
| [From Existing Python Code](#creating-a-project-from-existing-files) (A partir de código Python existente) | Crea un proyecto de Visual Studio a partir de código Python existente en una estructura de carpetas.  |
| Python Application (Aplicación de Python) | Estructura básica de proyecto para una nueva aplicación de Python con un solo archivo de origen vacío. De forma predeterminada, el proyecto se ejecuta en el intérprete de la consola del entorno global predeterminado, que se puede cambiar [asignando un entorno diferente](python-environments.md#project-specific-environments). |
| [Servicio en la nube de Azure](template-azure-cloud-service.md) | Proyecto para un servicio en la nube de Azure escrito en Python. |
| [Proyectos web](template-web.md) | Proyectos para servidores web basados en distintos marcos, incluidos Bottle, Django, Flask y Flask/Jade. |
| IronPython Application (Aplicación de IronPython) | Similar a la plantilla Python Application (Aplicación de Python), pero usa IronPython de forma predeterminada habilitando la interoperabilidad .NET y la depuración en modo mixto con lenguajes de. NET. |
| IronPython WPF Application (Aplicación WPF de IronPython ) | Estructura de proyecto que usa IronPython con archivos XAML de Windows Presentation Foundation para la interfaz de usuario de la aplicación. Visual Studio proporciona un diseñador de IU XAML, el código subyacente se puede escribir en Python y la aplicación se ejecuta sin mostrar una consola. |
| IronPython Silverlight Web Page (Página web de Silverlight en IronPython) | Proyecto de IronPython que se ejecuta en un explorador mediante Silverlight. El código Python de la aplicación se incluye en la página web como un script. Una etiqueta de script reutilizable extrae código de JavaScript que inicializa IronPython ejecutándose dentro de Silverlight, desde donde el código Python puede interactuar con DOM. |
| IronPython Windows Forms Application (Aplicación de Windows Forms en IronPython) | Estructura de proyecto que utiliza IronPython con una interfaz de usuario creada mediante código con Windows Forms. La aplicación se ejecuta sin mostrar una consola. |
| Background Application (IoT) (Aplicación en segundo plano (IoT)) | Admite la implementación de proyectos de Python para que se ejecuten como servicios en segundo plano en dispositivos. Visite el [Centro de desarrollo de Windows IoT](https://dev.windows.com/en-us/iot) para más información. |
| Módulo de extensión de Python | Esta plantilla aparece en Visual C++ si ha instalado las **herramientas de desarrollo nativo de Python** con la carga de trabajo de Python en Visual Studio 2017 (consulte [Instalación](installation.md)). Proporciona la estructura básica de un archivo DLL de extensión de C++, similar a lo que se describe en [Creating a C++ Extension for Python](cpp-and-python.md) (Crear una extensión de C++ para Python). |

<a name="create-project-from-existing-files"</a>

### <a name="creating-a-project-from-existing-files"></a>Creación de un proyecto a partir de archivos existentes

> [!Important]
> El proceso que se describe aquí no mueve ni copia los archivos de código fuente originales. Si quiere trabajar con una copia, duplique primero la carpeta.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Archivos vinculados

Los archivos vinculados son archivos que se incorporan a un proyecto pero normalmente residen fuera de las carpetas de proyecto de la aplicación. Aparecen en el Explorador de soluciones como archivos normales con un icono de acceso directo superpuesto: ![Icono de archivo vinculado](media/projects-linked-file-icon.png)

Los archivos vinculados se especifican en el archivo `.pyproj` mediante el elemento `<Compile Include="...">` normal. Pueden ser archivos vinculados implícitos si usan una ruta de acceso relativa fuera de la estructura de directorios, o pueden ser archivos vinculados explícitos mediante la especificación de su ruta de acceso en el Explorador de soluciones:

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

### <a name="working-with-linked-files"></a>Trabajo con archivos vinculados

Para agregar un elemento existente como un vínculo, haga clic con el botón derecho en la carpeta en el proyecto donde desea agregar el archivo, seleccione **Agregar > Elemento existente...** . En el cuadro de diálogo que aparece, seleccione un archivo y pulse **Agregar como vínculo** en la lista desplegable del botón **Agregar**. Siempre que no haya ningún archivo en conflicto, este comando crea un vínculo en la carpeta seleccionada. Sin embargo, el vínculo no se agrega si ya existe un archivo con el mismo nombre o ya existe un vínculo a ese archivo en el proyecto.

Si intenta establecer el vínculo a un archivo que ya existe en las carpetas de proyecto, se agrega como un archivo normal y no como un vínculo. Para convertir un archivo en un vínculo, seleccione **Archivo > Guardar como** para guardar el archivo en una ubicación fuera de la jerarquía del proyecto; Visual Studio lo convierte automáticamente en un vínculo. De forma similar, se puede convertir un vínculo usando **Archivo > Guardar como** para guardar el archivo en alguna parte dentro de la jerarquía del proyecto. 

Si mueve un archivo vinculado en el Explorador de soluciones, el vínculo se mueve, pero esta operación no afectará al archivo real. De manera similar, al eliminar un vínculo este se quita sin afectar al archivo.

El nombre de los archivos vinculados no se puede cambiar.

## <a name="references"></a>Referencias

Los proyectos de Visual Studio admiten la incorporación de referencias a proyectos y extensiones, que aparecen en el nodo **References** del Explorador de soluciones:

![Referencias de extensión en proyectos de Python](media/projects-extension-references.png)

Las referencias de extensión normalmente indican dependencias entre proyectos y se utilizan para proporcionar IntelliSense en tiempo de diseño o vinculación en tiempo de compilación. Los proyectos de Python usan referencias de manera similar pero, debido a la naturaleza dinámica de Python, se utilizan principalmente en tiempo de diseño para mejorar la funcionalidad IntelliSense. También se pueden utilizar para implementación en Microsoft Azure para instalar dependencias adicionales.

### <a name="extension-modules"></a>Módulos de extensión

Una referencia a un archivo `.pyd` habilita IntelliSense para el módulo generado. Visual Studio carga el archivo `.pyd` en el intérprete de Python y realiza introspecciones en sus tipos y funciones. También intenta analizar las cadenas de documento para que las funciones proporcionen ayuda para las firmas.

Si en cualquier momento el módulo de extensión se actualiza en el disco, Visual Studio vuelve a analizarlo en segundo plano. Esta acción no afecta al comportamiento en tiempo de ejecución, pero algunas finalizaciones no están disponibles hasta que se complete el análisis.

Puede que también necesite agregar una [ruta de acceso de búsqueda](python-environments.md#search-paths) a la carpeta que contiene el módulo.

### <a name="net-projects"></a>Proyectos de .NET

Cuando trabaje con IronPython, puede agregar referencias a ensamblados de .NET para habilitar IntelliSense. Para los proyectos de .NET de la solución, haga clic con el botón derecho en el nodo **References** en el proyecto de Python, seleccione **Agregar referencia**, seleccione la pestaña **Proyectos** y vaya al proyecto que desee. Para archivos DLL que haya descargado por separado, seleccione la pestaña **Examinar** y vaya al archivo DLL que desee.

Dado que las referencias de IronPython no están disponibles hasta que se realiza una llamada a `clr.AddReference('AssemblyName')`, también necesita agregar una llamada `clr.AddReference` al ensamblado.

### <a name="webpi-projects"></a>Proyectos de WebPI

Puede agregar referencias a entradas de producto de WebPI para la implementación en el servicio en la nube de Microsoft Azure donde puede instalar componentes adicionales a través de la fuente de WebPI. De manera predeterminada, la fuente que se muestra es específica de Python e incluye Django, CPython y otros componentes principales. También puede seleccionar su propia fuente tal como se muestra a continuación. Al publicar en Microsoft Azure, una tarea de configuración instala todos los productos a los que se hace referencia.

![Referencias de WebPI](media/projects-webPI-components.png)