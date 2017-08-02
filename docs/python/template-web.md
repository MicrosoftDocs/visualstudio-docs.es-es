---
title: Plantilla de proyecto web para Python en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 401e7725-8be5-4e67-862c-bf0690a529e3
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 20edb7a53adf400fba94556e659b4215a0060c1b
ms.contentlocale: es-es
ms.lasthandoff: 05/09/2017

---

# <a name="python-web-project-templates"></a>Plantillas de proyecto web de Python

Python en Visual Studio incluye compatibilidad para desarrollar proyectos web en marcos como Bottle, Django y Flask. Esto incluye plantillas de proyecto y un iniciador de depuración que se puede configurar para controlar diferentes marcos. Sin embargo, Visual Studio no incluye los propios marcos, que debe instalarlos por separado haciendo clic con el botón derecho en el proyecto y seleccionando **Python > Install/upgrade framework… (Instalar o actualizar marco…)**.

Cada plantilla (a la que se accede a través de **Archivo > Nuevo > Proyecto...** ) inicia un servidor web con un puerto local seleccionado aleatoriamente, abre el explorador predeterminado al depurar y permite la publicación directa en [Microsoft Azure](http://www.azure.com). Las plantillas se proporcionan para Bottle, Flask y Django, y puede usar la plantilla "Proyecto web" genérica para otros marcos como Pyramid.

![Nuevas plantillas de proyecto web](~/python/media/template-web-new-project.png)

Las plantillas Bottle, Flask y Django incluyen un sitio de inicio con algunas páginas y archivos estáticos. Este código es suficiente para ejecutar y depurar el servidor localmente (donde es necesario obtener algunas configuraciones del entorno) y para implementar en Microsoft Azure (donde se debe proporcionar un objeto de [aplicación WSGI](http://www.python.org/dev/peps/pep-3333/)).

Al crear un proyecto a partir de una plantilla específica del marco, aparecerá un cuadro de diálogo que le ayudará a instalar los paquetes necesarios mediante pip. También se recomienda usar un [entorno virtual](python-environments.md#virtual-environments) para proyectos web de forma que se incluyan las dependencias correctas cuando publique el sitio web:

![Cuadro de diálogo que instala los paquetes necesarios para una plantilla de proyecto](~/python/media/template-web-requirements-txt-wizard.png)

Cuando implemente Microsoft Azure App Service, necesitará seleccionar una versión de Python como una [extensión del sitio](https://aka.ms/PythonOnAppService) e instalar los paquetes manualmente. Además, dado que Azure App Service **no** instala automáticamente los paquetes de un archivo `requirements.txt` cuando se implementa desde Visual Studio, siga los detalles de configuración que se encuentran en [aka.ms/PythonOnAppService](https://aka.ms/PythonOnAppService).

Por otra parte, Microsoft Azure Cloud Service admite el archivo `requirements.txt`. Consulte [Azure Cloud Service Projects](template-azure-cloud-service.md) (Proyectos de servicio en la nube de Azure) para detalles.

Para una introducción a los proyectos web de Python, consulte el vídeo de youtube.com (3 minutos y 10 segundos) [Getting Started with PTVS, Part 6: Web sites](https://youtu.be/FJx5mutt1uk?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (Introducción a PTVS, parte 6: sitios web).

> [!VIDEO https://www.youtube.com/embed/FJx5mutt1uk]

## <a name="debugging"></a>Depuración

Cuando se inicie un proyecto web para la depuración, Visual Studio iniciará el servidor web localmente y abrirá el explorador predeterminado en esa dirección y puerto. Para especificar opciones adicionales, haga clic con el botón derecho en el proyecto, seleccione **Propiedades** y seleccione la pestaña **Iniciador web**:

  ![Propiedades del iniciador web de la plantilla web genérica](~/python/media/template-web-launcher-properties.png)

En el grupo **Depurar**:

- **Rutas de acceso de búsqueda**, **Argumentos de script**, **Interpreter Arguments (Argumentos del intérprete)** e **Interpreter Path (Ruta de acceso del intérprete)**: Son los mismos que para la [depuración normal](debugging.md).
- **Iniciar URL**: Especifica la dirección URL que se abrirá en el explorador. El valor predeterminado es `localhost`.
- **Número de puerto**: Puerto que se utilizará si no se especifica ninguno en la dirección URL (Visual Studio selecciona uno automáticamente de forma predeterminada). Esto le permite invalidar el valor predeterminado de la variable de entorno `SERVER_PORT`, que lo utilizan las plantillas para configurar el puerto en el que escucha el servidor de depuración local.

Las propiedades de los grupos **Run Server Command** (Comando de servidor de ejecución) y **Debug Server Command (Comando de servidor de depuración)** (este último está por debajo de lo que es visible en la imagen) determinan cómo se inicia el servidor web. Dado que muchos marcos requieren el uso de un script fuera del proyecto actual, se puede configurar aquí el script y el nombre del módulo de inicio se puede pasar como parámetro.

- **Comando**: Puede ser un script de Python (archivo `*.py`), un nombre de módulo (como en `python.exe -m module_name`) o una sola línea de código (como en `python.exe -c "code"`). El valor de la lista desplegable indica cuál de estos tipos está previsto.
- **Argumentos**: Se pasan en la línea de comandos después del comando.
- **Entorno**: Lista separada por nuevas líneas de pares `NAME=VALUE` que especifican variables de entorno. Estas se establecen después de todas las propiedades que pueden modificar el entorno, como el número de puerto y las rutas de acceso de búsqueda y, por lo tanto, pueden sobrescribir estos valores.

Cualquier propiedad de proyecto o variable de entorno se puede especificar con la sintaxis de MSBuild, por ejemplo: `$(StartupFile) --port $(SERVER_PORT)`.
`$(StartupFile)` es la ruta de acceso relativa al archivo de inicio y `{StartupModule}` es el nombre del archivo de inicio que se puede importar. `$(SERVER_HOST)` y `$(SERVER_PORT)` son variables de entorno normales que se establecen mediante las propiedades **URL de inicio** y **Número de puerto**, automáticamente o mediante la propiedad **Entorno**.

> [!Note]
> Los valores de **Run Server Command** (Comando de servidor de ejecución) se usan con el comando **Depurar > Start Server (Iniciar el servidor)** o Ctrl-F5; los valores del grupo **Debug Server Command** (Comando de servidor de depuración) se usan con el comando **Depurar > Start Debug Server (Iniciar servidor de depuración)** o F5.


### <a name="sample-bottle-configuration"></a>Configuración de Bottle de ejemplo

La plantilla de proyecto web de Bottle incluye código reutilizable que realiza la configuración necesaria. Sin embargo, una aplicación de Bottle importada no puede incluir este código, en cuyo caso la siguiente configuración inicia la aplicación mediante el módulo `bottle` instalado:

- Grupo **Run Server Command** (Comando de servidor de ejecución):
    - **Comando**: `bottle` (módulo)
    - **Argumentos**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- Grupo **Debug Server Command** (Comando de servidor de depuración):
    - **Comando**: `bottle` (módulo)
    - **Argumentos** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

La opción `--reload` no se recomienda cuando se usa Visual Studio para la depuración.

### <a name="sample-pyramid-configuration"></a>Configuración de Pyramid de ejemplo

Las aplicaciones de Pyramid actualmente se crean mejor mediante la herramienta de la línea de comandos `pcreate`. Una vez creada una aplicación, se puede importar utilizando la plantilla [From Existing Python Code](python-projects.md#creating-a-project-from-existing-files) (A partir de código Python existente). Después, seleccione la personalización **Generic Web Project** (Proyecto web genérico) para configurar las opciones. Esta configuración asume que Pyramid se ha instalado en un entorno virtual en `..\env`.

- Grupo **Depurar**:
    - **Puerto del servidor**: 6543 (o lo que se configure en los archivos. ini)

- Grupo **Run Server Command** (Comando de servidor de ejecución):
    - Comando: `..\env\scripts\pserve-script.py` (script)
    - Argumentos: `Production.ini`

- Grupo **Debug Server Command** (Comando de servidor de depuración):
    - Comando: `..\env\scripts\pserve-script.py` (script)
    - Argumentos: `Development.ini`

> [!Tip]
> Es probable que necesite configurar la propiedad **Directorio de trabajo** del proyecto porque las aplicaciones de Pyramid normalmente se encuentran un nivel de directorio más abajo que la parte superior del árbol de origen.


### <a name="other-configurations"></a>Otras configuraciones

Si tiene una configuración para otro marco que desea compartir, o si desea solicitar la configuración para otro marco, abra un [problema en GitHub](https://github.com/Microsoft/PTVS/issues).

## <a name="publishing-to-azure-app-service"></a>Publicación en Azure App Service

Hay dos formas principales de publicar en Azure App Service. En primer lugar, la implementación a partir del control de código fuente se puede utilizar de la misma manera que para otros lenguajes, como se describe en la [documentación de Azure](http://azure.microsoft.com/en-us/documentation/articles/web-sites-publish-source-control/). Para publicar directamente desde Visual Studio, haga clic con el botón derecho en el proyecto y seleccione **Publicar**:

![Comando Publicar en el menú contextual de un proyecto](~/python/media/template-web-publish-command.png)

Después de seleccionar el comando, un asistente le guiará para crear un sitio web o importar la configuración de publicación, obtener una vista previa de archivos modificados y publicar en un servidor remoto.

Cuando cree un sitio en App Service, debe instalar Python y todos los paquetes de los que depende dicho sitio. Puede publicar primero el sitio, pero no se ejecutará hasta que haya configurado Python.

Para instalar Python en App Service, se recomienda utilizar las [extensiones de sitio](http://www.siteextensions.net/packages?q=Tags%3A%22python%22) (siteextensions.net). Se trata de copias de las [versiones oficiales](https://www.python.org) de Python, optimizadas y reempaquetadas para Azure App Service.

Una extensión de sitio se puede implementar a través de [Azure Portal](https://portal.azure.com/) mediante la hoja **Herramientas de desarrollo > Extensiones** de su App Service, seleccionando **Agregar** y recorriendo la lista para buscar las correspondientes a Python:

![Agregar la extensión de sitio en Azure Portal](~/python/media/template-web-site-extensions.png)

Si usa plantillas de implementación de JSON, puede especificar la extensión de sitio como un recurso del sitio:

```json
{
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "[parameters('siteName')]",
        "type": "Microsoft.Web/sites",
        ...
    },
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "python352x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
            "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
    },
    ...
}
```

Por último, puede iniciar sesión a través de la [consola de desarrollo](https://github.com/projectkudu/kudu/wiki/Kudu-console) e instalar una extensión de sitio desde allí.

Actualmente, la manera recomendada de instalar paquetes es usar la consola de desarrollo después de instalar la extensión de sitio y ejecutar pip directamente. Utilizar la ruta de acceso completa a Python es importante (de lo contrario, puede ejecutar una incorrecta) y no suele ser necesario usar un entorno virtual. Por ejemplo:

```
c:\Python35\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt

c:\Python27\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt
```

Cuando se implemente en Azure App Service, el sitio se ejecutará detrás de Microsoft IIS. Para habilitar el sitio para trabajar con IIS, deberá agregar al menos un archivo `web.config`. Hay plantillas disponibles para algunos destinos de implementación comunes que puede obtener haciendo clic con el botón derecho en el proyecto y seleccionando **Agregar > Nuevo elemento... " (consulte el cuadro de diálogo siguiente). Además, se pueden modificar fácilmente para otros usos. Consulte [IIS Configuration Reference](https://www.iis.net/configreference) (Referencia de configuración de IIS) para obtener información sobre la configuración disponible.

![Plantillas de elementos de Azure](~/python/media/template-web-azure-items.png)

Los elementos disponibles incluyen:

- Azure web.config (FastCGI) (wef.config de Azure (FastCGI)): Agrega un archivo `web.config` para cuando la aplicación proporciona un objeto [WSGI](https://wsgi.readthedocs.io/en/latest/) para controlar las conexiones entrantes.
- Azure web.config (HttpPlatformHandler) (web.config de Azure (HttpPlatformHandler)): Agrega un archivo `web.config` para cuando la aplicación escucha en un socket para las conexiones entrantes.
- Azure Static files web.config (web.config de archivos estáticos de Azure): Si tiene uno de los archivos `web.config` anteriores, agregue esto a un subdirectorio para excluirlo del control de la aplicación.
- Azure Remote debugging web.config (web.config de depuración remota de Azure): Agrega los archivos necesarios para la depuración remota a través de WebSockets.
- Web Role Support Files (Archivos de soporte de rol web): Contiene los scripts de implementación predeterminados para roles web de servicio en la nube.
- Worker Role Support Files (Archivos de soporte de rol de trabajo): Contiene los scripts de implementación e inicio predeterminados para roles de trabajo de servicio en la nube.

Si agrega la plantilla `web.config` de depuración al proyecto y pretende usar la depuración remota de Python, debe publicar el sitio en la configuración "Depurar". Esta configuración es independiente de la configuración de la solución activa actual y siempre tiene como valor predeterminado "Liberar". Para cambiarlo, abra la pestaña **Configuración** y use el cuadro combinado **Configuración** del asistente para publicación (consulte la [documentación de Azure](https://azure.microsoft.com/develop/python/) para más información sobre la creación e implementación en Azure Web Apps):

![Cambio de la configuración de publicación](~/python/media/template-web-publish-config.png)

El comando **Convertir en un proyecto de servicio en la nube de Microsoft Azure** (imagen siguiente) agregará un proyecto de servicio en la nube a la solución. Este proyecto incluye la configuración de implementación y la configuración para las máquinas virtuales y los servicios que se van a usar. Debe utilizar el comando **Publicar** en el proyecto en la nube para implementar en el servicio en la nube; el comando **Publicar** del proyecto de Python seguirá implementando en Web Sites. Consulte [Azure Cloud Service Projects](template-azure-cloud-service.md) (Proyectos de servicio en la nube de Azure) para detalles.

![Convertir en proyecto de servicio de nube de Microsoft Azure, comando](~/python/media/template-web-convert-menu.png)

