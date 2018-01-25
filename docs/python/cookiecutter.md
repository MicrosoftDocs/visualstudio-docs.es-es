---
title: "Extensión CookieCutter para Python en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: d87beb4e8f475bd52c5be7f1d75f27ecf3b691ac
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2018
---
# <a name="using-the-cookiecutter-extension"></a>Uso de la extensión Cookiecutter

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) proporciona una interfaz gráfica de usuario para descubrir plantillas, opciones de plantilla de entrada y crear proyectos y archivos. Se incluye con Visual Studio de 2017 y puede instalarse por separado en versiones anteriores de Visual Studio.

Cookiecutter requiere Python 3.3 o posterior (32 o 64 bits) o Anaconda 3 4.2 o posterior (32 o 64 bits). Si no se dispone de un intérprete de Python adecuado, Visual Studio mostrará una advertencia. Si instala a un intérprete de Python mientras se está ejecutando Visual Studio, haga clic en el botón de inicio en la barra de herramientas de Cookiecutter para detectar el intérprete recién instalado. (Vea [Entornos de Python](managing-python-environments-in-visual-studio.md) para obtener más información sobre los entornos en general).

Una vez instalado, seleccione **View > Cookiecutter Explorer** (Ver > Explorador de Cookiecutter) para abrir la ventana:

