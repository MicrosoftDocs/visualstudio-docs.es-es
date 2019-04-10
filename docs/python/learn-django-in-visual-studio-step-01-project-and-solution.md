---
title: Información sobre el paso 1 del tutorial de Django en Visual Studio, Aspectos básicos de Django
titleSuffix: ''
description: Un recorrido por los aspectos básicos de Django en el contexto de los proyectos de Visual Studio, que muestra el soporte que brinda Visual Studio al desarrollo de Django.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b41ed3901cd4ad18a1b52ddbdc7ee6fd82cb5380
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59366424"
---
# <a name="tutorial-get-started-with-the-django-web-framework-in-visual-studio"></a>Tutorial: Introducción al marco web de Django en Visual Studio

[Django](https://www.djangoproject.com/) es un marco de Python de alto nivel diseñado para el desarrollo web rápido, seguro y escalable. En este tutorial se explora la plataforma de Django en el contexto de las plantillas de proyecto que proporciona Visual Studio para simplificar la creación de aplicaciones web basadas en Django.

En este tutorial aprenderá a:

> [!div class="checklist"]
> - Crear un proyecto básico de Django en un repositorio de Git con la plantilla "Proyecto web de Django en blanco" (paso 1)
> - Crear una aplicación de Django con una página y representar esa página con una plantilla (paso 2)
> - Atender archivos estáticos, agregar páginas y usar la herencia de plantilla (paso 3)
> - Utilizar la plantilla Proyecto web de Django para crear una aplicación con varias páginas y diseño con capacidad de respuesta (paso 4)
> - Autenticar usuarios (paso 5)
> - Usar la plantilla Proyecto web de Django de sondeos para crear una aplicación que use modelos, migraciones de base de datos y personalizaciones para la interfaz administrativa (paso 6)

## <a name="prerequisites"></a>Requisitos previos

- Visual Studio 2017 o posterior en Windows con las siguientes opciones:
  - La carga de trabajo **Desarrollo de Python** (pestaña **Carga de trabajo** del instalador). Para obtener instrucciones, vea [Instalación de la compatibilidad con Python en Visual Studio en Windows](installing-python-support-in-visual-studio.md).
  - **Git para Windows** y **Extensión de GitHub para Visual Studio** en la pestaña **Componentes individuales** de **Herramientas de código**.

Las plantillas de proyecto de Django también se incluyen con todas las versiones anteriores de las Herramientas de Python para Visual Studio, aunque los detalles pueden diferir de aquello que se describe en este tutorial (especialmente respecto de las versiones anteriores de la plataforma Django).

El desarrollo de Python no es compatible actualmente en Visual Studio para Mac. En Mac y Linux, use la [extensión de Python en Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

### <a name="visual-studio-projects-and-django-projects"></a>"Proyectos de Visual Studio" y "proyectos de Django"

En la terminología de Django, un "proyecto de Django" se compone de varios archivos de configuración de nivel de sitio junto con una o varias "aplicaciones" que el usuario implementa en un host web para crear una aplicación web completa. Un proyecto de Django puede contener varias aplicaciones, y la misma aplicación puede estar en varios proyectos de Django.

Un proyecto de Visual Studio, por su parte, puede contener el proyecto de Django junto con varias aplicaciones. Para facilitar la lectura, siempre que en este tutorial se mencione simplemente a"proyecto", nos estaremos refiriendo al proyecto de Visual Studio. Cuando se haga referencia a la parte del "proyecto de Django" de la aplicación web, usaremos específicamente "proyecto de Django".

En el transcurso de este tutorial creará una única solución de Visual Studio que contiene tres proyectos de Django independientes, cada uno de los cuales contiene una única aplicación de Django. Al mantener los proyectos en la misma solución, puede cambiar fácilmente entre distintos archivos para compararlos.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Paso 1-1: Creación de una solución y un proyecto de Visual Studio

Cuando se trabaja con Django desde la línea de comandos, normalmente se inicia un proyecto ejecutando el comando `django-admin startproject <project_name>`. En Visual Studio, con la plantilla "Proyecto web de Django en blanco" se obtiene la misma estructura dentro de un proyecto y una solución de Visual Studio.

1. En Visual Studio, seleccione **Archivo** > **Nuevo** > **Proyecto**, busque "Django" y seleccione la plantilla **Proyecto web de Django en blanco**. (La plantilla también se encuentra en **Python** > **Web** en la lista de la izquierda).

    ![Cuadro de diálogo Nuevo proyecto en Visual Studio para el Proyecto web de Django en blanco](media/django/step01-new-blank-project.png)

1. En los campos de la parte inferior del cuadro de diálogo, escriba la información siguiente (como se muestra en el gráfico anterior) y, a continuación, seleccione **Aceptar**:

    - **Nombre**: establezca el nombre del proyecto de Visual Studio en **BasicProject**. Este nombre también se usa para el proyecto Django.
    - **Ubicación**: especifique una ubicación en la que se va a crear la solución y el proyecto de Visual Studio.
    - **Solución**: deje este control establecido en la opción predeterminada **Crear nueva solución**.
    - **Nombre de la solución**: establézcalo en **LearningDjango**, que es adecuado para la solución como contenedor de varios proyectos de este tutorial.
    - **Crear directorio para la solución**: mantenga la opción activada (valor predeterminado).
    - **Crear nuevo repositorio Git**: active esta opción (que está desactivada de forma predeterminada) para que Visual Studio cree un repositorio Git local al generar la solución. Si no ve esta opción, ejecute el instalador de Visual Studio y agregue **Git para Windows** y **Extensión de GitHub para Visual Studio** en la pestaña **Componentes individuales** en **Herramientas de código**.

1. Tras un momento, Visual Studio muestra un cuadro de diálogo que indica **Este proyecto necesita paquetes externos** (se muestra abajo). Este cuadro de diálogo aparece porque la plantilla incluye un archivo *requirements.txt* que hace referencia al paquete Django 1.x más reciente. (Active **Mostrar paquetes necesarios** para ver las dependencias exactas).

    ![Cuadro de diálogo que indica que el proyecto requiere paquetes externos](media/django/step01-requirements-prompt-install-myself.png)

1. Seleccione la opción **Los instalaré de forma manual**. Cree el entorno virtual en breve para asegurarse de que se excluye del control de código fuente. (El entorno siempre puede crearse a partir de *requirements.txt*).

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Paso 1-2: Examen de los controles de Git y publicación en un repositorio remoto

Como seleccionó **Crear nuevo repositorio Git** en el cuadro de diálogo **Nuevo proyecto**, el proyecto ya estará confirmado para el control de código fuente local en cuanto se complete el proceso de creación. En este paso, familiarícese con los controles de Git de Visual Studio y la ventana de **Team Explorer** en la que se trabaja con el control de código fuente.

1. Examine los controles de Git en la esquina inferior de la ventana principal de Visual Studio. De izquierda a derecha, estos controles muestran confirmaciones sin insertar, cambios sin confirmar, el nombre del repositorio y la rama actual:

    ![Controles de Git en la ventana de Visual Studio](media/django/step01-git-controls.png)

    > [!Note]
    > Si no selecciona **Crear nuevo repositorio Git** en el cuadro de diálogo **Nuevo proyecto**, los controles de Git solo muestran un comando **Agregar al control de código fuente** que crea un repositorio local.
    >
    > ![Agregar al control de código fuente aparece en Visual Studio si no ha creado un repositorio](media/django/step01-git-add-to-source-control.png)

1. Seleccione el botón de cambios y Visual Studio abre su ventana de **Team Explorer** en la página **Cambios**. Dado que el proyecto recién creado ya se ha confirmado automáticamente en el control de código fuente, no verá cambios pendientes.

    ![Ventana de Team Explorer en la página Cambios](media/django/step01-team-explorer-changes.png)

1. En la barra de estado de Visual Studio, haga clic en el botón de confirmaciones sin insertar (la flecha arriba con **2**) para abrir la página **Sincronización** en **Team Explorer**. Como tiene solo un repositorio local, la página ofrece opciones sencillas para publicar el repositorio en repositorios remotos diferentes.

    ![Ventana de Team Explorer que muestra las opciones de repositorio Git para el control de código fuente](media/django/step01-team-explorer.png)

    Puede elegir cualquier servicio que desee para sus propios proyectos. En este tutorial se muestra el uso de GitHub, donde se mantiene el código de ejemplo completo del tutorial en el repositorio [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

1. Al seleccionar cualquiera de los controles de **Publicar**, **Team Explorer** le pedirá más información. Por ejemplo, al publicar el ejemplo para este tutorial, el propio repositorio tenía que haberse creado primero. En este caso, la opción **Insertar en repositorio remoto** se utilizó con la dirección URL del repositorio.

    ![Ventana de Team Explorer para insertar en un repositorio remoto existente](media/django/step01-push-to-github.png)

    Si no tiene ningún repositorio, las opciones **Publish to GitHub** (Publicar en GitHub) e **Insertar en Azure DevOps** le permiten crear uno directamente desde Visual Studio.

1. Mientras esté trabajando en este tutorial, adopte la costumbre de usar los controles de Visual Studio periódicamente para confirmar e insertar los cambios. Este tutorial se lo recuerda en los momentos adecuados.

> [!Tip]
> Para desplazarse rápidamente por **Team Explorer**, seleccione el encabezado (donde pone **Changes** o **Push** en las imágenes anteriores) para ver un menú emergente de las páginas disponibles.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Cuáles son algunas de las ventajas del uso del control de código fuente desde el principio de un proyecto?

Respuesta: En primer lugar, usar el control de código fuente desde el principio, especialmente si también se utiliza un repositorio remoto, proporciona una copia de seguridad periódica externa del proyecto. A diferencia de mantener un proyecto solo en un sistema de archivos local, el control de código fuente también proporciona un historial de cambios completo y la capacidad de revertir con facilidad un único archivo o todo el proyecto a un estado anterior. Ese historial de cambios ayuda a determinar la causa de regresiones (errores de prueba). Además, el control de código fuente es esencial si varias personas trabajan en un proyecto, ya que administra las sobrescrituras y ofrece solución para los conflictos. Por último, el control de código fuente, que es básicamente una forma de automatización, facilita la automatización de las compilaciones, las pruebas y la administración de versiones. Es realmente el primer paso para utilizar DevOps para un proyecto, y dado que las barreras de entrada son tan bajas, realmente no hay ninguna razón que impida usar el control de código fuente desde el principio.

Para obtener más información sobre el control de código fuente como automatización, vea [The Source of Truth: The Role of Repositories in DevOps](https://msdn.microsoft.com/magazine/mt763232) (El origen de la verdad: el rol de los repositorios en DevOps), un artículo de MSDN Magazine escrito para aplicaciones móviles que también se aplica a las aplicaciones web.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Puedo evitar que Visual Studio confirme automáticamente un nuevo proyecto?

Respuesta: Sí. Para deshabilitar la confirmación automática, vaya a la página **Configuración** de **Team Explorer**, seleccione **Git** > **Configuración global**, desactive la opción **Confirmar cambios tras la fusión mediante combinación de forma predeterminada** y, a continuación, seleccione **Actualizar**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Paso 1-3: Creación del entorno virtual y excluirlo del control de código fuente

Ahora que ha configurado el control de código fuente para el proyecto, puede crear el entorno virtual que contiene los paquetes necesarios de Django para el proyecto. A continuación, puede usar **Team Explorer** para excluir la carpeta del entorno del control de código fuente.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo **Entornos de Python** y seleccione **Agregar entorno virtual**.

    ![Comando Agregar entorno virtual en el Explorador de soluciones](media/django/step01-add-virtual-environment-command.png)

1. Aparece un cuadro de diálogo **Agregar entorno virtual** con un mensaje que indica **Hemos encontrado un archivo requirements.txt**. Este mensaje indica que Visual Studio usa ese archivo para configurar el entorno virtual.

    ![Cuadro de diálogo Agregar entorno virtual con mensaje requirements.txt](media/django/step01-add-virtual-environment-found-requirements.png)

1. Seleccione **Crear** para aceptar los valores predeterminados. (Puede cambiar el nombre del entorno virtual si lo desea, lo cual simplemente cambia el nombre de su subcarpeta, pero `env` es una convención estándar).

1. Dé su consentimiento para los privilegios de administrador si se le solicita y, a continuación, tenga paciencia durante unos minutos mientras Visual Studio descarga e instala los paquetes, lo que para Django significa expandir varios miles archivos en casi tantas subcarpetas. Puede ver el progreso en la ventana **Salida** de Visual Studio. Mientras espera, consulte la sección Preguntas a continuación.

1. En los controles de Git de Visual Studio (en la barra de estado), seleccione el indicador de cambios (que muestra **99&#42;**) que abre la página **Cambios** en **Team Explorer**.

    La creación del entorno virtual implica miles de cambios, pero no es necesario que incluya ninguno de ellos en el control de código fuente, dado que usted (o cualquier usuario que clone el proyecto) siempre puede volver a crear el entorno a partir de *requirements.txt*.

    Para excluir el entorno virtual, haga clic con el botón derecho en la carpeta **env** y seleccione **Omitir estos elementos locales**.

    ![Omisión de un entorno virtual en los cambios de control de código fuente](media/django/step01-ignore-local-items.png)

1. Después de excluir el entorno virtual, los únicos cambios que faltan son en el archivo de proyecto y en *.gitignore*. El archivo *.gitignore* contiene una entrada agregada para la carpeta del entorno virtual. Puede hacer doble clic en el archivo para ver las diferencias.

1. Escriba un mensaje de confirmación y seleccione el botón **Confirmar todo**, a continuación, inserte las confirmaciones en el repositorio remoto si lo desea.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Por qué es conveniente crear un entorno virtual?

Respuesta: Un entorno virtual es una excelente manera de aislar las dependencias exactas de la aplicación. Este tipo de aislamiento evita conflictos dentro de un entorno de Python global y contribuye a las pruebas y la colaboración. Con el tiempo, a medida que desarrolle una aplicación, es inevitable que incorpore muchos paquetes útiles de Python. Si mantiene los paquetes en un entorno virtual específico del proyecto, puede actualizar fácilmente el archivo *requirements.txt* del proyecto que describe ese entorno, el cual se incluye en el control de código fuente. Cuando el proyecto se copia en otros equipos, como los servidores de compilación, los servidores de implementación y otros equipos de desarrollo, es fácil volver a crear el entorno con solo *requirements.txt* (por este motivo no es necesario que el entorno esté en el control de código fuente). Para obtener más información, vea [Use virtual environments](selecting-a-python-environment-for-a-project.md#use-virtual-environments) (Usar entornos virtuales).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Cómo se quita un entorno virtual que ya se ha confirmado en el control de código fuente?

Respuesta: En primer lugar, edite el archivo *.gitignore* para excluir la carpeta: busque la sección del final con el comentario `# Python Tools for Visual Studio (PTVS)` y agregue una línea nueva para la carpeta del entorno virtual, como `/BasicProject/env`. (Dado que Visual Studio no muestra el archivo en el **Explorador de soluciones**, ábralo directamente mediante el comando de menú **Archivo** > **Abrir** > **Archivo**. También puede abrir el archivo desde **Team Explorer**: en la página **Configuración**, seleccione **Configuración de repositorios**, vaya a la sección **Archivos de omisión y de atributos** y luego seleccione el vínculo **Editar** junto a **.gitignore**).

En segundo lugar, abra una ventana de comandos, vaya a la carpeta como *BasicProject* que contiene la carpeta del entorno virtual, como *env*, y ejecute `git rm -r env`. A continuación, confirme esos cambios desde la línea de comandos (`git commit -m 'Remove venv'`), o bien desde la página **Cambios** de **Team Explorer**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Paso 1-4: Examen del código reutilizable

Una vez que finalice la creación del proyecto, examine el código del proyecto de Django reutilizable (que es de nuevo el mismo que se generó por el comando de la CLI `django-admin startproject <project_name>`).

1. En la raíz del proyecto se encuentra *manage.py*, la utilidad administrativa de línea de comandos de Django que Visual Studio establece automáticamente como archivo de inicio del proyecto. Ejecute la utilidad en la línea de comandos usando `python manage.py <command> [options]`. Para las tareas comunes de Django, Visual Studio proporciona los comandos de menú pertinentes. Haga clic con el botón derecho en el proyecto en el **Explorador de soluciones** y seleccione **Python** para ver la lista. Encontrará algunos de estos comandos en el transcurso de este tutorial.

    ![Comandos de Django en un menú contextual de proyecto de Python](media/django/step01-django-commands-menu.png)

2. En el proyecto se encuentra una carpeta que tiene el mismo nombre que el proyecto. Contiene los archivos de proyecto Django básicos:

   - *__init.py*: un archivo vacío que indica a Python que esta carpeta es un paquete de Python.
   - *wsgi.py*: un punto de entrada para los servidores web compatibles con WSGI que van a servir al proyecto. Normalmente dejará los archivos tal cual, puesto que sirven de enlace a los servidores web de producción.
   - *settings.py*: contiene la configuración del proyecto de Django, que se modifica durante el desarrollo de una aplicación web.
   - *urls.py*: contiene una tabla de contenido para el proyecto de Django, que también se modifica durante el desarrollo.

     ![Archivos de proyecto de Django en el Explorador de soluciones](media/django/step01-django-project-in-solution-explorer.png)

3. Como se ha indicado anteriormente, la plantilla de Visual Studio también agrega un archivo *requirements.txt* al proyecto que especifica la dependencia del paquete de Django. La presencia de este archivo es lo que le invita a crear un entorno virtual cuando empiece a crear el proyecto.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Puede Visual Studio generar un archivo requirements.txt a partir de un entorno virtual después de instalar otros paquetes?

Respuesta: Sí. Expanda el nodo **Entornos de Python**, haga clic con el botón derecho en su entorno virtual y seleccione el comando **Generar requirements.txt**. Es conveniente usar este comando periódicamente a medida que modifica el entorno, y confirmar los cambios de *requirements.txt* en el control de código fuente junto con cualquier otro cambio de código que dependa de ese entorno. Si configura la integración continua en un servidor de compilación, debe generar el archivo y confirmar los cambios cada vez que se modifique el entorno.

## <a name="step-1-5-run-the-empty-django-project"></a>Paso 1-5: Ejecución del proyecto de Django vacío

1. En Visual Studio, seleccione **Depurar** > **Iniciar depuración** (**F5**) o use el botón **Servidor web** de la barra de herramientas (el explorador puede variar):

    ![Ejecución del botón de la barra de herramientas del servidor web en Visual Studio](media/django/run-web-server-toolbar-button.png)

1. La ejecución del servidor implica la ejecución del comando `manage.py runserver <port>`, que inicia el servidor de desarrollo integrado de Django. Si Visual Studio indica **No se pudo iniciar el depurador** con un mensaje relacionado con la falta de un archivo de inicio, haga clic con el botón derecho en **manage.py** en el **Explorador de soluciones** y seleccione **Establecer como archivo de inicio**.

1. Al iniciar el servidor, verá una ventana de consola abierta que también muestra el registro del servidor. Visual Studio abre automáticamente un explorador en `http://localhost:<port>`. Sin embargo, dado que el proyecto de Django no tiene ninguna aplicación, Django muestra solo una página predeterminada para confirmar que lo que tiene hasta ahora funciona correctamente:

    ![Vista predeterminada del proyecto de Django](media/django/step01-first-run-success.png)

1. Cuando haya terminado, detenga el servidor cerrando la ventana de la consola o con el comando **Depurar** > **Detener depuración** en Visual Studio.

### <a name="question-is-django-a-web-server-as-well-as-a-framework"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Django es un servidor web además de una plataforma?

Respuesta: Sí y no. Django tiene un servidor web integrado que se usa para fines de desarrollo. Este servidor web es lo que se usa al ejecutar la aplicación web localmente, como al depurar en Visual Studio. Cuando se implementa en un host web, sin embargo, lo que Django utiliza es el servidor web. El módulo *wsgi.py* del proyecto de Django se ocupa de enlazar con los servidores de producción.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Pregunta: Estoy utilizando un certificado X.509 con mi servicio y obtengo un System.Security.Cryptography.CryptographicException. ¿Cuál es la diferencia entre el uso de los comandos de menú de depuración y los comandos de servidor en el submenú de Python del proyecto?

Respuesta: Además de con los comandos de menú de **Depurar** y los botones de la barra de herramientas, también se puede iniciar el servidor mediante los comandos **Python** > **Run server** (Ejecutar servidor) o **Python** > **Run debug server** (Ejecutar el servidor de depuración) en el menú contextual del proyecto. Ambos comandos abren una ventana de consola en la que se ve la dirección URL local (localhost:port) del servidor en ejecución. Sin embargo, debe abrir manualmente un explorador con esa dirección URL, y la ejecución del servidor de depuración no inicia automáticamente el depurador de Visual Studio. Puede adjuntar un depurador al proceso en ejecución más adelante, si lo desea, mediante el comando **Depurar** > **Asociar al proceso**.

## <a name="next-steps"></a>Pasos siguientes

En este momento, el proyecto de Django básico no contiene ninguna aplicación. Crearemos una aplicación en el paso siguiente. Dado que normalmente funcionan con las aplicaciones de Django más que con el proyecto de Django, no necesita saber mucho más acerca de los archivos de código reutilizable en este momento.

> [!div class="nextstepaction"]
> [Creación de una aplicación de Django con vistas y plantillas de página](learn-django-in-visual-studio-step-02-create-an-app.md)

## <a name="go-deeper"></a>Profundizar un poco más

- Código del proyecto de Django: [Creación de la primera aplicación en Django, parte 1](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) (docs.djangoproject.com)
- Utilidad administrativa: [django-admin and manage.py](https://docs.djangoproject.com/en/2.0/ref/django-admin/) (django-admin y manage.py) (docs.djangoproject.com)
- Código fuente del tutorial en GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
