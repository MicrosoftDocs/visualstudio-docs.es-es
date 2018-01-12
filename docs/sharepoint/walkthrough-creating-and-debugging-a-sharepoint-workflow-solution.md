---
title: "Tutorial: Crear y depurar una solución de flujo de trabajo de SharePoint | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload: office
ms.openlocfilehash: 687116b1fc7f3ad935583b41ff9c19d2d5d13613
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-and-debugging-a-sharepoint-workflow-solution"></a>Tutorial: Crear y depurar una solución de flujo de trabajo de SharePoint
  Este tutorial muestra cómo crear una plantilla de flujo de trabajo secuencial básica. El flujo de trabajo comprueba una propiedad de una biblioteca de documentos compartidos para determinar si se ha revisado un documento. Si el documento se ha revisado, el flujo de trabajo finaliza.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un proyecto de flujo de trabajo secuencial de definición de lista de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Crear actividades de flujo de trabajo.  
  
-   Control de eventos de actividad de flujo de trabajo.  
  
> [!NOTE]  
>  Aunque este tutorial usa un proyecto de flujo de trabajo secuencial, el proceso es idéntico para un proyecto de flujo de trabajo de equipo de estado.  
>   
>  Además, el equipo es posible que muestre nombres o ubicaciones para algunos de los usuarios de Visual Studio diferentes elementos de la interfaz en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Microsoft Windows y SharePoint. Para obtener más información, consulte [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="adding-properties-to-the-sharepoint-shared-documents-library"></a>Agregar propiedades a las de SharePoint biblioteca de documentos compartidos  
 Para realizar un seguimiento del estado de revisión de documentos en la **documentos compartidos** biblioteca, crearemos tres nuevas propiedades para documentos compartidos en nuestro sitio de SharePoint: `Status`, `Assignee`, y `Review Comments`. Definimos estas propiedades en el **documentos compartidos** biblioteca.  
  
#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Para agregar propiedades a la compartidas de SharePoint biblioteca de documentos  
  
1.  Abrir un sitio de SharePoint, por ejemplo, http://\<nombre del sistema > / SitePages, en un explorador Web.  
  
2.  En la barra Inicio rápido, elija **SharedDocuments**.  
  
3.  Elija **biblioteca** en el **herramientas de biblioteca** la cinta de opciones y, a continuación, elija la **crear columna** botón en la cinta de opciones para crear una nueva columna.  
  
4.  Nombre de la columna **estado del documento**, establezca su tipo en **elección (menú para elegir)**, especifique las tres opciones siguientes y, a continuación, elija la **Aceptar** botón:  
  
    -   **Revisión necesitado**  
  
    -   **Revisión completada**  
  
    -   **Cambios solicitados**  
  
5.  Crear dos columnas más y asignarles nombre **encargado** y **comentarios de revisión**. Establecer el tipo de usuario asignado a la columna como una sola línea de texto y el tipo de columna de comentarios de revisión como varias líneas de texto.  
  
## <a name="enabling-documents-to-be-edited-without-requiring-a-check-out"></a>Permitir que los documentos que se editen sin requerir la desprotección  
 Es más fácil probar la plantilla de flujo de trabajo cuando se pueden editar los documentos sin tener que desprotegerlos. En el siguiente procedimiento, configurará para permitir el sitio de SharePoint.  
  
#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Para habilitar los documentos que se editen sin haberlas desprotegido  
  
1.  En la barra Inicio rápido, elija la **documentos compartidos** vínculo.  
  
2.  En el **herramientas de biblioteca** la cinta de opciones, elija la **biblioteca** ficha y, a continuación, elija la **configuración de la biblioteca** botón para mostrar el **deconfiguracióndelabibliotecadedocumentos** página.  
  
3.  En el **configuración General** sección, elija el **configuración de versiones** vínculo para mostrar la **configuración de versiones** página.  
  
4.  Compruebe que la configuración de **solicitar que los documentos se desprotejan antes de que se pueden editar** es **No**. Si no es así, cámbielo a **No** y, a continuación, elija la **Aceptar** botón.  
  
5.  Cierre el explorador.  
  
## <a name="creating-a-sharepoint-sequential-workflow-project"></a>Crear un proyecto de flujo de trabajo secuencial de SharePoint  
 Flujo de trabajo secuencial es un conjunto de pasos que se ejecuta en orden hasta que finaliza la última actividad. En este procedimiento, se creará un flujo de trabajo secuencial que se aplicará a nuestra lista documentos compartidos. El Asistente de flujo de trabajo permite asociar el flujo de trabajo con la definición de sitio o la definición de lista y le permite determinar cuándo se iniciará el flujo de trabajo.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Para crear un proyecto de flujo de trabajo secuencial de SharePoint  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En la barra de menús, elija **archivo**, **New**, **proyecto** para mostrar la **nuevo proyecto** cuadro de diálogo.  
  
3.  Expanda el **SharePoint** nodo bajo **Visual C#** o **Visual Basic**y, a continuación, elija la **2010** nodo.  
  
4.  En el **plantillas** panel, elija la **proyecto de SharePoint 2010** plantilla.  
  
5.  En el **nombre** cuadro, escriba **MySharePointWorkflow** y, a continuación, elija la **Aceptar** botón.  
  
     El **Asistente para personalización de SharePoint** aparece.  
  
6.  En el **especificar el nivel de sitio y la seguridad para la depuración** página, elija la **implementar como solución de granja de servidores** botón de opción y, a continuación, elija la **finalizar** botón para aceptar el sitio de nivel y el valor predeterminado de confianza.  
  
     Este paso establece el nivel de confianza para la solución como solución de granja, la única opción disponible para los proyectos de flujo de trabajo. Para obtener más información, consulte [consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  En **el Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
8.  Bajo **Visual C#** o **Visual Basic**, expanda la **SharePoint** nodo y, a continuación, elija la **2010** nodo.  
  
9. En el **plantillas** panel, elija la **flujo de trabajo secuencial (solución de granja de servidores únicamente)** plantilla y, a continuación, elija la **agregar** botón.  
  
     El **Asistente para personalización de SharePoint** aparece.  
  
10. En el **especificar el nombre de flujo de trabajo para la depuración** , acepte el nombre predeterminado (**MySharePointWorkflow - Workflow1**). Mantenga el valor de tipo de plantilla de flujo de trabajo predeterminado, **flujo de trabajo de lista**y, a continuación, elija la **siguiente** botón.  
  
11. En el **desea que Visual Studio para asociar automáticamente el flujo de trabajo en una sesión de depuración?** página, elija la **siguiente** botón para aceptar todos los valores de configuración predeterminados.  
  
     Este paso asocia automáticamente el flujo de trabajo a la biblioteca de documentos compartidos.  
  
12. En el **especifican las condiciones de cómo se inicia el flujo de trabajo** página, deje las opciones predeterminadas seleccionadas en el **¿cómo desea iniciar el flujo de trabajo?** sección y elija la **finalizar** botón.  
  
     Esta página permite especificar cuando se inicia el flujo de trabajo. De forma predeterminada, el flujo de trabajo inicia cuando un usuario lo inicia manualmente en SharePoint o cuando se crea un elemento al que está asociado el flujo de trabajo.  
  
## <a name="creating-workflow-activities"></a>Crear actividades de flujo de trabajo  
 Flujos de trabajo contienen uno o varios *actividades* que representan acciones que puede realizar. Use el Diseñador de flujo de trabajo para organizar las actividades de un flujo de trabajo. En este procedimiento, agregaremos dos actividades al flujo de trabajo: HandleExternalEventActivity y OnWorkFlowItemChanged. Estas actividades supervisan el estado de revisión de documentos en la **documentos compartidos** lista  
  
#### <a name="to-create-workflow-activities"></a>Para crear actividades de flujo de trabajo  
  
1.  El flujo de trabajo se debe mostrar en el Diseñador de flujo de trabajo. Si no lo es, a continuación, abra **Workflow1.cs** o **Workflow1.vb** en **el Explorador de soluciones**.  
  
2.  En el diseñador, elija la **OnWorkflowActivated1** actividad.  
  
3.  En el **propiedades** ventana, escriba **onWorkflowActivated** junto a la **invocado** propiedad y, a continuación, elija la tecla ENTRAR.  
  
     Se abrirá el Editor de código y un método de controlador de eventos denominado onWorkflowActivated se agrega al archivo de código de Workflow1.  
  
4.  Volver al diseñador de flujo de trabajo, abra el cuadro de herramientas y, a continuación, expanda el **Windows Workflow v3.0** nodo.  
  
5.  En el **Windows Workflow v3.0** nodo de la **cuadro de herramientas**, realice uno de los siguientes conjuntos de pasos:  
  
    1.  Abra el menú contextual para el **mientras** actividad y, a continuación, elija **copia**. En el Diseñador de flujo de trabajo, abra el menú contextual de la línea en la **onWorkflowActivated1** actividad y, a continuación, elija **pegar**.  
  
    2.  Arrastre el **mientras** actividad desde la **cuadro de herramientas** hasta el Diseñador de flujo de trabajo y conecte la actividad a la línea en la **onWorkflowActivated1** actividad.  
  
6.  Elija la **WhileActivity1** actividad.  
  
7.  En el **propiedades** ventana, establezca **condición** a condición de código.  
  
8.  Expanda el **condición** propiedad, escriba **isWorkflowPending** al lado del elemento secundario **condición** propiedad y, a continuación, elija la tecla ENTRAR.  
  
     Se abrirá el Editor de código, y se agrega un método denominado isWorkflowPending al archivo de código de Workflow1.  
  
9. Volver al diseñador de flujo de trabajo, abra el cuadro de herramientas y, a continuación, expanda el **flujo de trabajo de SharePoint** nodo.  
  
10. En el **flujo de trabajo de SharePoint** nodo de la **cuadro de herramientas**, realice uno de los siguientes conjuntos de pasos:  
  
    -   Abra el menú contextual para el **OnWorkflowItemChanged** actividad y, a continuación, elija **copia**. En el Diseñador de flujo de trabajo, abra el menú contextual de la línea dentro del **whileActivity1** actividad y, a continuación, elija **pegar**.  
  
    -   Arrastre el **OnWorkflowItemChanged** actividad desde la **cuadro de herramientas** hasta el Diseñador de flujo de trabajo y conecte la actividad a la línea dentro de la **whileActivity1** actividad.  
  
11. Elija la **onWorkflowItemChanged1** actividad.  
  
12. En el **propiedades** ventana, establezca las propiedades tal como se muestra en la tabla siguiente.  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**CorrelationToken**|**workflowToken**|  
    |**Invoca**|**onWorkflowItemChanged**|  
  
## <a name="handling-activity-events"></a>Control de eventos de actividad  
 Por último, compruebe el estado del documento de cada actividad. Si se ha revisado el documento, se finaliza el flujo de trabajo.  
  
#### <a name="to-handle-activity-events"></a>Para controlar los eventos de actividad  
  
1.  En Workflow1.cs o Workflow1.vb, agregue el siguiente campo a la parte superior de la `Workflow1` clase. Este campo se utiliza en una actividad para determinar si el flujo de trabajo ha terminado.  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  Agregue el método siguiente a la clase `Workflow1`. Este método comprueba el valor de la `Document Status` propiedad de la lista de documentos para determinar si se ha revisado el documento. Si el `Document Status` propiedad está establecida en `Review Complete`, la `checkStatus` método establece la `workflowPending` campo **false** para indicar que el flujo de trabajo está listo para finalizar.  
  
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
  
3.  Agregue el código siguiente a la `onWorkflowActivated` y `onWorkflowItemChanged` métodos para llamar a la `checkStatus` método. Cuando se inicia el flujo de trabajo, el `onWorkflowActivated` llamadas al método el `checkStatus` método para determinar si el documento ya se ha revisado. Si no se ha revisado, el flujo de trabajo continúa. Cuando se guarda el documento, el `onWorkflowItemChanged` llamadas al método el `checkStatus` método nuevo para determinar si se ha revisado el documento. Mientras el `workflowPending` campo está establecido en **true**, el flujo de trabajo continúa ejecutándose.  
  
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
  
4.  Agregue el código siguiente a la `isWorkflowPending` método para comprobar el estado de la `workflowPending` propiedad. Cada vez que se guarda el documento, el **whileActivity1** llamadas de actividad el `isWorkflowPending` método. Este método examina la <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> propiedad de la <xref:System.Workflow.Activities.ConditionalEventArgs> objeto para determinar si la **WhileActivity1** actividad debe continuar o finalizar. Si la propiedad se establece en **true**, la actividad continúa. En caso contrario, la actividad finaliza y se finaliza el flujo de trabajo.  
  
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
  
## <a name="testing-the-sharepoint-workflow-template"></a>Probar la plantilla de flujo de trabajo de SharePoint  
 Cuando se inicia el depurador, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] implementa la plantilla de flujo de trabajo en el servidor de SharePoint y asocia el flujo de trabajo con el **documentos compartidos** lista. Para probar el flujo de trabajo, inicie una instancia del flujo de trabajo de un documento en el **documentos compartidos** lista.  
  
#### <a name="to-test-the-sharepoint-workflow-template"></a>Para probar la plantilla de flujo de trabajo de SharePoint  
  
1.  En Workflow1.cs o Workflow1.vb, establezca un punto de interrupción junto a la **onWorkflowActivated** método.  
  
2.  Presione la tecla F5 para compilar y ejecutar la solución.  
  
     Aparece el sitio de SharePoint.  
  
3.  En el panel de navegación en SharePoint, elija el **documentos compartidos** vínculo.  
  
4.  En el **documentos compartidos** página, elija la **documentos** crear vínculos en la **herramientas de biblioteca** ficha y, a continuación, elija la **cargar documento** botón .  
  
5.  En el **cargar documento** diálogo cuadro, elija la **examinar** botón, elija cualquier archivo de documento, elija la **abiertos** botón y, a continuación, elija el **Aceptar** botón.  
  
     Esto carga el documento seleccionado en el **documentos compartidos** lista e inicia el flujo de trabajo.  
  
6.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], compruebe que el depurador se detiene en el punto de interrupción junto a la `onWorkflowActivated` método.  
  
