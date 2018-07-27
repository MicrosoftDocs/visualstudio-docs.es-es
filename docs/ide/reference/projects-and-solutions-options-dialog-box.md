---
title: Proyectos y soluciones, Cuadro de diálogo Opciones
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbd3fe20377cd2aa4954e904fec50702cc9b7120
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843996"
---
# <a name="projects-and-solutions-page-options-dialog-box"></a>Página Proyectos y soluciones, Cuadro de diálogo Opciones

Establece el comportamiento de Visual Studio relacionado con proyectos y soluciones. Para acceder a estas opciones, seleccione **Herramientas** > **Opciones**, expanda **Proyectos y soluciones** y haga clic en **General**.

Las rutas de acceso predeterminadas para las carpetas de proyectos y plantillas se establecen a través de la pestaña **Ubicaciones** en el mismo cuadro de diálogo.

> [!NOTE]
> Las opciones disponibles en la interfaz de usuario podrían diferir de lo que se describe en este caso, dependiendo de la edición o configuración activa. Este artículo se ha redactado teniendo en cuenta la **Configuración general de desarrollo**. Para ver o cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**. Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-page"></a>Página general

Las siguientes opciones están disponibles en la páginas **General**.

### <a name="always-show-error-list-if-build-finishes-with-errors"></a>Mostrar siempre lista de errores si la compilación termina con errores

Abre la ventana **Lista de errores** al terminar la compilación solo si no se ha podido compilar un proyecto. Se muestran los errores que se producen durante el proceso de compilación. Cuando esta opción está desactivada, se siguen produciendo errores, pero no se abre la ventana una vez finalizada la compilación. Esta opción está habilitada de forma predeterminada.

### <a name="track-active-item-in-solution-explorer"></a>Realizar seguimiento del elemento activo en el Explorador de soluciones

Si esta opción está activada, el **Explorador de soluciones** se abre automáticamente y se selecciona el elemento activo. El elemento seleccionado cambia conforme trabaja con distintos archivos de un proyecto o solución o con distintos componentes de un diseñador. Si esta opción está desactivada, la selección del **Explorador de soluciones** no cambia automáticamente. Esta opción está habilitada de forma predeterminada.

### <a name="show-advanced-build-configurations"></a>Mostrar configuraciones de compilación avanzadas

Si está activada, las opciones de configuración de compilación aparecen en los cuadros de diálogo **Páginas de propiedades del proyecto** y **Páginas de propiedades de la solución**. Si está desactivada, las opciones de configuración de compilación no aparecen en los cuadros de diálogo **Páginas de propiedades del proyecto** y **Páginas de propiedades de la solución** de los proyectos de Visual Basic y C# que contienen una o las dos configuraciones de depuración y publicación. Si un proyecto tiene una configuración definida por el usuario, se muestran las opciones de configuración de compilación.

Si no está activada, los comandos del menú **Compilar**, como **Compilar solución**, **Recompilar solución** y **Limpiar solución**, se ejecutan en la configuración de publicación, mientras que los comandos del menú **Depurar**, como **Iniciar depuración** e **Iniciar sin depurar**, se ejecutan en la configuración de depuración.

### <a name="always-show-solution"></a>Mostrar solución siempre

Cuando se selecciona, la solución y todos los comandos que se aplican a soluciones siempre se muestran en el IDE. Cuando está desactivada, todos los proyectos se crean como proyectos independientes y no ve la solución en el Explorador de soluciones ni en los comandos que se aplican a las soluciones en el IDE si la solución solo contiene un proyecto.

### <a name="save-new-projects-when-created"></a>Guardar nuevos proyectos al crearlos

Si está activada, puede especificar una ubicación para el proyecto en el cuadro de diálogo **Nuevo proyecto**. Cuando está desactivada, todos los proyectos nuevos se crean como proyectos temporales. Cuando se trabaja con proyectos temporales, puede crear y experimentar con un proyecto sin tener que especificar una ubicación de disco.

### <a name="warn-user-when-the-project-location-is-not-trusted"></a>Advertir al usuario cuando la ubicación del proyecto no sea de confianza

Si intenta crear un nuevo proyecto o abrir un proyecto existente en una ubicación que no sea de plena confianza (por ejemplo, en una ruta de acceso UNC o HTTP), se muestra un mensaje. Use esta opción para especificar si el mensaje se muestra cada vez que intente crear o abrir un proyecto en una ubicación que no sea de plena confianza.

### <a name="show-output-window-when-build-starts"></a>Mostrar ventana de salida cuando empiece la compilación

Muestra automáticamente la [ventana de salida](../../ide/reference/output-window.md) en el IDE al empezar la compilación de la solución.

### <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Solicitar cambio de nombre simbólico al cambiar el nombre de los archivos

Cuando se selecciona, Visual Studio muestra un cuadro de mensaje que pregunta si también debe cambiar o no el nombre de todas las referencias del proyecto al elemento de código.

### <a name="prompt-before-moving-files-to-a-new-location"></a>Preguntar antes de mover los archivos a una nueva ubicación

Cuando se selecciona, Visual Studio muestra un cuadro de mensaje de confirmación antes de que las ubicaciones de archivos se cambien por las acciones en el **Explorador de soluciones**.

### <a name="reopen-documents-on-solution-load"></a>Volver a abrir documentos en la carga de la solución

**Novedad en Visual Studio 2017 (versión 15.8, versión preliminar 2 y posteriores)**

Cuando se selecciona, los documentos que estaban abiertos la última vez que se cerró esta solución se abren automáticamente al abrir la solución.

Volver a abrir determinados tipos de archivos o diseñadores puede retrasar la carga de la solución. Desactive esta opción para [mejorar el rendimiento de la carga de la solución](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) si no quiere restaurar el contexto previo de la solución.

## <a name="locations-page"></a>Página Ubicaciones

Las siguientes opciones están disponibles en la páginas **Ubicaciones**.

### <a name="projects-location"></a>Ubicación de proyectos

Especifica la ubicación predeterminada donde Visual Studio crea las nuevas carpetas de proyectos y soluciones. Varios cuadros de diálogo también usan la ubicación establecida en esta opción para los puntos iniciales de las carpetas. Por ejemplo, el cuadro de diálogo **Abrir proyecto** usa esta ubicación para el acceso directo **Mis proyectos**.

### <a name="user-project-templates-location"></a>Ubicación de plantillas de proyecto de usuario

Especifica la ubicación predeterminada que usa el cuadro de diálogo **Nuevo proyecto** para crear la lista de **Mis plantillas**. Para más información, vea [Cómo: Localizar y organizar plantillas](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

### <a name="user-item-templates-location"></a>Ubicación de plantillas de elemento de usuario

Especifica la ubicación predeterminada que usa el cuadro de diálogo **Agregar nuevo elemento** para crear la lista de **Mis plantillas**. Para más información, vea [Cómo: Localizar y organizar plantillas](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Vea también

- [Cuadro de diálogo Opciones, Proyectos y soluciones, Compilar y ejecutar](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Cuadro de diálogo Opciones, Proyectos y soluciones, Proyectos web](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
