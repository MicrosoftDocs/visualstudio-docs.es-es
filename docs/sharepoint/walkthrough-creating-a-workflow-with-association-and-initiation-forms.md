---
title: "Tutorial: Crear un flujo de trabajo con formularios de asociaci&#243;n y de iniciaci&#243;n | Microsoft Docs"
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
  - "formularios de asociación [desarrollo de SharePoint en Visual Studio]"
  - "formularios de iniciación [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, formularios de asociación de flujo de trabajo"
  - "desarrollo de SharePoint en Visual Studio, formularios de iniciación de flujo de trabajo"
  - "desarrollo de SharePoint en Visual Studio, flujos de trabajo"
  - "flujos de trabajo [desarrollo de SharePoint en Visual Studio]"
ms.assetid: c8666d8c-b173-4245-8014-9c1cd6acb071
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Tutorial: Crear un flujo de trabajo con formularios de asociaci&#243;n y de iniciaci&#243;n
  En este tutorial se muestra cómo crear un flujo de trabajo secuencial básico que incorpora el uso de formularios de asociación e iniciación.  Éstos son formularios ASPX que permiten agregar parámetros a un flujo de trabajo cuando el administrador de SharePoint lo asocia por primera vez \(formulario de asociación\) y cuando el usuario inicia el flujo de trabajo \(formulario de iniciación\).  
  
 En este tutorial se describe un escenario donde un usuario desea crear un flujo de trabajo de aprobación para los informes de gastos con los requisitos siguientes:  
  
-   Cuando el flujo de trabajo está asociado a una lista, el administrador recibe un formulario de asociación donde escribe un límite en dólares para los informes de gastos.  
  
-   Los empleados cargan sus informes de gastos en la lista Documentos compartidos, inician el flujo de trabajo y, a continuación, escriben el total de gastos en el formulario de iniciación del flujo de trabajo.  
  
-   Si el total de un informe de gastos supera el límite predefinido por el administrador, se crea una tarea para el jefe del empleado que le permita aprobar el informe de gastos.  Sin embargo, si el total del informe de gastos de un empleado es menor o igual que el límite establecido, se escribe un mensaje de aceptación automática en la lista de historial del flujo de trabajo.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un proyecto de flujo de trabajo secuencial de definición de lista de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Crear una programación del flujo de trabajo.  
  
-   Controlar eventos de actividad de flujo de trabajo.  
  
-   Crear formularios de asociación e iniciación de flujo de trabajo.  
  
-   Asociar el flujo de trabajo.  
  
-   Iniciar el flujo de trabajo manualmente.  
  
> [!NOTE]  
>  Aunque en el tutorial se utiliza un proyecto de flujo de trabajo secuencial, el proceso es el mismo para los flujos de trabajo de máquinas de estados.  
>   
>  También es posible que su equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en las siguientes instrucciones.  La edición de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y la configuración que esté usando determinan estos elementos.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Crear un proyecto de flujo de trabajo secuencial de SharePoint  
 Primero, cree un proyecto de flujo de trabajo secuencial en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Un flujo de trabajo secuencial es una sucesión de pasos que se ejecutan en orden hasta que finaliza la última actividad.  En este procedimiento, creará un flujo de trabajo secuencial que se aplica a la lista Documentos compartidos en SharePoint.  El asistente del flujo de trabajo permite asociar el flujo de trabajo con el sitio o la definición de lista y le permite determinar cuándo se iniciará el flujo de trabajo.  
  
#### Para crear un proyecto de flujo de trabajo secuencial de SharePoint  
  
1.  En la barra de menú, elija **archivo**, **new**, **Project** para mostrar el cuadro de diálogo de **Nuevo proyecto** .  
  
2.  Expanda el nodo de **sharepoint** en **Visual C\#** o **Visual Basic**y, a continuación el nodo de **2010** .  
  
3.  En el panel de **Plantillas** , elija la plantilla de proyecto de **SharePoint 2010 Project** .  
  
4.  En el cuadro de **Name** , entre en ExpenseReport y elija el botón de **Aceptar** .  
  
     Aparece el **Asistente para personalización de SharePoint**.  
  
