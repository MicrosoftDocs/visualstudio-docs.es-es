---
title: Plantillas de aplicación web para Python
description: Visual Studio proporciona plantillas para aplicaciones web Python con las plataformas Bottle, Flask y Django; la compatibilidad incluye configuraciones de depuración y la publicación en Azure App Service.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a309ba898c22836fb5c0cebfc390b6c8d7c116c5
ms.sourcegitcommit: f1dff6c4532c43b0444aa12ea57e90bb7dba6fba
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805996"
---
# <a name="python-web-application-project-templates"></a>Plantillas de proyecto de aplicación web para Python

Python en Visual Studio admite el desarrollo de proyectos web en los marcos Bottle, Flask y Django mediante plantillas de proyecto y un iniciador de depuración que puede configurarse para controlar varios marcos. Estas plantillas incluyen un archivo *requirements.txt* para declarar las dependencias necesarias. Al crear un proyecto a partir de alguna de estas plantillas, Visual Studio le pide que instale esos paquetes (vea [Instalar requisitos de proyecto](#install-project-requirements) más adelante en este artículo).

También puede usar la plantilla **Proyecto web** genérica para otras plataformas como Pyramid. En este caso, no se instala ningún marco con la plantilla. En su lugar, instale los paquetes necesarios en el entorno que va a usar para el proyecto (vea [Ventana Entornos de Python - Pestaña Paquetes](python-environments-window-tab-reference.md#packages-tab)).

Para obtener información sobre la implementación de una aplicación web de Python en Azure, vea [Publicar en Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

## <a name="use-a-project-template"></a>Usar una plantilla de proyecto

Para crear un proyecto a partir de una plantilla, seleccione **Archivo** > **Nuevo** > **Proyecto**. Para ver plantillas para proyectos web, seleccione **Python** > **Web** en el lado izquierdo del cuadro de diálogo. Después, seleccione una plantilla de su elección, asigne los nombres al proyecto y a la solución, defina las opciones para un directorio de la solución y el repositorio de Git y seleccione **Aceptar**.

![Cuadro de diálogo Nuevo proyecto para aplicaciones web](media/projects-new-project-dialog-web.png)

La plantilla genérica **Proyecto web**, que se ha mencionado anteriormente, solo ofrece un proyecto vacío de Visual Studio sin código ni supuestos, aparte de que se trata de un proyecto de Python. Para obtener detalles sobre la plantilla **Servicio en la nube de Azure**, vea [Azure cloud service projects for Python](python-azure-cloud-service-project-template.md) (Proyectos de servicio en la nube para Python).

Todas las demás plantillas se basan en los marcos web de Bottle, Flask o Django y se dividen en tres grupos generales, como se describe en las secciones siguientes. Las aplicaciones creadas con cualquiera de estas plantillas contienen código suficiente para ejecutar y depurar la aplicación en local. Cada una de ellas ofrece el [objeto de aplicación WSGI](https://www.python.org/dev/peps/pep-3333/) necesario (python.org) para el uso con servidores web de producción.

### <a name="blank-group"></a>Grupo en blanco

Todas las plantillas **Proyecto web de \<framework> en blanco** crean un proyecto con más o menos el código reutilizable mínimo y las dependencias necesarias declaradas en un archivo *requirements.txt*.

| Plantilla | Description |
| --- | --- |
| **Proyecto web de Bottle en blanco** | Genera una aplicación mínima en *app.py* con una página principal de `/` y una página `/hello/<name>` que devuelve `<name>` mediante una plantilla de página insertada muy breve. |
| **Proyecto web de Django en blanco** | Genera un proyecto de Django con la estructura del sitio principal de Django pero sin ninguna aplicación de Django. Para obtener más información, vea [Plantilla de proyecto web de Django](python-django-web-application-project-template.md) y [Tutorial: Introducción al marco web de Django en Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md). |
| **Proyecto web de Flask en blanco** | Genera un aplicación mínima con una única página "Hola mundo" para `/`. Esta aplicación es similar al resultado obtenido tras seguir los pasos detallados descritos en [Inicio rápido: usar Visual Studio para crear su primera aplicación web Python](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json). Vea también [Tutorial: Introducción al marco web de Flask en Visual Studio](learn-flask-visual-studio-step-01-project-solution.md).

### <a name="web-group"></a>Grupo web

Todas las plantillas **Proyecto web de \<Framework>** crean una aplicación web de inicio con un diseño idéntico, con independencia del marco elegido. La aplicación tiene una página de inicio, otra de Acerca de y otra de contacto, además de una barra de navegación y un diseño dinámico que usa el arranque. Cada aplicación está correctamente configurada para archivos estáticos (CSS, JavaScript y fuentes) y usa un mecanismo de plantilla de página adecuado para el marco.

| Plantilla | Description |
| --- | --- |
| **Proyecto web de Bottle** | Genera una aplicación cuyos archivos estáticos se encuentran en la carpeta *static* y se controlan mediante código en *app.py*. El enrutamiento de las páginas individuales se encuentra en *routes.py* y la carpeta *views* contiene las plantillas de página.|
| **Proyecto web de Django** | Genera un proyecto de Django y una aplicación de Django con tres páginas, compatibilidad con la autenticación y una base de datos de SQLite (pero no hay modelos de datos). Para obtener más información, vea [Plantilla de proyecto web de Django](python-django-web-application-project-template.md) y [Paso 4. Usar la plantilla completa de Proyecto web de Django](learn-django-in-visual-studio-step-04-full-django-project-template.md). |
| **Proyecto web de Flask** | Genera una aplicación cuyos archivos estáticos se encuentran en la carpeta *static*. El código de *views.py* controla el enrutamiento y las plantillas de página que usan el motor de Jinja están incluidas en la carpeta *templates*. El archivo *runserver.py* proporciona el código de inicio. Vea [Paso 4. Usar la plantilla de proyecto web completa de Flask](learn-flask-visual-studio-step-04-full-flask-project-template.md). |
| **Proyecto web de Flask/Jade** | Genera la misma aplicación que con la plantilla **Proyecto web de Flask**, pero con la extensión Jade para el motor de plantillas de Jinja. |

::: moniker range="vs-2017"
### <a name="polls-group"></a>Grupo de sondeos

Las plantillas **Proyecto web de \<framework> de sondeos** crean una aplicación web de inicio con la que los usuarios pueden votar sobre distintas preguntas de sondeo. Cada aplicación se basa en la estructura de las plantillas de proyecto **web** para usar una base de datos para administrar los sondeos y las respuestas de los usuarios. Las aplicaciones incluyen modelos de datos apropiados y una página de aplicación especial (/seed) que carga los sondeos desde un archivo *samples.json*.

| Plantilla | Description |
| --- | --- |
| **Proyecto web de Bottle de sondeos** | Genera una aplicación que se puede ejecutar en una base de datos en memoria, MongoDB o Azure Table Storage, que se configura mediante la variable de entorno `REPOSITORY_NAME`. Los modelos de datos y el código de almacén de datos se encuentran en la carpeta *models* y el archivo *settings.py* contiene código para determinar qué almacén de datos se usa. |
| **Proyecto web de Django de sondeos** | Genera un proyecto de Django y una aplicación de Django con tres páginas y una base de datos de SQLite. Incluye las personalizaciones de la interfaz administrativa de Django para permitir que un administrador autenticado cree y administre los sondeos. Para obtener más información, vea [Plantilla de proyecto web de Django](python-django-web-application-project-template.md) y [Paso 6. Usar la plantilla de proyecto web de Django de sondeos](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md). |
| **Proyecto web de Flask de sondeos** | Genera una aplicación que se puede ejecutar en una base de datos en memoria, MongoDB o Azure Table Storage, que se configura mediante la variable de entorno `REPOSITORY_NAME`. Los modelos de datos y el código de almacén de datos se encuentran en la carpeta *models* y el archivo *settings.py* contiene código para determinar qué almacén de datos se usa. La aplicación utiliza el motor de Jinja para las plantillas de página. Vea [Paso 5. Usar la plantilla de proyecto web de Flask de sondeos](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md). |
| **Proyecto web de Flask/Jade de sondeos** | Genera la misma aplicación que con la plantilla **Proyecto web de Flask de sondeos**, pero con la extensión Jade para el motor de plantillas de Jinja. |
::: moniker-end

## <a name="install-project-requirements"></a>Instalar requisitos de proyecto

Al crear un proyecto a partir de una plantilla específica del marco, aparece un cuadro de diálogo que le ayudará a instalar los paquetes necesarios mediante pip. También se recomienda usar un [entorno virtual](selecting-a-python-environment-for-a-project.md#use-virtual-environments) para proyectos web de forma que se incluyan las dependencias correctas cuando publique el sitio web:

![Cuadro de diálogo que instala los paquetes necesarios para una plantilla de proyecto](media/template-web-requirements-txt-wizard.png)

Si se usa control de código fuente, normalmente se omite la carpeta del entorno virtual, ya que dicho entorno solo puede volver a crearse con *requirements.txt*. La mejor forma de excluir la carpeta es seleccionar primero **I will install them myself** (Haré la instalación por mi cuenta) en el aviso mostrado anteriormente y luego deshabilitar la confirmación automática antes de crear el entorno virtual. Para obtener detalles, vea los [pasos 1-2 y 1-3 del tutorial de Django](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) y los [pasos 1-2 y 1-3 del tutorial de Flask](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository).

Cuando implemente Microsoft Azure App Service, seleccione una versión de Python como una [extensión del sitio](./managing-python-on-azure-app-service.md?view=vs-2019&preserve-view=true) e instale los paquetes manualmente. Además, dado que Azure App Service **no** instala automáticamente los paquetes de un archivo *requirements.txt* cuando se implementa desde Visual Studio, siga los detalles de configuración de [aka.ms/PythonOnAppService](managing-python-on-azure-app-service.md).

Microsoft Azure Cloud Services *admite* el archivo *requirements.txt*. Vea los [proyectos del servicio en la nube de Azure](python-azure-cloud-service-project-template.md) para obtener detalles.

## <a name="debugging"></a>Depuración

Cuando se inicia un proyecto web para la depuración, Visual Studio inicia el servidor web local en un puerto aleatorio y abre el explorador predeterminado en esa dirección y puerto. Para especificar opciones adicionales, haga clic con el botón derecho en el proyecto, seleccione **Propiedades** y haga clic en la pestaña **Iniciador web**:

![Propiedades del iniciador web de la plantilla web genérica](media/template-web-launcher-properties.png)

En el grupo **Depurar**:

- **Rutas de acceso de búsqueda**, **Argumentos de script**, **Argumentos del intérprete** y **Ruta del intérprete**: estas opciones son las mismas que para la [depuración normal](debugging-python-in-visual-studio.md).
- **Iniciar URL**: especifica la dirección URL que se abre en el explorador. El valor predeterminado es `localhost`.
- **Número de puerto**: Puerto que se utilizará si no se especifica ninguno en la dirección URL (Visual Studio selecciona uno automáticamente de forma predeterminada). Esta opción le permite invalidar el valor predeterminado de la variable de entorno `SERVER_PORT`, usado por las plantillas para configurar el puerto en el que escucha el servidor de depuración local.

Las propiedades de los grupos **Ejecutar comando del servidor** y **Comando del servidor de depuración** (este último está por debajo de lo que es visible en la imagen) determinan cómo se inicia el servidor web. Dado que muchos marcos requieren el uso de un script fuera del proyecto actual, se puede configurar aquí el script y el nombre del módulo de inicio se puede pasar como parámetro.

- **Comando**: puede ser un script de Python (archivo *\*.py*), un nombre de módulo (como en `python.exe -m module_name`) o una sola línea de código (como en `python.exe -c "code"`). El valor de la lista desplegable indica cuál de estos tipos está previsto.
- **Argumentos**: estos argumentos se pasan en la línea de comandos después del comando.
- **Entorno**: lista separada por nuevas líneas de pares \<NAME>=\<VALUE> que especifican variables de entorno. Estas variables se establecen después de todas las propiedades que pueden modificar el entorno, como el número de puerto y las rutas de acceso de búsqueda y, por lo tanto, pueden sobrescribir estos valores.

Cualquier propiedad de proyecto o variable de entorno se puede especificar con la sintaxis de MSBuild, por ejemplo: `$(StartupFile) --port $(SERVER_PORT)`.
`$(StartupFile)` es la ruta de acceso relativa al archivo de inicio y `{StartupModule}` es el nombre del archivo de inicio que se puede importar. `$(SERVER_HOST)` y `$(SERVER_PORT)` son variables de entorno normales que se establecen mediante las propiedades **URL de inicio** y **Número de puerto**, automáticamente o mediante la propiedad **Entorno**.

> [!Note]
> Los valores de **Ejecutar comando del servidor** se usan con el comando **Depurar** > **Iniciar servidor** o **Ctrl**+**F5**; los valores del grupo **Comando del servidor de depuración** se usan con el comando **Depurar** > **Iniciar el servidor de depuración** o **F5**.

### <a name="sample-bottle-configuration"></a>Configuración de Bottle de ejemplo

La plantilla **Proyecto web de Bottle** incluye código reutilizable que realiza la configuración necesaria. Sin embargo, una aplicación de Bottle importada no puede incluir este código, en cuyo caso la siguiente configuración inicia la aplicación mediante el módulo `bottle` instalado:

- Grupo **Run Server Command** (Comando de servidor de ejecución):
  - **Comando**: `bottle` (módulo)
  - **Argumentos**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- Grupo **Debug Server Command** (Comando de servidor de depuración):
  - **Comando**: `bottle` (módulo)
  - **Argumentos** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

La opción `--reload` no se recomienda cuando se usa Visual Studio para la depuración.

### <a name="sample-pyramid-configuration"></a>Configuración de Pyramid de ejemplo

Las aplicaciones de Pyramid actualmente se crean mejor mediante la herramienta de la línea de comandos `pcreate`. Una vez creada una aplicación, se puede importar mediante la plantilla [**Desde código de Python existente**](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files). Después de realizar esto, seleccione la personalización **Proyecto web genérico** para configurar las opciones. Esta configuración asume que Pyramid se ha instalado en un entorno virtual en `..\env`.

- Grupo **Depurar**:
  - **Puerto de servidor**: 6543 (o lo que se haya configurado en los archivos *.ini*)

- Grupo **Run Server Command** (Comando de servidor de ejecución):
  - Comando: `..\env\scripts\pserve-script.py` (script)
  - Argumentos: `Production.ini`

- Grupo **Debug Server Command** (Comando de servidor de depuración):
  - Comando: `..\env\scripts\pserve-script.py` (script)
  - Argumentos: `Development.ini`

> [!Tip]
> Es probable que tenga que configurar la propiedad **Directorio de trabajo** del proyecto porque las aplicaciones de Pyramid suelen encontrarse en una carpeta por debajo de la raíz del proyecto.

### <a name="other-configurations"></a>Otras configuraciones

Si tiene una configuración para otro marco que quiere compartir, o si quiere solicitar la configuración para otro marco, abra un [problema en GitHub](https://github.com/Microsoft/PTVS/issues).

## <a name="convert-a-project-to-azure-cloud-service"></a>Convertir en un proyecto de servicio en la nube de Azure

El comando **Convertir en un proyecto de servicio en la nube de Microsoft Azure** (imagen siguiente) agrega un proyecto de servicio en la nube a la solución. Este proyecto incluye la configuración de implementación y la configuración para las máquinas virtuales y los servicios que se van a usar. Use el comando **Publicar** en el proyecto de nube para implementar en Cloud Services; con el comando **Publicar** del proyecto de Python se sigue implementando en sitios web. Para obtener más información, vea [Proyectos de servicio en la nube de Azure para Python](python-azure-cloud-service-project-template.md).

![Comando Convertir en un proyecto de servicio en la nube de Microsoft Azure](media/template-web-convert-menu.png)

## <a name="see-also"></a>Vea también

- [Referencia de plantillas de elemento de Python](python-item-templates.md)
- [Publicación en Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)