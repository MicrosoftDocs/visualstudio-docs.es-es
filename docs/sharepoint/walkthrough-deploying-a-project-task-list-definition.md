---
title: 'Tutorial: Implementar una definición de lista de tareas de proyecto | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fb7f8445cf43209ffed47140b1d8d204c68eaa4f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-deploying-a-project-task-list-definition"></a>Tutorial: Implementar una definición de lista de tareas de proyecto

En este tutorial se muestra cómo usar [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] para crear, personalizar, depurar e implementar una lista de SharePoint para realizar el seguimiento de tareas del proyecto.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos

- Ediciones compatibles de Microsoft Windows y SharePoint. Para obtener más información, consulte [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

- 2017 de Visual Studio o una edición de Visual Studio Application Lifecycle Management (ALM).

## <a name="CreatingListDef"></a> Crear una lista de SharePoint

Cree un proyecto de la lista de SharePoint y asociar a la definición de lista de tareas.

1. Abra la **nuevo proyecto** cuadro de diálogo, expanda el **SharePoint** nodo y, a continuación, elija la **2010** nodo.

2. En el **plantillas** panel, elija la **proyecto de SharePoint 2010** plantilla, el nombre del proyecto **ProjectTaskList**y, a continuación, elija el **Aceptar**botón.

     El **Asistente para personalización de SharePoint** aparece.

3. Especifique el sitio de SharePoint local que usa para la depuración, elija el **implementar como solución de granja de servidores** botón de opción y, a continuación, elija la **finalizar** botón.

4. Abra el menú contextual para el proyecto y, a continuación, elija **agregar**, **nuevo elemento**.

5. En el **plantillas** panel, elija la **lista** plantilla y, a continuación, elija la **agregar** botón.

     El **Asistente para personalización de SharePoint** aparece.

6. En el **¿qué nombre desea mostrar para la lista?** cuadro, escriba **lista de tareas de proyecto**.

7. Elija la **crear una lista no se puede personalizar en función de un tipo de lista existente de** botón de opción y, a continuación, en la lista, elija **tareas**y, a continuación, elija la **finalizar** botón.

     La lista, la característica y el paquete aparecen en **el Explorador de soluciones**.

## <a name="AddEventRcvr"></a> Agregar un receptor de eventos

En la lista de tareas, puede agregar un receptor de eventos que establece automáticamente el vencimiento Fecha y una descripción de la tarea. El siguiente procedimiento agrega un controlador de eventos simples a la instancia de lista como un receptor de eventos.

1. Abra el menú contextual del nodo de proyecto, elija **agregar**y, a continuación, elija **nuevo elemento**.

2. En la lista de plantillas de SharePoint, elija el **receptor de eventos** plantilla y, a continuación, asígnele el nombre **ReceptorEventosListaTareasProyecto**.

     El **Asistente para personalización de SharePoint** aparece.

3. En el **elegir configuración de receptor de eventos** página, elija **eventos de elementos de lista** como el tipo de receptor de eventos en el **¿qué tipo de receptor de eventos desea** lista.

4. En el **qué elemento debe ser el origen del evento** elija **tareas**.

5. En la lista de eventos para controlar, active la casilla de verificación junto a **se agregó un elemento**y, a continuación, elija la **finalizar** botón.

     Un nuevo nodo de receptor de eventos se agrega al proyecto con un archivo de código que se denomina **ReceptorEventosListaTareasProyecto**.

6. Agregue código a la `ItemAdded` método en el **ReceptorEventosListaTareasProyecto** archivo de código. Cada vez que se ha agregado una nueva tarea, se agrega un valor predeterminado fecha de vencimiento y una descripción para la tarea. El valor predeterminado de vencimiento fecha es el 1 de julio de 2009.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="CustomizeFeature"></a> Personalizar la característica de lista de tareas de proyecto

Cuando se crea una solución de SharePoint, Visual Studio crea automáticamente características de la predeterminada de elementos de proyecto. Puede personalizar la configuración de lista de tareas de proyecto para el sitio de SharePoint mediante el Diseñador de características.

1. En **el Explorador de soluciones**, expanda **características**.

2. Abra el menú contextual para **Feature1**y, a continuación, elija **Diseñador de vistas**.

3. En el **título** cuadro, escriba **característica de lista de tareas de proyecto**.

4. En el **ámbito** elija **Web**.

5. En el **propiedades** ventana, escriba **1.0.0.0** como el valor de la **versión** propiedad.

## <a name="CustomizePackage"></a> Personalizar el paquete de lista de tareas de proyecto

Cuando crea un proyecto de SharePoint, Visual Studio agrega automáticamente las características que contienen los elementos de proyecto predeterminados para el paquete. Puede personalizar la configuración de lista de tareas de proyecto para el sitio de SharePoint mediante el Diseñador de paquetes.

1. En **SolutionExplorer**, abra el menú contextual para **paquete**y, a continuación, elija **Diseñador de vistas**.

2. En el **nombre** cuadro, escriba **PaqueteListaTareasProyecto**.

3. Seleccione el **restablecer el servidor de Web** casilla de verificación.

## <a name="BuildTest"></a> Compilar y probar la lista de tareas de proyecto

Cuando se ejecuta el proyecto, se abre el sitio de SharePoint. Sin embargo, debe navegar manualmente a la ubicación de la lista de tareas.

1. Presione la tecla F5 para compilar e implementar su lista de tareas de proyecto.

     Se abre el sitio de SharePoint.

2. Elija la **inicio** ficha.

3. En la barra lateral izquierda, elija el **lista de tareas de proyecto** vínculo.

     Aparecerá la página de lista de tareas de proyecto.

4. En el **herramientas de lista** ficha, elija la **elementos** ficha.

5. En el **elementos** grupo, elija la **nuevo elemento** botón.

6. En el **título** texto cuadro, escriba **Tarea1**.

7. Elija la **guardar** botón.

     Después de actualizar el sitio, el **Tarea1** tareas aparición con una fecha de vencimiento de 1/7/2009.

8. Elija **Tarea1**.

     Aparece la vista detallada de la tarea y la descripción muestra "Es una tarea crítica".

## <a name="Deploy"></a> Implementación de la lista de tareas de proyecto

Después de compilar y probar la lista de tareas de proyecto, puede implementarlo en el *sistema local* o un *sistema remoto*. El sistema local es el mismo equipo en el que se ha desarrollado la solución, mientras que un sistema remoto es un equipo diferente.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Para implementar la lista de tareas de proyecto en el sistema local

En la barra de menús de Visual Studio, elija **generar**, **implementar solución**.

Visual Studio recicla el grupo de aplicaciones de IIS, retira las versiones existentes de la solución, copia el archivo de paquete (.wsp) de la solución en SharePoint y, a continuación, activa sus características. Ahora puede utilizar la solución de SharePoint. Para obtener más información acerca de los pasos de configuración de implementación, consulte [Cómo: editar una configuración de implementación de SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Para implementar la lista de tareas de proyecto en un sistema remoto

1. En la barra de menús de Visual Studio, elija **generar**, **publicar**.

2. En el **publicar** diálogo cuadro, elija la **publicar en el sistema de archivos** botón de opción.

     Puede cambiar la ubicación de destino en la **publicar** cuadro de diálogo, elija el botón de puntos suspensivos ![icono puntos suspensivos](../sharepoint/media/ellipsisicon.gif "icono puntos suspensivos") y, a continuación, navegar a otra ubicación.

3. Elija la **publicar** botón.

     Se crea un archivo .wsp para la solución.

4. Copie el archivo .wsp en el sistema remoto de SharePoint.

5. Use el PowerShell `Add-SPUserSolution` comando para instalar el paquete en la instalación remota de SharePoint. (Para las soluciones de granja de servidores, use el `Add-SPSolution` comando.)

     Por ejemplo: `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. Use el PowerShell `Install-SPUserSolution` comando para implementar la solución. (Para las soluciones de granja de servidores, use el `Install-SPSolution` comando.)

     Por ejemplo: `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Para obtener más información sobre la implementación remota, vea [utilizando soluciones](http://go.microsoft.com/fwlink/?LinkId=217680) y [agregar o implementar soluciones con PowerShell en SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=217682).

## <a name="next-steps"></a>Pasos siguientes

Puede aprender más acerca de cómo personalizar e implementar soluciones de SharePoint en los temas siguientes:

- [Tutorial: Crear una lista, tipo de contenido y columna de sitio para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Cómo: Crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)

- [Windows PowerShell para SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)

## <a name="see-also"></a>Vea también

[Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)