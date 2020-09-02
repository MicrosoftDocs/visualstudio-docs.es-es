---
title: Crear flujo de trabajo con formularios de asociación e iniciación
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6f257dfed2fe439c5ab22ab9951b6258116c6567
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86017132"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>Tutorial: creación de un flujo de trabajo con formularios de asociación e iniciación
  En este tutorial se muestra cómo crear un flujo de trabajo secuencial básico que incorpora el uso de los formularios de asociación e iniciación. Se trata de formularios ASPX que permiten agregar parámetros a un flujo de trabajo cuando el administrador de SharePoint lo asocia primero (el formulario de asociación) y cuando el usuario inicia el flujo de trabajo (el formulario de inicio).

 En este tutorial se describe un escenario en el que un usuario desea crear un flujo de trabajo de aprobación para los informes de gastos que tiene los siguientes requisitos:

- Cuando el flujo de trabajo está asociado a una lista, se solicita al administrador un formulario de asociación en el que se especifica un límite de dólar para los informes de gastos.

- Los empleados cargan sus informes de gastos en la lista Documentos compartidos, inician el flujo de trabajo y, a continuación, escriben el total de gastos en el formulario de inicio del flujo de trabajo.

- Si el total del informe de gastos de un empleado supera el límite predefinido del administrador, se crea una tarea para que el administrador del empleado apruebe el informe de gastos. Sin embargo, si el total del informe de gastos de un empleado es menor o igual que el límite de gastos, se escribe un mensaje aprobado automáticamente en la lista de historial del flujo de trabajo.

  En este tutorial se muestran las tareas siguientes:

- Crear un proyecto de flujo de trabajo secuencial de definición de lista de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Crear una programación de flujo de trabajo.

- Controlar eventos de actividad de flujo de trabajo.

- Crear la Asociación de flujo de trabajo y los formularios de iniciación.

- Asociar el flujo de trabajo.

- Iniciar manualmente el flujo de trabajo.

> [!NOTE]
> Aunque en este tutorial se usa un proyecto de flujo de trabajo secuencial, el proceso es el mismo para los flujos de trabajo de equipo de estado.
>
> Además, es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] interfaz de usuario en las siguientes instrucciones. La [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] edición que tiene y la configuración que usa determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint.

- Visual Studio.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Crear un proyecto de flujo de trabajo secuencial de SharePoint
 En primer lugar, cree un proyecto de flujo de trabajo secuencial en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Un flujo de trabajo secuencial es una serie de pasos que se ejecutan en orden hasta que finaliza la última actividad. En este procedimiento, creará un flujo de trabajo secuencial que se aplica a la lista de documentos compartidos de SharePoint. El asistente del flujo de trabajo le permite asociar el flujo de trabajo con el sitio o la definición de la lista, y le permite determinar cuándo se iniciará el flujo de trabajo.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Para crear un proyecto de flujo de trabajo secuencial de SharePoint

1. En la barra de menús, elija **archivo**  >  **nuevo**  >  **proyecto** para mostrar el cuadro de diálogo **nuevo proyecto** .

2. Expanda el nodo **SharePoint** en **Visual C#** o **Visual Basic**y, a continuación, elija el nodo **2010** .

3. En el panel **plantillas** , elija la plantilla de proyecto de **proyecto de SharePoint 2010** .

4. En el cuadro **nombre** , escriba **ExpenseReport** y elija el botón **Aceptar** .

     Aparece el **Asistente para la personalización de SharePoint** .

5. En la página **especifique el sitio y el nivel de seguridad de la depuración** , elija el botón de opción **implementar como solución de granja de servidores** y, después, elija el botón **Finalizar** para aceptar el nivel de confianza y el sitio predeterminado.

     En este paso también se establece el nivel de confianza de la solución como solución de granja de servidores, que es la única opción disponible para los proyectos de flujo de trabajo.

6. En el **Explorador de soluciones**, elija el nodo de proyecto.

7. En la barra de menús, elija **proyecto**  >  **Agregar nuevo elemento**.

8. En **Visual C#** o **Visual Basic**, expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

9. En el panel **plantillas** , elija plantilla **flujo de trabajo secuencial (solo solución de granja de servidores)** y, a continuación, elija el botón **Agregar** .

     Aparece el **Asistente para la personalización de SharePoint** .

