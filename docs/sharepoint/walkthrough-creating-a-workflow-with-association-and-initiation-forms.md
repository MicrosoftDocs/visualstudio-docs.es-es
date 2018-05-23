---
title: 'Tutorial: Crear un flujo de trabajo con una asociación y formularios de iniciación | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0c232d541e985944fe64d9eb40da7e344b32c0cc
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="walkthrough-creating-a-workflow-with-association-and-initiation-forms"></a>Tutorial: Crear un flujo de trabajo con formularios de asociación y de iniciación
  Este tutorial muestra cómo crear un flujo de trabajo secuencial básico que incorpora el uso de formularios de asociación e iniciación. Se trata de formularios ASPX que permiten parámetros para agregarse a un flujo de trabajo al que asociar primero el Administrador de SharePoint (el formulario de asociación) y cuando se inicia el flujo de trabajo por el usuario (el formulario de inicio).  
  
 En este tutorial se describe un escenario donde un usuario desea volver a crear un flujo de trabajo aprobación para los informes de gastos que tiene los siguientes requisitos:  
  
-   Cuando el flujo de trabajo está asociado a una lista, el administrador se indica con un formulario de asociación en el que especificar un límite en dólares para los informes de gastos.  
  
-   Los empleados cargar sus informes de gastos en la lista de documentos compartidos, iniciar el flujo de trabajo y, a continuación, escriba el gasto total en el formulario de iniciación de flujo de trabajo.  
  
-   Si un informe de gastos de empleado total supera el límite predefinido del administrador, se crea una tarea para que el jefe del empleado aprobar el informe de gastos. Sin embargo, si el total de informes de gastos de un empleado es menor o igual que el límite de gastos, se escribe un mensaje aprobada automáticamente a la lista del historial del flujo de trabajo.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un proyecto de flujo de trabajo secuencial de definición de lista de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Crear una programación de flujo de trabajo.  
  
-   Control de eventos de actividad de flujo de trabajo.  
  
-   Crear formularios de asociación e iniciación de flujo de trabajo.  
  
-   Asociar el flujo de trabajo.  
  
-   Iniciar manualmente el flujo de trabajo.  
  
