---
title: "Tutorial: Crear una pesta&#241;a personalizada usando el dise&#241;ador de la cinta de opciones | Microsoft Docs"
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
helpviewer_keywords: 
  - "paneles de acciones [desarrollo de Office en Visual Studio], controlar desde la cinta de opciones"
  - "Cinta de opciones personalizada, pestañas"
  - "pestaña personalizada [desarrollo de Office en Visual Studio]"
  - "personalizar la cinta de opciones, pestañas"
  - "Cinta [desarrollo de Office en Visual Studio], personalizar"
  - "Diseñador de la cinta de opciones [desarrollo de Office en Visual Studio]"
ms.assetid: 312865e6-950f-46ab-88de-fe7eb8036bfe
caps.latest.revision: 68
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 67
---
# Tutorial: Crear una pesta&#241;a personalizada usando el dise&#241;ador de la cinta de opciones
  El diseñador de la cinta de opciones permite crear una pestaña personalizada y, a continuación, agregar y colocar controles en ella.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   [Crear paneles de acciones](#BKMK_CreateActionsPanes).  
  
-   [Crear una ficha personalizada](#BKMK_CreateCustomTab).  
  
-   [Ocultar y mostrar paneles de acciones con botones de la pestaña personalizada](#BKMK_HideShowActionsPane).  
  
> [!NOTE]  
>  Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos.  Para obtener más información, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## Crear un proyecto de libro de Excel  
 Los pasos para utilizar el diseñador de la cinta de opciones son casi idénticos para todas las aplicaciones de Office.  En este ejemplo se utiliza un libro de Excel.  
  
#### Para crear un proyecto de libro de Excel  
  
-   Cree un proyecto de libro de Excel con el nombre MyExcelRibbon.  Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto **MyExcelRibbon** al **Explorador de soluciones**.  
  
##  <a name="BKMK_CreateActionsPanes"></a> Crear paneles de acciones  
 Agregue dos paneles de acciones personalizados al proyecto.  Posteriormente agregará botones a la pestaña personalizada que muestren y oculten estos paneles de acciones.  
  
#### Para crear paneles de acciones  
  
1.  En el menú **Proyecto**, elija **Agregar nuevo elemento**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento**, seleccione **ActionsPaneControl** y, a continuación, elija **Agregar**.  
  
     En el diseñador se abre el archivo **ActionsPaneControl1.cs** o **ActionsPaneControl1.vb**.  
  
3.  Desde la ficha **Controles comunes** del **Cuadro de herramientas**, agregue una etiqueta a la superficie del diseñador.  
  
4.  En la ventana **Propiedades**, establezca la propiedad **Texto** de label1 en Actions Pane 1.  
  
5.  Repita los pasos del 1 al 5 para crear un segundo panel de acciones y una etiqueta.  Establezca la propiedad **Texto** de la segunda etiqueta en Actions Pane 2.  
  
##  <a name="BKMK_CreateCustomTab"></a> Crear una ficha personalizada  
 Una de las instrucciones de diseño de las aplicaciones de Office es que los usuarios siempre deberían tener control de su interfaz de usuario.  Para agregar esta capacidad en los paneles de acciones, puede agregar botones que muestren y oculten cada panel de acciones en una pestaña personalizada de la cinta de opciones.  Para crear una ficha personalizada, agregue un elemento **Cinta \(diseñador visual\)** al proyecto.  El diseñador ayuda a agregar y colocar controles, a establecer las propiedades del control y a controlar los eventos de control.  
  
#### Para crear una ficha personalizada  
  
1.  En el menú **Proyecto**, elija **Agregar nuevo elemento**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento**, seleccione **Cinta \(diseñador visual\)**.  
  
3.  Cambie el nombre de la nueva cinta de opciones a **MyRibbon** y elija **Agregar**.  
  
     El archivo **MyRibbon.cs** o **MyRibbon.vb** se abre en el diseñador de la cinta de opciones y muestra una ficha y un grupo predeterminados.  
  
4.  En el diseñador de la cinta de opciones, elija la pestaña predeterminada.  
  
5.  En la ventana **Propiedades**, expanda la propiedad **ControlId** y, a continuación, establezca la propiedad **ControlIdType** en **Personalizar**.  
  
6.  Establezca la propiedad **Etiqueta** en My Custom Tab.  
  
7.  En el diseñador de la cinta de opciones, elija **grupo1**.  
  
8.  En la ventana **Propiedades**, establezca **Etiqueta** en Actions Pane Manager.  
  
9. Desde la pestaña **Controles de la cinta de opciones de Office** del **Cuadro de herramientas**, arrastre un botón hasta **grupo1**.  
  
10. Seleccione **button1**.  
  
11. En la ventana **Propiedades**, establezca **Etiqueta** en Show Actions Pane 1.  
  
12. Agregue un segundo botón a **grupo1**y establezca la propiedad **Etiqueta** en Show Actions Pane 2.  
  
13. Desde la ficha **Controles de la cinta de opciones de Office** del **Cuadro de herramientas**, arrastre un control **ToggleButton** a **grupo1**.  
  
14. Establezca la propiedad **Etiqueta** en Hide Actions Pane.  
  
##  <a name="BKMK_HideShowActionsPane"></a> Ocultar y mostrar paneles de acciones con botones de la pestaña personalizada  
 El último paso consiste en agregar código que responda al usuario.  Agregue controladores de eventos para los eventos <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> de los dos botones y el evento <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> del botón de alternancia.  Agregue código a estos controladores de eventos para ocultar o mostrar los paneles de acciones.  
  
#### Para ocultar y mostrar paneles de acciones con botones de la ficha personalizada  
  
1.  En el **Explorador de soluciones**, abra el menú contextual de MyRibbon.cs o MyRibbon.vb y, a continuación, elija **Ver código**.  
  
2.  Agregue el siguiente código al comienzo de la clase `MyRibbon`.  Este código crea dos objetos de panel de acciones.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/CS/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/VB/MyRibbon.vb#1)]  
  
3.  Reemplace el método `MyRibbon_Load` por el código siguiente.  Este código agrega los objetos de panel de acciones a la colección <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> y oculta los objetos de la vista.  El código de Visual C\# también asocia delegados a varios eventos de control de la cinta de opciones.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/CS/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/VB/MyRibbon.vb#2)]  
  
4.  Agregue los tres métodos de control de eventos siguientes a la clase `MyRibbon`.  Estos métodos controlan los eventos <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> de los dos botones y el evento <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> del botón de alternancia.  Los controladores de eventos de button1 y button2 muestran paneles de acciones alternativos.  El controlador de eventos de toggleButton1 muestra y oculta el panel de acciones activo.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/CS/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/VB/MyRibbon.vb#3)]  
  
## Probar la ficha personalizada  
 Al ejecutar el proyecto, se inicia Excel y aparece la pestaña **My Custom Tab** en la cinta.  Elija los botones de **My Custom Tab** para mostrar u ocultar los paneles de acciones.  
  
#### Para probar la ficha personalizada  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Elija la pestaña **My Custom Tab**.  
  
3.  En el grupo **Custom Actions Pane Manager**, elija **Show Actions Pane 1**.  
  
     El panel de acciones aparece y muestra la etiqueta Actions Pane 1.  
  
4.  Elija **Show Actions Pane 2**.  
  
     El panel de acciones aparece y muestra la etiqueta Actions Pane 2.  
  
5.  Elija **Hide Actions Pane**.  
  
     Los paneles de acciones ya no están visibles.  
  
## Pasos siguientes  
 Puede aprender más acerca de la personalización de la interfaz de usuario de Office en estos temas:  
  
-   Agregar una interfaz de usuario basada en contexto a cualquier personalización de nivel de documento.  Para obtener más información, vea [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md).  
  
-   Extender un formulario estándar o personalizado de Microsoft Office Outlook.  Para obtener más información, vea [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## Vea también  
 [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)   
 [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)   
 [Personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Cómo: Iniciarse en la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Cómo: Cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)   
 [Cómo: Agregar controles en la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Información general sobre el modelo de objetos para la cinta de opciones](../vsto/ribbon-object-model-overview.md)  
  
  