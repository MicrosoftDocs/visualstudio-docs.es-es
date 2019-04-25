---
title: Plantilla de proyecto web de Django para Python
description: Visual Studio proporciona una plantilla completa para la creación rápida de aplicaciones web de Django con Python.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 136c03ef11071e5d548e36e45a6a541cffce1469
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62784888"
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

    ![Resultados del comando Abrir Shell de Django](media/template-django-console-shell.png)

- **Django Sync DB** (Base de datos de sincronización de Django): ejecuta `manage.py syncdb` en una ventana **interactiva**:

    ![Resultados del comando Sincronizar base de datos de Django](media/template-django-console-sync-db.png)

- **Collect Static** (Recopilar estáticos): ejecuta `manage.py collectstatic --noinput` para copiar todos los archivos estáticos en la ruta de acceso que `STATIC_ROOT` especifica en *settings.py*.

    ![Resultado del comando Recopilar archivos estáticos](media/template-django-console-collect-static.png)

- **Validar**: ejecuta `manage.py validate`, que informa de los errores de validación en los modelos instalados que especifica `INSTALLED_APPS` en *settings.py*:

    ![Resultado del comando Validar](media/template-django-console-validate.png)

## <a name="see-also"></a>Vea también

- [Tutorial de aprendizaje de Django](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Publicación en Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
