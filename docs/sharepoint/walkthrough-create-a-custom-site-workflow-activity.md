---
title: "Tutorial: Crear una actividad de flujo de trabajo personalizada | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "actividades del flujo de trabajo personalizadas [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, actividades del flujo de trabajo personalizadas"
  - "desarrollo de SharePoint en Visual Studio, Flujos de trabajo del sitio"
  - "flujos de trabajo del sitio [desarrollo de SharePoint en Visual Studio]"
  - "actividades del flujo de trabajo [desarrollo de SharePoint en Visual Studio]"
ms.assetid: 8219a779-c27b-4186-92c9-5bda03328aa9
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Tutorial: Crear una actividad de flujo de trabajo personalizada
  En este tutorial se muestra cómo crear una actividad personalizada para un flujo de trabajo de nivel de sitio con [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. \(Los flujos de trabajo de nivel de sitio se aplican al sitio entero, no solo a una lista del sitio.\) La actividad personalizada crea una lista Anuncios auxiliar y copia el contenido de la lista Anuncios en ella.  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Crear un flujo de trabajo de nivel de sitio.  
  
-   Crear una actividad de flujo de trabajo personalizada.  
  
-   Crear y eliminar una lista de SharePoint.  
  
-   Copiar los elementos de una lista en otra.  
  
-   Mostrar una lista en la barra de inicio rápido.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Crear un proyecto de actividad personalizada de flujo de trabajo del sitio  
 Primero, cree un proyecto para hospedar y probar la actividad de flujo de trabajo personalizada.  
  
#### Para crear un proyecto de actividad personalizada de flujo de trabajo del sitio  
  
1.  En la barra de menú, elija **archivo**, **new**, **Project** para mostrar el cuadro de diálogo de **Nuevo proyecto** .  
  
2.  Expanda el nodo de **sharepoint** en **Visual C\#** o **Visual Basic**y, a continuación el nodo de **2010** .  
  
3.  En el panel de **Plantillas** , elija la plantilla de **SharePoint 2010 Project** .  
  
4.  En el cuadro de **Name** , entre en AnnouncementBackup, y elija el botón de **Aceptar** .  
  
     Aparece el **Asistente para personalización de SharePoint**.  
  
5.  En la página de **Especifique el sitio y el nivel de seguridad de la depuración** , elija el botón de opción de **Implementar como solución de granja de servidores** , y elija el botón de **Finalizar** para aceptar el sitio de nivel de confianza y predeterminado.  
  
     Este paso también establece el nivel de confianza para la solución como una solución de granja de servidores, la única opción disponible para los proyectos de flujo de trabajo.  
  
6.  En **Explorador de soluciones**, elija el nodo de proyecto y, a continuación, en la barra de menús, elija **Project**, **Agregar nuevo elemento**.  
  
7.  En **Visual C\#** o **Visual Basic**, expanda el nodo de **sharepoint** y, a continuación el nodo de **2010** .  
  
8.  En el panel de **Plantillas** , elija la plantilla de **Flujo de trabajo secuencial \(solución de granja de servidores únicamente\)** , y elija el botón de **Add** .  
  
     Aparece el **Asistente para personalización de SharePoint**.  
  
9. En la página de **Especifique el nombre del flujo de trabajo de depuración** , acepte el nombre predeterminado \(AnnouncementBackup \- Workflow1\).  Cambie la plantilla de flujo de trabajo a un tipo **Flujo de trabajo de sitio**, y elija el botón de **siguiente** .  
  
10. Elija el botón de **Finalizar** para aceptar los valores predeterminados restantes.  
  
## Agregar una clase de actividad de flujo de trabajo personalizada  
 A continuación, agregue una clase al proyecto para el código de la actividad de flujo de trabajo personalizada.  
  
#### Para agregar una clase de actividad de flujo de trabajo personalizada  
  
1.  En la barra de menú, elija **Project**, **Agregar nuevo elemento** para mostrar el cuadro de diálogo de **Agregar nuevo elemento** .  
  
2.  En la vista de árbol de **Plantillas instaladas** , elija el nodo de **code** , y elija la plantilla de **Class** en la lista de plantillas de elemento de proyecto.  Utilice el nombre predeterminado Class1.  Elija el botón de **Agregar**.  
  
3.  Reemplace el código de Class1 por el código siguiente:  
  
     [!code-csharp[SP_AnnBackup#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_annbackup/cs/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_annbackup/vb/class1.vb#1)]  
  
4.  Guarde el proyecto y, a continuación, en la barra de menú, elija **Compilación**, **Compilar solución**.  
  
     Class1 aparece como una acción personalizada en **Cuadro de herramientas** en la pestaña de **Componentes de AnnouncementBackup** .  
  
## Agregar la actividad personalizada al flujo de trabajo del sitio  
 A continuación agregue una actividad al flujo de trabajo para que contenga el código personalizado.  
  
#### Para agregar la actividad personalizada al flujo de trabajo de sitio  
  
1.  Abra el Workflow1 en el diseñador de flujos de trabajo en la Vista de diseño.  
  
2.  Arrastre Class1 de **Cuadro de herramientas** para que aparezca bajo la actividad de `onWorkflowActivated1` , o abra el menú contextual para Class1, elija **copiar**, abra el menú contextual para la línea bajo la actividad de `onWorkflowActivated1` , y elija **Pegar**.  
  
3.  Guarde el proyecto.  
  
## Probar la actividad personalizada de flujo de trabajo de sitio  
 A continuación, ejecute el proyecto e inicie el flujo de trabajo del sitio.  La actividad personalizada crea una lista Anuncios auxiliar y copia el contenido de la lista Anuncios en ella.  El código también comprueba si ya existe una lista auxiliar antes de crear otra.  Si existe una, se elimina.  El código también agrega un vínculo a la nueva lista en la barra de inicio rápido del sitio de SharePoint.  
  
#### Para probar la actividad personalizada de flujo de trabajo del sitio  
  
1.  Elija la tecla F5 para ejecutar el proyecto e implementarlo en SharePoint.  
  
2.  En la barra de inicio rápido, elija el vínculo de **Listas** para mostrar todas las listas disponibles en el sitio de SharePoint.  Observe que hay una única lista para los anuncios denominada **Anuncios**.  
  
3.  En la parte superior de la página Web de SharePoint, elija el vínculo de **Flujos de trabajo de sitio** .  
  
4.  Bajo la sección iniciar un de nuevo flujo de trabajo, elija el vínculo de **AnnouncementBackup – Workflow1** .  Esto inicia el flujo de trabajo del sitio y ejecuta el código de la acción personalizada.  
  
5.  En la barra de inicio rápido, elija el vínculo de **Avisos auxiliares** .  Observe que todos los anuncios que contiene la lista **Anuncios** se han copiado en esta nueva lista.  
  
## Vea también  
 [Cómo: Crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  