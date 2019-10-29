---
title: 'Tutorial: implementar una definición de Lista de tareas de proyecto | Microsoft Docs'
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
ms.openlocfilehash: 854037d096ceac01969bcb0ec2e074f4cd24a2f3
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983860"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>Tutorial: implementar una definición de lista de tareas de proyecto

En este tutorial se muestra cómo usar [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] para crear, personalizar, depurar e implementar una lista de SharePoint para realizar el seguimiento de las tareas del proyecto.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos

- Ediciones compatibles de Microsoft Windows y SharePoint.

- Visual Studio 2017 o Azure DevOps Services.

## <a name="create-a-sharepoint-list"></a>Crear una lista de SharePoint

Cree un proyecto de lista de SharePoint y asocie la definición de lista con las tareas.

1. Abra el cuadro de diálogo **nuevo proyecto** , expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

2. En el panel **plantillas** , elija la plantilla de **proyecto de SharePoint 2010** , asigne al proyecto el nombre **ProjectTaskList**y, a continuación, elija el botón **Aceptar** .

     Aparece el **Asistente para la personalización de SharePoint** .

3. Especifique el sitio de SharePoint local que se usa para la depuración, elija el botón de opción **implementar como solución de granja de servidores** y elija el botón **Finalizar** .

4. Abra el menú contextual del proyecto y, a continuación, elija **agregar** > **nuevo elemento**.

5. En el panel **plantillas** , elija la plantilla **lista** y, a continuación, elija el botón **Agregar** .

     Aparece el **Asistente para la personalización de SharePoint** .

6. En el cuadro **¿Qué nombre desea mostrar en la lista?** , escriba **proyecto lista de tareas**.

7. Elija el botón **de opción crear una lista que no se puede personalizar según un tipo de lista de** opciones y, a continuación, en la lista, elija **tareas**y, después, elija el botón **Finalizar** .

     La lista, la característica y el paquete aparecen en **Explorador de soluciones**.

## <a name="add-an-event-receiver"></a>Adición de un receptor de eventos

En la lista de tareas, puede Agregar un receptor de eventos que establezca automáticamente la fecha de vencimiento y la descripción de la tarea. El procedimiento siguiente agrega un controlador de eventos simple a la instancia de lista como un receptor de eventos.

1. Abra el menú contextual del nodo del proyecto, elija **Agregar**y, a continuación, elija **nuevo elemento**.

2. En la lista de plantillas de SharePoint, elija la plantilla de **receptor de eventos** y asígnele el nombre **ProjectTaskListEventReceiver**.

     Aparece el **Asistente para la personalización de SharePoint** .

3. En la página **elegir configuración de receptor de eventos** , seleccione eventos de elemento de **lista** como tipo de receptor de eventos en la lista **¿Qué tipo de receptor de eventos desea?** .

4. En la lista **qué elemento debe ser el origen del evento** , elija **tareas**.

5. En la lista de eventos que se van a controlar, active la casilla situada junto a **un elemento que se ha agregado**y, a continuación, elija el botón **Finalizar** .

     Se agrega un nuevo nodo de receptor de eventos al proyecto con un archivo de código denominado **ProjectTaskListEventReceiver**.

6. Agregue código al método `ItemAdded` en el archivo de código **ProjectTaskListEventReceiver** . Cada vez que se agrega una nueva tarea, se agrega una fecha de vencimiento predeterminada y una descripción a la tarea. La fecha de vencimiento predeterminada es el 1 de julio de 2009.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>Personalizar la característica de lista de tareas de proyecto

Al crear una solución de SharePoint, Visual Studio crea automáticamente características para los elementos de proyecto predeterminados. Puede personalizar la configuración de la lista de tareas del proyecto para el sitio de SharePoint mediante el diseñador de características.

1. En **Explorador de soluciones**, expanda **características**.

2. Abra el menú contextual de **Feature1**y, a continuación, elija **Diseñador de vistas**.

3. En el cuadro **título** , escriba **proyecto lista de tareas característica**.

4. En la lista **ámbito** , elija **Web**.

5. En la ventana **propiedades** , escriba **1.0.0.0** como el valor de la propiedad **version** .

## <a name="customize-the-project-task-list-package"></a>Personalizar el paquete de la lista de tareas del proyecto