![Ventana principal de Cookiecutter](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Flujo de trabajo Cookiecutter

Trabajar con Cookiecutter es un proceso que implica explorar y seleccionar una plantilla, clonarla en la máquina local, configurar opciones y luego crear código a partir de esa plantilla, tal como se describe en las secciones siguientes.

### <a name="browsing-templates"></a>Exploración de plantillas

La página de inicio de Cookiecutter muestra una lista de plantillas para elegir, organizada en los siguientes grupos:

| Agrupar | Description | 
| --- | --- |
| Instalado | Plantillas que se han instalado en la máquina local. Cuando se usa una plantilla en línea, su repositorio se clona automáticamente en una subcarpeta de `~/.cookiecutters`. Puede eliminar una plantilla instalada seleccionada presionando **Supr**. |
| Se recomienda | Plantillas cargadas desde la fuente recomendada. Microsoft mantiene la fuente predeterminada. Consulte [Opciones de Cookiecutter](#cookiecutter-options) a continuación para más información sobre cómo personalizar la fuente. |
| GitHub | Resultados de búsqueda de GitHub de la palabra clave cookiecutter. Los resultados de GitHub vuelven paginados; si hay más resultados disponibles, aparece **Load More** (Cargar más) al final de la lista. |
| Personalizados | Cuando se especifica una ubicación personalizada en el cuadro de búsqueda, aparece en este grupo. Puede escribir una ruta de acceso completa al repositorio de GitHub, o la ruta de acceso completa a una carpeta de su disco local. |

### <a name="cloning"></a>Clonación

Al seleccionar una plantilla y luego hacer clic en **Next** (Siguiente), Cookiecutter hace una copia local con la que trabaja.

Si selecciona una plantilla de los grupos **Recomendado** o **GitHub**, o escribe una URL personalizada en el cuadro de búsqueda y selecciona esa plantilla, esta se clona e instala en su máquina local. Si esa plantilla se instaló en una sesión anterior de Visual Studio, se elimina automáticamente y se clona la versión más reciente.

Si selecciona una plantilla del grupo **Instalado** o escribe una ruta de acceso personalizada a una carpeta en el cuadro de búsqueda y seleccione esa plantilla, Visual Studio carga esa plantilla sin clonarla.

> [!Important]
> Las plantillas de Cookiecutter se clonan en una sola carpeta `~/.cookiecutters`. Cada subcarpeta se nombra después del nombre del repositorio GIT, que no incluye el nombre de usuario de GitHub. Pueden surgir conflictos si clona distintas plantillas con el mismo nombre que proceden de diferentes autores. En este caso, Cookiecutter le impide sobrescribir la plantilla existente con una plantilla diferente del mismo nombre. Para instalar la otra plantilla, primero debe eliminar la existente.

### <a name="setting-template-options"></a>Configuración de las opciones de plantilla

Después de que la plantilla está instalada localmente, Cookiecutter muestra una página de opciones donde puede especificar, entre otras opciones, dónde desea que Cookiecutter genere los archivos:

![Página de opciones de Cookiecutter](media/cookiecutter-template-options.png)

Cada plantilla de Cookiecutter define su propio conjunto de opciones y especifica un valor predeterminado para cada una (se muestra como el texto sugerido en cada campo de entrada). Un valor predeterminado puede ser un fragmento de código, normalmente cuando es un valor dinámico que usa otras opciones. 

Es posible personalizar los valores predeterminados para opciones específicas con un archivo de configuración de usuario. Cuando la extensión Cookiecutter detecta un archivo de configuración de usuario, sobrescribe los valores predeterminados de la plantilla con los valores predeterminados de la configuración de usuario. Esto se explica en la sección [User Config](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) (Configuración de usuario) de la documentación de Cookiecutter.

Si la plantilla especifica tareas de Visual Studio concretas para ejecutar después de la generación de código, aparece una opción adicional **Run additional tasks on completion** (Ejecutar tareas adicionales al terminar) que le permite optar por esas tareas. El uso más común de tareas es abrir un explorador web, abrir archivos en el editor, instalar dependencias, etc.

### <a name="create"></a>Crear

Una vez configuradas las opciones, seleccione **Crear** para generar el código (aparece una advertencia si la carpeta de salida no está vacía). Si está familiarizado con la salida de la plantilla y no le importa sobrescribir los archivos, puede pasarla por alto. En caso contrario, seleccione **Cancel** (Cancelar), especifique una carpeta vacía y luego copie manualmente los archivos creados en la carpeta de salida que no está vacía.

Después de que los archivos se crean correctamente, Cookiecutter proporciona una opción para abrirlos en el **Explorador de soluciones**:

![Cookiecutter que muestra el comando Solution Explorer](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Opciones de Cookiecutter

Las opciones de Cookiecutter están disponibles en **Tools > Options > Cookiecutter** (Herramientas > Opciones > Cookiecutter):

![Opciones de Cookiecutter](media/cookiecutter-tools-options.png)

| Opción | Description |
| --- | --- |
| Recommended Feed URL (URL de fuente recomendada) | La ubicación de la fuente de plantillas recomendadas. Puede ser una dirección URL o una ruta de acceso a un archivo local. Deje en blanco la dirección URL para usar la fuente protegida por Microsoft predeterminada. La fuente proporciona una sencilla lista de ubicaciones de plantillas, separadas por nuevas líneas. Para solicitar cambios en la fuente protegida, realice una solicitud de extracción contra [el origen de GitHub](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt). |
| Show Help (Mostrar ayuda) | Controla la visibilidad de la barra de información de ayuda en la parte superior de la ventana de Cookiecutter. |

## <a name="optimizing-cookiecutter-templates-for-visual-studio"></a>Optimización de plantillas de Cookiecutte para Visual Studio

Para información sobre los aspectos básicos de la creación de una plantilla de Cookiecutter, consulte la [documentación de Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/first_steps.html). La extensión Cookiecutter para Visual Studio admite plantillas creadas por Cookiecutter v1.4.

La representación predeterminada de variables de plantilla depende del tipo de datos (cadena o lista):

- Cadena: etiqueta para el nombre de variable, cuadro de texto para escribir el valor y una marca de agua que muestra el valor predeterminado. La información sobre herramientas en el cuadro de texto muestra el valor predeterminado.
- Lista: etiqueta para nombre de variable, cuadro combinado para seleccionar un valor. La información sobre herramientas en el cuadro combinado muestra el valor predeterminado.

Se pueden realizar mejoras adicionales en esta representación mediante la especificación de metadatos adicionales en el archivo `cookiecutter.json` que es específico de Visual Studio (y la CLI de Cookiecutter lo omite). Todas las propiedades son opcionales:

| Property | Description |
| --- | --- |
| Etiqueta | Especifica lo que aparece encima del editor para la variable, en lugar del nombre de la variable. |
| Description | Especifica la información sobre herramientas que aparece en el control de edición, en lugar del valor predeterminado de esa variable. |
| Dirección URL | Transforma la etiqueta en un hipervínculo, con una información sobre herramientas que muestra la URL. Al hacer clic en el hipervínculo se abrirá el explorador predeterminado del usuario con esa URL. |
| Selector | Permite la personalización del editor de una variable. Actualmente se admiten los siguientes selectores:<ul><li>`string`: cuadro de texto estándar, de forma predeterminada para las cadenas.</li><li>`list`: cuadro combinado estándar, de forma predeterminada para las listas.</li><li>`yesno`: cuadro combinado elegir entre `y` y `n`, para las cadenas.</li><li>`odbcConnection`: cuadro de texto con un botón "..." que hace que muestra cuadro de diálogo de conexión de base de datos.</li></ul> |

Ejemplo:

```json
{
    "site_name": "web-app",
    "python_version": ["3.5.2", "2.7.12"],
    "use_azure": "y",

    "_visual_studio": {
        "site_name": {
            "label": "Site name",
            "description": "E.g. <site-name>.azurewebsites.net (can only contain alphanumeric characters and `-`)"
        },
        "python_version": {
            "label": "Python version",
            "description": "The version of Python to run the site on"
        },
        "use_azure" : {
            "label": "Use Azure",
            "description": "Include Azure deployment files",
            "selector": "yesno",
            "url": "https://azure.microsoft.com"
        }
    }
}
```

### <a name="running-visual-studio-tasks"></a>Ejecución de tareas de Visual Studio

Cookiecutter presenta una característica llamada *Post-Generate Hooks* (Enlaces posteriores a la generación) que permite ejecutar código de Python arbitrario después de que se generan los archivos. Aunque flexible, no permite un acceso fácil a Visual Studio.

Por ejemplo, puede que quiera abrir un archivo en el editor de Visual Studio o en su explorador web, o activar la interfaz de usuario de Visual Studio que pide al usuario que cree un entorno virtual e instale los requisitos de paquete.

Para permitir estos escenarios, Visual Studio busca metadatos extendidos en `cookiecutter.json` que describen los comandos que se ejecutarán después de que el usuario abra los archivos generados en el Explorador de soluciones o después de que los archivos se agreguen a un proyecto existente. (Nuevamente, el usuario puede optar por ejecutar las tareas si desactiva **Ejecutar tareas adicionales después de la finalización** en las opciones de plantilla).

Ejemplo:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": "{{cookiecutter._output_folder_path}}\\readme.txt"
    },
    {
        "name": "Cookiecutter.ExternalWebBrowser",
        "args": "https://docs.microsoft.com"
    },
    {
        "name": "Python.InstallProjectRequirements",
        "args": "{{cookiecutter._output_folder_path}}\\dev-requirements.txt"
    }
]
```

Los comandos se especifican por nombre y deben usar el nombre no localizado (en inglés) para funcionar en instalaciones localizadas de Visual Studio. Puede probar y detectar nombres de comando en la ventana de comandos de Visual Studio.

Si desea pasar un solo argumento, puede especifíquelo como una cadena, como en el ejemplo anterior.

Si no necesita pasar un argumento, deje una cadena vacía u omítalo de JSON:

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

Use una matriz para varios argumentos. Para modificadores, divida el modificador y su valor en argumentos distintos y use el entrecomillado correcto. Por ejemplo:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": [
            "{{cookiecutter._output_folder_path}}\\read me.txt",
            "/e:",
            "Source Code (text) Editor"
        ]
    }
]
```

Los argumentos pueden hacer referencia a otros variables de Cookiecutter. En los ejemplos anteriores, la variable interna `_output_folder_path` se usa para formar una ruta de acceso absoluta a los archivos generados.

Tenga en cuenta que el comando `Python.InstallProjectRequirements` funciona solo al agregar archivos a un proyecto existente. Esta limitación existe porque el comando se procesa mediante el proyecto de Python en el Explorador de soluciones, y no hay ningún proyecto para recibir el mensaje mientras se está en la vista de carpeta del Explorador de soluciones. Esperamos eliminar la limitación en una versión futura (y proporcionar mejor compatibilidad con la vista de carpetas en general).

## <a name="troubleshooting"></a>Solución de problemas

### <a name="error-loading-template"></a>Error al cargar la plantilla

Puede que algunas plantillas usen tipos de datos no válidos, como booleanos, en sus archivos `cookiecutter.json`. Informe sobre estas instancias al autor de la plantilla haciendo clic en el vínculo **Problemas**.

### <a name="hook-script-failed"></a>Error de script de enlace

Algunas plantillas pueden usar scripts posteriores a la generación que no son compatibles con la interfaz de usuario de Cookiecutter. Por ejemplo, se producirá un error en los scripts que consultan la entrada del usuario por no tener una consola de terminal.

### <a name="hook-script-not-supported-on-windows"></a>Script de enlace no admitido en Windows

Si el script posterior es `.sh`, puede que no esté asociado con una aplicación de su máquina de Windows. Es posible que vea un diálogo de Windows que le pide que busque una aplicación compatible en la Tienda Windows.

### <a name="templates-with-known-issues"></a>Plantillas con problemas conocidos

Errores de clonación:

- **wildfish/cookiecutter-django-crud** (carácter no válido `|` en nombre de subcarpeta)
- **cookiecutter-pyvanguard** (carácter no válido `|` en nombre de subcarpeta)

Errores de carga:

- **chrisdev/wagtail-cookiecutter-foundation** (usa un tipo booleano en cookiecutter.json)
- **quintoandar/cookiecutter-android** (ninguna carpeta de plantilla)

Errores de ejecución:

- **iknite/cookiecutter-ansible-role** (script de enlace posterior que requiere entrada de consola)
- **benregn/cookiecutter-django-ansible** (error de Jinja)

Usa bash (no fatal):

- **openstack-dev/cookiecutter**