5.  En la página de **Especifique el sitio y el nivel de seguridad de la depuración** , elija el botón de opción de **Implementar como solución de granja de servidores** , y elija el botón de **Finalizar** para aceptar el sitio de nivel de confianza y predeterminado.  
  
     Este paso también establece el nivel de confianza para la solución como solución de granja, la única opción disponible para los proyectos de flujo de trabajo.  
  
6.  En el **Explorador de soluciones**, elija el nodo del proyecto.  
  
7.  En la barra de menús, elija **Proyecto**, **Agregar nuevo elemento**.  
  
8.  En **Visual C\#** o **Visual Basic**, expanda el nodo de **sharepoint** y, a continuación el nodo de **2010** .  
  
9. En el panel de **Plantillas** , elija la plantilla de **Flujo de trabajo secuencial \(solución de granja de servidores únicamente\)** , y elija el botón de **Add** .  
  
     Aparece el **Asistente para personalización de SharePoint**.  
  
10. En la página **Especifique el nombre del flujo de trabajo de depuración**, acepte el nombre predeterminado \(**ExpenseReport \- Workflow1**\).  Mantenga el valor del tipo de la plantilla de flujo de trabajo predeterminado \(**List Workflow\)**.  Elija el botón **Siguiente**.  
  
11. En la página **¿Desea que Visual Studio asocie automáticamente el flujo de trabajo en una sesión de depuración?**, desactive el cuadro que asocia automáticamente la plantilla de flujo de trabajo si está activado.  
  
     Este paso le permite asociar manualmente el flujo de trabajo a la lista Documentos compartidos más adelante, que muestra el formulario de asociación.  
  
12. Elija el botón **Finalizar**.  
  
## Agregar un formulario de asociación al flujo de trabajo  
 A continuación, cree un formulario de asociación .ASPX que aparecerá cuando el administrador de SharePoint asocie por primera vez el flujo de trabajo a un documento de informe de gastos.  
  
#### Para agregar un formulario de asociación al flujo de trabajo  
  
1.  Elija el nodo de **Workflow1** en **Explorador de soluciones**.  
  
2.  En la barra de menú, elija **Project**, **Agregar nuevo elemento** para mostrar el cuadro de diálogo de **Agregar nuevo elemento** .  
  
3.  En la vista de árbol del cuadro de diálogo, expanda **Visual C\#** o **Visual Basic** \(dependiendo del lenguaje del proyecto\), expanda el nodo de **sharepoint** , y después elija el nodo de **2010** .  
  
4.  En la lista de plantillas, elija la plantilla de **Formulario de asociación de flujo de trabajo** .  
  
5.  En el cuadro de texto de **Name** , escriba ExpenseReportAssocForm.aspx.  
  
6.  Elija el botón de **Add** para agregar el formulario al proyecto.  
  
## Diseñar y codificar el formulario de asociación  
 En este procedimiento, se introduce la funcionalidad en el formulario de asociación agregando controles y código.  
  
#### Para diseñar y codificar el formulario de asociación  
  
1.  En el formulario de asociación \(ExpenseReportAssocForm.aspx\), busque el elemento `asp:Content` que tenga `ID="Main"`.  
  
2.  Justo después de la primera línea de este elemento de contenido, agregue el código siguiente para crear una etiqueta y cuadro de texto que solicite el límite de aprobación de gasto \(*AutoApproveLimit*\):  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  Expanda el archivo **ExpenseReportAssocForm.aspx** en el **Explorador de soluciones** para mostrar sus archivos dependientes.  
  
    > [!NOTE]  
    >  Si el proyecto está en [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], debe elegir el botón de **Ver todos los archivos** para realizar este paso.  
  
4.  Abrir el menú contextual para el archivo ExpenseReportAssocForm.aspx y elija **Ver código**.  
  
5.  Reemplace el método `GetAssociationData` por lo siguiente:  
  
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
  
## Agregar un formulario de iniciación al flujo de trabajo  
 A continuación cree el formulario de iniciación que aparece cuando los usuarios ejecutan el flujo de trabajo en los informes de gastos.  
  
#### Para crear un formulario de iniciación  
  
