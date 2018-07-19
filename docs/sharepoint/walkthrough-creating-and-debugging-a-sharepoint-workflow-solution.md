---
title: 'Tutorial: Crear y depurar una solución de flujo de trabajo de SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6035b8ceb693434e2e8bc652b91ee31ceb3ebe02
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119482"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>Tutorial: Crear y depurar una solución de flujo de trabajo de SharePoint
  Este tutorial muestra cómo crear una plantilla de flujo de trabajo secuencial básico. El flujo de trabajo comprueba una propiedad de una biblioteca de documentos compartidos para determinar si se ha revisado un documento. Si el documento se ha revisado, el flujo de trabajo finaliza.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un proyecto de flujo de trabajo secuencial de definición de lista de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Creación de actividades de flujo de trabajo.  
  
-   Controlar eventos de actividad de flujo de trabajo.  
  
> [!NOTE]  
>  Aunque este tutorial usa un proyecto de flujo de trabajo secuencial, el proceso es idéntico para un proyecto de flujo de trabajo de equipo de estado.  
>   
>  Además, el equipo podría mostrar nombres o ubicaciones para algunos de los usuarios de Visual Studio diferentes elementos de la interfaz en las instrucciones siguientes. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Microsoft Windows y SharePoint. Para obtener más información, consulte [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>Agregar propiedades a la biblioteca de documentos compartidos de SharePoint
 Para realizar un seguimiento del estado de revisión de documentos en el **documentos compartidos** biblioteca, crearemos tres nuevas propiedades de documentos compartidos en nuestro sitio de SharePoint: `Status`, `Assignee`, y `Review Comments`. Se definen estas propiedades en el **documentos compartidos** biblioteca.  
  
#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Para agregar propiedades a la compartidas de SharePoint biblioteca de documentos  
  
1.  Abrir un sitio de SharePoint, como http://\<nombre del sistema > / SitePages en un explorador Web.  
  
2.  En la barra Inicio rápido, elija **SharedDocuments**.  
  
3.  Elija **biblioteca** en el **herramientas de biblioteca** la cinta de opciones y, a continuación, elija el **crear columna** botón en la cinta de opciones para crear una nueva columna.  
  
4.  Nombre de la columna **estado del documento**, establezca su tipo en **elección (menú para elegir)**, especifique las tres opciones siguientes y, a continuación, elija el **Aceptar** botón:  
  
    -   **Revisión necesaria**  
  
    -   **Revisión completada**  
  
    -   **Cambios solicitados**  
  
5.  Cree dos columnas más y llámelos **Assignee** y **comentarios de revisión**. Establecer el tipo de columna de persona asignada como una sola línea de texto y el tipo de columna de comentarios de revisión como varias líneas de texto.  
  
## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Habilitar documentos se editen sin necesidad de una desprotección
 Es más fácil probar la plantilla de flujo de trabajo cuando se pueden editar los documentos sin tener que eche un vistazo. En el siguiente procedimiento, configurará para permitir el sitio de SharePoint.  
  
#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Para habilitar los documentos se editen sin haberlas desprotegido  
  
1.  En la barra Inicio rápido, elija el **documentos compartidos** vínculo.  
  
2.  En el **herramientas de biblioteca** la cinta de opciones, elija la **biblioteca** pestaña y, a continuación, elija el **configuración de la biblioteca** botón para mostrar el **Document Library Settings** página.  
  
3.  En el **configuración General** sección, elija el **configuración de control de versiones** vínculo para mostrar el **configuración de control de versiones** página.  
  
4.  Compruebe que la configuración de **requerir que los documentos que se desprotegerán antes de que se pueden editar** es **No**. Si no es así, cámbielo a **No** y, a continuación, elija el **Aceptar** botón.  
  
5.  Cierre el explorador.  
  
## <a name="create-a-sharepoint-sequential-workflow-project"></a>Crear un proyecto de flujo de trabajo secuencial de SharePoint
 Un flujo de trabajo secuencial es un conjunto de pasos que se ejecuta en orden hasta que finaliza la última actividad. En este procedimiento, se creará un flujo de trabajo secuencial que se aplicará a nuestra lista de documentos compartidos. El Asistente de flujo de trabajo le permite asociar el flujo de trabajo con la definición de sitio o la definición de lista y le permite determinar cuándo se iniciará el flujo de trabajo.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Para crear un proyecto de flujo de trabajo secuencial de SharePoint  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En la barra de menús, elija **archivo** > **New** > **proyecto** para mostrar el **nuevo proyecto** cuadro de diálogo.  
  
3.  Expanda el **SharePoint** nodo bajo **Visual C#** o **Visual Basic**y, a continuación, elija el **2010** nodo.  
  
4.  En el **plantillas** panel, elija el **proyecto de SharePoint 2010** plantilla.  
  
5.  En el **nombre** , escriba **MySharePointWorkflow** y, a continuación, elija el **Aceptar** botón.  
  
     El **Asistente de personalización de SharePoint** aparece.  
  
6.  En el **especificar el nivel de sitio y de seguridad para la depuración** página, elija el **implementar como solución de granja de servidores** botón de opción y, a continuación, elija el **finalizar** botón para aceptar el sitio predeterminado y de nivel de confianza.  
  
     Este paso establece el nivel de confianza para la solución como solución de granja, la única opción disponible para los proyectos de flujo de trabajo. Para obtener más información, consulte [consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  En **el Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija **proyecto** > **Agregar nuevo elemento**.  
  
8.  Bajo **Visual C#** o **Visual Basic**, expanda el **SharePoint** nodo y, a continuación, elija el **2010** nodo.  
  
9. En el **plantillas** panel, elija el **flujo de trabajo secuencial (solución de granja de servidores únicamente)** plantilla y, a continuación, elija el **agregar** botón.  
  
     El **Asistente de personalización de SharePoint** aparece.  
  
10. En el **especificar el nombre de flujo de trabajo de depuración** , acepte el nombre predeterminado (**MySharePointWorkflow - Workflow1**). Mantenga el valor de tipo de plantilla de flujo de trabajo predeterminado, **flujo de trabajo de lista**y, a continuación, elija el **siguiente** botón.  
  
11. En el **desea que Visual Studio asocie automáticamente el flujo de trabajo en una sesión de depuración?** página, elija el **siguiente** botón para aceptar todos los valores predeterminados.  
  
     Este paso asocia automáticamente el flujo de trabajo a la biblioteca de documentos compartidos.  
  
12. En el **especificar las condiciones de cómo se inicia el flujo de trabajo** página, deje las opciones predeterminadas seleccionadas en el **cómo desea iniciar el flujo de trabajo?** sección y elija el **finalizar** botón.  
  
     Esta página permite especificar cuando se inicia el flujo de trabajo. De forma predeterminada, el flujo de trabajo inicia cuando un usuario lo inicia manualmente en SharePoint o cuando se crea un elemento al que está asociado el flujo de trabajo.  
  
## <a name="create-workflow-activities"></a>Crear actividades de flujo de trabajo
 Flujos de trabajo contienen uno o varios *actividades* que representan acciones que deben realizarse. Usar el Diseñador de flujo de trabajo para organizar las actividades de un flujo de trabajo. En este procedimiento, agregaremos dos actividades al flujo de trabajo: HandleExternalEventActivity y OnWorkFlowItemChanged. Estas actividades supervisan el estado de revisión de documentos en el **documentos compartidos** lista  
  
#### <a name="to-create-workflow-activities"></a>Para crear actividades de flujo de trabajo  
  
1.  El flujo de trabajo se debe mostrar en el Diseñador de flujo de trabajo. Si no es así, a continuación, abra **Workflow1.cs** o **Workflow1.vb** en **el Explorador de soluciones**.  
  
2.  En el diseñador, elija el **OnWorkflowActivated1** actividad.  
  
3.  En el **propiedades** ventana, escriba **onWorkflowActivated** junto a la **Invoked** propiedad y, a continuación, elija la tecla ENTRAR.  
  
     Se abre el Editor de código y un método de controlador de eventos denominado onWorkflowActivated se agrega al archivo de código Workflow1.  
  
4.  Cambie al diseñador de flujo de trabajo, abra el cuadro de herramientas y, a continuación, expanda el **Windows Workflow v3.0** nodo.  
  
5.  En el **Windows Workflow v3.0** nodo de la **cuadro de herramientas**, realice uno de los siguientes conjuntos de pasos:  
  
    1.  Abra el menú contextual para el **mientras** actividad y, a continuación, elija **copia**. En el Diseñador de flujo de trabajo, abra el menú contextual de la línea bajo el **onWorkflowActivated1** actividad y, a continuación, elija **pegar**.  
  
    2.  Arrastre el **mientras** actividad desde la **cuadro de herramientas** hasta el Diseñador de flujo de trabajo y conecte la actividad a la línea bajo el **onWorkflowActivated1** actividad.  
  
6.  Elija la **WhileActivity1** actividad.  
  
7.  En el **propiedades** ventana, establezca **condición** a condición de código.  
  
8.  Expanda el **condición** propiedad, escriba **isWorkflowPending** junto a la secundaria **condición** propiedad y, a continuación, elija la tecla ENTRAR.  
  
     Se abre el Editor de código y se agrega un método denominado isWorkflowPending al archivo de código Workflow1.  
  
9. Cambie al diseñador de flujo de trabajo, abra el cuadro de herramientas y, a continuación, expanda el **SharePoint Workflow** nodo.  
  
10. En el **SharePoint Workflow** nodo de la **cuadro de herramientas**, realice uno de los siguientes conjuntos de pasos:  
  
    -   Abra el menú contextual para el **OnWorkflowItemChanged** actividad y, a continuación, elija **copia**. En el Diseñador de flujo de trabajo, abra el menú contextual de la línea dentro de la **whileActivity1** actividad y, a continuación, elija **pegar**.  
  
    -   Arrastre el **OnWorkflowItemChanged** actividad desde la **cuadro de herramientas** hasta el Diseñador de flujo de trabajo y conecte la actividad a la línea dentro de la **whileActivity1** actividad.  
  
11. Elija la **onWorkflowItemChanged1** actividad.  
  
12. En el **propiedades** ventana, establezca las propiedades tal como se muestra en la tabla siguiente.  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**correlationToken**|**workflowToken**|  
    |**Invoca**|**onWorkflowItemChanged**|  
  
## <a name="handle-activity-events"></a>Controlar eventos de actividad
 Por último, compruebe el estado del documento de cada actividad. Si se ha revisado el documento, a continuación, el flujo de trabajo ha finalizado.  
  
#### <a name="to-handle-activity-events"></a>Para controlar los eventos de actividad  
  
1.  En *Workflow1.cs* o *Workflow1.vb*, agregue el siguiente campo a la parte superior de la `Workflow1` clase. Este campo se utiliza en una actividad para determinar si el flujo de trabajo ha terminado.  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  Agregue el método siguiente a la clase `Workflow1`. Este método comprueba el valor de la `Document Status` propiedad de la lista de documentos para determinar si se ha revisado el documento. Si el `Document Status` propiedad está establecida en `Review Complete`, el `checkStatus` método establece el `workflowPending` campo **false** para indicar que el flujo de trabajo está listo para finalizar.  
  
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
  
3.  Agregue el código siguiente a la `onWorkflowActivated` y `onWorkflowItemChanged` métodos para llamar a la `checkStatus` método. Cuando se inicia el flujo de trabajo, el `onWorkflowActivated` llamadas al método el `checkStatus` método para determinar si se ha revisado el documento. Si no se ha revisado, el flujo de trabajo continúa. Cuando se guarda el documento, el `onWorkflowItemChanged` llamadas al método el `checkStatus` método nuevo para determinar si se ha revisado el documento. Mientras el `workflowPending` campo se establece en **true**, el flujo de trabajo continúa ejecutándose.  
  
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
  
4.  Agregue el código siguiente a la `isWorkflowPending` método para comprobar el estado de la `workflowPending` propiedad. Cada vez que se guarda el documento, el **whileActivity1** llamadas actividad el `isWorkflowPending` método. Este método examina el <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> propiedad de la <xref:System.Workflow.Activities.ConditionalEventArgs> objeto para determinar si el **WhileActivity1** actividad debe continuar o en Finalizar. Si la propiedad se establece en **true**, la actividad continúa. En caso contrario, la actividad finaliza y el flujo de trabajo finaliza.  
  
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
  
5.  Guarde el proyecto.  
  
## <a name="test-the-sharepoint-workflow-template"></a>Probar la plantilla de flujo de trabajo de SharePoint
 Cuando se inicia el depurador, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] implementa la plantilla de flujo de trabajo en el servidor de SharePoint y asocia el flujo de trabajo con el **documentos compartidos** lista. Para probar el flujo de trabajo, iniciar una instancia del flujo de trabajo desde un documento en el **documentos compartidos** lista.  
  
#### <a name="to-test-the-sharepoint-workflow-template"></a>Para probar la plantilla de flujo de trabajo de SharePoint  
  
1.  En *Workflow1.cs* o *Workflow1.vb*, establezca un punto de interrupción junto a la **onWorkflowActivated** método.  
  
2.  Elija la **F5** clave para compilar y ejecutar la solución.  
  
     Aparece el sitio de SharePoint.  
  
3.  En el panel de navegación en SharePoint, elija el **documentos compartidos** vínculo.  
  
4.  En el **documentos compartidos** página, elija el **documentos** vincular en el **herramientas de biblioteca** pestaña y, a continuación, elija el **cargar documento** botón .  
  
5.  En el **cargar documento** diálogo cuadro, elija el **examinar** botón, elija cualquier archivo de documento, el **abierto** botón y, a continuación, elija el **Aceptar** botón.  
  
     Esto carga el documento seleccionado en el **documentos compartidos** lista e inicia el flujo de trabajo.  
  
6.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], compruebe que el depurador se detiene en el punto de interrupción junto a la `onWorkflowActivated` método.  
  
