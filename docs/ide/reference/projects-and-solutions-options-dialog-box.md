---
title: Proyectos y soluciones, cuadro de diálogo Opciones
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31d829a668a2c9690333315c30904623187fe51d
ms.sourcegitcommit: f42b5318c5c93e2b5ecff44f408fab8bcdfb193d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2019
ms.locfileid: "69976734"
---
# <a name="options-dialog-box-projects-and-solutions--general"></a>Cuadro de diálogo Opciones: Proyectos y soluciones \> General

Use esta página para definir el comportamiento de Visual Studio relacionado con proyectos y soluciones. Para acceder a estas opciones, seleccione **Herramientas** > **Opciones**, expanda **Proyectos y soluciones** y haga clic en **General**.

Las siguientes opciones están disponibles en la páginas **General**.

## <a name="always-show-error-list-if-build-finishes-with-errors"></a>Mostrar siempre lista de errores si la compilación termina con errores

Abre la ventana **Lista de errores** al terminar la compilación solo si no se ha podido compilar un proyecto. Se muestran los errores que se producen durante el proceso de compilación. Cuando esta opción está desactivada, se siguen produciendo errores, pero no se abre la ventana una vez finalizada la compilación. Esta opción está habilitada de forma predeterminada.

## <a name="track-active-item-in-solution-explorer"></a>Realizar seguimiento del elemento activo en el Explorador de soluciones

Si esta opción está activada, el **Explorador de soluciones** se abre automáticamente y se selecciona el elemento activo. El elemento seleccionado cambia conforme trabaja con distintos archivos de un proyecto o solución o con distintos componentes de un diseñador. Si esta opción está desactivada, la selección del **Explorador de soluciones** no cambia automáticamente. Esta opción está habilitada de forma predeterminada.

## <a name="show-advanced-build-configurations"></a>Mostrar configuraciones de compilación avanzadas

Si está activada, las opciones de configuración de compilación aparecen en los cuadros de diálogo **Páginas de propiedades del proyecto** y **Páginas de propiedades de la solución**. Si está desactivada, las opciones de configuración de compilación no aparecen en los cuadros de diálogo **Páginas de propiedades del proyecto** y **Páginas de propiedades de la solución** de los proyectos de Visual Basic y C# que contienen una o las dos configuraciones de depuración y publicación. Si un proyecto tiene una configuración definida por el usuario, se muestran las opciones de configuración de compilación.

Si no está activada, los comandos del menú **Compilar**, como **Compilar solución**, **Recompilar solución** y **Limpiar solución**, se ejecutan en la configuración de publicación, mientras que los comandos del menú **Depurar**, como **Iniciar depuración** e **Iniciar sin depurar**, se ejecutan en la configuración de depuración.

## <a name="always-show-solution"></a>Mostrar solución siempre

Cuando se selecciona, la solución y todos los comandos que se aplican a soluciones siempre se muestran en el IDE. Cuando está desactivada, todos los proyectos se crean como proyectos independientes y no ve la solución en el Explorador de soluciones ni en los comandos que se aplican a las soluciones en el IDE si la solución solo contiene un proyecto.

::: moniker range="vs-2017"

## <a name="save-new-projects-when-created"></a>Guardar nuevos proyectos al crearlos

Si está activada, puede especificar una ubicación para el proyecto en el cuadro de diálogo **Nuevo proyecto**. Cuando está desactivada, todos los proyectos nuevos se crean como proyectos temporales. Cuando se trabaja con proyectos temporales, puede crear y experimentar con un proyecto sin tener que especificar una ubicación de disco.

::: moniker-end

## <a name="warn-user-when-the-project-location-is-not-trusted"></a>Advertir al usuario cuando la ubicación del proyecto no sea de confianza

Si intenta crear un nuevo proyecto o abrir un proyecto existente en una ubicación que no sea de plena confianza (por ejemplo, en una ruta de acceso UNC o HTTP), se muestra un mensaje. Use esta opción para especificar si el mensaje se muestra cada vez que intente crear o abrir un proyecto en una ubicación que no sea de plena confianza.

