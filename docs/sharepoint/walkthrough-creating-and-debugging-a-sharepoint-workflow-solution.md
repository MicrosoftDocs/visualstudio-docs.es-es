---
title: Crear & solución depurar flujo de trabajo de SharePoint
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e51f346501b680b8183f8552aad48ffff84a71dd
ms.sourcegitcommit: 3a19319e2599bd193fb2ca32020ca53942974bfd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "73983726"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>Tutorial: crear y depurar una solución de flujo de trabajo de SharePoint
  En este tutorial se muestra cómo crear una plantilla de flujo de trabajo secuencial básica. El flujo de trabajo comprueba una propiedad de una biblioteca de documentos compartidos para determinar si se ha revisado un documento. Si el documento se ha revisado, el flujo de trabajo finaliza.

 En este tutorial se muestran las tareas siguientes:

- Crear un proyecto de flujo de trabajo secuencial de definición de lista de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- Crear actividades de flujo de trabajo.

- Controlar eventos de actividad de flujo de trabajo.

> [!NOTE]
> Aunque en este tutorial se usa un proyecto de flujo de trabajo secuencial, el proceso es idéntico para un proyecto de flujo de trabajo de equipo de estado.
>
> Además, es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesita los componentes siguientes para completar este tutorial:

- Ediciones compatibles de Microsoft Windows y SharePoint.

- Visual Studio.

## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>Agregar propiedades a la biblioteca de documentos compartidos de SharePoint
 Para realizar un seguimiento del estado de revisión de los documentos en la biblioteca de **documentos compartidos** , crearemos tres nuevas propiedades para los documentos compartidos en nuestro sitio de SharePoint: `Status`, `Assignee`y `Review Comments`. Definimos estas propiedades en la biblioteca de **documentos compartidos** .

#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Para agregar propiedades a la biblioteca de documentos compartidos de SharePoint

1. Abra un sitio de SharePoint, como http://\<nombre del sistema >/SitePages/Home.aspx, en un explorador Web.

2. En la barra de inicio rápido, elija **SharedDocuments**.

3. Elija **biblioteca** en la cinta **herramientas de bibliotecas** y, a continuación, elija el botón **crear columna** en la cinta de opciones para crear una nueva columna.

4. Asigne un nombre al **Estado del documento**de la columna, establezca su tipo en **Choice (menú para elegir)** , especifique las tres opciones siguientes y, a continuación, elija el botón **Aceptar** :

    - **Revisión necesaria**

    - **Revisión completada**

    - **Cambios solicitados**

5. Cree dos columnas más y asígneles un nombre **asignado** y **Revise los comentarios**. Establezca el tipo de columna de asignación como una sola línea de texto y el tipo de columna revisar comentarios como varias líneas de texto.

## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Habilitar la edición de documentos sin necesidad de una desprotección
 Es más fácil probar la plantilla de flujo de trabajo cuando se pueden editar los documentos sin tener que desprotegerlos. En el procedimiento siguiente, configurará el sitio de SharePoint para habilitarlo.

#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Para permitir que los documentos se editen sin desprotegerlos

1. En la barra de inicio rápido, elija el vínculo **documentos compartidos** .

2. En la cinta **herramientas de biblioteca** , elija la pestaña **biblioteca** y, después, elija el botón configuración de la **biblioteca** para mostrar la página Configuración de la **biblioteca de documentos** .

3. En la sección **Configuración general** , elija el vínculo **configuración de versiones** para mostrar la página de configuración de control de **versiones** .

4. Compruebe que la configuración de **requerir que los documentos se** desprotejan antes de que se puedan editar es **no**. Si no es así, cámbielo a **no** y elija el botón **Aceptar** .

5. Cierre el explorador.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Crear un proyecto de flujo de trabajo secuencial de SharePoint
 Un flujo de trabajo secuencial es un conjunto de pasos que se ejecutan en orden hasta que finaliza la última actividad. En este procedimiento, se creará un flujo de trabajo secuencial que se aplicará a nuestra lista de documentos compartidos. El Asistente para flujos de trabajo le permite asociar el flujo de trabajo con la definición del sitio o la definición de la lista, y le permite determinar cuándo se iniciará el flujo de trabajo.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Para crear un proyecto de flujo de trabajo secuencial de SharePoint

1. Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. En la barra de menús, elija **archivo**  > **nuevo**  > **proyecto** para mostrar el cuadro de diálogo **nuevo proyecto** .

3. Expanda el nodo **SharePoint** en **Visual C#**  o en **Visual Basic**y, a continuación, elija el nodo **2010** .

4. En el panel **plantillas** , elija la plantilla de **proyecto de SharePoint 2010** .

5. En el cuadro **nombre** , escriba **MySharePointWorkflow** y elija el botón **Aceptar** .

     Aparece el **Asistente para la personalización de SharePoint** .

6. En la página **especifique el sitio y el nivel de seguridad de la depuración** , elija el botón de opción **implementar como solución de granja de servidores** y, después, elija el botón **Finalizar** para aceptar el nivel de confianza y el sitio predeterminado.

     Este paso establece el nivel de confianza de la solución como solución de granja, la única opción disponible para los proyectos de flujo de trabajo. Para obtener más información, vea [consideraciones sobre las soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).

7. En **Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija **proyecto** > **Agregar nuevo elemento**.

8. En **Visual C#**  o **Visual Basic**, expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

9. En el panel **plantillas** , elija la plantilla **flujo de trabajo secuencial (solo solución de granja de servidores)** y, a continuación, elija el botón **Agregar** .

     Aparece el **Asistente para la personalización de SharePoint** .

10. En la página **especificar el nombre del flujo de trabajo para la depuración** , acepte el nombre predeterminado (**MySharePointWorkflow-Workflow1**). Mantenga el valor predeterminado de tipo de plantilla de flujo de trabajo, **lista flujo de trabajo**y, a continuación, elija el botón **siguiente** .

11. En la página ¿desea que **Visual Studio asocie automáticamente el flujo de trabajo en una sesión de depuración?** , elija el botón **siguiente** para aceptar todos los valores predeterminados.

     Este paso asocia automáticamente el flujo de trabajo a la biblioteca de documentos compartidos.

12. En la página **especificar las condiciones de inicio del flujo de trabajo** , deje las opciones predeterminadas seleccionadas en la sección **¿Cómo desea que se inicie el flujo** de trabajo? y elija el botón **Finalizar** .

     Esta página le permite especificar Cuándo se inicia el flujo de trabajo. De forma predeterminada, el flujo de trabajo se inicia cuando un usuario lo inicia manualmente en SharePoint o cuando se crea un elemento al que está asociado el flujo de trabajo.

## <a name="create-workflow-activities"></a>Crear actividades de flujo de trabajo
 Los flujos de trabajo contienen una o varias *actividades* que representan las acciones que se deben realizar. Use el diseñador de flujo de trabajo para organizar las actividades de un flujo de trabajo. En este procedimiento, agregaremos dos actividades al flujo de trabajo: HandleExternalEventActivity y OnWorkFlowItemChanged. Estas actividades supervisan el estado de revisión de los documentos en la lista de **documentos compartidos**

#### <a name="to-create-workflow-activities"></a>Para crear actividades de flujo de trabajo

1. El flujo de trabajo se debe mostrar en el diseñador de flujo de trabajo. Si no es así, Abra **Workflow1.CS** o **Workflow1. VB** en **Explorador de soluciones**.

2. En el diseñador, elija la actividad **OnWorkflowActivated1** .

3. En la ventana **propiedades** , escriba **onWorkflowActivated** junto a la propiedad **invocada** y, a continuación, elija la tecla entrar.

     Se abre el editor de código y se agrega un método de control de eventos denominado onWorkflowActivated al archivo de código Workflow1.

4. Vuelva al diseñador de flujo de trabajo, abra el cuadro de herramientas y, a continuación, expanda el nodo **Windows Workflow v 3.0** .

