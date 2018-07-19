---
title: 'Tutorial: Crear un flujo de trabajo con la asociación y formularios de iniciación | Microsoft Docs'
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
ms.openlocfilehash: a83dbde9bbb9907ee58909c254953554ad7de285
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119890"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>Tutorial: Crear un flujo de trabajo con formularios de asociación e iniciación
  Este tutorial muestra cómo crear un flujo de trabajo secuencial básico que incorpora el uso de formularios de asociación e iniciación. Estos son los formularios ASPX que habilite los parámetros que se agregarán a un flujo de trabajo al que asociar primero el Administrador de SharePoint (el formulario de asociación), y cuando se inicia el flujo de trabajo por el usuario (el formulario de iniciación).  
  
 En este tutorial se describe un escenario donde un usuario desea crear un flujo de trabajo aprobación para los informes de gastos que tiene los siguientes requisitos:  
  
-   Cuando el flujo de trabajo está asociado con una lista, el administrador se solicita con un formulario de asociación que especifique un límite de dólares para los informes de gastos.  
  
-   Los empleados cargar sus informes de gastos a la lista de documentos compartidos, iniciar el flujo de trabajo y, a continuación, escriba el gasto total en el formulario de iniciación de flujo de trabajo.  
  
-   Si un informe de gastos total supera el límite predefinido del administrador, se crea una tarea para que el jefe del empleado aprobar el informe de gastos. Sin embargo, si el total de informes de gastos de un empleado es menor o igual que el límite de gasto, un mensaje aprobado automáticamente se escribe en la lista del historial del flujo de trabajo.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un proyecto de flujo de trabajo secuencial de definición de lista de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Crear una programación de flujo de trabajo.  
  
-   Controlar eventos de actividad de flujo de trabajo.  
  
-   Crear formularios de asociación e iniciación de flujo de trabajo.  
  
-   Asociación de flujo de trabajo.  
  
-   Iniciar manualmente el flujo de trabajo.  
  
