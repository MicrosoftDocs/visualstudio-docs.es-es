---
title: Proyectos de Python en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9c53f76-d0ef-4095-8b39-b7eb9bb33aba
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: eb3abd0f37e52f2b1db3793a5471b74a5e0c37ff
ms.lasthandoff: 04/10/2017

---

# <a name="python-projects"></a>Proyectos de Python

Las aplicaciones de Python suelen definirse usando solo carpetas y archivos, pero esto se puede complicar a medida que aplicaciones se van haciendo cada vez más grandes y pueden llegar a afectar a los archivos generados automáticamente, a JavaScript para aplicaciones web, etc. Para ayudar a administrar esta complejidad, puede crear proyectos de Visual Studio para aplicaciones de Python. Un proyecto de Python (un archivo `.pyproj`) identifica todos los archivos de origen y de contenido asociados al proyecto, contiene información de compilación para cada archivo, mantiene la información para integrarse con sistemas de control de código fuente y ayuda a organizar la aplicación en componentes lógicos.

Además, los proyectos siempre se administran dentro de una *solución* de Visual Studio, que puede contener cualquier número de proyectos que pueden hacerse referencia entre sí. Por ejemplo, un proyecto de Python puede hacer referencia a un proyecto de C++ para un módulo de extensión, de modo que Visual Studio compilará automáticamente el proyecto de C++ (si es necesario) al iniciar la depuración del proyecto de Python. (Para obtener información general, consulte [Soluciones y proyectos en Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)).

![Proyecto de Python en el Explorador de soluciones](media/projects-solution-explorer.png)