> [!NOTE]  
>  Aunque este tutorial usa un proyecto de flujo de trabajo secuencial, el proceso es el mismo para los flujos de trabajo de máquina de Estados.  
>   
>  Además, el equipo puede mostrar diferentes nombres o ubicaciones para algunos de los [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elementos de la interfaz de usuario en las siguientes instrucciones. La [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] edición que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint. Para obtener más información, consulte [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="creating-a-sharepoint-sequential-workflow-project"></a>Crear un proyecto de flujo de trabajo secuencial de SharePoint  
 En primer lugar, cree un proyecto de flujo de trabajo secuencial en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Flujo de trabajo secuencial es una serie de pasos que se ejecuta en orden hasta que finaliza la última actividad. En este procedimiento, creará un flujo de trabajo secuencial que se aplica a la lista de documentos compartidos en SharePoint. Asistente del flujo de trabajo permite asociar el flujo de trabajo con el sitio o la definición de lista y le permite determinar cuándo se iniciará el flujo de trabajo.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Para crear un proyecto de flujo de trabajo secuencial de SharePoint  
  
1.  En la barra de menús, elija **archivo**, **New**, **proyecto** para mostrar la **nuevo proyecto** cuadro de diálogo.  
  
2.  Expanda el **SharePoint** nodo bajo **Visual C#** o **Visual Basic**y, a continuación, elija la **2010** nodo.  
  
3.  En el **plantillas** panel, elija la **proyecto de SharePoint 2010** plantilla de proyecto.  
  
4.  En el **nombre** cuadro, escriba **ExpenseReport** y, a continuación, elija la **Aceptar** botón.  
  
     El **Asistente para personalización de SharePoint** aparece.  
  
5.  En el **especificar el nivel de sitio y la seguridad para la depuración** página, elija la **implementar como solución de granja de servidores** botón de opción y, a continuación, elija la **finalizar** botón para aceptar el sitio de nivel y el valor predeterminado de confianza.  
  
     Este paso también establece el nivel de confianza para la solución como solución de granja de servidores, que es la única opción disponible para los proyectos de flujo de trabajo.  
  
6.  En el **Explorador de soluciones**, elija el nodo de proyecto.  
  
7.  En la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
8.  Bajo **Visual C#** o **Visual Basic**, expanda la **SharePoint** nodo y, a continuación, elija la **2010** nodo.  
  
9. En el **plantillas** panel, elija **flujo de trabajo secuencial (solución de granja de servidores únicamente)** plantilla y, a continuación, elija la **agregar** botón.  
  
     El **Asistente para personalización de SharePoint** aparece.  
  
10. En el **especificar el nombre de flujo de trabajo para la depuración** , acepte el nombre predeterminado (**ExpenseReport - Workflow1**). Mantenga el valor de tipo de plantilla de flujo de trabajo predeterminado (**flujo de trabajo de lista)**. Elija el botón **Siguiente**.  
  
11. En el **desea que Visual Studio para asociar automáticamente el flujo de trabajo en una sesión de depuración?** página, desactive la casilla que se asocia automáticamente la plantilla de flujo de trabajo si está activada.  
  
     Este paso le permite asociar manualmente el flujo de trabajo con la lista de documentos compartidos en versiones posteriores, que muestra el formulario de asociación.  
  
12. Elija la **finalizar** botón.  
  
## <a name="adding-an-association-form-to-the-workflow"></a>Agregar un formulario de asociación al flujo de trabajo  
 A continuación, cree una. Formulario de asociación de ASPX que aparece cuando el Administrador de SharePoint asocie por primera vez el flujo de trabajo con un documento de informe de gastos.  
  
#### <a name="to-add-an-association-form-to-the-workflow"></a>Para agregar un formulario de asociación al flujo de trabajo  
  
1.  Elija la **Workflow1** nodo **el Explorador de soluciones**.  
  
2.  En la barra de menús, elija **proyecto**, **Agregar nuevo elemento** para mostrar la **Agregar nuevo elemento** cuadro de diálogo.  
  
3.  En la vista de árbol del cuadro de diálogo, expanda **Visual C#** o **Visual Basic** (dependiendo del lenguaje del proyecto), expanda el **SharePoint** nodo y, a continuación, elija la **2010** nodo.  
  
4.  En la lista de plantillas, elija la **formulario de asociación de flujo de trabajo** plantilla.  
  
5.  En el **nombre** texto cuadro, escriba **ExpenseReportAssocForm.aspx**.  
  
6.  Elija la **agregar** botón para agregar el formulario al proyecto.  
  
## <a name="designing-and-coding-the-association-form"></a>Diseñar y codificar el formulario de asociación  
 En este procedimiento, se introduce la funcionalidad en el formulario de asociación agregando controles y código en él.  
  
#### <a name="to-design-and-code-the-association-form"></a>Para diseñar y codificar el formulario de asociación  
  
1.  En el formulario de asociación (ExpenseReportAssocForm.aspx), busque el `asp:Content` elemento que tiene `ID="Main"`.  
  
2.  Directamente después de la primera línea de este elemento de contenido, agregue el código siguiente para crear una etiqueta y un cuadro de texto que solicita el límite de aprobación de gastos (*AutoApproveLimit*):  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  Expanda el **ExpenseReportAssocForm.aspx** en el archivo **el Explorador de soluciones** para mostrar sus archivos dependientes.  
  
    > [!NOTE]  
    >  Si el proyecto está en [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], debe elegir el **ver todos los archivos** botón para realizar este paso.  
  
4.  Abra el menú contextual para el archivo ExpenseReportAssocForm.aspx y elija **ver código**.  
  
5.  Reemplace el `GetAssociationData` método con:  
  
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
  
## <a name="adding-an-initiation-form-to-the-workflow"></a>Agregar un formulario de inicio al flujo de trabajo  
 A continuación, cree el formulario de inicio que aparece cuando los usuarios ejecuten el flujo de trabajo en sus informes de gastos.  
  
#### <a name="to-create-an-initiation-form"></a>Para crear un formulario de inicio  
  
1.  Elija la **Workflow1** nodo **el Explorador de soluciones**.  
  
2.  En la barra de menús, elija **proyecto**, **Agregar nuevo elemento** mostrar la **Agregar nuevo elemento** cuadro de diálogo.  
  
3.  En la vista de árbol del cuadro de diálogo, expanda **Visual C#** o **Visual Basic** (dependiendo del lenguaje del proyecto), expanda el **SharePoint** nodo y, a continuación, elija la **2010** nodo.  
  
4.  En la lista de plantillas, elija la **formulario de iniciación de flujo de trabajo** plantilla.  
  
5.  En el **nombre** texto cuadro, escriba **ExpenseReportInitForm.aspx**.  
  
6.  Elija la **agregar** botón para agregar el formulario al proyecto.  
  
## <a name="designing-and-coding-the-initiation-form"></a>Diseñar y codificar el formulario de inicio  
 A continuación, introduce funcionalidad en el formulario de inicio mediante la adición de controles y código en él.  
  
#### <a name="to-code-the-initiation-form"></a>Para codificar el formulario de inicio  
  
1.  En el formulario de iniciación (ExpenseReportInitForm.aspx), busque el `asp:Content` elemento que contiene `ID="Main"`.  
  
2.  Justo después de la primera línea de este elemento de contenido, agregue el código siguiente para crear una etiqueta y un cuadro de texto que muestra el límite de aprobación de gastos (*AutoApproveLimit*) que se escribió en el formulario de asociación y otra etiqueta y cuadro de texto para solicitar el total de gastos (*ExpenseTotal*):  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  Expanda el **ExpenseReportInitForm.aspx** en el archivo **el Explorador de soluciones** para mostrar sus archivos dependientes.  
  
4.  Abra el menú contextual para el archivo ExpenseReportInitForm.aspx y elija **ver código**.  
  
5.  Reemplace el `Page_Load` método con el ejemplo siguiente:  
  
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
  
6.  Reemplace el `GetInitiationData` método con el ejemplo siguiente:  
  
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
  
## <a name="customizing-the-workflow"></a>Personalizar el flujo de trabajo  
 A continuación, personalice el flujo de trabajo. Más adelante, asociará dos formularios al flujo de trabajo.  
  
#### <a name="to-customize-the-workflow"></a>Para personalizar el flujo de trabajo  
  
1.  Muestra el flujo de trabajo en el Diseñador de flujo de trabajo abriendo Workflow1 en el proyecto.  
  
2.  En el **cuadro de herramientas**, expanda la **Windows Workflow v3.0** nodo y busque la **IfElse** actividad.  
  
3.  Agregue esta actividad al flujo de trabajo llevando a cabo uno de los siguientes pasos:  
  
    -   Abra el menú contextual para el **IfElse** actividad, elija **copia**, abra el menú contextual de la línea en la **onWorkflowActivated1** actividad en el Diseñador de flujo de trabajo y, a continuación, elija **pegar**.  
  
    -   Arrastre el **IfElse** actividad desde la **cuadro de herramientas**y conectarlo a la línea en la **onWorkflowActiviated1** actividad en el Diseñador de flujo de trabajo.  
  
4.  En el cuadro de herramientas, expanda el **flujo de trabajo de SharePoint** nodo y busque la **CreateTask** actividad.  
  
5.  Agregue esta actividad al flujo de trabajo llevando a cabo uno de los siguientes pasos:  
  
    -   Abra el menú contextual para el **CreateTask** actividad, elija **copia**, abra el menú contextual para uno de los dos **colocar aquí las actividades** las distintas áreas de  **IfElseActivity1** en el Diseñador de flujo de trabajo y, a continuación, elija **pegar**.  
  
    -   Arrastre el **CreateTask** actividad desde la **cuadro de herramientas** en uno de los dos **colocar aquí las actividades** las distintas áreas de **IfElseActivity1**.  
  
6.  En el **propiedades** ventana, escriba un valor de propiedad *taskToken* para el **CorrelationToken** propiedad.  
  
7.  Expanda el **CorrelationToken** propiedad eligiendo el signo más (![signo más de TreeView](../sharepoint/media/plus.gif "signo más de TreeView")) junto a ella.  
  
8.  Elija la flecha de lista desplegable en el **OwnerActivityName** sub propiedad y establezca el *Workflow1* valor.  
  
9. Elija la **TaskId** propiedad y, a continuación, elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) botón para mostrar el **Enlazar propiedad** cuadro de diálogo.  
  
10. Elija la **enlazar a un nuevo miembro** ficha, elija la **Crear campo** botón de opción y, a continuación, elija la **Aceptar** botón.  
  
11. Elija la **TaskProperties** propiedad y, a continuación, elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) botón para mostrar el  **Enlazar la propiedad** cuadro de diálogo.  
  