> [!NOTE]  
>  Aunque este tutorial usa un proyecto de flujo de trabajo secuencial, el proceso es el mismo para los flujos de trabajo de máquina de Estados.  
>   
>  Además, el equipo podría mostrar diferentes nombres o ubicaciones para algunos de los [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elementos de interfaz de usuario en las instrucciones siguientes. El [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] edition que tiene y la configuración que utilice determina estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint. Para obtener más información, consulte [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="create-a-sharepoint-sequential-workflow-project"></a>Crear un proyecto de flujo de trabajo secuencial de SharePoint
 En primer lugar, cree un proyecto de flujo de trabajo secuencial en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Un flujo de trabajo secuencial es una serie de pasos que se ejecuta en orden hasta que finaliza la última actividad. En este procedimiento, creará un flujo de trabajo secuencial que se aplica a la lista de documentos compartidos en SharePoint. Asistente del flujo de trabajo le permite asociar el flujo de trabajo con el sitio o la definición de lista y le permite determinar cuándo se iniciará el flujo de trabajo.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Para crear un proyecto de flujo de trabajo secuencial de SharePoint  
  
1.  En la barra de menús, elija **archivo** > **New** > **proyecto** para mostrar el **nuevo proyecto** cuadro de diálogo.  
  
2.  Expanda el **SharePoint** nodo bajo **Visual C#** o **Visual Basic**y, a continuación, elija el **2010** nodo.  
  
3.  En el **plantillas** panel, elija el **proyecto de SharePoint 2010** plantilla de proyecto.  
  
4.  En el **nombre** , escriba **ExpenseReport** y, a continuación, elija el **Aceptar** botón.  
  
     El **Asistente de personalización de SharePoint** aparece.  
  
5.  En el **especificar el nivel de sitio y de seguridad para la depuración** página, elija el **implementar como solución de granja de servidores** botón de opción y, a continuación, elija el **finalizar** botón para aceptar el sitio predeterminado y de nivel de confianza.  
  
     Este paso también establece el nivel de confianza para la solución como solución de granja de servidores, que es la única opción disponible para los proyectos de flujo de trabajo.  
  
6.  En el **Explorador de soluciones**, elija el nodo de proyecto.  
  
7.  En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.  
  
8.  Bajo **Visual C#** o **Visual Basic**, expanda el **SharePoint** nodo y, a continuación, elija el **2010** nodo.  
  
9. En el **plantillas** panel, elija **flujo de trabajo secuencial (solución de granja de servidores únicamente)** plantilla y, a continuación, elija el **agregar** botón.  
  
     El **Asistente de personalización de SharePoint** aparece.  
  
10. En el **especificar el nombre de flujo de trabajo de depuración** , acepte el nombre predeterminado (**ExpenseReport - Workflow1**). Mantenga el valor de tipo de plantilla de flujo de trabajo predeterminada (**flujo de trabajo de lista)**. Elija el botón **Siguiente**.  
  
11. En el **desea que Visual Studio asocie automáticamente el flujo de trabajo en una sesión de depuración?** página, desactive la casilla que se asocia automáticamente la plantilla de flujo de trabajo si está activada.  
  
     Este paso le permite asociar manualmente el flujo de trabajo con la lista de documentos compartidos en versiones posteriores, que muestra el formulario de asociación.  
  
12. Elija la **finalizar** botón.  
  
## <a name="add-an-association-form-to-the-workflow"></a>Agregar un formulario de asociación al flujo de trabajo
 A continuación, cree una. Formulario de asociación de ASPX que aparece cuando el Administrador de SharePoint en primer lugar asocia el flujo de trabajo a un documento de informe de gastos.  
  
#### <a name="to-add-an-association-form-to-the-workflow"></a>Para agregar un formulario de asociación al flujo de trabajo  
  
1.  Elija la **Workflow1** nodo **el Explorador de soluciones**.  
  
2.  En la barra de menús, elija **proyecto** > **Agregar nuevo elemento** para mostrar el **Agregar nuevo elemento** cuadro de diálogo.  
  
3.  En la vista de árbol del cuadro de diálogo, expanda el **Visual C#** o **Visual Basic** (dependiendo del lenguaje del proyecto), expanda el **SharePoint** nodo y, a continuación, elija el **2010** nodo.  
  
4.  En la lista de plantillas, elija el **formulario de asociación de flujo de trabajo** plantilla.  
  
5.  En el **nombre** texto, escriba **ExpenseReportAssocForm.aspx**.  
  
6.  Elija la **agregar** para agregar el formulario al proyecto.  
  
## <a name="designing-and-coding-the-association-form"></a>Diseñar y codificar el formulario de asociación
 En este procedimiento, se introduce la funcionalidad para el formulario de asociación agregando controles y código.  
  
#### <a name="to-design-and-code-the-association-form"></a>Para diseñar y codificar el formulario de asociación  
  
1.  En el formulario de asociación (ExpenseReportAssocForm.aspx), busque el `asp:Content` elemento que tiene `ID="Main"`.  
  
2.  Directamente después de la primera línea en este elemento de contenido, agregue el código siguiente para crear una etiqueta y un cuadro de texto que solicita el límite de aprobación de gastos (*AutoApproveLimit*):  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  Expanda el **ExpenseReportAssocForm.aspx** archivo **el Explorador de soluciones** para mostrar sus archivos dependientes.  
  
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
  
## <a name="add-an-initiation-form-to-the-workflow"></a>Agregar un formulario de iniciación de flujo de trabajo
 A continuación, cree el formulario de iniciación que aparece cuando los usuarios ejecutan el flujo de trabajo en sus informes de gastos.  
  
#### <a name="to-create-an-initiation-form"></a>Para crear un formulario de iniciación  
  
1.  Elija la **Workflow1** nodo **el Explorador de soluciones**.  
  
2.  En la barra de menús, elija **proyecto** > **Agregar nuevo elemento** mostrar la **Agregar nuevo elemento** cuadro de diálogo.  
  
3.  En la vista de árbol del cuadro de diálogo, expanda el **Visual C#** o **Visual Basic** (dependiendo del lenguaje del proyecto), expanda el **SharePoint** nodo y, a continuación, elija el **2010** nodo.  
  
4.  En la lista de plantillas, elija el **formulario de iniciación de flujo de trabajo** plantilla.  
  
5.  En el **nombre** texto, escriba **ExpenseReportInitForm.aspx**.  
  
6.  Elija la **agregar** para agregar el formulario al proyecto.  
  
## <a name="designing-and-coding-the-initiation-form"></a>Diseñar y codificar el formulario de iniciación
 A continuación, introduce la funcionalidad en el formulario de iniciación agregando controles y código.  
  
#### <a name="to-code-the-initiation-form"></a>Para codificar el formulario de iniciación  
  
1.  En el formulario de iniciación (ExpenseReportInitForm.aspx), busque el `asp:Content` elemento que contiene `ID="Main"`.  
  
2.  Directamente después de la primera línea en este elemento de contenido, agregue el código siguiente para crear una etiqueta y un cuadro de texto que muestra el límite de aprobación de gastos (*AutoApproveLimit*) que se escribió en el formulario de asociación y otra etiqueta y cuadro de texto para solicitar el total de gastos (*ExpenseTotal*):  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  Expanda el **ExpenseReportInitForm.aspx** archivo **el Explorador de soluciones** para mostrar sus archivos dependientes.  
  
4.  Abra el menú contextual para el archivo ExpenseReportInitForm.aspx y elija **ver código**.  
  
5.  Reemplace el `Page_Load` método con el siguiente ejemplo:  
  
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
  
6.  Reemplace el `GetInitiationData` método con el siguiente ejemplo:  
  
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
  
## <a name="cutomize-the-workflow"></a>Personalizar el flujo de trabajo
 A continuación, personalizar el flujo de trabajo. Más adelante, asociará dos formularios al flujo de trabajo.  
  
#### <a name="to-customize-the-workflow"></a>Para personalizar el flujo de trabajo  
  
1.  Mostrar el flujo de trabajo en el Diseñador de flujo de trabajo abriendo Workflow1 en el proyecto.  
  
2.  En el **cuadro de herramientas**, expanda el **Windows Workflow v3.0** nodo y busque el **IfElse** actividad.  
  
3.  Agregue esta actividad al flujo de trabajo realizando uno de los pasos siguientes:  
  
    -   Abra el menú contextual para el **IfElse** actividad, elija **copia**, abra el menú contextual de la línea bajo el **onWorkflowActivated1** actividad en el Diseñador de flujo de trabajo y, a continuación, elija **pegar**.  
  
    -   Arrastre el **IfElse** actividad desde la **cuadro de herramientas**y conéctelo a la línea bajo el **onWorkflowActiviated1** actividad en el Diseñador de flujo de trabajo.  
  
4.  En el cuadro de herramientas, expanda el **SharePoint Workflow** nodo y busque el **CreateTask** actividad.  
  
5.  Agregue esta actividad al flujo de trabajo realizando uno de los pasos siguientes:  
  
    -   Abra el menú contextual para el **CreateTask** actividad, elija **copia**, abra el menú contextual para uno de los dos **colocar actividades aquí** áreas dentro de  **IfElseActivity1** en el Diseñador de flujo de trabajo y, a continuación, elija **pegar**.  
  
    -   Arrastre el **CreateTask** actividad desde la **cuadro de herramientas** en uno de los dos **colocar actividades aquí** áreas dentro de **IfElseActivity1**.  
  
6.  En el **propiedades** ventana, escriba un valor de propiedad *taskToken* para el **CorrelationToken** propiedad.  
  
7.  Expanda el **CorrelationToken** propiedad eligiendo el signo más (![signo más de TreeView](../sharepoint/media/plus.gif "signo más de TreeView")) junto a él.  
  
8.  Elija la flecha de lista desplegable en el **OwnerActivityName** sub propiedad y establecer el *Workflow1* valor.  
  
9. Elija la **TaskId** propiedad y, a continuación, elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) botón para mostrar el **Enlazar propiedad** cuadro de diálogo.  
  
10. Elija la **enlazar a un nuevo miembro** ficha, elija la **Crear campo** botón de opción y, a continuación, elija el **Aceptar** botón.  
  
11. Elija la **TaskProperties** propiedad y, a continuación, elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) botón para mostrar el  **Enlazar la propiedad** cuadro de diálogo.  
  