7.  Elija la tecla F5 para continuar la ejecución.  
  
8.  Puede cambiar la configuración del documento aquí, pero deje los valores predeterminados por ahora eligiendo la **guardar** botón.  
  
     Esto le devuelve a la **documentos compartidos** página del sitio Web de SharePoint de forma predeterminada.  
  
9. En el **documentos compartidos** , comprueba que el valor por debajo del **MySharePointWorkflow - Workflow1** columna se establece en **en curso**. Esto indica que el flujo de trabajo está en curso y que el documento está esperando la revisión.  
  
10. En el **documentos compartidos** página, elija el documento, elija la flecha que aparece y, a continuación, elija la **editar propiedades** elemento de menú.  
  
11. Establecer **estado del documento** a **revisión completa**y, a continuación, elija la **guardar** botón.  
  
     Esto le devuelve a la **documentos compartidos** página del sitio Web de SharePoint de forma predeterminada.  
  
12. En el **documentos compartidos** , comprueba que el valor por debajo del **estado del documento** columna se establece en **revisión completa**. Actualizar el **documentos compartidos** página y compruebe que el valor por debajo del **MySharePointWorkflow - Workflow1** columna se establece en **completado**. Esto indica que ha finalizado el flujo de trabajo y que se ha revisado el documento.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Se puede obtener más información sobre cómo crear plantillas de flujo de trabajo en estos temas:  
  
-   Para obtener más información acerca de las actividades de flujo de trabajo de SharePoint, vea [las actividades de flujo de trabajo para SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=178992).  
  
-   Para más información acerca de las actividades de Windows Workflow Foundation, consulte [System.Workflow.Activities Namespace](http://go.microsoft.com/fwlink/?LinkId=178993).  
  
## <a name="see-also"></a>Vea también  
 [Crear soluciones de flujo de trabajo de SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Proyecto de SharePoint y plantillas de elemento de proyecto](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [Compilar y depurar soluciones de SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  