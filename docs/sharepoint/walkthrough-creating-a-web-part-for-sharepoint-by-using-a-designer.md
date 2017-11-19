---
title: "Tutorial: Crear un elemento Web para SharePoint utilizando un diseñador | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
ms.assetid: 3dd62654-ada2-468f-b7da-eb5704a2ff7a
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 55da85b9740216cefe55911d79dab2c16b035695
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer"></a>Tutorial: Crear un elemento web para SharePoint mediante un diseñador
  Si crear elementos web para un sitio de SharePoint, los usuarios pueden modificar directamente el contenido, la apariencia y el comportamiento de las páginas de ese sitio mediante un explorador. Este tutorial muestra cómo crear un elemento web visualmente mediante SharePoint **elemento Web Visual** plantilla de proyecto en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 El elemento web que creará, muestra una vista de calendario mensual y una casilla para cada lista de calendario en el sitio. Los usuarios pueden especificar listas de calendario que se va a incluir en la vista de calendario mensual activando las casillas de verificación.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un elemento web mediante el uso de la **elemento Web Visual** plantilla de proyecto.  
  
-   Diseñar el elemento web mediante el Diseñador de Visual Web Developer en Visual Studio.  
  
-   Agregar código para controlar los eventos de los controles en el elemento web.  
  
-   Probar el elemento web en SharePoint.  
  
    > [!NOTE]  
    >  El equipo, es posible que muestre nombres o ubicaciones en algunos elementos de la interfaz de usuario de Visual Studio diferentes en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Windows y SharePoint. Vea [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]o posterior.  
  
## <a name="creating-a-web-part-project"></a>Crear un proyecto de elementos web  
 En primer lugar, cree un proyecto de elementos web mediante el uso de la **elemento Web Visual** plantilla de proyecto.  
  
#### <a name="to-create-a-visual-web-part-project"></a>Para crear un proyecto de elemento Web Visual  
  
1.  Iniciar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mediante el uso de la **ejecutar como administrador** opción.  
  
2.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
     Aparecerá el cuadro de diálogo **Nuevo proyecto** .  
  
3.  En el **nuevo proyecto** cuadro de diálogo, bajo **Visual C#** o **Visual Basic**, expanda **Office/SharePoint**y, a continuación, elija la  **Soluciones de SharePoint** categoría.  
  
4.  En la lista de plantillas, elija la **SharePoint 2013 - elemento Web Visual** plantilla y, a continuación, elija la **Aceptar** botón.  
  
     El **Asistente para personalización de SharePoint** aparece. Mediante este asistente, puede especificar el sitio que va a utilizar para depurar el proyecto y el nivel de confianza de la solución.  
  
5.  En el **¿qué es el nivel de confianza para esta solución de SharePoint?** sección, elija el **implementar como solución de granja de servidores** botón de opción.  
  
6.  Elija la **finalizar** botón para aceptar el sitio local predeterminado de SharePoint.  
  
## <a name="designing-the-web-part"></a>Diseñar el elemento web  
 Diseñar el elemento web agregando controles desde el **cuadro de herramientas** a la superficie del Diseñador de Visual Web Developer.  
  
#### <a name="to-design-the-layout-of-the-web-part"></a>Para definir el diseño del elemento web  
  
1.  En el Diseñador de Visual Web Developer, elija la **diseño** ficha para cambiar a la vista Diseño.  
  
2.  En la barra de menús, pulse **Ver**, **Cuadro de herramientas**.  
  
3.  En el **estándar** nodo de la **cuadro de herramientas**, elija la **CheckBoxList** controlar y, a continuación, realice uno de los siguientes pasos:  
  
    -   Abra el menú contextual para el **CheckBoxList** de control, elija **copia**, abra el menú contextual para la primera línea en el diseñador y, a continuación, elija **pegar**.  
  
    -   Arrastre el **CheckBoxList** controlar desde la **cuadro de herramientas**y conectar el control a la primera línea en el diseñador.  
  
4.  Repita el paso anterior, pero mover un botón a la línea siguiente del diseñador.  
  
5.  En el diseñador, elija la **Button1** botón.  
  
6.  En la barra de menús, elija **vista**, **ventana propiedades**.  
  
     El **propiedades** abre la ventana.  
  
7.  En el **texto** propiedad del botón, escriba **actualización**.  
  
## <a name="handling-the-events-of-controls-on-the-web-part"></a>Controlar los eventos de controles en el elemento web  
 Agregue código que permita al usuario agregar calendarios a la vista de calendario principal.  
  
#### <a name="to-handle-events-of-controls-on-the-web-part"></a>Para controlar los eventos de los controles en el elemento web  
  