5. En el nodo **Windows Workflow v 3.0** del **cuadro de herramientas**, realice uno de los siguientes conjuntos de pasos:

    1. Abra el menú contextual de la actividad **While** y, a continuación, elija **copiar**. En el diseñador de flujo de trabajo, abra el menú contextual de la línea bajo la actividad **onWorkflowActivated1** y, a continuación, elija **pegar**.

    2. Arrastre la actividad **While** desde el **cuadro de herramientas** al diseñador de flujo de trabajo y conecte la actividad a la línea bajo la actividad **onWorkflowActivated1** .

6. Elija la actividad **WhileActivity1** .

7. En la ventana **propiedades** **, establezca condición en condición de** código.

8. Expanda la propiedad **condición** , escriba **isWorkflowPending** junto a la propiedad **condición** secundaria y, a continuación, elija la tecla entrar.

     Se abre el editor de código y se agrega un método denominado isWorkflowPending al archivo de código Workflow1.

9. Vuelva al diseñador de flujo de trabajo, abra el cuadro de herramientas y, a continuación, expanda el nodo **flujo de trabajo de SharePoint** .

10. En el nodo **flujo de trabajo de SharePoint** del cuadro de **herramientas**, realice uno de los siguientes conjuntos de pasos:

    - Abra el menú contextual de la actividad **OnWorkflowItemChanged** y, a continuación, elija **copiar**. En el diseñador de flujo de trabajo, abra el menú contextual de la línea dentro de la actividad **whileActivity1** y, a continuación, elija **pegar**.

    - Arrastre la actividad **OnWorkflowItemChanged** desde el **cuadro de herramientas** al diseñador de flujo de trabajo y conecte la actividad a la línea dentro de la actividad **whileActivity1** .

11. Elija la actividad **onWorkflowItemChanged1** .

12. En la ventana **propiedades** , establezca las propiedades como se muestra en la tabla siguiente.

    |Propiedad.|Valor|
    |--------------|-----------|
    |**CorrelationToken**|**workflowToken**|
    |**Invoca**|**onWorkflowItemChanged**|

## <a name="handle-activity-events"></a>Controlar eventos de actividad
 Por último, compruebe el estado del documento de cada actividad. Si el documento se ha revisado, el flujo de trabajo ha finalizado.

#### <a name="to-handle-activity-events"></a>Para controlar eventos de actividad

1. En *Workflow1.CS* o *Workflow1. VB*, agregue el siguiente campo a la parte superior de la clase `Workflow1`. Este campo se utiliza en una actividad para determinar si el flujo de trabajo ha finalizado.

    ```vb
    Dim workflowPending As Boolean = True
    ```

    ```csharp
    Boolean workflowPending = true;
    ```

2. Agregue el método siguiente a la clase `Workflow1`. Este método comprueba el valor de la propiedad `Document Status` de la lista documentos para determinar si se ha revisado el documento. Si la propiedad `Document Status` está establecida en `Review Complete`, el método `checkStatus` establece el campo `workflowPending` en **false** para indicar que el flujo de trabajo está listo para finalizar.

    ```vb
    Private Sub checkStatus()
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then
            workflowPending = False
        End If
    End Sub
    ```

    ```csharp
    private void checkStatus()
    {
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")
        workflowPending = false;
    }
    ```

3. Agregue el código siguiente a los métodos `onWorkflowActivated` y `onWorkflowItemChanged` para llamar al método `checkStatus`. Cuando se inicia el flujo de trabajo, el método `onWorkflowActivated` llama al método `checkStatus` para determinar si el documento ya se ha revisado. Si no se ha revisado, el flujo de trabajo continúa. Cuando se guarda el documento, el método `onWorkflowItemChanged` llama de nuevo al método `checkStatus` para determinar si se ha revisado el documento. Aunque el campo `workflowPending` está establecido en **true**, el flujo de trabajo continúa ejecutándose.

    ```vb
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)
        checkStatus()
    End Sub

    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)
        checkStatus()
    End Sub
    ```

    ```csharp
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)
    {
        // Check the status.
        checkStatus();
    }

    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)
    {
        // Check the status.
        checkStatus();
    }
    ```

