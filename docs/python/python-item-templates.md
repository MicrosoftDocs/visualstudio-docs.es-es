---
title: Plantillas de elementos para proyectos de Python
description: Una lista de referencia de las plantillas de elementos para un proyecto de Python que están disponibles a través del cuadro de diálogo Agregar > Nuevo elemento en Visual Studio.
ms.date: 12/06/2018
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 528606356c2d976de71ab2c0317a1a0236d2e63f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533398"
---
# <a name="python-item-templates"></a>Plantillas de elementos de Python

Las plantillas de elementos están disponibles en proyectos de Python a través del comando de menú **Proyecto** > **Agregar nuevo elemento** o el comando **Agregar** > **Nuevo elemento** en el menú contextual del **Explorador de soluciones**.

![Cuadro de diálogo Add New Item](media/project-item-templates.png)

Con el nombre que proporcione para el elemento, una plantilla suele crear uno o varios archivos y carpetas dentro de la carpeta actualmente seleccionada en el proyecto (al hacer clic con el botón derecho en una carpeta para que aparezca el menú contextual se selecciona automáticamente esa carpeta). Al agregar un elemento, lo incluye en el proyecto de Visual Studio y aparecerá en el **Explorador de soluciones**.

En la tabla siguiente se explica brevemente el efecto de cada plantilla de elemento dentro de un proyecto de Python:

| Plantilla | Qué crea la plantilla |
| --- | --- |
| **Archivo de Python vacío** | Un archivo vacío con la extensión *.py*. |
| **Clase de Python** | Un archivo *.py* que contiene una única definición de clase vacía de Python. |
| **Paquete de Python** | Una carpeta que contiene un archivo *\_\_init\_\_.py*. |
| **Prueba unitaria de Python** | Un archivo *.py* con una sola prueba unitaria basada en la plataforma `unittest`, junto con una llamada a `unittest.main()` para ejecutar las pruebas en el archivo. |
| **Página HTML** | Un archivo *.html* con una estructura de página sencilla que consta de un elemento `<head>` y `<body>`. |
| **JavaScript** | Un archivo *.js* vacío. |
| **Hoja de estilos** | Un archivo *.css* que contiene un estilo vacío para `body`. |
| **Archivo de texto** | Un archivo *.txt* vacío. |
| **Aplicación Django 1.9**<br/>**Aplicación Django 1.4** | Una carpeta con el nombre de la aplicación, que contiene los archivos principales de una aplicación de Django como se explica en [Información acerca de Django en Visual Studio, paso 2.2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) para Django 1.9. En el caso de Django 1.4, no se incluyen la carpeta *migrations* ni los archivos *admin.py* y *apps.py*. |
| **Ventana de WPF de IronPython** | Una ventana de WPF que consta de dos archivos paralelos: un archivo *.xaml* que define un `<Window>` con un elemento `<Grid>` vacío, y un archivo *.py* asociado que carga el archivo XAML mediante la biblioteca `wpf`. Suele usarse dentro de un proyecto creado con una de las plantillas de proyecto de IronPython. Vea [Proyectos de Python - Plantillas de proyecto](managing-python-projects-in-visual-studio.md#project-templates). |
| **Archivos auxiliares de rol web** | Una carpeta *bin* en la raíz del proyecto (independientemente de la carpeta seleccionada en el proyecto). La carpeta contiene un script de implementación predeterminado y un archivo *web.config* para los roles web del Servicio en la nube de Azure. La plantilla también incluye un archivo *readme.html* donde se explican los detalles. |
| **Archivos de compatibilidad de rol de trabajo** | Una carpeta *bin* en la raíz del proyecto (independientemente de la carpeta seleccionada en el proyecto). La carpeta contiene el script de implementación e inicio predeterminado, junto con un archivo *web.config*, para los roles de trabajo del servicio en la nube de Azure. La plantilla también incluye un archivo *readme.html* donde se explican los detalles. |
| **web.config de Azure (FastCGI)** | Un archivo *web.config* que contiene las entradas para las aplicaciones con un objeto [WSGI](https://wsgi.readthedocs.io/en/latest/) para controlar las conexiones entrantes. Este archivo normalmente se implementa en la raíz de un servidor web que ejecuta IIS. Para más información, consulte [Configure an app for IIS](configure-web-apps-for-iis-windows.md) (Configurar una aplicación para IIS). |
| **web.config de Azure (HttpPlatformHandler)** | Un archivo *web.config* que contiene las entradas para las aplicaciones que escuchan en un socket para las conexiones entrantes. Este archivo normalmente se implementa en la raíz de un servidor web que ejecuta IIS, por ejemplo, Azure App Service. Para más información, consulte [Configure an app for IIS](configure-web-apps-for-iis-windows.md) (Configurar una aplicación para IIS). |
| **web.config de archivos estáticos de Azure** | Un archivo *web.config* que normalmente se agrega a una carpeta *static* (u otra carpeta que contiene elementos estáticos) para deshabilitar el control de Python para esa carpeta. Este archivo de configuración funciona junto con uno de los archivos de configuración FastCGI o HttpPlatformHandler anteriores. Para más información, consulte [Configure an app for IIS](configure-web-apps-for-iis-windows.md) (Configurar una aplicación para IIS). |
| **web.config de depuración remota de Azure** | En desuso (se usaba para depuración remota en Azure App Service para Windows, que ya no se admite). |

## <a name="see-also"></a>Consulte también

- [Proyectos de Python - Plantillas de proyecto](managing-python-projects-in-visual-studio.md#project-templates)
- [Plantillas de proyecto web de Python](python-web-application-project-templates.md)
- [Publicación en Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
