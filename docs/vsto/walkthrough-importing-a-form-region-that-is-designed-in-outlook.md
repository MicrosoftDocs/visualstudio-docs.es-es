---
title: 'Tutorial: Importar un área de formulario diseñada en Outlook'
description: Obtenga información sobre cómo diseñar un área de formulario en Microsoft Outlook y, a continuación, importar el área de formulario en un proyecto de complemento de VSTO de Outlook mediante el Asistente para nueva región de formulario.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- importing form regions
- form regions [Office development in Visual Studio], importing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4ce8c334be74f2643bfc7fa263b01a74db109eb7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827752"
---
# <a name="walkthrough-import-a-form-region-that-is-designed-in-outlook"></a>Tutorial: Importar un área de formulario diseñada en Outlook
  En este tutorial se muestra cómo diseñar un área de formulario en Microsoft Office Outlook y cómo importarla a un proyecto de complemento de VSTO para Outlook mediante el asistente para **nueva área de formulario** . Al diseñar el área de formulario en Outlook, se pueden agregar controles nativos de Outlook a dicha área que se enlazan a datos de Outlook. Después de importar el área de formulario, puede controlar los eventos de cada control.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Diseñar un área de formulario mediante el Diseñador de áreas de formulario de Outlook.

- Importar un área de formulario a un proyecto de complemento de VSTO para Outlook.