10. En la página **especificar el nombre del flujo de trabajo para la depuración** , acepte el nombre predeterminado (**ExpenseReport-Workflow1**). Mantenga el valor predeterminado de tipo de plantilla de flujo de trabajo (**Mostrar flujo de trabajo)**. Elija el botón **Siguiente**.

11. En la página **¿quiere que Visual Studio asocie automáticamente el flujo de trabajo en una sesión de depuración?** , desactive la casilla que asocia automáticamente la plantilla de flujo de trabajo si está activada.

     Este paso le permite asociar manualmente el flujo de trabajo a la lista de documentos compartidos más adelante, donde se muestra el formulario de asociación.

12. Elija el botón **Finalizar**.

## <a name="add-an-association-form-to-the-workflow"></a>Agregar un formulario de asociación al flujo de trabajo
 A continuación, cree un. Formulario de asociación ASPX que aparece cuando el administrador de SharePoint asocia primero el flujo de trabajo a un documento de informe de gastos.

#### <a name="to-add-an-association-form-to-the-workflow"></a>Para agregar un formulario de asociación al flujo de trabajo

1. Elija el nodo **Workflow1** en **Explorador de soluciones**.

2. En la barra de menús, elija **proyecto**  >  **Agregar nuevo elemento** para mostrar el cuadro de diálogo **Agregar nuevo elemento** .

3. En la vista de árbol del cuadro de diálogo, expanda **Visual C#** o **Visual Basic** (dependiendo del lenguaje del proyecto), expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

4. En la lista de plantillas, elija la plantilla de **formulario Asociación de flujo de trabajo** .

5. En el cuadro de texto **nombre** , escriba **ExpenseReportAssocForm. aspx**.

6. Elija el botón **Agregar** para agregar el formulario al proyecto.

## <a name="designing-and-coding-the-association-form"></a>Diseñar y codificar el formulario de asociación
 En este procedimiento, se introduce la funcionalidad en el formulario de asociación mediante la adición de controles y código.

#### <a name="to-design-and-code-the-association-form"></a>Para diseñar y codificar el formulario de asociación

1. En el formulario de asociación (ExpenseReportAssocForm. aspx), busque el `asp:Content` elemento que contiene `ID="Main"` .