7.  Elija la **F5** tecla para continuar la ejecución.  
  
8.  Puede cambiar la configuración para el documento, pero deje los valores predeterminados por ahora eligiendo el **guardar** botón.  
  
     Esto le devuelve a la **documentos compartidos** página del sitio Web de SharePoint de forma predeterminada.  
  
9. En el **documentos compartidos** , comprueba que el valor por debajo del **MySharePointWorkflow - Workflow1** columna está establecida en **en curso**. Esto indica que el flujo de trabajo está en curso y que el documento está esperando la revisión.  
  
10. En el **documentos compartidos** página, elija el documento, elija la flecha que aparece y, a continuación, elija el **editar propiedades** elemento de menú.  
  
11. Establecer **estado del documento** a **Review Complete**y, a continuación, elija el **guardar** botón.  
  
     Esto le devuelve a la **documentos compartidos** página del sitio Web de SharePoint de forma predeterminada.  
  
12. En el **documentos compartidos** , comprueba que el valor por debajo del **estado del documento** columna está establecida en **Review Complete**. Actualizar el **documentos compartidos** página y compruebe que el valor por debajo del **MySharePointWorkflow - Workflow1** columna está establecida en **completado**. Esto indica que ha finalizado el flujo de trabajo y que se ha revisado el documento.  
  
## <a name="next-steps"></a>Pasos siguientes
 Puede obtener más información acerca de cómo crear plantillas de flujo de trabajo en los siguientes temas:  
  
-   Para obtener más información acerca de las actividades de flujo de trabajo de SharePoint, vea [las actividades de flujo de trabajo de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=178992).  
  
-   Para obtener más información acerca de las actividades de Windows Workflow Foundation, vea [System.Workflow.Activities Namespace](http://go.microsoft.com/fwlink/?LinkId=178993).  
  
## <a name="see-also"></a>Vea también
 [Crear soluciones de flujo de trabajo de SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Proyecto de SharePoint y las plantillas de elemento de proyecto](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [Compilar y depurar soluciones de SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
