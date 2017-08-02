---
title: "Tutorial: Dise&#241;ar un &#225;rea de formulario de Outlook"
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
  - "áreas de formulario [desarrollo de Office en Visual Studio], crear"
ms.assetid: b033fc06-cdeb-4d7f-804b-86d15bfa022a
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Tutorial: Dise&#241;ar un &#225;rea de formulario de Outlook
  Las áreas de formulario personalizadas extienden los formularios estándar o personalizados de Microsoft Office Outlook.  En este tutorial diseñará un área de formulario personalizada que aparece como una nueva página en la ventana del inspector de un elemento de contacto.  Esta área de formulario muestra una asignación de cada dirección incluida para el contacto, enviando la información de la dirección al sitio web de búsqueda local de Windows Live.  Para obtener información sobre las áreas de formulario, consulte [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un proyecto de complemento de VSTO de Outlook  
  
-   Agregar un área de formulario al proyecto de complemento de VSTO.  
  
-   Definir el diseño del área de formulario.  
  
-   Personalizar el comportamiento del área de formulario.  
  
-   Probar el área de formulario de Outlook.  
  
> [!NOTE]  
>  Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos.  Para obtener más información, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] o [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].  
  
 ![vínculo a vídeo](~/docs/data-tools/media/playvideo.gif "vínculo a vídeo") Para ver una versión en vídeo de este tema, consulte el vídeo sobre cómo [Diseñar un área de formulario de Outlook](http://go.microsoft.com/fwlink/?LinkID=140824).  
  
## Crear un proyecto de complemento de VSTO de Outlook  
 En primer lugar, cree un proyecto básico de complemento de VSTO.  
  
#### Para crear un proyecto de complemento de VSTO de Outlook  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cree un proyecto de complemento de VSTO de Outlook con el nombre MapItAddIn.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, seleccione **Crear directorio para la solución**.  
  
3.  Guarde el proyecto en cualquier directorio.  
  
     Para obtener más información, consulte [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## Agregar un área de formulario al proyecto de complemento de VSTO de Outlook  
 Una solución de complemento de VSTO de Outlook puede contener uno o varios elementos de área de formulario de Outlook.  Agregue un elemento de área de formulario al proyecto mediante el asistente **Nueva área de formulario de Outlook**.  
  
#### Para agregar un área de formulario al proyecto de complemento de VSTO de Outlook  
  
1.  En el **Explorador de soluciones**, seleccione el proyecto **MapItAddIn**.  
  
2.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
3.  En el cuadro de diálogo **Agregar nuevo elemento**, seleccione **Área de formulario de Outlook**, asigne al archivo el nombre MapIt y, después, haga clic en **Agregar**.  
  
     Se inicia el asistente **Nuevaárea de formulario de Outlook**.  
  
4.  En la página **Seleccione cómo desea crear el área de formulario**, haga clic en **Diseñar una nueva área de formulario** y, después, en **Siguiente**.  
  
5.  En la página **Seleccione el tipo de área de formulario que desea crear**, haga clic en **Independiente** y, después, en **Siguiente**.  
  
     Un área de formulario *independiente* agrega una nueva página a un formulario de Outlook.  Para obtener más información sobre los tipos de áreas de formulario, consulte [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md).  
  
6.  En la página **Proporcione texto descriptivo y seleccione sus preferencias de presentación**, escriba **Map It** en el cuadro **Nombre**.  
  
     Este nombre aparece en la cinta de opciones de la ventana del inspector cuando se abre el elemento de contacto.  
  
7.  Seleccione **Inspectores que están en modo de redacción** e **Inspectores que están en modo de lectura** y, después, haga clic en **Siguiente**.  
  
8.  En la página **Identifique las clases de mensaje que mostrarán esta área de formulario**, desactive la opción **Mensaje de correo**, seleccione **Contacto** y, después, haga clic en **Finalizar**.  
  
     Se agregará un archivo MapIt.cs o MapIt.vb al proyecto.  
  
## Definir el diseño del área de formulario  
 Desarrolle áreas de formulario de forma visual mediante el *Diseñador de áreas de formulario*.  Puede arrastrar controles administrados a la superficie del Diseñador de áreas de formulario.  Use el diseñador y la ventana **Propiedades** para ajustar el diseño y la apariencia del control.  
  
#### Para definir el diseño del área de formulario  
  
1.  En el **Explorador de soluciones**, expanda el proyecto **MapItAddIn** y, después, haga doble clic en MapIt.cs o MapIt.vb para abrir el Diseñador de áreas de formulario.  
  
2.  Haga clic con el botón derecho en el diseñador y, después, haga clic en **Propiedades**.  
  
3.  En la ventana **Propiedades** , establezca **Tamaño** en 664, 469.  
  
     De esta forma se garantiza que el área de formulario sea suficientemente grande para mostrar una asignación.  
  
4.  En el menú **Ver**, haga clic en **Cuadro de herramientas**.  
  
5.  Desde la pestaña **Controles comunes** del **Cuadro de herramientas**, agregue un **WebBrowser** al área de formulario.  
  
     El **WebBrowser** mostrará una asignación de cada dirección enumerada para el contacto.  
  
## Personalizar el comportamiento del área de formulario  
 Agregue código a los controladores de eventos del área de formulario para personalizar el comportamiento de un área de formulario en tiempo de ejecución.  Para esta área de formulario, el código examina las propiedades de un elemento de Outlook y determina si se va a mostrar el área de formulario Map It.  Si muestra el área de formulario, el código se desplaza a la búsqueda local de Windows Live y carga una asignación de cada dirección incluida en el elemento de contacto de Outlook.  
  
#### Para personalizar el comportamiento del área de formulario  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en MapIt.cs o MapIt.vb y, después, haga clic en **Ver código**.  
  
     Se abre MapIt.cs o MapIt.vb en el Editor de código.  
  
2.  Expanda el área de código **Generador de áreas de formulario**.  
  
     Se expone la clase de generador de áreas de formulario llamada `MapItFactory`.  
  
3.  Agregue el código siguiente al controlador de eventos `MapItFactory_FormRegionInitializing`.  Se llama a este controlador de eventos cuando el usuario abre un elemento de contacto.  El siguiente código determina si el elemento de contacto contiene una dirección.  Si el elemento de contacto no contiene ninguna dirección, este código establece la propiedad <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> de la clase <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> en **true** y no se muestra el área de formulario.  De lo contrario, el complemento de VSTO provoca el evento <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> y muestra el área de formulario.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#1)]
     [!code-vb[Trin_Outlook_FR_Separate#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#1)]  
  
4.  Agregue el código siguiente al controlador de eventos <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>.  Este código realiza las tareas siguientes:  
  
    -   Concatena cada dirección del elemento de contacto y crea una cadena de dirección URL.  
  
    -   Llama al método <xref:System.Windows.Forms.WebBrowser.Navigate%2A> del objeto <xref:System.Windows.Forms.WebBrowser> y pasa la cadena de dirección URL como parámetro.  
  
     El sitio web de búsqueda local aparece en el área de formulario Map It y presenta las direcciones en el bloc de notas.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#2)]  
  
## Probar el área de formulario de Outlook  
 Al ejecutar el proyecto, Visual Studio abrirá Outlook.  Abra un elemento de contacto para ver el área de formulario Map It.  El área de formulario Map It aparece como página en el formulario de cualquier elemento de contacto que contenga una dirección.  
  
#### Para comprobar el área de formulario Map It  
  
1.  Presione F5 para ejecutar el proyecto.  
  
     Se abre Outlook.  
  
2.  En Outlook, en la pestaña **Inicio**, haga clic en **Nuevos elementos** y en **Contacto**.  
  
3.  En el formulario de contacto, escriba **Ana Díaz** como nombre de contacto y especifique las tres direcciones siguientes.  
  
    |Tipo de dirección|Dirección|  
    |-----------------------|---------------|  
    |**Trabajo**|C\/ Araquil 67  Madrid|  
    |**Inicio**|C\/ Moralzarzal 86  Madrid|  
    |**Otro**|C\/ Romero 33  Sevilla|  
  
4.  Guarde y cierre el elemento de contacto.  
  
5.  Vuelva a abrir el elemento de contacto **Ana Díaz**.  
  
6.  En el grupo **Mostrar** de la cinta de opciones del elemento, haga clic en **Map It** para abrir el área de formulario Map It.  
  
     Aparece el área de formulario Map It y muestra el sitio web de búsqueda local.  Las direcciones **Trabajo**, **Casa** y **Otros** aparecen en el bloc de notas.  En dicho bloc, seleccione la dirección que desea asignar.  
  
## Pasos siguientes  
 Puede obtener más información sobre cómo personalizar la interfaz de usuario de una aplicación de Outlook en estos temas:  
  
-   Para obtener información sobre cómo personalizar la cinta de opciones de un elemento de Outlook, consulte [Personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
## Vea también  
 [Obtener acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)   
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Instrucciones para crear áreas de formulario de Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Tutorial: Importar un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Asociar un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Acciones personalizadas en áreas de formulario de Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Cómo: Impedir que Outlook muestre un área de formulario](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  