12. Elija la **enlazar a un nuevo miembro** ficha, elija la **Crear campo** botón de opción y, a continuación, elija el **Aceptar** botón.  
  
13. En el **cuadro de herramientas**, expanda el **SharePoint Workflow** nodo y busque el **LogToHistoryListActivity** actividad.  
  
14. Agregue esta actividad al flujo de trabajo realizando uno de los pasos siguientes:  
  
    -   Abra el menú contextual para el **LogToHistoryListActivity** actividad, elija **copia**, abra el menú contextual para los demás **colocar actividades aquí** área dentro de **IfElseActivity1** en el Diseñador de flujo de trabajo y, a continuación, elija **pegar**.  
  
    -   Arrastre el **LogToHistoryListActivity** actividad desde la **cuadro de herramientas**y se coloca en el otro **colocar actividades aquí** área dentro de **IfElseActivity1** .  
  
## <a name="add-code-to-the-workflow"></a>Agregue código al flujo de trabajo
 A continuación, agregue código al flujo de trabajo para darle funcionalidad.  
  
#### <a name="to-add-code-to-the-workflow"></a>Para agregar código al flujo de trabajo  
  
1.  Abra el menú contextual para el **createTask1** actividad en el Diseñador de flujo de trabajo y, a continuación, elija **ver código**.  
  
