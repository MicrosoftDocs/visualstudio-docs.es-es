---
title: 'Tutorial: Implementación de una definición de lista de tareas de proyecto | Documentos de Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7ea7063ce432841e812312b7c7c36721a7d2d099
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62784236"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>Tutorial: Implementar una definición de lista de tareas de proyecto

En este tutorial se muestra cómo usar [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] para crear, personalizar, depurar e implementar una lista de SharePoint para realizar un seguimiento de las tareas del proyecto.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos

- Ediciones compatibles de Microsoft Windows y SharePoint.

- Visual Studio 2017 o servicios de Azure DevOps.

## <a name="create-a-sharepoint-list"></a>Crear una lista de SharePoint

Cree un proyecto de la lista de SharePoint y asociar a la definición de lista de tareas.

1. Abra el **nuevo proyecto** cuadro de diálogo, expanda el **SharePoint** nodo y, a continuación, elija el **2010** nodo.

2. En el **plantillas** panel, elija el **proyecto de SharePoint 2010** plantilla, el nombre del proyecto **ProjectTaskList**y, a continuación, elija el **Aceptar**botón.

     El **Asistente de personalización de SharePoint** aparece.

3. Especifique el sitio de SharePoint local que usa para la depuración, elija el **implementar como solución de granja de servidores** botón de opción y, a continuación, elija el **finalizar** botón.

4. Abra el menú contextual para el proyecto y, a continuación, elija **agregar** > **nuevo elemento**.

5. En el **plantillas** panel, elija el **lista** plantilla y, a continuación, elija el **agregar** botón.

     El **Asistente de personalización de SharePoint** aparece.

6. En el **qué nombre desea mostrar para la lista?** , escriba **lista de tareas de proyecto**.

7. Elija la **crear una lista no se puede personalizar en función de un tipo de lista existente de** botón de opción y, a continuación, en su lista, elija **tareas**y, a continuación, elija el **finalizar** botón.

     La lista, la característica y paquete aparecen en **el Explorador de soluciones**.

## <a name="add-an-event-receiver"></a>Agregar un receptor de eventos

En la lista de tareas, puede agregar un receptor de eventos que establece automáticamente el vencimiento Fecha y la descripción de la tarea. El siguiente procedimiento agrega un controlador de eventos simple a la instancia de lista como un receptor de eventos.

1. Abra el menú contextual del nodo de proyecto, elija **agregar**y, a continuación, elija **nuevo elemento**.

2. En la lista de plantillas de SharePoint, elija el **receptor de eventos** plantilla y, a continuación, asígnele el nombre **ReceptorEventosListaTareasProyecto**.

     El **Asistente de personalización de SharePoint** aparece.

3. En el **elegir configuración del receptor de eventos** página, elija **eventos del elemento de lista** como el tipo de receptor de eventos en el **qué tipo de receptor de eventos desea** lista.

4. En el **qué elemento debe ser el origen del evento** elija **tareas**.

5. En la lista de eventos para controlar, active la casilla de verificación junto a **se agregó un elemento**y, a continuación, elija el **finalizar** botón.

     Un nuevo nodo de receptor de eventos se agrega al proyecto con un archivo de código que se denomina **ReceptorEventosListaTareasProyecto**.

6. Agregue código a la `ItemAdded` método en el **ReceptorEventosListaTareasProyecto** archivo de código. Cada vez que se agrega una nueva tarea, se agrega un valor predeterminado due date y una descripción para la tarea. El valor predeterminado de vencimiento fecha es el 1 de julio de 2009.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>Personalizar la característica de lista de tareas de proyecto

Cuando se crea una solución de SharePoint, Visual Studio crea automáticamente las características para el valor predeterminado en elementos de proyecto. Puede personalizar la configuración de lista de tareas de proyecto para el sitio de SharePoint mediante el Diseñador de características.

1. En **el Explorador de soluciones**, expanda **características**.

2. Abra el menú contextual para **Feature1**y, a continuación, elija **Diseñador de vistas**.

3. En el **título** , escriba **característica lista de tareas de proyecto**.

4. En el **ámbito** elija **Web**.

5. En el **propiedades** ventana, escriba **1.0.0.0** como el valor de la **versión** propiedad.