1.  Elija el nodo de **Workflow1** en **Explorador de soluciones**.  
  
2.  En la barra de menú, elija **Project**, presentación de **Agregar nuevo elemento** el cuadro de diálogo de **Agregar nuevo elemento** .  
  
3.  En la vista de árbol del cuadro de diálogo, expanda **Visual C\#** o **Visual Basic**  \(dependiendo del lenguaje del proyecto\), expanda el nodo de **sharepoint** , y después elija el nodo de **2010** .  
  
4.  En la lista de plantillas, elija la plantilla de **Formulario de iniciación de flujo de trabajo** .  
  
5.  En el cuadro de texto de **Name** , escriba ExpenseReportInitForm.aspx.  
  
6.  Elija el botón de **Add** para agregar el formulario al proyecto.  
  
## Diseñar y codificar el formulario de iniciación  
 A continuación, incluya la funcionalidad en el formulario de iniciación agregando los controles y código.  
  
#### Para codificar el formulario de iniciación  
  
1.  En el formulario de iniciación \(ExpenseReportInitForm.aspx\), busque el elemento de `asp:Content` que contiene `ID="Main"`.  
  
2.  Justo después de la primera línea de este elemento de contenido, agregue el código siguiente para crear una etiqueta y cuadro de texto donde se muestre el límite de aprobación de gastos \(*AutoApproveLimit*\) que se escribió en el formulario de asociación, y otra etiqueta y cuadro de texto para el indicador del total de gastos \(*ExpenseTotal*\):  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  Expanda el archivo **ExpenseReportInitForm.aspx** en el **Explorador de soluciones** para mostrar sus archivos dependientes.  
  
4.  Abrir el menú contextual para el archivo ExpenseReportInitForm.aspx y elija **Ver código**.  
  
5.  Reemplace el método `Page_Load` por el siguiente ejemplo:  
  
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
  
6.  Reemplace el método `GetInitiationData` por el siguiente ejemplo:  
  
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
  
## Personalizar el flujo de trabajo  
 A continuación, personalice el flujo de trabajo.  Después, asociará dos formularios al flujo de trabajo.  
  
#### Para personalizar el flujo de trabajo  
  
1.  Muestre el flujo de trabajo en el diseñador de flujo de trabajo por Workflow1 que se abre en el proyecto.  
  
2.  En **Cuadro de herramientas**, expanda el nodo de **Windows workflow v3.0** y busque la actividad de **IfElse** .  
  
3.  Agregue esta actividad al flujo de trabajo mediante uno de los siguientes pasos:  
  
    -   Abrir el menú contextual de la actividad de **IfElse** , elija **copiar**, abra el menú contextual para la línea bajo la actividad de **onWorkflowActivated1** en el diseñador de flujo de trabajo y, a continuación **Pegar**.  
  
    -   Arrastre la actividad de **IfElse** de **Cuadro de herramientas**, y conéctela a la línea bajo la actividad de **onWorkflowActiviated1** en el diseñador de flujo de trabajo.  
  
4.  En el Cuadro de herramientas, expanda el nodo **Flujo de trabajo de SharePoint** y busque la actividad **CreateTask**.  
  
5.  Agregue esta actividad al flujo de trabajo mediante uno de los siguientes pasos:  
  
    -   Abrir el menú contextual de la actividad de **CreateTask** , elija **copiar**, abra el menú contextual para una de las dos áreas de **Actividades de entrega aquí** dentro de IfElseActivity1 en el diseñador de flujo de trabajo y, a continuación **Pegar**.  
  
    -   Arrastre la actividad de **CreateTask** de **Cuadro de herramientas** sobre una de las dos áreas de **Actividades de entrega aquí** dentro de IfElseActivity1.  
  
6.  En la ventana **Propiedades**, especifique un valor de *taskToken* para la propiedad **CorrelationToken**.  
  
7.  Expanda la propiedad de **CorrelationToken** eligiendo el signo más \(![Signo más de TreeView](../sharepoint/media/plus.png "Signo más de TreeView")\) situado al lado.  
  
