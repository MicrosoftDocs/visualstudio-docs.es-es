---
title: Plantilla de proyecto web de Django para Python en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c479be58-13eb-4d77-9a27-c97ddc290963
caps.latest.revision: 1
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
ms.openlocfilehash: 4a5db2deb3633e8305dbf83cbe6ba8c0e3344c72
ms.contentlocale: es-es
ms.lasthandoff: 05/09/2017

---

# <a name="django-web-project-template"></a>Plantilla de proyecto web de Django

[Django](https://www.djangoproject.com/) es un marco de Python de alto nivel diseñado para el desarrollo web rápido, seguro y escalable. La compatibilidad de Python en Visual Studio proporciona una plantilla de proyecto para configurar la estructura de una aplicación web basada en Django. Para usar la plantilla en Visual Studio, seleccione **Archivo > Nuevo > Proyecto**, busque "Django" y seleccione la plantilla "Django Web Project" (Proyecto web de Django). El proyecto resultante incluirá código reutilizable, así como una base de datos de SQLite predeterminada. La plantilla "Blank Django Web Project" (Proyecto web de Django en blanco) es similar, pero no incluye la base de datos.

Visual Studio proporciona IntelliSense al completo para proyectos de Django:

- Variables de contexto que se pasan en la plantilla:

    ![IntelliSense para variables de contexto](media/template-django-intellisense.png)

- Etiquetado y filtrado para elementos integrados y definidos por el usuario:

    ![IntelliSense para etiquetas y filtros](media/template-django-intellisense-filter.png)

- Color de sintaxis para JavaScript y CSS insertado:

    ![IntelliSense para CSS](media/template-django-intellisense-css.png)

    ![IntelliSense para JavaScript](media/template-django-intellisense-js.png)


Visual Studio también proporciona [compatibilidad con la depuración](debugging.md) completa para los proyectos de Django: 

![Puntos de interrupción](media/template-django-debugging.png)

## <a name="django-management-console"></a>Consola de administración de Django

El acceso a la consola de administración de Django se realiza a través de varios comandos del menú **Proyecto** o haciendo clic con el botón derecho en el proyecto en el Explorador de soluciones.

- **Open Django Shell...** (Abrir shell de Django... ): abre un shell en el contexto de la aplicación que le permite manipular los modelos:

    ![Consola](media/template-django-console-shell.png)

- **Django Sync DB** (Base de datos de sincronización de Django): ejecuta `manage.py syncdb` en una ventana interactiva:

    ![Consola](media/template-django-console-sync-db.png)

- **Collect Static** (Recopilar estáticos): ejecuta `manage.py collectstatic --noinput` para copiar todos los archivos estáticos en la ruta de acceso que especificada `STATIC_ROOT` en `settings.py`. Tenga en cuenta que cuando [publicar en Microsoft Azure](template-web.md#publishing-to-azure-app-service), automáticamente se recopilan los archivos estáticos como parte de la operación de publicación.

    ![Consola](media/template-django-console-collect-static.png)

- **Validar**: ejecuta `manage.py validate`, que informa de los errores de validación en los modelos instalados que especifica `INSTALLED_APPS` en `settings.py`:

    ![Consola](media/template-django-console-validate.png)
