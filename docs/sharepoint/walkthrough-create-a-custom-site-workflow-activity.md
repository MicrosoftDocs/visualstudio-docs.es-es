---
title: 'Tutorial: Crear una actividad de flujo de trabajo de sitio personalizado | Microsoft Docs'
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
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b366db32a4caadf0f454f893d8f98e2d288f2390
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42627362"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Tutorial: Crear una actividad de flujo de trabajo de sitio personalizado
  En este tutorial se muestra cómo crear una actividad personalizada para un flujo de trabajo de nivel de sitio mediante [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. (Los flujos de trabajo de nivel de sitio se aplican a todo el sitio, no solo en una lista en el sitio). La actividad personalizada crea una lista de anuncios de copia de seguridad y, a continuación, copia el contenido de la lista de anuncios en él.  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Creación de un flujo de trabajo de nivel de sitio.  
  
-   Creación de una actividad de flujo de trabajo personalizado.  
  
-   Creación y eliminación de una lista de SharePoint.  
  
-   Copiar elementos de una lista a otra.  
  
-   Mostrar una lista en la barra Inicio rápido.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint.
  
-   Visual Studio.  
  
## <a name="create-a-site-workflow-custom-activity-project"></a>Crear un proyecto de actividad personalizada de flujo de trabajo de sitio
 En primer lugar, cree un proyecto para hospedar y probar la actividad de flujo de trabajo personalizado.  
  
#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Para crear un proyecto de actividad personalizada de flujo de trabajo de sitio  
  
1.  En la barra de menús, elija **archivo** > **New** > **proyecto** para mostrar el **nuevo proyecto** cuadro de diálogo.  
  
2.  Expanda el **SharePoint** nodo bajo **Visual C#** o **Visual Basic**y, a continuación, elija el **2010** nodo.  
  
3.  En el **plantillas** panel, elija el **proyecto de SharePoint 2010** plantilla.  
  
4.  En el **nombre** , escriba **AnnouncementBackup**y, a continuación, elija el **Aceptar** botón.  
  
     El **Asistente de personalización de SharePoint** aparece.  
  
5.  En el **especificar el nivel de sitio y de seguridad para la depuración** página, elija el **implementar como solución de granja de servidores** botón de opción y, a continuación, elija el **finalizar** botón para aceptar el sitio predeterminado y de nivel de confianza.  
  
     Este paso establece el nivel de confianza para la solución como solución de granja, la única opción disponible para los proyectos de flujo de trabajo.  
  
6.  En **el Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija **proyecto** > **Agregar nuevo elemento**.  
  
7.  Bajo **Visual C#** o **Visual Basic**, expanda el **SharePoint** nodo y, a continuación, elija el **2010** nodo.  
  
8.  En el **plantillas** panel, elija el **flujo de trabajo secuencial (solución de granja de servidores únicamente)** plantilla y, a continuación, elija el **agregar** botón.  
  
     El **Asistente de personalización de SharePoint** aparece.  
  
9. En el **especificar el nombre de flujo de trabajo de depuración** , acepte el nombre predeterminado (AnnouncementBackup - Workflow1). Cambie el tipo de plantilla de flujo de trabajo a **flujo de trabajo del sitio**y, a continuación, elija el **siguiente** botón.  
  
10. Elija la **finalizar** botón para aceptar los valores predeterminados restantes.  
  
## <a name="add-a-custom-workflow-activity-class"></a>Agregue una clase de actividad de flujo de trabajo personalizado
 A continuación, agregue una clase al proyecto para incluir el código de la actividad de flujo de trabajo personalizado.  
  
#### <a name="to-add-a-custom-workflow-activity-class"></a>Para agregar una clase de actividad de flujo de trabajo personalizado  
  
1.  En la barra de menús, elija **proyecto** > **Agregar nuevo elemento** para mostrar el **Agregar nuevo elemento** cuadro de diálogo.  
  
2.  En el **plantillas instaladas** vista de árbol, elija el **código** nodo y, a continuación, elija el **clase** plantilla en la lista de plantillas de elemento de proyecto. Utilice el nombre predeterminado Class1. Elija el botón de **Agregar** .  
  
3.  Reemplace todo el código de Class1 con lo siguiente:  
  
     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]  
  
4.  Guarde el proyecto y, a continuación, en la barra de menús, elija **compilar** > **compilar solución**.  
  
     Class1 aparece como una acción personalizada en el **cuadro de herramientas** en el **AnnouncementBackup componentes** ficha.  
  
## <a name="add-the-custom-activity-to-the-site-workflow"></a>Agregar la actividad personalizada al flujo de trabajo de sitio
 A continuación, agregue una actividad al flujo de trabajo para que contenga el código personalizado.  
  
#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Para agregar una actividad personalizada al flujo de trabajo de sitio
  
1.  Abra Workflow1 en el Diseñador de flujo de trabajo en la vista Diseño.  
  
2.  Arrastre Class1 desde el **cuadro de herramientas** para que aparezca bajo el `onWorkflowActivated1` actividad, o abra el menú contextual para Class1, elija **copia**, abra el menú contextual de la línea bajo el `onWorkflowActivated1` actividad y, a continuación, elija **pegar**.  
  
3.  Guarde el proyecto.  
  
## <a name="test-the-site-workflow-custom-activity"></a>Probar la actividad personalizada de flujo de trabajo de sitio
 A continuación, ejecute el proyecto e iniciar el flujo de trabajo del sitio. La actividad personalizada crea una lista de anuncios de copia de seguridad y copia el contenido de la lista actual de anuncios en él. El código también comprueba si ya existe una lista de copia de seguridad antes de crear uno. Si ya existe una lista de copia de seguridad, se elimina. El código también agrega un vínculo a la nueva lista en la barra de inicio rápido del sitio de SharePoint.  
  
#### <a name="to-test-the-site-workflow-custom-activity"></a>Para probar la actividad personalizada de flujo de trabajo de sitio  
  
1.  Elija la **F5** clave para ejecutar el proyecto e implementarlo en SharePoint.  
  
2.  En la barra Inicio rápido, elija el **enumera** vínculo para mostrar todas las listas que están disponibles en el sitio de SharePoint. Observe que hay solo una lista de anuncios denominado **anuncios**.  
  
3.  En la parte superior de la página Web de SharePoint, elija el **flujos de trabajo sitio** vínculo.  
  
4.  En el inicio de una sección del nuevo flujo de trabajo, elija la **AnnouncementBackup - Workflow1** vínculo. Esto inicia el flujo de trabajo del sitio y ejecuta el código de la acción personalizada.  
  
5.  En la barra Inicio rápido, elija el **copia de seguridad de los anuncios** vínculo. Tenga en cuenta que todos los anuncios que se encuentran en el **anuncios** lista se han copiado a esta lista nueva.  
  
## <a name="see-also"></a>Vea también
 [Cómo: crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)   
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