4. Agregue el código siguiente al método `isWorkflowPending` para comprobar el estado de la propiedad `workflowPending`. Cada vez que se guarda el documento, la actividad **whileActivity1** llama al método `isWorkflowPending`. Este método examina la propiedad <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> del objeto <xref:System.Workflow.Activities.ConditionalEventArgs> para determinar si la actividad **WhileActivity1** debe continuar o finalizar. Si la propiedad se establece en **true**, la actividad continúa. De lo contrario, la actividad finaliza y el flujo de trabajo finaliza.

    ```vb
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)
        e.Result = workflowPending
    End Sub
    ```

    ```csharp
    private void isWorkflowPending(object sender, ConditionalEventArgs e)
    {
        e.Result = workflowPending;
    }
    ```

5. Guarde el proyecto.

## <a name="test-the-sharepoint-workflow-template"></a>Probar la plantilla de flujo de trabajo de SharePoint
 Al iniciar el depurador, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] implementa la plantilla de flujo de trabajo en el servidor de SharePoint y asocia el flujo de trabajo a la lista de **documentos compartidos** . Para probar el flujo de trabajo, inicie una instancia del flujo de trabajo desde un documento en la lista **documentos compartidos** .

#### <a name="to-test-the-sharepoint-workflow-template"></a>Para probar la plantilla de flujo de trabajo de SharePoint

1. En *Workflow1.CS* o *Workflow1. VB*, establezca un punto de interrupción junto al método **onWorkflowActivated** .

2. Elija la tecla **F5** para compilar y ejecutar la solución.

     Aparece el sitio de SharePoint.

3. En el panel de navegación de SharePoint, elija el vínculo **documentos compartidos** .

4. En la página **documentos compartidos** , elija el vínculo **documentos** en la pestaña **herramientas de biblioteca** y, a continuación, elija el botón **cargar documento** .

5. En el cuadro de diálogo **cargar documento** , elija el botón **examinar** , elija cualquier archivo de documento, elija el botón **abrir** y, a continuación, elija el botón **Aceptar** .

     Esto carga el documento seleccionado en la lista **documentos compartidos** e inicia el flujo de trabajo.

6. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], compruebe que el depurador se detiene en el punto de interrupción situado junto al método `onWorkflowActivated`.

7. Elija la tecla **F5** para continuar con la ejecución.

8. Puede cambiar la configuración del documento aquí, pero deje los valores predeterminados por ahora eligiendo el botón **Guardar** .

     Esto le devolverá a la página **documentos compartidos** del sitio web predeterminado de SharePoint.

9. En la página **documentos compartidos** , compruebe que el valor que se encuentra debajo de la columna **MySharePointWorkflow-Workflow1** está establecido **en en curso**. Esto indica que el flujo de trabajo está en curso y que el documento está a la espera de la revisión.

10. En la página **documentos compartidos** , elija el documento, elija la flecha que aparece y, a continuación, elija el elemento de menú **Editar propiedades** .

11. Establezca el **Estado del documento** en **revisión completada**y, a continuación, elija el botón **Guardar** .

     Esto le devolverá a la página **documentos compartidos** del sitio web predeterminado de SharePoint.

12. En la página **documentos compartidos** , compruebe que el valor que se encuentra debajo de la columna **Estado del documento** está establecido en **revisar completado**. Actualice la página **documentos compartidos** y compruebe que el valor que se encuentra debajo de la columna **MySharePointWorkflow-Workflow1** está establecido en **completado**. Esto indica que el flujo de trabajo ha finalizado y que se ha revisado el documento.

## <a name="next-steps"></a>Pasos siguientes
 Puede obtener más información sobre cómo crear plantillas de flujo de trabajo en estos temas:

- Para obtener más información sobre las actividades de flujo de trabajo de SharePoint, vea [actividades de flujo de trabajo para SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

- Para obtener más información sobre las actividades de Windows Workflow Foundation, vea [espacio de nombres System. Workflow. Activities](/dotnet/api/system.windows.media.color).

## <a name="see-also"></a>Vea también
- [Crear soluciones de flujo de trabajo de SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Plantillas de proyecto y de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md)
- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md) (Compilar y depurar las soluciones de SharePoint)
