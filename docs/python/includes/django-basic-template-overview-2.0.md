---
ms.topic: include
ms.openlocfilehash: 0ee0234e91cdf07c2b52c39d065d527a776dc4ce
ms.sourcegitcommit: 64bf371ffe294e9b3cf769db03cf0f5c1a9b680c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2018
ms.locfileid: "35666982"
---
### <a name="create-a-project-using-django-20"></a>Creación de un proyecto con Django 2.0

En la actualidad, la plantilla Proyecto web de Django en blanco utiliza la versión más reciente de Django 1.x. Para usar Django 2.x, el medio más rápido es importar archivos de Django 2.x en un proyecto de Django 1.x. Si sigue este proceso, podrá aprovechar las ventajas de otros detalles que controla la plantilla de proyecto de Visual Studio.

1. Cree un proyecto de Django 1.x mediante la plantilla "Proyecto web de Django en blanco" tal como se describe en la sección anterior. Sin embargo, cuando salga el mensaje "This project requires external dependencies" (Este proyecto requiere dependencias externas), seleccione **Los instalaré de forma manual**. Elija esta opción para evitar la instalación de dependencias que se desinstalan en un paso posterior.

1. Abra un símbolo del sistema y vaya a una carpeta temporal.

1. Ejecute `pip install django` para instalar el paquete de Django más reciente en su entorno global de Python.

1. Ejecute `django-admin startproject <project_name>` reemplazando `<project_name>` por el mismo nombre de proyecto que se utilizó en el paso 1, por ejemplo, "HelloDjango". El comando `startproject` crea un archivo `manage.py` junto con la correspondiente carpeta `<project_name>` que contiene los archivos `__init__.py`, `settings.py`, `urls.py` y `wsgi.py`.

1. En Visual Studio, reemplace los archivos de Django 1.x del proyecto por los archivos de Django 2.x del modo siguiente:

  a. En el **Explorador de soluciones**, elimine `manage.py` y la carpeta de la aplicación de Django.
  b. Haga clic con el botón derecho en el proyecto, seleccione el comando **Agregar > Elemento existente...** , vaya al archivo `manage.py` creado en el paso 4 y selecciónelo; por último, seleccione **Aceptar**. Visual Studio copia entonces ese archivo en el proyecto.
  c. Haga clic de nuevo con el botón derecho en el proyecto, seleccione el comando **Agregar > Carpeta existente...** , vaya a la carpeta de aplicaciones creada en el paso 4 y selecciónela; por último, seleccione **Aceptar**. A continuación, Visual Studio copia esa carpeta y sus cuatro archivos en el proyecto.
  d. Haga clic con el botón derecho en `manage.py` y seleccione **Establecer como archivo de inicio**.

  > [!Important]
  > El nombre de aplicación que aparece en el proyecto de Visual Studio debe coincidir con el `<project_name>` utilizado con la utilidad `django-admin`, porque la utilidad usa ese nombre como un espacio de nombres dentro de los archivos de código de Python.

1. Abra `requirements.txt`, cambie su contenido a `django >=2.0, <3` y guarde el archivo.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo **Entornos de Python** y seleccione **Agregar entorno virtual...** Acepte los valores predeterminados del cuadro de diálogo que aparece y seleccione **Crear**. Acepte las solicitudes de privilegios de administrador.