2.  Agregue el siguiente método:  
  
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
    >  En el código, reemplace `somedomain\\someuser` con un nombre de usuario y dominio para el que se creará una tarea, como por ejemplo, "`Office\\JoeSch`". Para las pruebas es más fácil usar la cuenta que se va a desarrollar con.  
  
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
  
6.  Expanda el **condición** propiedad eligiendo el signo más (![signo más de TreeView](../sharepoint/media/plus.gif "signo más de TreeView")) junto a él y, a continuación, establezca su valor en *checkApprovalNeeded* .  
  
7.  En el Diseñador de flujo de trabajo, abra el menú contextual para el **logToHistoryListActivity1** actividad y, a continuación, elija **generar controladores** para generar un método vacío para el `MethodInvoking` eventos.  
  
8.  Reemplace el `MethodInvoking` código con lo siguiente:  
  
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
  
9. Elija la **F5** clave para depurar el programa.  
  
     Esto compila la aplicación, lo empaqueta, lo implementa, sus características se activa, se recicla el [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] grupo de aplicaciones y, a continuación, se inicia el explorador en la ubicación especificado en el **dirección Url del sitio** propiedad.  
  
## <a name="associating-the-workflow-to-the-documents-list"></a>Asociar el flujo de trabajo a la lista de documentos
 A continuación, mostrar el formulario de asociación de flujo de trabajo mediante la asociación de flujo de trabajo con el **SharedDocuments** lista en el sitio de SharePoint.  
  
#### <a name="to-associate-the-workflow"></a>Para asociar el flujo de trabajo  
  
1.  Elija la **documentos compartidos** vínculo en la barra de inicio rápido.  
  
2.  Elija la **biblioteca** vincular en el **herramientas de biblioteca** ficha y, a continuación, elija el **configuración de la biblioteca** botón de la cinta.  
  
3.  En el **permisos y administración** sección, elija el **Workflow Settings** vincular y, a continuación, elija el **agregar un flujo de trabajo** vincular en el **losflujosdetrabajo** página.  
  
