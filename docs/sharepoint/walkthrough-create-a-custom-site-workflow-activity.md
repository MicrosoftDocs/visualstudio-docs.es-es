---
title: 'Tutorial: crear una actividad de flujo de trabajo de sitio personalizada | Microsoft Docs'
description: En este tutorial, vea cómo crear una actividad personalizada para un flujo de trabajo de SharePoint de nivel de sitio mediante Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29a3cd6fe37ec824a3db3a2c83aad7434d0018cb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218053"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Tutorial: Creación de una actividad de flujo de trabajo de sitio personalizada
  En este tutorial se muestra cómo crear una actividad personalizada para un flujo de trabajo de nivel de sitio mediante [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . (Los flujos de trabajo de nivel de sitio se aplican a todo el sitio, no solo a una lista en el sitio). La actividad personalizada crea una lista de anuncios de copia de seguridad y, a continuación, copia en ella el contenido de la lista de anuncios.

 En este tutorial se muestran las siguientes tareas:

- Crear un flujo de trabajo de nivel de sitio.

- Crear una actividad de flujo de trabajo personalizada.

- Crear y eliminar una lista de SharePoint.

- Copiar elementos de una lista a otra.

- Mostrar una lista en la barra de inicio rápido.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint.

- Visual Studio.

## <a name="create-a-site-workflow-custom-activity-project"></a>Crear un proyecto de actividad personalizada de flujo de trabajo de sitio
 En primer lugar, cree un proyecto para que contenga y pruebe la actividad de flujo de trabajo personalizada.

#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Para crear un proyecto de actividad personalizada de flujo de trabajo de sitio

1. En la barra de menús, elija **archivo**  >  **nuevo**  >  **proyecto** para mostrar el cuadro de diálogo **nuevo proyecto** .

2. Expanda el nodo **SharePoint** en **Visual C#** o **Visual Basic** y, a continuación, elija el nodo **2010** .

3. En el panel **plantillas** , elija la plantilla de **proyecto de SharePoint 2010** .

4. En el cuadro **nombre** , escriba **AnnouncementBackup** y elija el botón **Aceptar** .

     Aparece el **Asistente para la personalización de SharePoint** .

5. En la página **especifique el sitio y el nivel de seguridad de la depuración** , elija el botón de opción **implementar como solución de granja de servidores** y, después, elija el botón **Finalizar** para aceptar el nivel de confianza y el sitio predeterminado.

     Este paso establece el nivel de confianza de la solución como solución de granja, la única opción disponible para los proyectos de flujo de trabajo.

6. En **Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija **proyecto**  >  **Agregar nuevo elemento**.

7. En **Visual C#** o **Visual Basic**, expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

8. En el panel **plantillas** , elija la plantilla **flujo de trabajo secuencial (solo solución de granja de servidores)** y, a continuación, elija el botón **Agregar** .

     Aparece el **Asistente para la personalización de SharePoint** .

9. En la página **especificar el nombre del flujo de trabajo para la depuración** , acepte el nombre predeterminado (AnnouncementBackup-Workflow1). Cambie el tipo de plantilla de flujo de trabajo a **flujo de trabajo de sitio** y elija el botón **siguiente** .

10. Elija el botón **Finalizar** para aceptar la configuración predeterminada restante.

## <a name="add-a-custom-workflow-activity-class"></a>Agregar una clase de actividad de flujo de trabajo personalizada
 A continuación, agregue una clase al proyecto para que contenga el código de la actividad de flujo de trabajo personalizada.

#### <a name="to-add-a-custom-workflow-activity-class"></a>Para agregar una clase de actividad de flujo de trabajo personalizada

1. En la barra de menús, elija **proyecto**  >  **Agregar nuevo elemento** para mostrar el cuadro de diálogo **Agregar nuevo elemento** .

2. En la vista de árbol **plantillas instaladas** , elija el nodo **código** y, a continuación, elija la plantilla **clase** en la lista de plantillas de elementos de proyecto. Use el nombre predeterminado Class1. Elija el botón **Agregar**.

3. Reemplace todo el código en Class1 por lo siguiente:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb" id="Snippet1":::

4. Guarde el proyecto y, a continuación, en la barra de menús, elija **compilar** compilar  >  **solución**.

     Class1 aparece como una acción personalizada en el **cuadro de herramientas** de la pestaña **componentes de AnnouncementBackup** .

## <a name="add-the-custom-activity-to-the-site-workflow"></a>Agregar la actividad personalizada al flujo de trabajo del sitio
 A continuación, agregue una actividad al flujo de trabajo para que contenga el código personalizado.

#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Para agregar una actividad personalizada al flujo de trabajo del sitio

1. Abra Workflow1 en el diseñador de flujo de trabajo en la vista de diseño.

2. Arrastre Class1 desde el **cuadro de herramientas** para que aparezca en la `onWorkflowActivated1` actividad, o abra el menú contextual de Class1, elija **copiar**, abra el menú contextual de la línea en la `onWorkflowActivated1` actividad y, a continuación, elija **pegar**.

3. Guarde el proyecto.

## <a name="test-the-site-workflow-custom-activity"></a>Prueba de la actividad personalizada del flujo de trabajo del sitio
 A continuación, ejecute el proyecto e inicie el flujo de trabajo del sitio. La actividad personalizada crea una lista de anuncios de copias de seguridad y copia en ella el contenido de la lista de anuncios actual. El código también comprueba si ya existe una lista de copia de seguridad antes de crear una. Si ya existe una lista de copia de seguridad, se elimina. El código también agrega un vínculo a la nueva lista en la barra de inicio rápido del sitio de SharePoint.

#### <a name="to-test-the-site-workflow-custom-activity"></a>Para probar la actividad personalizada del flujo de trabajo del sitio

1. Elija la tecla **F5** para ejecutar el proyecto e implementarlo en SharePoint.

2. En la barra de inicio rápido, elija el vínculo **listas** para mostrar todas las listas que están disponibles en el sitio de SharePoint. Observe que solo hay una lista para los anuncios denominados **anuncios**.

3. En la parte superior de la Página Web de SharePoint, elija el vínculo **flujos de trabajo del sitio** .

4. En la sección iniciar un nuevo flujo de trabajo, elija el vínculo **AnnouncementBackup-Workflow1** . Esto inicia el flujo de trabajo del sitio y ejecuta el código en la acción personalizada.

5. En la barra de inicio rápido, elija el vínculo de **copia de seguridad de anuncios** . Observe que todos los anuncios contenidos en la lista de **anuncios** se han copiado en esta nueva lista.

## <a name="see-also"></a>Consulte también
- [Cómo: para crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