Visual Studio proporciona numerosas plantillas de proyecto de Python para configurar rápidamente una serie de estructuras de aplicación, incluida una plantilla para crear un proyecto a partir de un árbol de carpetas existente y una plantilla para crear un proyecto vacío y limpio. Consulte la sección [Plantillas de proyecto](#project-templates) a continuación para un índice.

En este tema:

- [Incorporación de archivos, asignación de un archivo de inicio y establecimiento de entornos](#adding-files-assigning-a-startup-file-and-setting-environments)
- [Plantillas de proyecto](#project-templates)
- [Archivos vinculados](#linked-files)
- [Referencias](#references)

<a name="lightweight-usage-project-free"</a>
> [!Tip]
> Incluso sin un proyecto, Visual Studio funciona bien con código Python, ya que puede abrir un archivo de Python por sí mismo y disfrutar de las funciones de autocompletar, IntellSense y depuración (haciendo clic con el botón derecho en el editor y seleccionando **Iniciar [con | sin] depurar**). No obstante, dado que dicho código siempre usará el entorno global predeterminado, puede ver finalizaciones incorrectas o errores si el código está pensado para un entorno diferente. Además, Visual Studio analiza todos los archivos y paquetes de la carpeta desde la que se abrió el archivo único, lo que podría consumir mucho tiempo de CPU.
>
> Se puede crear fácilmente un proyecto de Visual Studio a partir de código existente, como se describe a continuación en [Creación de un proyecto a partir de archivos existentes](#creating-a-project-from-existing-files).

Para obtener una introducción a los proyectos de Python en Visual Studio, consulte el vídeo de youtube.com (3 minutos y 18 segundos) [Getting Started with Python Tools Part 2: Projects](https://youtu.be/KHPoVpL7zHg?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (Introducción a las Herramientas de Python - Parte 2: proyectos).

> [!VIDEO https://www.youtube.com/embed/KHPoVpL7zHg]

Consulte también el vídeo de youtube.com (8 minutos y 55 segundos) [Deep Dive: Using source control with Python projects](https://youtu.be/Aq8eqApnugM) (Profundización: uso del control de código fuente con proyectos de Python).

> [!VIDEO https://www.youtube.com/embed/Aq8eqApnugM]


## <a name="adding-files-assigning-a-startup-file-and-setting-environments"></a>Incorporación de archivos, asignación de un archivo de inicio y establecimiento de entornos

Al desarrollar la aplicación, normalmente necesitará agregar nuevos archivos de distintos tipos al proyecto. Esto se realiza fácilmente haciendo clic con el botón derecho en el proyecto y seleccionando **Agregar > Elemento existente...**, lo que le permitirá buscar un archivo que desea agregar, o mediante **Agregar > Nuevo elemento... **, que abre un cuadro de diálogo con numerosas plantillas de elementos que incluyen archivos de Python vacíos, una clase de Python, una prueba unitaria y varios archivos relacionados con aplicaciones web. Le recomendamos que explore estas opciones con un proyecto de prueba para saber lo que está disponible en la versión de Visual Studio.

Cada proyecto de Python tiene un archivo de inicio asignado, que se muestra en negrita en el Explorador de soluciones. Se trata del archivo que se ejecuta al iniciar la depuración (F5 o **Depurar > Iniciar depuración**) o que ejecuta el proyecto en la ventana interactiva (Alt+Mayús+F5 o **Depurar > Ejecutar proyecto en Python interactivo**). Para cambiarlo, haga clic con el botón derecho en el archivo nuevo y seleccione **Set as Startup File** (Establecer como archivo de inicio).

> [!Tip]
> Si quita de un proyecto el archivo de inicio seleccionado y no selecciona uno nuevo, cuando intente ejecutar el proyecto aparecerá una ventana de salida de Python que desaparecerá casi de inmediato. Si se produce este comportamiento, compruebe que tiene un archivo de inicio asignado. Además, para mantener abierta la ventana de salida en estos casos, haga clic con el botón derecho en el proyecto, seleccione **Propiedades**, seleccione la pestaña **Depurar** y, después, agregue `-i` al campo **Argumentos del intérprete**. Esto hará que el intérprete entre en modo interactivo una vez que haya finalizado un programa, con lo que la ventana se mantendrá abierta hasta que pulse Ctrl+Z, ENTRAR para salir.

Un proyecto nuevo siempre está asociado al entorno de Python global predeterminado. Para asociar el proyecto a otro entorno (incluidos los entornos virtuales), haga clic con el botón derecho en el nodo **Python Environments** (Entornos de Python) del proyecto, seleccione **Add/Remove Python Environments** (Agregar o quitar entornos de Python) y seleccione los que desee. Para cambiar el entorno activo, haga clic con el botón derecho en el entorno que desee y seleccione **Activate Environment** (Activar entorno) tal como se muestra a continuación. Para más información, consulte [Entornos de Python](python-environments.md#project-specific-environments).

![Activación de un entorno para un proyecto de Python](media/projects-activate-environment.png)

<a name="project-types"</a>
## <a name="project-templates"></a>Plantillas de proyecto

Visual Studio ofrece varias maneras de configurar un proyecto de Python, desde cero o a partir de código existente. Para usar una plantilla, seleccione el comando de menú **Archivo > Nuevo > Proyecto...** o haga clic con el botón secundario en la solución en el Explorador de soluciones y seleccione **Agregar > Nuevo proyecto... **. Ambas acciones abrirán el cuadro de diálogo **Nuevo proyecto** que se muestra a continuación. Para ver plantillas específicas de Python, busque "Python" o seleccione el nodo **Plantillas > Other Languages (Otros lenguajes) > Python**:

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
| Módulo de extensión de Python | Esta plantilla aparece en Visual C++ si ha instalado las **herramientas de desarrollo nativo Python** con la carga de trabajo de Python en Visual Studio 2017 Preview (vea [Instalación](installation.md)). Proporciona la estructura básica de un archivo DLL de extensión de C++, similar a lo que se describe en [Creating a C++ Extension for Python](cpp-and-python.md) (Crear una extensión de C++ para Python). |

<a name="create-project-from-existing-files"</a>
### <a name="creating-a-project-from-existing-files"></a>Creación de un proyecto a partir de archivos existentes

1. Seleccione el menú **Archivo > Nuevo > Proyecto...** y luego seleccione la plantilla **From Existing Python Code** (A partir de código Python existente).
1. En el cuadro de diálogo siguiente, establezca la ruta de acceso al código existente, un filtro para tipos de archivo y cualquier ruta de acceso de búsqueda que requiera el proyecto. Por último, seleccione **Siguiente**:

    ![Nuevo proyecto a partir de código existente, paso uno](media/projects-from-existing-1.png)

1. Elija un entorno para el proyecto y el archivo de inicio; luego presione **Siguiente**. (Tenga en cuenta que el cuadro de diálogo solo muestra los archivos de la raíz del árbol de carpetas; si el archivo que desea está en una subcarpeta, deje el archivo de inicio en blanco y establézcalo posteriormente en el Explorador de soluciones).

    ![Nuevo proyecto a partir de código existente, paso dos](media/projects-from-existing-2.png)

1. Seleccione la ubicación para guardar el archivo de proyecto (esto no mueve o copia los archivos de origen originales, por lo que si desea una copia, debe hacer una antes de utilizar la plantilla). En este cuadro de diálogo también puede incluir la detección automática de entornos virtuales y personalizar el proyecto para marcos web diferentes.

    ![Nuevo proyecto a partir de código existente, paso tres](media/projects-from-existing-3.png)

1.  Seleccione **Finalizar** y Visual Studio creará el proyecto y lo abrirá en el Explorador de soluciones. Si desea mover el archivo .pyproj a otra parte, selecciónelo en el Explorador de soluciones y elija **Archivo > Guardar como**. Esto actualiza las referencias de archivo en el proyecto pero no moverá ningún archivo de código.

## <a name="linked-files"></a>Archivos vinculados

Los archivos vinculados son aquellos que se incorporan a un proyecto pero normalmente residen fuera de las carpetas de proyecto de la aplicación. Aparecen en el Explorador de soluciones como archivos normales con un icono de acceso directo superpuesto: ![Icono de archivo vinculado](media/projects-linked-file-icon.png)

Los archivos vinculados se especifican en el archivo `.pyproj` mediante el elemento `<Compile Include="...">` normal. Pueden ser archivos vinculados implícitos si usan una ruta de acceso relativa fuera de la estructura de directorios, o pueden ser archivos vinculados explícitos mediante la especificación de su ruta de acceso en el Explorador de soluciones:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Los archivos vinculados se omitirán en cualquiera de las condiciones siguientes:

- El archivo vinculado contiene metadatos de vínculo y la ruta de acceso especificada en el atributo Include reside dentro del directorio del proyecto.
- El archivo vinculado duplica un archivo que existe dentro de la jerarquía del proyecto.
- El archivo vinculado contiene metadatos de vínculo y la ruta de acceso del vínculo es una ruta de acceso relativa fuera de la jerarquía del proyecto.
- La ruta de acceso del vínculo es raíz.

### <a name="working-with-linked-files"></a>Trabajo con archivos vinculados

Para agregar un elemento existente como un vínculo, haga clic con el botón derecho en la carpeta en el proyecto donde desea agregar el archivo, seleccione **Agregar > Elemento existente...**. En el cuadro de diálogo que aparece, seleccione un archivo y elija **Agregar como vínculo** en la lista desplegable del botón **Agregar**. Siempre que no haya ningún archivo en conflicto, esta acción creará un vínculo en la carpeta seleccionada. Sin embargo, el vínculo no se agrega si ya existe un archivo con el mismo nombre o ya existe un vínculo a ese archivo en el proyecto.

Si intenta establecer el vínculo a un archivo que ya existe en las carpetas de proyecto, se agregará como un archivo normal y no como un vínculo. Para convertir un archivo en un vínculo, seleccione **Archivo > Guardar como** para guardar el archivo en una ubicación fuera de la jerarquía del proyecto; Visual Studio lo convertirá automáticamente en un vínculo. De forma similar, se puede convertir un vínculo usando **Archivo > Guardar como** para guardar el archivo en alguna parte dentro de la jerarquía del proyecto. 

Si mueve un archivo vinculado en el Explorador de soluciones, el vínculo se moverá, pero esta operación no afectará al archivo real. De forma similar, al eliminar un vínculo este se quitará pero no afectará al archivo.

El nombre de los archivos vinculados no se puede cambiar.

## <a name="references"></a>Referencias

Los proyectos de Visual Studio admiten la incorporación de referencias a proyectos y extensiones, que aparecen en el nodo **References** del Explorador de soluciones:

![Referencias de extensión en proyectos de Python](media/projects-extension-references.png)

Las referencias de extensión normalmente indican dependencias entre proyectos y se utilizan para proporcionar IntelliSense en tiempo de diseño o vinculación en tiempo de compilación. Los proyectos de Python usan referencias de manera similar pero, debido a la naturaleza dinámica de Python, se utilizan principalmente en tiempo de diseño para mejorar la funcionalidad IntelliSense. También se pueden utilizar para implementación en Microsoft Azure para instalar dependencias adicionales.

### <a name="extension-modules"></a>Módulos de extensión

Una referencia a un archivo `.pyd` habilita IntelliSense para el módulo generado. Visual Studio carga el archivo `.pyd` en el intérprete de Python y realiza introspecciones en sus tipos y funciones. También intenta analizar las cadenas de documento para que las funciones proporcionen ayuda para las firmas.

Si en cualquier momento el módulo de extensión se actualiza en el disco, Visual Studio vuelve a analizarlo en segundo plano. Esta operación no afecta al comportamiento en tiempo de ejecución, pero algunas finalizaciones no estarán disponibles hasta que se complete el análisis.

Puede que también necesite agregar una [ruta de acceso de búsqueda](python-environments.md#search-paths) a la carpeta que contiene el módulo.

### <a name="net-projects"></a>Proyectos de .NET

Cuando trabaje con IronPython, puede agregar referencias a ensamblados de .NET para habilitar IntelliSense. Para los proyectos de .NET de la solución, haga clic con el botón derecho en el nodo **References** en el proyecto de Python, seleccione **Agregar referencia**, seleccione la pestaña **Proyectos** y vaya al proyecto que desee. Para archivos DLL que haya descargado por separado, seleccione la pestaña **Examinar** y vaya al archivo DLL que desee.

Dado que las referencias de IronPython no están disponibles hasta que se realiza una llamada a `clr.AddReference('AssemblyName')`, también necesitará agregar una llamada `clr.AddReference` al ensamblado.

### <a name="webpi-projects"></a>Proyectos de WebPI

Puede agregar referencias a entradas de producto de WebPI para la implementación en el servicio en la nube de Microsoft Azure donde puede instalar componentes adicionales a través de la fuente de WebPI. De forma predeterminada, la fuente que se muestra es específica de Python e incluye Django, CPython y otros componentes principales. También puede seleccionar su propia fuente tal como se muestra a continuación. Al publicar en Microsoft Azure, una tarea de configuración instala todos los productos a los que se hace referencia.

![Referencias de WebPI](media/projects-webPI-components.png)