4.  En la lista superior en la página de configuración del flujo de trabajo, elija la **ExpenseReport - Workflow1** plantilla.  
  
5.  En el siguiente campo, escriba **ExpenseReportWorkflow** y, a continuación, elija el **siguiente** botón.  
  
     Esto asocia el flujo de trabajo con el **documentos compartidos** lista y muestra el formulario de asociación de flujo de trabajo.  
  
6.  En el **límite de aprobación automática** texto, escriba **1200** y, a continuación, elija el **asociar el flujo de trabajo** botón.  
  
## <a name="start-the-workflow"></a>Iniciar el flujo de trabajo
 A continuación, asociar el flujo de trabajo a uno de los documentos en el **documentos compartidos** lista para mostrar el formulario de iniciación de flujo de trabajo.  
  
#### <a name="to-start-the-workflow"></a>Para iniciar el flujo de trabajo  
  
1.  En la página de SharePoint, elija el **inicio** botón.  
  
2.  Elija la **documentos compartidos** vínculo en la barra de inicio rápido para mostrar la **documentos compartidos** lista.  
  
3.  Elija la **documentos** vincular en el **herramientas de biblioteca** pestaña en la parte superior de la página y, a continuación, elija el **cargar documento** botón en la cinta de opciones para cargar un nuevo documento en el **Documentos compartidos** lista.  
  
4.  En el **cargar documento** diálogo cuadro, elija el **examinar** botón, elija cualquier archivo de documento, el **abierto** botón y, a continuación, elija el **Aceptar** botón.  
  
     Puede cambiar la configuración para el documento en este cuadro de diálogo, pero deje los valores predeterminados, elija el **guardar** botón.  
  
5.  Elija el documento cargado, elija la flecha de lista desplegable que aparece y, a continuación, elija el **flujos de trabajo** elemento.  
  
6.  Elija una imagen junto a ExpenseReportWorkflow.  
  
     Esto muestra el formulario de iniciación de flujo de trabajo. (Tenga en cuenta que el valor se muestra en el **límite de aprobación automática** cuadro es de solo lectura porque se ha escrito en el formulario de asociación.)  
  
7.  En el **gasto Total** texto, escriba **1600**y, a continuación, elija el **iniciar flujo de trabajo** botón.  
  
     Esto muestra la **documentos compartidos** vuelva a enumerar. Una nueva columna denominada **ExpenseReportWorkflow** con el valor **completado** se agrega al elemento que acaba de iniciar el flujo de trabajo.  
  
8.  Elija la flecha desplegable situada junto al documento cargado y, a continuación, elija el **flujos de trabajo** elemento para mostrar la página de estado de flujo de trabajo. Elija la **completado** valor bajo **flujos de trabajo completado**. La tarea aparece en la **tareas** sección.  
  
9. Elija el título de la tarea para mostrar sus detalles de tarea.  
  
10. Vuelva a la **SharedDocuments** lista y reinicie el flujo de trabajo, utilizando el mismo documento o en uno diferente.  
  
11. Especifique la cantidad en la página de inicio que es menor o igual que la cantidad especificada en la página de asociación (**1200**).  
  
     Cuando esto ocurre, se crea una entrada en la lista del historial en lugar de una tarea. La entrada se muestra en el **historial de flujo de trabajo** sección de la página de estado de flujo de trabajo. Tenga en cuenta el mensaje en el **resultado** columna del evento del historial. Contiene el texto escrito en el `logToHistoryListActivity1.MethodInvoking` evento que incluye la cantidad que se aprueba automáticamente.  
  
## <a name="next-steps"></a>Pasos siguientes
 Puede obtener más información acerca de cómo crear plantillas de flujo de trabajo en los siguientes temas:  
  
-   Para obtener más información acerca de los flujos de trabajo de SharePoint, vea [flujos de trabajo en Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=166275).  
  
## <a name="see-also"></a>Vea también
 [Crear soluciones de flujo de trabajo de SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Tutorial: Agregar una página de aplicación a un flujo de trabajo](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
