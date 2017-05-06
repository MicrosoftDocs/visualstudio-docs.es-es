---
title: "Tutorial: Crear un elemento web para SharePoint mediante un dise&#241;ador"
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
  - "elementos web [desarrollo de SharePoint en Visual Studio], crear"
  - "elementos web [desarrollo de SharePoint en Visual Studio], diseñador"
  - "elementos web [desarrollo de SharePoint en Visual Studio], diseñar"
ms.assetid: 3dd62654-ada2-468f-b7da-eb5704a2ff7a
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Tutorial: Crear un elemento web para SharePoint mediante un dise&#241;ador
  Si crea elementos web para un sitio de SharePoint, sus usuarios podrán modificar directamente el contenido, el aspecto y el comportamiento de las páginas de dicho sitio a través de un explorador.  En este tutorial se muestra cómo crear un elemento web utilizando la plantilla de proyecto **Elemento web visual** de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 El elemento web que se crea, muestra una vista de calendario mensual y una casilla para cada lista de calendarios del sitio.  Los usuarios pueden especificar qué listas de calendario incluir en la vista de calendario mensual activando las casillas.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un elemento web utilizando la plantilla de proyecto **Elemento web visual**.  
  
-   Diseñar el elemento web con el diseñador de Visual Web Developer en Visual Studio.  
  
-   Agregar código para controlar eventos de controles en el elemento web.  
  
-   Probar el elemento web en SharePoint.  
  
    > [!NOTE]  
    >  Puede que su equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que tenga y la configuración que esté utilizando determinan estos elementos.  Vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Windows y SharePoint.  Vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] o más.  
  
## Crear un proyecto de elemento web  
 Primero, cree un proyecto de elemento web utilizando la plantilla de proyecto **Elemento web visual**.  
  
#### Para crear un proyecto de elemento web visual  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con la opción **Ejecutar como administrador**.  
  
2.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
     Aparece el cuadro de diálogo **Nuevo proyecto**.  
  
3.  En el cuadro de diálogo de **Nuevo proyecto**, en **Visual C\#** o **Visual Basic**, expanda **Office\/SharePoint** y, a continuación, elija la categoría de **Soluciones de SharePoint**.  
  
4.  En la lista de plantillas, elija la plantilla de **SharePoint 2013 \- Elemento web visual** y elija el botón de **Aceptar**.  
  
     Aparece el **Asistente para personalización de SharePoint**.  Usando este asistente, puede especificar el sitio que se va a usar para depurar el proyecto, así como el nivel de confianza de la solución.  
  
5.  En la sección **¿Cuál es el nivel de confianza de esta solución de SharePoint?**, elija el botón de opción **Implementar como solución de granja de servidores**.  
  
6.  Elija el botón **Finalizar** para aceptar el sitio local predeterminado de SharePoint.  
  
## Diseñar el elemento web  
 Diseñe el elemento web arrastrando los controles del **Cuadro de herramientas** a la superficie del diseñador de Visual Web Developer.  
  
#### Para diseñar el área del elemento web  
  
1.  En el diseñador de Visual Web Developer, elija la pestaña **Diseño** para pasar a la Vista de diseño.  
  
2.  En la barra de menús, elija **Ver**, **Cuadro de herramientas**.  
  
3.  En el nodo de **Estándar** de **Cuadro de herramientas**, elija el control de **CheckBoxList** y después realice uno de los pasos siguientes:  
  
    -   Abra el menú contextual para el control de **CheckBoxList**, elija **Copia**, abra el menú contextual para la primera línea en el diseñador y, a continuación, elija **Pegar**.  
  
    -   Arrastre el control **CheckBoxList** desde **Cuadro de herramientas** y conéctelo a la primera línea del diseñador.  
  
4.  Repita el paso anterior, pero mueva un botón a la línea siguiente del diseñador.  
  
5.  En el diseñador, elija el botón de **Button1**.  
  
6.  En la barra de menús, elija **Ver** y después elija **Ventana Propiedades**.  
  
     Se abre la ventana **Propiedades**.  
  
7.  En la propiedad de **Texto** del botón, escriba update.  
  
## Controlar los eventos de los controles del elemento web  
 Agregue código que permita agregar calendarios a la vista de calendario principal.  
  
#### Para controlar eventos de controles del elemento web  
  
1.  Siga una de estas series de procedimientos:  
  
    -   En el diseñador, haga doble clic en el botón **Update**.  
  
    -   En la ventana **Propiedades** para el botón **Actualizar**, elija el botón **Eventos**.  En la propiedad de **Click**, escriba **Button1\_Click** y elija la tecla Intro.  
  
     El archivo de código del control de usuario se abre en el editor de código y aparece el controlador de eventos `Button1_Click`.  Después, agregará código a este controlador de eventos.  
  
