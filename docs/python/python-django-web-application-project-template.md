---
title: Plantilla de proyecto web de Django para Python
description: Información general de las plantillas de Visual Studio para aplicaciones web escritas en Python con el marco Django.
ms.date: 07/03/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 4ea90a97067e92d39772bd4257dc3abbae58d1d8
ms.sourcegitcommit: 40b6438b5acd7e59337a382c39ec711b9e99cc8a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100970"
---
# <a name="django-web-project-template"></a>Plantilla de proyecto web de Django

[Django](https://www.djangoproject.com/) es un marco de Python de alto nivel diseñado para el desarrollo web rápido, seguro y escalable. La compatibilidad de Python en Visual Studio proporciona varias plantillas de proyecto para configurar la estructura de una aplicación web basada en Django. Para usar una plantilla en Visual Studio, seleccione **Archivo** > **Nuevo** > **Proyecto**, busque "Django" y seleccione alguna de las plantillas **Proyecto web de Django en blanco**, **Proyecto web de Django** y **Proyecto web de Django de sondeos**. Vea el [tutorial de aprendizaje de Django](learn-django-in-visual-studio-step-01-project-and-solution.md) para obtener una guía detallada de todas las plantillas.

Visual Studio proporciona IntelliSense al completo para proyectos de Django:

- Variables de contexto que se pasan en la plantilla:

    ![IntelliSense para variables de contexto](media/template-django-intellisense.png)

- Etiquetado y filtrado para elementos integrados y definidos por el usuario:

    ![IntelliSense para etiquetas y filtros](media/template-django-intellisense-filter.png)

- Color de sintaxis para JavaScript y CSS insertado:

    ![IntelliSense para CSS](media/template-django-intellisense-css.png)

    ![IntelliSense para JavaScript](media/template-django-intellisense-js.png)

Visual Studio también proporciona [compatibilidad con la depuración](debugging-python-in-visual-studio.md) completa para los proyectos de Django: 

![Puntos de interrupción](media/template-django-debugging.png)

Es habitual que los proyectos de Django se administren mediante su archivo *manage.py*, que es una hipótesis que sigue Visual Studio. Si deja de usar ese archivo como el punto de entrada, básicamente divide el archivo del proyecto. En ese caso necesita [volver a crear el proyecto de archivos existentes](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) sin marcarlo como un proyecto de Django.

## <a name="django-management-console"></a>Consola de administración de Django

El acceso a la consola de administración de Django se realiza a través de varios comandos del menú **Proyecto** o haciendo clic con el botón derecho en el proyecto en el **Explorador de soluciones**.

- **Abrir Shell de Django**: abre un Shell en el contexto de la aplicación que le permite manipular los modelos:

    ![Consola](media/template-django-console-shell.png)

- **Django Sync DB** (Base de datos de sincronización de Django): ejecuta `manage.py syncdb` en una ventana **interactiva**:

    ![Consola](media/template-django-console-sync-db.png)

- **Collect Static** (Recopilar estáticos): ejecuta `manage.py collectstatic --noinput` para copiar todos los archivos estáticos en la ruta de acceso que `STATIC_ROOT` especifica en *settings.py*.

    ![Consola](media/template-django-console-collect-static.png)

- **Validar**: ejecuta `manage.py validate`, que informa de los errores de validación en los modelos instalados que especifica `INSTALLED_APPS` en *settings.py*:

    ![Consola](media/template-django-console-validate.png)

## <a name="see-also"></a>Vea también

- [Tutorial de aprendizaje de Django](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Publicación en Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