2. Directamente después de la primera línea de este elemento de contenido, agregue el código siguiente para crear una etiqueta y un cuadro de texto que solicite el límite de aprobación de gastos (*AutoApproveLimit*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" runat="server" />
    <br /><br />
    ```

3. Expanda el archivo **ExpenseReportAssocForm. aspx** en **Explorador de soluciones** para mostrar sus archivos dependientes.

    > [!NOTE]
    > Si el proyecto está en [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] , debe elegir el botón **Ver todos los archivos** para realizar este paso.

4. Abra el menú contextual del archivo ExpenseReportAssocForm. aspx y elija **Ver código**.

5. Reemplace el `GetAssociationData` método por:

    ```vb
    Private Function GetAssociationData() As String
        ' TODO: Return a string that contains the association data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return Me.AutoApproveLimit.Text
    End Function
    ```

    ```csharp
    private string GetAssociationData()
    {
        // TODO: Return a string that contains the association data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.AutoApproveLimit.Text;
    }
    ```

## <a name="add-an-initiation-form-to-the-workflow"></a>Agregar un formulario de inicio al flujo de trabajo
 A continuación, cree el formulario de inicio que aparece cuando los usuarios ejecutan el flujo de trabajo con sus informes de gastos.

#### <a name="to-create-an-initiation-form"></a>Para crear un formulario de inicio

1. Elija el nodo **Workflow1** en **Explorador de soluciones**.

2. En la barra de menús, elija **proyecto**  >  **Agregar nuevo elemento** mostrar el cuadro de diálogo **Agregar nuevo elemento** .

3. En la vista de árbol del cuadro de diálogo, expanda **Visual C#** o **Visual Basic**  (dependiendo del lenguaje del proyecto), expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

4. En la lista de plantillas, elija la plantilla **formulario de inicio de flujo de trabajo** .

5. En el cuadro de texto **nombre** , escriba **ExpenseReportInitForm. aspx**.

6. Elija el botón **Agregar** para agregar el formulario al proyecto.

## <a name="designing-and-coding-the-initiation-form"></a>Diseñar y codificar el formulario de inicio
 A continuación, introduzca la funcionalidad en el formulario de inicio agregando controles y código.

#### <a name="to-code-the-initiation-form"></a>Para codificar el formulario de inicio

1. En el formulario de inicio (ExpenseReportInitForm. aspx), busque el `asp:Content` elemento que contiene `ID="Main"` .

2. Directamente después de la primera línea de este elemento de contenido, agregue el código siguiente para crear una etiqueta y un cuadro de texto que muestre el límite de aprobación de gastos (*AutoApproveLimit*) que se especificó en el formulario de asociación, y otra etiqueta y un cuadro de texto para solicitar el total de gastos (*ExpenseTotal*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />
    <br /><br />
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />

    <asp:TextBox ID="ExpenseTotal" runat="server" />
    <br /><br />
    ```

3. Expanda el archivo **ExpenseReportInitForm. aspx** en **Explorador de soluciones** para mostrar sus archivos dependientes.

4. Abra el menú contextual del archivo ExpenseReportInitForm. aspx y elija **Ver código**.

5. Reemplace el `Page_Load` método por el ejemplo siguiente:

    ```vb
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As
      EventArgs) Handles Me.Load
        InitializeParams()
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New
          Guid(associationGuid)).AssociationData
        ' Optionally, add code here to pre-populate your form fields.
    End Sub
    ```

    ```csharp
    protected void Page_Load(object sender, EventArgs e)
    {
        InitializeParams();
        this.AutoApproveLimit.Text =
          workflowList.WorkflowAssociations[new
          Guid(associationGuid)].AssociationData;
    }
    ```

6. Reemplace el `GetInitiationData` método por el ejemplo siguiente:

    ```vb
    ' This method is called when the user clicks the button to start the workflow.
    Private Function GetInitiationData() As String
        Return Me.ExpenseTotal.Text
        ' TODO: Return a string that contains the initiation data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return String.Empty
    End Function
    ```

    ```csharp
    // This method is called when the user clicks the button to start the workflow.
    private string GetInitiationData()
    {
        // TODO: Return a string that contains the initiation data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.ExpenseTotal.Text;
    }
    ```

## <a name="cutomize-the-workflow"></a>Cutomize el flujo de trabajo
 A continuación, personalice el flujo de trabajo. Más adelante, asociará dos formularios al flujo de trabajo.

#### <a name="to-customize-the-workflow"></a>Para personalizar el flujo de trabajo

1. Para mostrar el flujo de trabajo en el diseñador de flujo de trabajo, abra Workflow1 en el proyecto.

2. En el **cuadro de herramientas**, expanda el nodo **Windows Workflow v 3.0** y busque la actividad **ifelse** .

3. Agregue esta actividad al flujo de trabajo mediante uno de los siguientes pasos:

    - Abra el menú contextual de la actividad **ifelse** , elija **copiar**, abra el menú contextual de la línea bajo la actividad **onWorkflowActivated1** en el diseñador de flujo de trabajo y, a continuación, elija **pegar**.

    - Arrastre la actividad **ifelse** desde el **cuadro de herramientas**y conéctela a la línea bajo la actividad **onWorkflowActiviated1** en el diseñador de flujo de trabajo.

4. En el cuadro de herramientas, expanda el nodo **flujo de trabajo de SharePoint** y busque la actividad **CreateTask** .

5. Agregue esta actividad al flujo de trabajo mediante uno de los siguientes pasos:

    - Abra el menú contextual de la actividad **CreateTask** , elija **copiar**, abra el menú contextual de una de las dos áreas de **colocar actividades aquí** dentro de **IfElseActivity1** en el diseñador de flujo de trabajo y, a continuación, elija **pegar**.

    - Arrastre la actividad **CreateTask** desde el **cuadro de herramientas** hasta una de las dos áreas de **colocación aquí** en **IfElseActivity1**.

6. En la ventana **propiedades** , escriba un valor de propiedad de *taskToken* para la propiedad **CorrelationToken** .

7. Expanda la propiedad **CorrelationToken** eligiendo el signo más (![TreeView Plus](../sharepoint/media/plus.gif "Signo más de TreeView")) junto a ella.

8. Elija la flecha desplegable de la subpropiedad **OwnerActivityName** y establezca el valor de *Workflow1* .

9. Elija la propiedad **TaskId** y, a continuación, elija el botón de puntos suspensivos (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")) para mostrar el cuadro de diálogo **propiedad de enlace** .

10. Elija la pestaña **enlazar a un nuevo miembro** , elija el botón de opción **crear campo** y, a continuación, elija el botón **Aceptar** .

11. Elija la propiedad **TaskProperties** y, a continuación, elija el botón de puntos suspensivos (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")) para mostrar el cuadro de diálogo **propiedad de enlace** .

12. Elija la pestaña **enlazar a un nuevo miembro** , elija el botón de opción **crear campo** y, a continuación, elija el botón **Aceptar** .

13. En el **cuadro de herramientas**, expanda el nodo **flujo de trabajo de SharePoint** y busque la actividad **LogToHistoryListActivity** .

14. Agregue esta actividad al flujo de trabajo mediante uno de los siguientes pasos:

    - Abra el menú contextual de la actividad **LogToHistoryListActivity** , elija **copiar**, abra el menú contextual del área otras **actividades de colocación aquí** en **IfElseActivity1** en el diseñador de flujo de trabajo y, a continuación, elija **pegar**.

    - Arrastre la actividad **LogToHistoryListActivity** desde el **cuadro de herramientas**y colóquela en el área otras **actividades de colocación aquí** dentro de **IfElseActivity1**.

## <a name="add-code-to-the-workflow"></a>Agregar código al flujo de trabajo
 A continuación, agregue código al flujo de trabajo para proporcionarle la funcionalidad.

#### <a name="to-add-code-to-the-workflow"></a>Para agregar código al flujo de trabajo

1. Abra el menú contextual de la actividad **createTask1** en el diseñador de flujo de trabajo y, a continuación, elija **Ver código**.

2. Agregue el método siguiente:

    ```vb
    Private Sub createTask1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        createTask1_TaskId1 = Guid.NewGuid
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"
        createTask1_TaskProperties1.Description = "Please approve the
          expense report"
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed"
    End Sub
    ```

    ```csharp
    private void createTask1_MethodInvoking(object sender, EventArgs e)
    {
        createTask1_TaskId1 = Guid.NewGuid();
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";
        createTask1_TaskProperties1.Description = "Please approve the
          expense report";
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed";
    }
    ```

    > [!NOTE]
    > En el código, reemplace `somedomain\\someuser` por un dominio y nombre de usuario para los que se creará una tarea, como, por ejemplo, " `Office\\JoeSch` ". Para realizar pruebas, es más fácil usar la cuenta con la que está desarrollando.

3. Debajo del `MethodInvoking` método, agregue el siguiente ejemplo:

    ```vb
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As
      ConditionalEventArgs)
        Dim approval As Boolean = False
        If (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData)) Then
            approval = True
        End If
        e.Result = approval
    End Sub
    ```

    ```csharp
    private void checkApprovalNeeded(object sender, ConditionalEventArgs
      e)
    {
        bool approval = false;
        if (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData))
        {
            approval = true;
        }
        e.Result = approval;
    }
    ```

4. En el diseñador de flujo de trabajo, elija la actividad **ifElseBranchActivity1** .

5. En la ventana **propiedades** , elija la flecha desplegable de la propiedad **condición** y, a continuación, establezca el valor de *condición de código* .

6. Expanda la propiedad **condición** eligiendo el signo más (![TreeView Plus](../sharepoint/media/plus.gif "Signo más de TreeView")) junto a ella y, a continuación, establezca su valor en *checkApprovalNeeded*.

7. En el diseñador de flujo de trabajo, abra el menú contextual de la actividad **logToHistoryListActivity1** y, a continuación, elija **generar controladores** para generar un método vacío para el `MethodInvoking` evento.

8. Reemplace el `MethodInvoking` código por lo siguiente:

    ```vb
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto
          approved for " + workflowProperties.InitiationData)
    End Sub
    ```

    ```csharp
    private void logToHistoryListActivity1_MethodInvoking(object sender,
      EventArgs e)
    {
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was
          auto approved for " + workflowProperties.InitiationData;
    }
    ```

9. Elija la tecla **F5** para depurar el programa.

     Esto compila la aplicación, la empaqueta, la implementa, activa sus características, recicla el [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] grupo de aplicaciones y, a continuación, inicia el explorador en la ubicación especificada en la propiedad **dirección URL del sitio** .

## <a name="associating-the-workflow-to-the-documents-list"></a>Asociar el flujo de trabajo a la lista de documentos
 A continuación, muestre el formulario de Asociación de flujo de trabajo asociando el flujo de trabajo a la lista de **SharedDocuments** en el sitio de SharePoint.

#### <a name="to-associate-the-workflow"></a>Para asociar el flujo de trabajo

1. Elija el vínculo **documentos compartidos** en la barra de inicio rápido.

2. Elija el vínculo **biblioteca** en la pestaña **herramientas de biblioteca** y, a continuación, elija el botón de la cinta configuración de la **biblioteca** .

3. En la sección **permisos y administración** , elija el vínculo **configuración de flujo de trabajo** y, a continuación, elija el vínculo **Agregar un flujo de trabajo** en la página flujos de **trabajo** .

4. En la lista superior de la página Configuración del flujo de trabajo, elija la plantilla **ExpenseReport-Workflow1** .

5. En el campo siguiente, escriba **ExpenseReportWorkflow** y, a continuación, elija el botón **siguiente** .

     Esto asocia el flujo de trabajo a la lista de **documentos compartidos** y muestra el formulario de Asociación de flujo de trabajo.

6. En el cuadro de texto **límite de aprobación automática** , escriba **1200** y, a continuación, elija el botón **asociar flujo de trabajo** .

## <a name="start-the-workflow"></a>Iniciar el flujo de trabajo
 A continuación, asocie el flujo de trabajo a uno de los documentos de la lista **documentos compartidos** para mostrar el formulario de inicio del flujo de trabajo.

#### <a name="to-start-the-workflow"></a>Para iniciar el flujo de trabajo

1. En la página de SharePoint, elija el botón **Inicio** .

2. Elija el vínculo **documentos compartidos** en la barra de inicio rápido para mostrar la lista **documentos compartidos** .

3. Elija el vínculo **documentos** en la pestaña **herramientas de biblioteca** en la parte superior de la página y, a continuación, elija el botón **cargar documento** en la cinta de opciones para cargar un nuevo documento en la lista **documentos compartidos** .

4. En el cuadro de diálogo **cargar documento** , elija el botón **examinar** , elija cualquier archivo de documento, elija el botón **abrir** y, a continuación, elija el botón **Aceptar** .

     Puede cambiar la configuración del documento en este cuadro de diálogo, pero dejarlos en los valores predeterminados eligiendo el botón **Guardar** .

5. Elija el documento cargado, elija la flecha desplegable que aparece y, a continuación, elija el elemento **flujos de trabajo** .

6. Elija la imagen situada junto a ExpenseReportWorkflow.

     Esto muestra el formulario de inicio del flujo de trabajo. (Tenga en cuenta que el valor mostrado en el cuadro **límite de aprobación automática** es de solo lectura porque se escribió en el formulario de asociación).

7. En el cuadro de texto **total de gastos** , escriba **1600**y, a continuación, elija el botón **Iniciar flujo de trabajo** .

     Se volverá a mostrar la lista de **documentos compartidos** . Una nueva columna denominada **ExpenseReportWorkflow** con el valor **completado** se agrega al elemento que acaba de iniciar el flujo de trabajo.

8. Elija la flecha desplegable situada junto al documento cargado y, a continuación, elija el elemento **flujos de trabajo** para mostrar la página estado del flujo de trabajo. Elija el valor **completado** en **flujos de trabajo completados**. La tarea se muestra en la sección **tareas** .

9. Elija el título de la tarea para mostrar los detalles de la tarea.

10. Vuelva a la lista **SharedDocuments** y reinicie el flujo de trabajo usando el mismo documento o uno diferente.

11. Escriba una cantidad en la página de inicio que sea menor o igual que la cantidad especificada en la página de asociación (**1200**).

     Cuando esto ocurre, se crea una entrada en la lista de historial en lugar de una tarea. La entrada se muestra en la sección **historial de flujo de trabajo** de la página de estado del flujo de trabajo. Observe el mensaje en la columna **resultado** del evento del historial. Contiene el texto escrito en el `logToHistoryListActivity1.MethodInvoking` evento que incluye la cantidad que se aprobó automáticamente.

## <a name="next-steps"></a>Pasos siguientes
 Puede obtener más información sobre cómo crear plantillas de flujo de trabajo en estos temas:

- Para obtener más información acerca de los flujos de trabajo de SharePoint, vea [flujos de trabajo en Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms416312(v=office.14)).

## <a name="see-also"></a>Consulte también
- [Crear soluciones de flujo de trabajo de SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Tutorial: agregar una página de aplicación a un flujo de trabajo](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)