12. Elija la **enlazar a un nuevo miembro** ficha, elija la **Crear campo** botón de opción y, a continuación, elija la **Aceptar** botón.  
  
13. En el **cuadro de herramientas**, expanda la **flujo de trabajo de SharePoint** nodo y busque el **LogToHistoryListActivity** actividad.  
  
14. Agregue esta actividad al flujo de trabajo llevando a cabo uno de los siguientes pasos:  
  
    -   Abra el menú contextual para el **LogToHistoryListActivity** actividad, elija **copia**, abra el menú contextual para los demás **colocar aquí las actividades** área dentro de **IfElseActivity1** en el Diseñador de flujo de trabajo y, a continuación, elija **pegar**.  
  
    -   Arrastre el **LogToHistoryListActivity** actividad desde la **cuadro de herramientas**y se coloca en el otro **colocar aquí las actividades** área dentro de **IfElseActivity1** .  
  
## <a name="adding-code-to-the-workflow"></a>Agregar código para el flujo de trabajo  
 A continuación, agregue código al flujo de trabajo para darle funcionalidad.  
  
#### <a name="to-add-code-to-the-workflow"></a>Para agregar código al flujo de trabajo  
  
1.  Abra el menú contextual para el **createTask1** actividad en el Diseñador de flujo de trabajo y, a continuación, elija **ver código**.  
  
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
    >  En el código, reemplace `somedomain\\someuser` con un nombre de usuario y de dominio para el que se creará una tarea, como por ejemplo, "`Office\\JoeSch`". Para las pruebas es más fácil de utilizar la cuenta que está desarrollando con.  
  
