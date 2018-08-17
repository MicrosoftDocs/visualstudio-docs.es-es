---
ms.topic: include
ms.openlocfilehash: ff6523d33e29f4fcc6fd02c08e0a35ac00892829
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638394"
---
### <a name="create-a-project-using-django-20"></a>Creación de un proyecto con Django 2.0

Actualmente, la **plantilla Proyecto web de Django en blanco** utiliza la versión más reciente de Django 1.x. Para usar Django 2.x, el medio más rápido es importar archivos de Django 2.x en un proyecto de Django 1.x. Si sigue este proceso, podrá aprovechar las ventajas de otros detalles que controla la plantilla de proyecto de Visual Studio.

1. Cree un proyecto de Django 1.x mediante la plantilla **Proyecto web de Django en blanco** tal como se describe en la sección anterior. Sin embargo, cuando se muestre el mensaje **This project requires external dependencies" (Este proyecto requiere dependencias externas)**, seleccione **Los instalaré de forma manual**. Elija esta opción para evitar la instalación de dependencias que se desinstalan en un paso posterior.

1. Abra un símbolo del sistema y vaya a una carpeta temporal.

1. Ejecute `pip install django` para instalar el paquete de Django más reciente en su entorno global de Python.

1. Ejecute `django-admin startproject <project_name>` reemplazando `<project_name>` por el mismo nombre de proyecto que se utilizó en el paso 1, por ejemplo, "HelloDjango". El comando `startproject` creará un archivo *manage.py* junto a una carpeta que coincida con `<project_name>` y que contenga los archivos *\_\_init\_\_.py*, *settings.py*, *urls.py* y *wsgi.py*.

1. En Visual Studio, reemplace los archivos de Django 1.x del proyecto por los archivos de Django 2.x del modo siguiente:

    1. En el **Explorador de soluciones**, elimine **manage.py** y la carpeta de la aplicación de Django.
    1. Haga clic con el botón derecho en el proyecto, seleccione el comando **Agregar** > **Elemento existente**, vaya al archivo **manage.py** creado en el paso 4 y selecciónelo; por último, seleccione **Aceptar**. Visual Studio copia entonces ese archivo en el proyecto.
    1. Haga clic de nuevo con el botón derecho en el proyecto, seleccione el comando **Agregar** > **Carpeta existente**, vaya a la carpeta de aplicaciones creada en el paso 4 y selecciónela; por último, seleccione **Aceptar**. A continuación, Visual Studio copia esa carpeta y sus cuatro archivos en el proyecto.
    1. Haga clic con el botón derecho en el archivo **manage.py** y seleccione **Establecer como archivo de inicio**.

    > [!Important]
    > El nombre de aplicación que aparece en el proyecto de Visual Studio debe coincidir con el `<project_name>` utilizado con la utilidad `django-admin`, porque la utilidad usa ese nombre como un espacio de nombres dentro de los archivos de código de Python.

1. Abra el archivo *requirements.txt*, cambie su contenido a `django >=2.0, <3` y guárdelo.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo **Entornos de Python** y seleccione **Agregar entorno virtual**. Acepte los valores predeterminados del cuadro de diálogo que aparece y seleccione **Crear**. Acepte las solicitudes de privilegios de administrador.