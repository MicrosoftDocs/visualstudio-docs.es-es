---
title: "Tutorial: Importar un &#225;rea de formulario dise&#241;ada en Outlook"
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
  - "importar áreas de formulario"
  - "áreas de formulario [desarrollo de Office en Visual Studio], importar"
ms.assetid: 86b0ef1a-6d7e-4ea5-b90e-458ffe4e1d10
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# Tutorial: Importar un &#225;rea de formulario dise&#241;ada en Outlook
  En este tutorial se muestra cómo diseñar un área de formulario en Microsoft Office Outlook y cómo importarla a un proyecto de complemento de VSTO para Outlook mediante el asistente para **nueva área de formulario** . Al diseñar el área de formulario en Outlook, se pueden agregar controles nativos de Outlook a dicha área que se enlazan a datos de Outlook. Después de importar el área de formulario, puede controlar los eventos de cada control.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Diseñar un área de formulario mediante el Diseñador de áreas de formulario de Outlook.  
  
-   Importar un área de formulario a un proyecto de complemento de VSTO para Outlook.  
  
-   Controlar los eventos de los controles en el área de formulario.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] o [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].  
  
> [!NOTE]  
>  Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 ![vínculo a vídeo](../vsto/media/playvideo.png "vínculo a vídeo") Puede ver una demostración en vídeo relacionada en [Cómo: crear áreas de formulario de Outlook mediante Visual Studio 2008](http://go.microsoft.com/fwlink/?LinkID=130305).  
  
## Diseñar un área de formulario mediante el Diseñador de áreas de formulario de Outlook  
 En este paso diseñará un área de formulario en Outlook. A continuación, guardará el área de formulario en una ubicación fácil de encontrar para que pueda importar a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Esta área de formulario de ejemplo reemplaza por completo el formulario habitual de tareas. Proporciona una forma de realizar un seguimiento del progreso de todas las tareas que deben completarse \(tareas necesarias\) para poder realizar la tarea principal. El área de formulario muestra una lista de las tareas de necesarias y además del estado de finalización de cada tarea de la lista. Los usuarios pueden agregar tareas a la lista y quitarlas. También pueden actualizar el estado de finalización de cada tarea.  
  
#### Para diseñar un área de formulario mediante el Diseñador de áreas de formulario de Outlook  
  
1.  Inicie Microsoft Office Outlook.  
  
2.  En Outlook, en la pestaña **Desarrollador** haga clic en **Diseñar un formulario**. Para obtener más información, consulta [Cómo: Mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  En el cuadro **Diseñar formulario**, haga clic en **Tarea** y luego en **Abrir**.  
  
4.  En Outlook, en el la pestaña **Desarrollador**, del grupo **Diseño**, haga clic en **Nueva área de formulario**.  
  
     Se abrirá una nueva área de formulario. Si no se muestra el **Selector de campos**, haga clic en **Selector de campos** en el grupo **Herramientas**.  
  
5.  Arrastre los campos **Asunto** y **% completado** del **Selector de campos** al área de formulario.  
  
6.  En el grupo **Herramientas**, haga clic en **Cuadro de controles** para abrir el **Cuadro de herramientas**.  
  
7.  Arrastre una etiqueta desde el **Cuadro de herramientas** al área de formulario. Coloque la etiqueta debajo de los campos **Asunto** y **% completado**.  
  
8.  Haga clic con el botón derecho en la etiqueta y luego haga clic en **Propiedades avanzadas**.  
  
9. En la ventana **Propiedades**, establezca el valor de la propiedad **Caption** en **Esta tarea depende de las siguientes tareas**, establezca el valor de la propiedad **Width** en **200** y luego haga clic en **Aplicar**.  
  
10. Arrastre un control ListBox desde el **Cuadro de herramientas** al área de formulario. Coloque el cuadro de lista debajo de la etiqueta **Esta tarea depende de las siguientes tareas**.  
  
11. Seleccione el cuadro de lista que agregó hace unos instantes.  
  
12. En la ventana **Propiedades**, establezca el valor de **Ancho** en **300** y haga clic en **Aplicar**.  
  
13. Arrastre una etiqueta desde el **Cuadro de herramientas** al área de formulario. Coloque la etiqueta debajo del cuadro de lista.  
  
14. Seleccione la etiqueta que agregó hace unos instantes.  
  
15. En la ventana **Propiedades**, establezca el valor de la propiedad **Caption** en **Seleccionar una tarea para agregarla a la lista de tareas dependientes**, establezca el valor de la propiedad **Width** en **200** y luego haga clic en **Aplicar**.  
  
16. Arrastre un control ComboBox desde el **Cuadro de herramientas** al área de formulario. Coloque el cuadro combinado debajo de la etiqueta **Seleccionar una tarea para agregarla a la lista de tareas dependientes**.  
  
17. Seleccione el cuadro combinado que agregó hace unos instantes.  
  
18. En la ventana **Propiedades**, establezca el valor de la propiedad **Width** en **300** y haga clic en **Aplicar**.  
  
19. Arrastre un control CommandButton desde el **Cuadro de herramientas** al área de formulario. Coloque el botón de comando junto al cuadro combinado.  
  
20. Seleccione el botón de comando que agregó hace unos instantes.  
  
21. En la ventana **Propiedades**, establezca el valor de **Nombre** en **AddDependentTask**, el valor de **Descripción** en **Agregar tarea dependiente**, el valor de **Ancho** en **100** y luego haga clic en **Aplicar**.  
  
22. En el **Selector de campos**, haga clic en **Nuevo**.  
  
23. En el cuadro de diálogo **Nuevo campo**, escriba **hiddenField** en el campo **Nombre** haga clic en **Aceptar**.  
  
24. Arrastre el campo **hiddenField** desde el **Selector de campos** al área de formulario.  
  
25. En la ventana **Propiedades**, defina el valor de **Visible** en **0 \- Falso** y haga clic en **Aplicar**.  
  
26. En Outlook, en la pestaña **Desarrollador**, del grupo **Diseño**, haga clic en el **Guardar** y luego haga clic en **Guardar área de formulario como**.  
  
     Asigne el nombre **TaskFormRegion** al área de formulario y guárdela en un directorio local del equipo.  
  
     Outlook guarda el área de formulario como un archivo de almacén de formulario de Outlook \(.ofs\). El área de formulario se guarda con el nombre TaskFormRegion.ofs.  
  
27. Cierre Outlook.  
  
## Crear un nuevo proyecto de complemento de Outlook  
 En este paso, creará un proyecto de complemento de VSTO para Outlook. Más adelante en este tutorial, importaremos el área de formulario al proyecto.  
  
#### Para crear un proyecto de complemento de VSTO de Outlook  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cree un proyecto de complemento de VSTO para Outlook con el nombre **TaskAddIn**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, seleccione **Crear directorio para la solución**.  
  
3.  Guarde el proyecto en el directorio de proyecto predeterminado.  
  
     Para obtener más información, consulta [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## Importar el área de formulario  
 Puede importar el área de formulario diseñada en Outlook al proyecto de complemento de VSTO para Outlook mediante el asistente para **nueva región de formulario de Outlook**.  
  
#### Para importar el área de formulario al proyecto de complemento de VSTO para Outlook  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto **TaskAddIn**, elija **Agregar** y después haga clic en **Nuevo elemento**.  
  
2.  En el panel **Plantillas**, seleccione **Área de formulario de Outlook**, asigne el nombre **TaskFormRegion** al archivo y luego haga clic en **Agregar**.  
  
     Se iniciará el asistente para **nuevaárea de formulario de Outlook**.  
  
3.  En la página **Seleccione cómo desea crear el área de formulario**, seleccione **Importar archivo de almacén de formulario de Outlook \(.ofs\)** y haga clic en **Examinar**.  
  
4.  En el cuadro de diálogo **Ubicación de archivo de área de formulario de Outlook existente**, vaya a la ubicación de **TaskFormRegion.ofs**, seleccione **TaskFormRegion.ofs**, haga clic en **Abrir** y, por último, haga clic en **Siguiente**.  
  
5.  En la página **Seleccione el tipo de área de formulario que desea crear**, haga clic en **Reemplazo total** y después en **Siguiente**.  
  
     Un área de formulario del tipo *reemplazo total* sustituirá todo el formulario de Outlook. Para obtener más información sobre los tipos de áreas de formulario, consulte [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md).  
  
6.  En la página **Proporcione texto descriptivo y seleccione sus preferencias de presentación**, haga clic en **Siguiente**.  
  
7.  En la página **Identifique las clases de mensaje que mostrarán esta área de formulario**, del campo **¿Qué clases de mensaje personalizadas mostrarán esta área de formulario?** escriba **IPM.Task.TaskFormRegion** y luego haga clic en **Finalizar**.  
  
     Se agregará un archivo TaskFormRegion.cs o TaskFormRegion.vb al proyecto.  
  
## Controlar los eventos de los controles en el área de formulario  
 Ahora que ha incluido el área de formulario en el proyecto, puede agregar código que controle el evento Microsoft.Office.Interop.Outlook.OlkCommandButton.Click del botón que agregó al área de formulario en Outlook.  
  
 También agregue código al evento <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> para actualizar los controles del área de formulario cuando esta se muestra.  
  
#### Para controlar los eventos de los controles en el área de formulario  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en TaskFormRegion.cs o TaskFormRegion.vb y luego haga clic en **Ver código**.  
  
     El archivo TaskFormRegion.cs o TaskFormRegion.vb se abrirá en el Editor de código.  
  
2.  Agregue el código siguiente a la clase `TaskFormRegion`. Este código rellena el cuadro combinado en el área de formulario con la línea de asunto de cada tarea de la carpeta Tareas de Outlook.  
  
     [!code-csharp[Trin_Outlook_FR_Import#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Import/CS/TaskFormRegion.cs#1)]
     [!code-vb[Trin_Outlook_FR_Import#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Import/VB/TaskFormRegion.vb#1)]  
  
3.  Agregue el código siguiente a la clase `TaskFormRegion`. Este código realiza las tareas siguientes:  
  
    -   Busca Microsoft.Office.Interop.Outlook.TaskItem en la carpeta Tareas llamando al método auxiliar `FindTaskBySubjectName` y pasando el asunto de la tarea deseada. En el paso siguiente agregará el método auxiliar `FindTaskBySubjectName`.  
  
    -   Agrega los valores Microsoft.Office.Interop.Outlook.TaskItem.Subject y Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete al cuadro de lista de tareas dependientes.  
  
    -   Agrega el asunto de la tarea al campo oculto en el área de formulario. El campo oculto almacena estos valores como parte del elemento de Outlook.  
  
     [!code-csharp[Trin_Outlook_FR_Import#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Import/CS/TaskFormRegion.cs#2)]
     [!code-vb[Trin_Outlook_FR_Import#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Import/VB/TaskFormRegion.vb#2)]  
  
4.  Agregue el código siguiente a la clase `TaskFormRegion`. Este código proporciona el método auxiliar `FindTaskBySubjectName` descrito en el paso anterior.  
  
     [!code-csharp[Trin_Outlook_FR_Import#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Import/CS/TaskFormRegion.cs#3)]
     [!code-vb[Trin_Outlook_FR_Import#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Import/VB/TaskFormRegion.vb#3)]  
  
5.  Agregue el código siguiente a la clase `TaskFormRegion`. Este código realiza las tareas siguientes:  
  
    -   Actualiza el cuadro de lista del área de formulario con el estado de finalización actual de cada tarea dependiente.  
  
    -   Analiza el campo de texto oculto para obtener al asunto de cada tarea dependiente. A continuación, busca cada elemento Microsoft.Office.Interop.Outlook.TaskItem en la carpeta Tareas llamando al método auxiliar `FindTaskBySubjectName` y pasando el asunto de cada tarea.  
  
    -   Agrega los valores Microsoft.Office.Interop.Outlook.TaskItem.Subject y Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete al cuadro de lista de tareas dependientes.  
  
     [!code-csharp[Trin_Outlook_FR_Import#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Import/CS/TaskFormRegion.cs#4)]
     [!code-vb[Trin_Outlook_FR_Import#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Import/VB/TaskFormRegion.vb#4)]  
  
6.  Reemplace el controlador de eventos `TaskFormRegion_FormRegionShowing` por el siguiente código: Este código realiza las tareas siguientes:  
  
    -   Rellena el cuadro combinado del área de formulario con los asuntos de las tarea cuando aparece dicha área.  
  
    -   Llama al método auxiliar `RefreshTaskListBox` cuando aparece el área de formulario. Este método muestra las tareas dependientes que se agregaron al cuadro de lista cuando se abrió el elemento anteriormente.  
  
     [!code-csharp[Trin_Outlook_FR_Import#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Import/CS/TaskFormRegion.cs#5)]
     [!code-vb[Trin_Outlook_FR_Import#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Import/VB/TaskFormRegion.vb#5)]  
  
## Probar el área de formulario de Outlook  
 Para probar el área de formulario, agregue tareas a la lista de tareas necesarias en el área de formulario. Actualice el estado de finalización de una tarea necesario y luego vea el estado de finalización actualizado de la tarea en la lista de tareas necesarias.  
  
#### Para probar el área de formulario  
  
1.  Presione F5 para ejecutar el proyecto.  
  
     Se inicia Outlook.  
  
2.  En Outlook, en la pestaña **Inicio**, haga clic en **Nuevos elementos** y en **Tarea**.  
  
3.  En el formulario de tareas, escriba **Tarea dependiente** en el campo **Asunto**.  
  
4.  En el pestaña **Tarea** de la cinta de opciones, en el grupo **Acciones**, haga clic en **Guardar y cerrar**.  
  
5.  En Outlook, en la pestaña **Inicio**, haga clic **Nuevos elementos**, haga clic en **Más elementos** y, por último, en **Elegir formulario**.  
  
6.  En el cuadro de diálogo **Elegir formulario**, haga clic en **TaskFormRegion** y luego en **Abrir**.  
  
     Se mostrará el formulario **TaskFormRegion**. Este formulario reemplaza el formulario de tareas completo. El cuadro combinado **Seleccionar una tarea para agregarla a la lista de tareas dependientes** se rellena con otras tareas de la carpeta de Tareas.  
  
7.  En el formulario de tareas, en el campo **Asunto** escriba **Tarea principal**.  
  
8.  En el cuadro combinado **Seleccionar una tarea para agregarla a la lista de tareas dependientes**, seleccione **Tarea dependiente** y haga clic en **Agregar tarea dependiente**.  
  
     En el cuadro de lista **Esta tarea depende de las siguientes tareas** se muestra **0 % completado: tarea dependiente**. Esto demuestra que ha controlado correctamente el evento Microsoft.Office.Interop.Outlook.OlkCommandButton.Click del botón.  
  
9. Guarde el elemento **Tarea principal** y ciérrelo.  
  
10. Vuelva a abrir el elemento Tarea dependiente en Outlook.  
  
11. En el formulario Tareas dependiente, modifique el valor del campo **% completado** a **50 %**.  
  
12. En el pestaña **Tarea** de la cinta de opciones de Tarea dependiente, en el grupo **Acciones**, haga clic en **Guardar y cerrar**.  
  
13. Vuelva a abrir el elemento **Tarea principal** en Outlook.  
  
     En el cuadro de lista **Esta tarea depende de las siguientes tareas** ahora se muestra **50 % completado: tarea dependiente**.  
  
## Pasos siguientes  
 Puede obtener más información sobre cómo personalizar la interfaz de usuario de una aplicación de Outlook en estos temas:  
  
-   Para obtener más información sobre cómo diseñar el aspecto de un área de formulario arrastrando controles administrados a un diseñador visual, consulte [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
-   Para obtener información sobre cómo personalizar la cinta de opciones de un elemento de Outlook, consulte [Personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
-   Para obtener más información sobre cómo agregar un panel de tareas personalizado a Outlook, consulte [Paneles de tareas personalizados](../vsto/custom-task-panes.md).  
  
## Vea también  
 [Obtener acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)   
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Instrucciones para crear áreas de formulario de Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Asociar un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Acciones personalizadas en áreas de formulario de Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Cómo: Impedir que Outlook muestre un área de formulario](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  