## <a name="customize-the-project-task-list-package"></a>Personalizar el paquete de lista de tareas de proyecto

Al crear un proyecto de SharePoint, Visual Studio agrega automáticamente las características que contienen los elementos de proyecto predeterminada para el paquete. Puede personalizar la configuración de lista de tareas de proyecto para el sitio de SharePoint mediante el Diseñador de paquetes.

1. En **SolutionExplorer**, abra el menú contextual para **paquete**y, a continuación, elija **Diseñador de vistas**.

2. En el **nombre** , escriba **PaqueteListaTareasProyecto**.

3. Seleccione el **restablecer el servidor de Web** casilla de verificación.

## <a name="build-and-test-the-project-task-list"></a>Compilar y probar la lista de tareas de proyecto

Cuando se ejecuta el proyecto, se abre el sitio de SharePoint. Sin embargo, debe navegar de forma manual a la ubicación de la lista de tareas.

1. Elija la **F5** clave para compilar e implementar la lista de tareas del proyecto.

     Se abre el sitio de SharePoint.

2. Elija la **inicio** ficha.

3. En la barra lateral izquierda, elija el **lista de tareas de proyecto** vínculo.

     Aparece la página de lista de tareas del proyecto.

4. En el **herramientas de lista** ficha, elija la **elementos** ficha.

5. En el **elementos** grupo, elija la **nuevo elemento** botón.

6. En el **título** texto, escriba **Task1**.

7. Elija la **guardar** botón.

     Después de actualizar el sitio, el **Task1** tareas aparece con una fecha de vencimiento de 1/7/2009.

8. Elija **Task1**.

     Aparece la vista detallada de la tarea y la descripción se muestra "Es una tarea crítica".

## <a name="deploy-the-project-task-list"></a>Implementación de la lista de tareas de proyecto

Después de compilar y probar la lista de tareas de proyecto, puede implementarla en el *sistema local* o un *sistema remoto*. El sistema local es el mismo equipo en el que ha desarrollado la solución, mientras que un sistema remoto es un equipo diferente.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Para implementar la lista de tareas de proyecto en el sistema local

En la barra de menús de Visual Studio, elija **compilar** > **implementar solución**.

Visual Studio se recicla el grupo de aplicaciones de IIS, retira las versiones existentes de la solución, copia el paquete de solución (*.wsp*) del archivo a SharePoint y, a continuación, activa sus características. Ahora puede usar la solución en SharePoint. Para obtener más información acerca de los pasos de configuración de implementación, consulte [Cómo: Editar una configuración de implementación de SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Para implementar la lista de tareas de proyecto en un sistema remoto

1. En la barra de menús de Visual Studio, elija **compilar** > **publicar**.

2. En el **publicar** diálogo cuadro, elija el **publicar en el sistema de archivos** botón de opción.

     Puede cambiar la ubicación de destino en el **publicar** cuadro de diálogo eligiendo el botón de puntos suspensivos ![icono de puntos suspensivos](../sharepoint/media/ellipsisicon.gif "icono de puntos suspensivos") y, a continuación, vaya a otra ubicación.

3. Elija la **publicar** botón.

     Un *.wsp* archivo se crea para la solución.

4. Copia el *.wsp* archivo en el sistema remoto de SharePoint.

5. Usar PowerShell `Add-SPUserSolution` comando para instalar el paquete en la instalación de SharePoint remota. (Para las soluciones de granja de servidores, use el `Add-SPSolution` comando.)

     Por ejemplo: `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. Usar PowerShell `Install-SPUserSolution` comando para implementar la solución. (Para las soluciones de granja de servidores, use el `Install-SPSolution` comando.)

     Por ejemplo: `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Para obtener más información sobre la implementación remota, vea [soluciones utilizando](http://go.microsoft.com/fwlink/?LinkId=217680) y [adición y la implementación de soluciones con PowerShell en SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=217682).

## <a name="next-steps"></a>Pasos siguientes

Puede obtener más información sobre cómo personalizar e implementar soluciones de SharePoint en los temas siguientes:

- [Tutorial: Crear una columna de sitio, el tipo de contenido y la lista de SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Cómo: Crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)

- [Windows PowerShell para SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)

## <a name="see-also"></a>Vea también
[Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