1.  Siga una de estas series de procedimientos:  
  
    -   En el diseñador, haga doble clic en el **actualización** botón.  
  
    -   En el **propiedades** ventana para el **actualización** botón, elija la **eventos** botón. En el **haga clic en** propiedad, escriba **Button1_Click**y, a continuación, elija la tecla ENTRAR.  
  
     El archivo de código de control de usuario se abre en el Editor de código y la `Button1_Click` aparece el controlador de eventos. Más adelante, agregará código a este controlador de eventos.  
  
2.  Agregue las siguientes instrucciones al principio del archivo de código de control de usuario.  
  
     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
3.  Agregue la siguiente línea de código para el `VisualWebPart1` clase. Este código declara un control de vista de calendario mensual.  
  
     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]  
  
4.  Reemplace el `Page_Load` método de la `VisualWebPart1` clase con el código siguiente. Este código realiza las tareas siguientes:  
  
    -   Agrega una vista de calendario mensual para el control de usuario.  
  
    -   Agrega una casilla de verificación para cada lista de calendario en el sitio.  
  
    -   Especifica una plantilla para cada tipo de elemento que aparece en la vista del calendario.  
  
     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]  
  
5.  Reemplace el `Button1_Click` método de la `VisualWebPart1` clase con el código siguiente. Este código agrega los elementos de cada calendario seleccionado a la vista de calendario principal.  
  
     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]  
  
## <a name="testing-the-web-part"></a>Probar el elemento web  
 Cuando se ejecuta el proyecto, se abre el sitio de SharePoint. El elemento web se agrega automáticamente a la Galería de elementos Web en SharePoint. Para probar este proyecto, se llevarán a cabo las siguientes tareas:  
  
-   Agregar un evento a cada uno de dos listas de calendarios independientes.  
  
-   Agregar el elemento web a una página de elementos web.  
  
-   Especifique las listas que desea incluir en la vista de calendario mensual.  
  
#### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Para agregar eventos a listas de calendario en el sitio  
  
1.  En Visual Studio, presione la tecla F5.  
  
     Se abre el sitio de SharePoint y el [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] barra Inicio rápido aparece en la página.  
  
2.  En la barra Inicio rápido, en **enumera**, elija la **calendario** vínculo.  
  
     El **calendario** aparecerá la página.  
  
     Si no hay ningún vínculo de calendario aparece en la barra Inicio rápido, elija la **contenido del sitio Web** vínculo. Si no aparece la página de contenido del sitio Web un **calendario** item, cree uno.  
  
3.  En la página de calendario, elija un día y, a continuación, elija la **agregar** vínculo en el día seleccionado para agregar un evento.  
  
4.  En el **título** cuadro, escriba **evento en el calendario predeterminado**y, a continuación, elija la **guardar** botón.  
  
5.  Elija la **contenido del sitio Web** vincular y, a continuación, elija la **agregar una aplicación** icono.  
  
6.  En el **crear** página, elija la **calendario** escribe, asignar nombre al calendario y, a continuación, elija la **crear** botón.  
  
7.  Agregar un evento para el nuevo calendario, asigne el nombre del evento **evento en el calendario personalizado**y, a continuación, elija la **guardar** botón.  
  
#### <a name="to-add-the-web-part-to-a-web-part-page"></a>Para agregar el elemento web a una página de elementos web  
  
1.  En el **contenido del sitio Web** página, abra la **páginas del sitio** carpeta.  
  
2.  En la cinta de opciones, elija la **archivos** ficha, abra el **nuevo documento** menú y, a continuación, elija la **página de elementos Web** comando.  
  
3.  En el **nueva página de elementos Web** página, asigne el nombre de la página **SampleWebPartPage.aspx**y, a continuación, elija la **crear** botón.  
  
     Aparece la página de elementos web.  
  
4.  En la zona de la parte superior de la página de elementos web, elija la **insertar** ficha y, a continuación, elija la **elemento Web** botón.  
  
5.  Elija la **personalizado** carpeta, elija la **VisualWebPart1** elemento web y, a continuación, elija la **agregar** botón.  
  
     El elemento web aparece en la página. Los siguientes controles aparecen en el elemento web:  
  
    -   Una vista de calendario mensual.  
  
    -   Un **actualización** botón.  
  
    -   A **calendario** casilla de verificación.  
  
    -   A **calendario personalizado** casilla de verificación.  
  
#### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Para especificar listas para incluir en la vista de calendario mensual  
  
1.  En el elemento web, especifique los calendarios que desea incluir en la vista de calendario mensual y, a continuación, elija la **actualización** botón.  
  
     Eventos de todos los calendarios que especificó aparecen en la vista de calendario mensual.  
  
## <a name="see-also"></a>Vea también  
 [Crear elementos Web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Cómo: crear un elemento Web de SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Cómo: crear un elemento Web de SharePoint utilizando un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Tutorial: Crear un elemento web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)  
  
  