## <a name="show-output-window-when-build-starts"></a>Mostrar ventana de salida cuando empiece la compilación

Muestra automáticamente la [ventana de salida](../../ide/reference/output-window.md) en el IDE al empezar la compilación de la solución.

## <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Solicitar cambio de nombre simbólico al cambiar el nombre de los archivos

Cuando se selecciona, Visual Studio muestra un cuadro de mensaje que pregunta si también debe cambiar o no el nombre de todas las referencias del proyecto al elemento de código.

## <a name="prompt-before-moving-files-to-a-new-location"></a>Preguntar antes de mover los archivos a una nueva ubicación

Cuando se selecciona, Visual Studio muestra un cuadro de mensaje de confirmación antes de que las ubicaciones de archivos se cambien por las acciones en el **Explorador de soluciones**.

## <a name="reopen-documents-on-solution-load"></a>Volver a abrir documentos en la carga de la solución

Cuando se selecciona, los documentos que estaban abiertos la última vez que se cerró esta solución se abren automáticamente al abrir la solución.

Volver a abrir determinados tipos de archivos o diseñadores puede retrasar la carga de la solución. Desactive esta opción para [mejorar el rendimiento de la carga de la solución](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) si no quiere restaurar el contexto previo de la solución.

::: moniker range=">=vs-2019"

## <a name="restore-solution-explorer-project-hierarchy-state-on-solution-load"></a>Restaurar estado de jerarquía de proyecto del Explorador de soluciones en la carga de la solución

Cuando se selecciona, restaura el estado de los nodos en el Explorador de soluciones teniendo en cuenta si estaban expandidos o contraídos la última vez que se abrió la solución. Anule la selección de esta opción para disminuir el tiempo de carga de la solución en el caso de soluciones de gran tamaño.

> [!TIP]
> Si deshabilita esta opción, una manera sencilla de desplazarse al documento activo en el Explorador de soluciones consiste en seleccionar **Sincronizar con el documento activo** en la barra de herramientas del **Explorador de soluciones**.
>
> ![Sincronizar con el documento activo en el Explorador de soluciones](media/sync-active-document.png)

## <a name="open-sdk-style-project-files-with-double-click-or-the-enter-key"></a>Abrir archivos de proyecto de estilo SDK con doble clic o la tecla ENTRAR

Cuando se selecciona esta opción y se hace doble clic en un nodo de proyecto de estilo SDK en el Explorador de soluciones, o bien se selecciona y se presiona **ENTRAR**, el archivo de proyecto (por ejemplo, \*.csproj) se abre como XML en el editor. Cuando se anula la selección, al hacer doble clic en un nodo de proyecto de estilo SDK en el Explorador de soluciones o al seleccionarlo y presionar **ENTRAR**, solo se expande o se contrae el nodo.

Si no tiene esta opción seleccionada y quiere editar un archivo de proyecto de estilo SDK, haga clic con el botón derecho en el nodo del proyecto en el Explorador de soluciones y seleccione **Editar archivo de proyecto**. En el caso de otros tipos de proyecto, primero debe descargar el proyecto para poder editarlo en Visual Studio.

> [!TIP]
> Un *proyecto de estilo SDK*, o [SDK de proyecto](../../msbuild/how-to-use-project-sdk.md), tiene un formato de archivo de proyecto más nuevo y sencillo que se introdujo con MSBuild 15.0. Un proyecto de estilo SDK contiene un atributo `Sdk` en el elemento `Project`, por ejemplo, `<Project Sdk="Microsoft.NET.Sdk">`. Visual Studio crea un proyecto de estilo SDK cuando se crea un proyecto de .NET Core a partir de una de las plantillas de Visual Studio, por ejemplo.

::: moniker-end

## <a name="see-also"></a>Vea también

- [Cuadro de diálogo Opciones: Proyectos y soluciones \> Ubicaciones](projects-solutions-locations-options.md)
- [Cuadro de diálogo Opciones, Proyectos y soluciones, Compilar y ejecutar](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Cuadro de diálogo Opciones, Proyectos y soluciones, Proyectos web](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