8.  Elija la flecha de lista desplegable en la propiedad del método de **OwnerActivityName** , y establezca el valor de *Workflow1* .  
  
9. Elija la propiedad de **TaskId** , y elija el botón de puntos suspensivos \(![Elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.png "Elipse del Diseñador de ASP.NET Mobile")\) para mostrar el cuadro de diálogo de **Propiedad de enlace** .  
  
10. Elija la ficha de **Enlace a un nuevo miembro** , elija el botón de opción de **Cree el campo** , y elija el botón de **Aceptar** .  
  
11. elija la propiedad de **TaskProperties** , y elija el botón de puntos suspensivos \(![Elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.png "Elipse del Diseñador de ASP.NET Mobile")\) para mostrar el cuadro de diálogo de **Propiedad de enlace** .  
  
12. Elija la ficha de **Enlace a un nuevo miembro** , elija el botón de opción de **Cree el campo** , y elija el botón de **Aceptar** .  
  
13. En **Cuadro de herramientas**, expanda el nodo de **Flujo de trabajo de SharePoint** , y busque la actividad de **LogToHistoryListActivity** .  
  
14. Agregue esta actividad al flujo de trabajo mediante uno de los siguientes pasos:  
  
    -   Abrir el menú contextual de la actividad de **LogToHistoryListActivity** , elija **copiar**, abra el menú contextual para otra área de **Actividades de entrega aquí** dentro de IfElseActivity1 en el diseñador de flujo de trabajo y, a continuación **Pegar**.  
  
    -   Arrastre la actividad de **LogToHistoryListActivity** de **Cuadro de herramientas**, y colóquelo sobre otra área de **Actividades de entrega aquí** dentro de IfElseActivity1.  
  
## Agregar código al flujo de trabajo  
 A continuación agregue el código al flujo de trabajo para darle funcionalidad.  
  
#### Para agregar código al flujo de trabajo  
  
1.  Abrir el menú contextual de la actividad de **createTask1** en el diseñador de flujo de trabajo y, a continuación **Ver código**.  
  
2.  Agregue el método siguiente:  
  
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
    >  En el código, reemplace `somedomain\\someuser` por un dominio y un nombre de usuario para los que se creará una tarea; por ejemplo, "`Office\\JoeSch`".  Para probarlo es más fácil es utilizar la cuenta con la que está desarrollando.  
  
3.  Agregue el ejemplo siguiente bajo el método `MethodInvoking`:  
  
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
  
4.  En el diseñador de flujo de trabajo, elija la actividad de **ifElseBranchActivity1** .  
  
5.  En la ventana de **Propiedades** , elija la flecha de lista desplegable de la propiedad de **Condición** , y establezca el valor de *Code Condition* .  
  
6.  Expanda la propiedad de **Condición** eligiendo el signo más \(![Signo más de TreeView](../sharepoint/media/plus.png "Signo más de TreeView")\) situado junto a él, y establezca su valor en *checkApprovalNeeded*.  
  
7.  En el diseñador de flujo de trabajo, abra el menú contextual de la actividad de **logToHistoryListActivity1** y, a continuación **Generar controladores** para generar un método vacío para el evento de `MethodInvoking` .  
  
8.  Reemplace el código `MethodInvoking` por el siguiente:  
  
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
  
9. Elija la tecla F5 para depurar el programa.  
  
     Esto compila la aplicación, la empaqueta, la implementa, activa sus características, recicla el grupo de aplicaciones de [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] y, a continuación, inicia el explorador en la ubicación especificada en la propiedad **Site Url**.  
  
## Asociar el flujo de trabajo a la lista Documentos  
 A continuación muestre el formulario de asociación de flujo de trabajo asociando el flujo de trabajo a la lista **Documentoscompartidos** en el sitio de SharePoint.  
  
#### Para asociar el flujo de trabajo  
  
1.  Elija el vínculo de **Documentos compartidos** en la barra de inicio rápido.  
  
2.  Elija el vínculo de **Biblioteca** en la pestaña de **Herramientas de biblioteca** y elija el botón de la cinta de opciones de **Valores de biblioteca** .  
  