Al crear un proyecto de SharePoint, Visual Studio agrega automáticamente las características que contienen los elementos de proyecto predeterminados al paquete. Puede personalizar la configuración de la lista de tareas del proyecto para el sitio de SharePoint mediante el diseñador de paquetes.

1. En **SolutionExplorer**, abra el menú contextual del **paquete**y, a continuación, elija **Diseñador de vistas**.

2. En el cuadro **nombre** , escriba **ProjectTaskListPackage**.

3. Active la casilla **restablecer servidor Web** .

## <a name="build-and-test-the-project-task-list"></a>Compilar y probar la lista de tareas del proyecto

Cuando se ejecuta el proyecto, se abre el sitio de SharePoint. Sin embargo, debe desplazarse manualmente a la ubicación de la lista de tareas.

1. Elija la tecla **F5** para compilar e implementar la lista de tareas del proyecto.

     Se abre el sitio de SharePoint.

2. Elija la pestaña **Inicio** .

3. En la barra lateral izquierda, elija el vínculo **proyecto lista de tareas** .

     Aparece la página Lista de tareas del proyecto.

4. En la pestaña **herramientas de lista** , elija la pestaña **elementos** .

5. En el grupo **elementos** , elija el botón **nuevo elemento** .

6. En el cuadro de texto **título** , escriba **Task1**.

7. Elija el botón **Guardar** .

     Una vez actualizado el sitio, aparece la tarea **Task1** con una fecha de vencimiento de 7/1/2009.

8. Elija **Task1**.

     Aparece la vista detallada de la tarea y la descripción muestra "se trata de una tarea crítica".

## <a name="deploy-the-project-task-list"></a>Implementación de la lista de tareas del proyecto

Después de compilar y probar la lista de tareas del proyecto, puede implementarla en el *sistema local* o en un *sistema remoto*. El sistema local es el mismo equipo en el que desarrolló la solución, mientras que un sistema remoto es un equipo diferente.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Para implementar la lista de tareas del proyecto en el sistema local

En la barra de menús de Visual Studio, elija **Compilar** > **implementar solución**.

Visual Studio recicla el grupo de aplicaciones de IIS, retira cualquier versión existente de la solución, copia el archivo de paquete de solución ( *. wsp*) en SharePoint y, a continuación, activa sus características. Ahora puede usar la solución en SharePoint. Para obtener más información sobre los pasos de configuración de implementación, vea [Cómo: editar una configuración de implementación de SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Para implementar la lista de tareas del proyecto en un sistema remoto

1. En la barra de menús de Visual Studio, elija **Compilar** > **publicar**.

2. En el cuadro de diálogo **publicar** , elija el botón de opción **publicar en sistema de archivos** .

     Puede cambiar la ubicación de destino en el cuadro de diálogo **publicar** seleccionando el ![icono de puntos suspensivos](../sharepoint/media/ellipsisicon.gif "Icono Puntos suspensivos") del botón de puntos suspensivos y navegando a otra ubicación.

3. Elija el botón **publicar** .

     Se crea un archivo *. wsp* para la solución.

4. Copie el archivo *. wsp* en el sistema de SharePoint remoto.

5. Use el comando de `Add-SPUserSolution` de PowerShell para instalar el paquete en la instalación remota de SharePoint. (Para las soluciones de granja, use el comando `Add-SPSolution`).

     Por ejemplo: `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. Use el comando de `Install-SPUserSolution` de PowerShell para implementar la solución. (Para las soluciones de granja, use el comando `Install-SPSolution`).

     Por ejemplo: `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Para obtener más información acerca de la implementación remota, vea [usar soluciones](/previous-versions/office/developer/sharepoint-2010/ee534972(v=office.14)) y [Agregar e implementar soluciones con PowerShell en SharePoint 2010](http://www.dotnetmafia.com/blogs/dotnettipoftheday/archive/2009/12/02/adding-and-deploying-solutions-with-powershell-in-sharepoint-2010.aspx).

## <a name="next-steps"></a>Pasos siguientes

Puede obtener más información sobre cómo personalizar e implementar soluciones de SharePoint en los temas siguientes:

- [Tutorial: crear una columna de sitio, un tipo de contenido y una lista para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Cómo: crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)

- [Windows PowerShell para SharePoint Server 2010](/powershell/module/sharepoint-server/&view=sharepoint-ps)

## <a name="see-also"></a>Vea también
[Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