3.  A continuación el `MethodInvoking` método, agregue el siguiente ejemplo:  
  
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
  
4.  En el Diseñador de flujo de trabajo, elija la **ifElseBranchActivity1** actividad.  
  
5.  En el **propiedades** ventana, elija la flecha de lista desplegable de la **condición** propiedad y, a continuación, establezca el *condición de código* valor.  
  
6.  Expanda el **condición** propiedad eligiendo el signo más (![signo más de TreeView](../sharepoint/media/plus.gif "signo más de TreeView")) junto a ella y, a continuación, establezca su valor en *checkApprovalNeeded* .  
  
7.  En el Diseñador de flujo de trabajo, abra el menú contextual para el **logToHistoryListActivity1** actividad y, a continuación, elija **generar controladores** para generar un método vacío para el `MethodInvoking` eventos.  
  
8.  Reemplace la `MethodInvoking` código con lo siguiente:  
  
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
  
9. Presione la tecla F5 para depurar el programa.  
  
     Esto compila la aplicación, lo empaqueta, implementa, activa sus características, recicla el [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] grupo de aplicaciones y, a continuación, inicia el explorador en la ubicación especificado en el **dirección Url del sitio** propiedad.  
  
## <a name="associating-the-workflow-to-the-documents-list"></a>Asociar el flujo de trabajo a la lista de documentos  
 A continuación, mostrar el formulario de asociación de flujo de trabajo asociando el flujo de trabajo con el **SharedDocuments** lista en el sitio de SharePoint.  
  
#### <a name="to-associate-the-workflow"></a>Para asociar el flujo de trabajo  
  
1.  Elija la **documentos compartidos** vínculo en la barra Inicio rápido.  
  
2.  Elija la **biblioteca** crear vínculos en la **herramientas de biblioteca** ficha y, a continuación, elija la **configuración de la biblioteca** botón de la cinta de opciones.  
  