- Controlar los eventos de los controles en el área de formulario.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] o [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Diseño de un área de formulario mediante el diseñador de área de formulario en Outlook
 En este paso diseñará un área de formulario en Outlook. A continuación, guardará el área de formulario en una ubicación fácil de encontrar para que pueda importar a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

 Esta área de formulario de ejemplo reemplaza por completo el formulario habitual de tareas. Proporciona una forma de realizar un seguimiento del progreso de todas las tareas que deben completarse (tareas necesarias) para poder realizar la tarea principal. El área de formulario muestra una lista de las tareas de necesarias y además del estado de finalización de cada tarea de la lista. Los usuarios pueden agregar tareas a la lista y quitarlas. También pueden actualizar el estado de finalización de cada tarea.

### <a name="to-design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Para diseñar un área de formulario mediante el Diseñador de áreas de formulario de Outlook

1. Inicie Microsoft Office Outlook.

2. En Outlook, en la pestaña **Desarrollador** haga clic en **Diseñar un formulario**. Para obtener más información, [vea Cómo: Mostrar la pestaña para desarrolladores en la cinta](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)de opciones .

3. En el cuadro **Diseñar formulario** , haga clic en **Tarea** y luego en **Abrir**.

4. En Outlook, en el la pestaña **Desarrollador** , del grupo **Diseño** , haga clic en **Nueva área de formulario**.

     Se abrirá una nueva área de formulario. Si no se muestra el **Selector de campos** , haga clic en **Selector de campos** en el grupo **Herramientas** .

5. Arrastre los campos **Asunto** y **% completado** del **Selector de campos** al área de formulario.

6. En el grupo **Herramientas** , haga clic en **Cuadro de controles** para abrir el **Cuadro de herramientas**.

7. Arrastre una etiqueta desde el **Cuadro de herramientas** al área de formulario. Coloque la etiqueta debajo de los campos **Asunto** y **% completado** .

8. Haga clic con el botón derecho en la etiqueta y luego haga clic en **Propiedades avanzadas**.

9. En la ventana **Propiedades** , establezca el valor de la propiedad **Caption** en **Esta tarea depende de las siguientes tareas**, establezca el valor de la propiedad **Width** en **200** y luego haga clic en **Aplicar**.

10. Arrastre un control ListBox desde el **Cuadro de herramientas** al área de formulario. Coloque el cuadro de lista debajo de la etiqueta **Esta tarea depende de las siguientes tareas** .

11. Seleccione el cuadro de lista que agregó hace unos instantes.

12. En la ventana **Propiedades** , establezca el valor de **Ancho** en **300** y haga clic en **Aplicar**.

13. Arrastre una etiqueta desde el **Cuadro de herramientas** al área de formulario. Coloque la etiqueta debajo del cuadro de lista.

14. Seleccione la etiqueta que agregó hace unos instantes.

15. En la ventana **Propiedades** , establezca el valor de la propiedad **Caption** en **Seleccionar una tarea para agregarla a la lista de tareas dependientes**, establezca el valor de la propiedad **Width** en **200** y luego haga clic en **Aplicar**.

16. Arrastre un control ComboBox desde el **Cuadro de herramientas** al área de formulario. Coloque el cuadro combinado debajo de la etiqueta **Seleccionar una tarea para agregarla a la lista de tareas dependientes** .

17. Seleccione el cuadro combinado que agregó hace unos instantes.

18. En la ventana **Propiedades** , establezca el valor de la propiedad **Width** en **300** y haga clic en **Aplicar**.

19. Arrastre un control CommandButton desde el **Cuadro de herramientas** al área de formulario. Coloque el botón de comando junto al cuadro combinado.

20. Seleccione el botón de comando que agregó hace unos instantes.

21. En la ventana **Propiedades** , establezca el valor de **Nombre** en **AddDependentTask**, el valor de **Descripción** en **Agregar tarea dependiente**, el valor de **Ancho** en **100** y luego haga clic en **Aplicar**.

22. En el **Selector de campos**, haga clic en **Nuevo**.

23. En el cuadro de diálogo **Nuevo campo** , escriba **hiddenField** en el campo **Nombre** haga clic en **Aceptar**.

24. Arrastre el campo **hiddenField** desde el **Selector de campos** al área de formulario.

25. En la ventana **Propiedades** , defina el valor de **Visible** en **0 - Falso** y haga clic en **Aplicar**.

26. En Outlook, en la pestaña **Desarrollador** , del grupo **Diseño** , haga clic en el **Guardar** y luego haga clic en **Guardar área de formulario como**.

     Asigne el nombre **TaskFormRegion** al área de formulario y guárdela en un directorio local del equipo.

     Outlook guarda el área de formulario como un archivo de Almacenamiento de formularios de Outlook *(.ofs).* El área de formulario se guarda con el nombre *TaskFormRegion.ofs*.

27. Cierre Outlook.

## <a name="create-a-new-outlook-add-in-project"></a>Creación de un nuevo proyecto de complemento de Outlook
 En este paso, creará un proyecto de complemento de VSTO para Outlook. Más adelante en este tutorial, importaremos el área de formulario al proyecto.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Para crear un proyecto de complemento de VSTO de Outlook

1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cree un proyecto de complemento de VSTO para Outlook con el nombre **TaskAddIn**.

2. En el cuadro de diálogo **Nuevo proyecto** , seleccione **Crear directorio para la solución**.

3. Guarde el proyecto en el directorio de proyecto predeterminado.

     Para obtener más información, [vea Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="import-the-form-region"></a>Importar el área de formulario
 Puede importar el área de formulario diseñada en Outlook al proyecto de complemento de VSTO para Outlook mediante el asistente para **nueva región de formulario de Outlook** .

### <a name="to-import-the-form-region-into-the-outlook-vsto-add-in-project"></a>Para importar el área de formulario al proyecto de complemento de VSTO para Outlook

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto **TaskAddIn** , elija **Agregar** y después haga clic en **Nuevo elemento**.

2. En el panel **Plantillas** , seleccione **Área de formulario de Outlook**, asigne el nombre **TaskFormRegion** al archivo y luego haga clic en **Agregar**.

     Se **inicia el Asistente para área de formulario NewOutlook.**

3. En la página **Seleccione cómo desea crear el área de formulario** , seleccione **Importar archivo de almacén de formulario de Outlook (.ofs)** y haga clic en **Examinar**.

4. En el cuadro de diálogo **Ubicación de archivo de área de formulario de Outlook existente** , vaya a la ubicación de *TaskFormRegion.ofs*, seleccione **TaskFormRegion.ofs**, haga clic en **Abrir** y, por último, haga clic en **Siguiente**.

5. En la página **Seleccione el tipo de área de formulario que desea crear** , haga clic en **Reemplazo total** y después en **Siguiente**.

     Un área de formulario del tipo *reemplazo total* sustituirá todo el formulario de Outlook. Para obtener más información sobre los tipos de área de formulario, vea [Crear regiones de formulario de Outlook.](../vsto/creating-outlook-form-regions.md)

6. En la página **Proporcione texto descriptivo y seleccione sus preferencias de presentación** , haga clic en **Siguiente**.

7. En la página **Identifique las clases de mensaje que mostrarán esta área de formulario** , del campo **¿Qué clases de mensaje personalizadas mostrarán esta área de formulario?** escriba **IPM.Task.TaskFormRegion** y luego haga clic en **Finalizar**.

     Se *agrega un archivo TaskFormRegion.cs* o *TaskFormRegion.vb* al proyecto.

## <a name="handle-the-events-of-controls-on-the-form-region"></a>Controlar los eventos de los controles en el área de formulario
 Ahora que ha incluido el área de formulario en el proyecto, puede agregar código que controle el evento `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` del botón que agregó al área de formulario en Outlook.

 También agregue código al evento <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> para actualizar los controles del área de formulario cuando esta se muestra.

### <a name="to-handle-the-events-of-controls-on-the-form-region"></a>Para controlar los eventos de los controles en el área de formulario

1. En **Explorador de soluciones**, haga clic con el botón derecho *en TaskFormRegion.cs* o *TaskFormRegion.vb* y, a continuación, haga clic **en Ver código**.

    *TaskFormRegion.cs* o *TaskFormRegion.vb* se abre en el Editor de código.

2. Agregue el siguiente código a la clase `TaskFormRegion` . Este código rellena el cuadro combinado en el área de formulario con la línea de asunto de cada tarea de la carpeta Tareas de Outlook.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb" id="Snippet1":::

3. Agregue el siguiente código a la clase `TaskFormRegion` . Este código realiza las tareas siguientes:

   - Busca `Microsoft.Office.Interop.Outlook.TaskItem` en la carpeta Tareas llamando al método del asistente `FindTaskBySubjectName` y pasando el asunto de la tarea deseada. En el paso siguiente agregará el método del asistente `FindTaskBySubjectName`.

   - Agrega los valores `Microsoft.Office.Interop.Outlook.TaskItem.Subject` y `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` al cuadro de lista de tareas dependientes.

   - Agrega el asunto de la tarea al campo oculto en el área de formulario. El campo oculto almacena estos valores como parte del elemento de Outlook.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb" id="Snippet2":::

4. Agregue el siguiente código a la clase `TaskFormRegion` . Este código proporciona el método del asistente `FindTaskBySubjectName` descrito en el paso anterior.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs" id="Snippet3":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb" id="Snippet3":::

5. Agregue el siguiente código a la clase `TaskFormRegion` . Este código realiza las tareas siguientes:

   - Actualiza el cuadro de lista del área de formulario con el estado de finalización actual de cada tarea dependiente.

   - Analiza el campo de texto oculto para obtener al asunto de cada tarea dependiente. A continuación, busca cada uno de ellos en la carpeta Tasks llamando `Microsoft.Office.Interop.Outlook.TaskItem` al método auxiliar y pasando el asunto de cada  `FindTaskBySubjectName` tarea.

   - Agrega los valores `Microsoft.Office.Interop.Outlook.TaskItem.Subject` y `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` al cuadro de lista de tareas dependientes.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb" id="Snippet4":::

6. Reemplace el controlador de eventos `TaskFormRegion_FormRegionShowing` por el siguiente código: Este código realiza las tareas siguientes:

   - Rellena el cuadro combinado del área de formulario con los asuntos de las tarea cuando aparece dicha área.

   - Llama al método del asistente `RefreshTaskListBox` cuando aparece el área de formulario. Este método muestra las tareas dependientes que se agregaron al cuadro de lista cuando se abrió el elemento anteriormente.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb" id="Snippet5":::

## <a name="test-the-outlook-form-region"></a>Prueba del área de formulario de Outlook
 Para probar el área de formulario, agregue tareas a la lista de tareas necesarias en el área de formulario. Actualice el estado de finalización de una tarea necesario y luego vea el estado de finalización actualizado de la tarea en la lista de tareas necesarias.

### <a name="to-test-the-form-region"></a>Para probar el área de formulario

1. Presione **F5** para ejecutar el proyecto.

     Se inicia Outlook.

2. En Outlook, en la pestaña **Inicio** , haga clic en **Nuevos elementos** y en **Tarea**.

3. En el formulario de tareas, escriba **Tarea dependiente** en el campo **Asunto** .

4. En la **pestaña Tarea** de la cinta de opciones, en el **grupo Acciones** , haga clic en Guardar **& Cerrar**.

5. En Outlook, en la pestaña **Inicio** , haga clic **Nuevos elementos**, haga clic en **Más elementos** y, por último, en **Elegir formulario**.

6. En el cuadro de diálogo **Elegir formulario** , haga clic en **TaskFormRegion** y luego en **Abrir**.

     Se mostrará el formulario **TaskFormRegion** . Este formulario reemplaza el formulario de tareas completo. El cuadro combinado **Seleccionar una tarea para agregarla a la lista de tareas dependientes** se rellena con otras tareas de la carpeta de Tareas.

7. En el formulario de tareas, en el campo **Asunto** escriba **Tarea principal**.

8. En el cuadro combinado **Seleccionar una tarea para agregarla a la lista de tareas dependientes** , seleccione **Tarea dependiente** y haga clic en **Agregar tarea dependiente**.

     En el cuadro de lista **Esta tarea depende de las siguientes tareas** se muestra **0 % completado: tarea dependiente** . Esto demuestra que ha controlado correctamente el evento `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` del botón.

9. Guarde el elemento **Tarea principal** y ciérrelo.

10. Vuelva a abrir el elemento Tarea dependiente en Outlook.

11. En el formulario Tareas dependiente, modifique el valor del campo **% completado** a **50 %**.

12. En la **pestaña Tarea** de la cinta de opciones Tarea dependiente , en el **grupo Acciones** , haga clic en Guardar **& Cerrar**.

13. Vuelva a abrir el elemento **Tarea principal** en Outlook.

     En el cuadro de lista **Esta tarea depende de las siguientes tareas** ahora se muestra **50 % completado: tarea dependiente** .

## <a name="next-steps"></a>Pasos siguientes
 Puede obtener más información sobre cómo personalizar la interfaz de usuario de una aplicación de Outlook en estos temas:

- Para obtener más información sobre cómo diseñar la apariencia de un área de formulario arrastrando controles administrados a un diseñador visual, vea Tutorial: Diseñar un [área de formulario de Outlook.](../vsto/walkthrough-designing-an-outlook-form-region.md)

- Para obtener información sobre cómo personalizar la cinta de opciones de un elemento de Outlook, vea [Personalizar una cinta de opciones para Outlook.](../vsto/customizing-a-ribbon-for-outlook.md)

- Para obtener más información sobre cómo agregar un panel de tareas personalizado a Outlook, vea [Paneles de tareas personalizados](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Consulte también
- [Acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)
- [Creación de regiones de formulario de Outlook](../vsto/creating-outlook-form-regions.md)
- [Directrices para crear regiones de formulario de Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Tutorial: Diseño de un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Asociación de un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Acciones personalizadas en las regiones de formulario de Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Cómo: Impedir que Outlook muestre un área de formulario](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