3.  En la sección de **Permisos y administración** , elija el vínculo de **Valores de flujo de trabajo** y elija el vínculo de **Agregue un flujo de trabajo** en la página de **Flujos de trabajo** .  
  
4.  En la lista superior de la página de configuración de flujo de trabajo, elija la plantilla de **ExpenseReport \- Workflow1** .  
  
5.  En el campo siguiente, entre en ExpenseReportWorkflow y elija el botón de **siguiente** .  
  
     Esto asocia el flujo de trabajo con la lista **Documentos compartidos** y muestra el formulario de asociación de flujo de trabajo.  
  
6.  En el cuadro de texto de **Límite auto de aprobación** , escriba 1200 y elija el botón de **Asociar flujo de trabajo** .  
  
## Iniciar el flujo de trabajo  
 A continuación asocie el flujo de trabajo a uno de los documentos en la lista **Documentos compartidos** para mostrar el formulario de iniciación del flujo de trabajo.  
  
#### Para iniciar el flujo de trabajo  
  
1.  En la página de SharePoint, elija el botón de **Domicilio** .  
  
2.  Elija el vínculo de **Documentos compartidos** en la barra de inicio rápido para mostrar la lista de **Documentos compartidos** .  
  
3.  Elija el vínculo de **Documentos** en la pestaña de **Herramientas de biblioteca** en la parte superior de la página, y elija el botón de **Cargar documento** en la cinta de opciones para cargar un nuevo documento en la lista de **Documentos compartidos** .  
  
4.  En el cuadro de diálogo de **Cargar documento** , elija el botón de **Browse** , elija cualquier archivo de documento, elija el botón de **Abierta** , y elija el botón de **Aceptar** .  
  
     Puede cambiar la configuración del documento en este cuadro de diálogo, pero los deja en los valores predeterminados eligiendo el botón de **Guardar** .  
  
5.  Elija el documento cargado, elija la flecha de lista desplegable que aparece, y elija el elemento de **Flujos de trabajo** .  
  
6.  Elija la imagen junto a ExpenseReportWorkflow.  
  
     Esto muestra el formulario de iniciación del flujo de trabajo. \(Observe que el valor mostrado en el cuadro **Límite de aprobación automática** es de solo lectura porque se escribió en el formulario de asociación\).  
  
7.  En el cuadro de texto de **Total de gastos** , escriba 1600 y, a continuación elija el botón de **Iniciar flujo de trabajo** .  
  
     Esto muestra la lista **Documentos compartidos** de nuevo.  Una nueva columna denominada **ExpenseReportWorkflow** con el valor **Completado** se agrega al elemento que el flujo de trabajo acaba de iniciar.  
  
8.  Elija la flecha de lista desplegable situada junto al documento cargado y elija el elemento de **Flujos de trabajo** para mostrar la página de estado de flujo de trabajo.  Elija el valor de **Completado** en **Flujos de trabajo completos**.  La tarea aparece bajo la sección **Tareas**.  
  
9. Elija el título de la tarea para mostrar sus detalles.  
  
10. Regrese a la lista **Documentoscompartidos** y reinicie el flujo de trabajo utilizando el mismo documento u otro diferente.  
  
11. Escriba una cantidad en la página de inicio que es menor o igual que la cantidad escrita en la página de asociación \(1200\).  
  
     Cuando esto se produce, se crea una entrada en la lista de historial en lugar de una tarea.  La entrada muestra en la sección **Historial del flujo de trabajo** de la página de estado del flujo de trabajo.  Observe el mensaje de la columna **Resultado** del evento de historial.  Contiene el texto escrito en el evento `logToHistoryListActivity1.MethodInvoking` que incluye la cantidad aprobada automáticamente.  
  
## Pasos siguientes  
 Puede aprender más acerca de la creación de plantillas de flujo de trabajo en estos temas:  
  
-   Para obtener más información sobre los flujos de trabajo de SharePoint, vea [Flujos de trabajo en Windows SharePoint services](http://go.microsoft.com/fwlink/?LinkID=166275).  
  
## Vea también  
 [Crear soluciones de flujo de trabajo de SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Tutorial: Agregar una página de aplicación a un flujo de trabajo](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
  