3.  En el **permisos y administración** sección, elija el **configuración de flujo de trabajo** vincular y, a continuación, elija la **agregar un flujo de trabajo** crear vínculos en la **deflujosdetrabajo** página.  
  
4.  En la lista superior en la página de configuración de flujo de trabajo, elija la **ExpenseReport - Workflow1** plantilla.  
  
5.  En el siguiente campo, escriba **ExpenseReportWorkflow** y, a continuación, elija la **siguiente** botón.  
  
     Esto asocia el flujo de trabajo con el **documentos compartidos** lista y muestra el formulario de asociación de flujo de trabajo.  
  
6.  En el **límite de aprobación automática** texto cuadro, escriba **1200** y, a continuación, elija la **asociar el flujo de trabajo** botón.  
  
## <a name="starting-the-workflow"></a>A partir del flujo de trabajo  
 A continuación, asociar el flujo de trabajo a uno de los documentos en la **documentos compartidos** lista para mostrar el formulario de iniciación de flujo de trabajo.  
  
#### <a name="to-start-the-workflow"></a>Para iniciar el flujo de trabajo  
  
1.  En la página de SharePoint, elija el **inicio** botón.  
  
2.  Elija la **documentos compartidos** vínculo en la barra Inicio rápido para mostrar la **documentos compartidos** lista.  
  
3.  Elija la **documentos** crear vínculos en la **herramientas de biblioteca** pestaña en la parte superior de la página y, a continuación, elija la **cargar documento** botón en la cinta de opciones para cargar un documento nuevo en el **Documentos compartidos** lista.  
  
4.  En el **cargar documento** diálogo cuadro, elija la **examinar** botón, elija cualquier archivo de documento, elija la **abiertos** botón y, a continuación, elija el **Aceptar** botón.  
  
     Puede cambiar la configuración para el documento en este cuadro de diálogo, pero deje los valores predeterminados, elija el **guardar** botón.  
  
5.  Elija el documento cargado, elija la flecha de lista desplegable que aparece y, a continuación, elija la **flujos de trabajo** elemento.  
  
6.  Elija la imagen junto a ExpenseReportWorkflow.  
  
     Esto muestra el formulario de iniciación de flujo de trabajo. (Tenga en cuenta que el valor se muestra en el **límite de aprobación automática** cuadro es de solo lectura porque se escribió en el formulario de asociación.)  
  
7.  En el **gastos Total** texto cuadro, escriba **1600**y, a continuación, elija la **iniciar flujo de trabajo** botón.  
  
     Esto muestra la **documentos compartidos** vuelva a enumerar. Una nueva columna denominada **ExpenseReportWorkflow** con el valor **completado** se agrega al elemento que se acaba de iniciar el flujo de trabajo.  
  
8.  Elija la flecha de lista desplegable situada junto al documento cargado y, a continuación, elija la **flujos de trabajo** elemento para mostrar la página de estado de flujo de trabajo. Elija la **completado** valor bajo **flujos de trabajo completados**. La tarea aparece en la **tareas** sección.  
  
9. Elija el título de la tarea para mostrar sus detalles de tarea.  
  
10. Vuelva a la **SharedDocuments** lista y reinicie el flujo de trabajo, con el mismo documento o en uno diferente.  
  
11. Escriba una cantidad en la página de inicio que sea menor o igual a la cantidad especificada en la página de asociación (**1200**).  
  
     Cuando esto ocurre, se crea una entrada en la lista del historial en lugar de una tarea. La entrada se muestra en el **historial de flujo de trabajo** sección de la página de estado de flujo de trabajo. Tenga en cuenta el mensaje en el **resultado** columna del evento de historial. Contiene el texto escrito en el `logToHistoryListActivity1.MethodInvoking` eventos que incluye la cantidad que fue aprobada automáticamente.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Se puede obtener más información sobre cómo crear plantillas de flujo de trabajo en estos temas:  
  
-   Para obtener más información sobre los flujos de trabajo de SharePoint, vea [flujos de trabajo en Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=166275).  
  
## <a name="see-also"></a>Vea también  
 [Crear soluciones de flujo de trabajo de SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Tutorial: Agregar una página de aplicación a un flujo de trabajo](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
  