2.  Agregue las siguientes instrucciones a la parte superior del archivo de código del control de usuario.  
  
     [!code-csharp[SP_VisualWebPart#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]
     [!code-vb[SP_VisualWebPart#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]  
  
3.  Agregue la siguiente línea de código a la clase `VisualWebPart1`.  Este código declara un control de vista de calendario mensual.  
  
     [!code-csharp[SP_VisualWebPart#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]
     [!code-vb[SP_VisualWebPart#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]  
  
4.  Reemplace el método `Page_Load` de la clase `VisualWebPart1` por el código siguiente.  Este código realiza las tareas siguientes:  
  
    -   Agrega una vista de calendario mensual al control de usuario.  
  
    -   Agrega una casilla para cada lista de calendarios del sitio.  
  
    -   Especifica una plantilla para cada tipo de elemento que aparece en la vista de calendario.  
  
     [!code-csharp[SP_VisualWebPart#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]
     [!code-vb[SP_VisualWebPart#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]  
  
5.  Reemplace el método `Button1_Click` de la clase `VisualWebPart1` por el código siguiente.  Este código agrega los elementos de cada calendario seleccionado a la vista de calendario principal.  
  
     [!code-csharp[SP_VisualWebPart#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]
     [!code-vb[SP_VisualWebPart#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]  
  
## Prueba del elemento web  
 Cuando se ejecuta el proyecto, se abre el sitio de SharePoint.  El elemento web se agrega automáticamente a la Galería de elementos web de SharePoint.  Para probar este proyecto, realizará las tareas siguientes:  
  
-   Agregar un evento a cada una de dos listas de calendarios independientes.  
  
-   Agregar el elemento web a una página de elemento web.  
  
-   Especifique listas para incluir en la vista de calendario mensual.  
  
#### Para agregar eventos a listas de calendario del sitio  
  
1.  En Visual Studio, elija la tecla F5.  
  
     El sitio de SharePoint se abre y aparece la barra de inicio rápido de [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] en la página.  
  
2.  En la barra de Inicio rápido, en **Listas**, elija el vínculo de **Calendario**.  
  
     Aparece la página **Calendario**.  
  
     Si ningún vínculo de calendario aparece en la barra de Inicio rápido, elija el vínculo de **Contenido del sitio**.  Si la página de contenido de sitio no muestra un elemento de **Calendario**, cree uno.  
  
3.  En la página del calendario, elija un día y elija el vínculo de **Agregar** en el día seleccionado para agregar un evento.  
  
4.  En el cuadro **Título**, escriba Evento en el calendario predeterminado y, a continuación, elija el botón **Guardar**.  
  
5.  Elija el vínculo **Contenido del sitio** y, a continuación, el mosaico **Agregar una aplicación**.  
  
6.  En la página de **Crear**, elija el tipo de **Calendario**, asigne un nombre al calendario y elija el botón de **Crear**.  
  
7.  Agregue un evento al nuevo calendario, llame al evento Event en el calendario personalizado y después elija el botón **Guardar**.  
  
#### Para agregar el elemento web a una página de elemento web  
  
1.  En la página de **Contenido del sitio**, abra la carpeta de **Páginas del sitio**.  
  
2.  En la cinta de opciones, elija la ficha de **Archivos**, abra el menú de **Nuevo documento** y elija el comando de **Página de elementos web**.  
  
3.  En la página **Nueva página de elementos web**, dé a la página el nombre **SampleWebPartPage.aspx** y elija el botón **Crear**.  
  
     Aparece la página de elementos web.  
  
4.  En la zona superior de la página de elementos web, elija la ficha de **Insertar** y elija el botón **Elemento web**.  
  
5.  Elija la carpeta **Personalizado**, elija el elemento web **VisualWebPart1** y después elija el botón **Agregar**.  
  
     El elemento web aparece en la página.  Los siguientes controles aparecen en el elemento web:  
  
    -   Una vista de calendario mensual.  
  
    -   Un botón **Actualizar**.  
  
    -   Una casilla **Calendario**.  
  
    -   Una casilla **Calendario personalizado**.  
  
#### Para especificar listas para incluir en la vista de calendario mensual  
  
1.  En el elemento web, especifique los calendarios que desea incluir en la vista de calendario mensual y, a continuación, elija el botón **Actualizar**.  
  
     Los eventos de todos los calendarios especificados aparecen en la vista de calendario mensual.  
  
## Vea también  
 [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Cómo: Crear un elemento web de SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Cómo: Crear un elemento web de SharePoint con un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Tutorial: Crear un elemento web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)  
  
  