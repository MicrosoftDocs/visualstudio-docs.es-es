---
title: "Tutorial: Crear y depurar una soluci&#243;n de flujo de trabajo de SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Workflow.WorkflowConditions"
  - "VS.SharePointTools.Workflow.WorkflowList"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, flujos de trabajo"
  - "flujos de trabajo [desarrollo de SharePoint en Visual Studio]"
ms.assetid: 81756490-ab5a-4fa4-96c6-eed2cfbf8374
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Tutorial: Crear y depurar una soluci&#243;n de flujo de trabajo de SharePoint
  En este tutorial se muestra cómo crear una plantilla de flujo de trabajo secuencial básica.  El flujo de trabajo comprueba una propiedad de una biblioteca de documentos compartidos para determinar si se ha revisado un documento.  Si se ha revisado el documento, el flujo de trabajo finaliza.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un proyecto de flujo de trabajo secuencial de definición de lista de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Crear actividades de flujo de trabajo.  
  
-   Controlar eventos de actividad de flujo de trabajo.  
  
> [!NOTE]  
>  Aunque en este tutorial se utiliza un proyecto de flujo de trabajo secuencial, el proceso es idéntico para un proyecto de flujo de trabajo de máquina de estados.  
>   
>  También es posible que su equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que tenga y la configuración que esté utilizando determinan estos elementos.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Microsoft Windows y SharePoint.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Agregar propiedades a la biblioteca de documentos compartidos de SharePoint  
 Para hacer el seguimiento del estado de la revisión de documentos de la biblioteca **Documentos compartidos**, crearemos tres nuevas propiedades para documentos compartidos en nuestro sitio de SharePoint: `Status`, `Assignee` y `Review Comments`.  Definimos estas propiedades en la biblioteca **Documentos compartidos**.  
  
#### Para agregar propiedades a la biblioteca de documentos compartidos de SharePoint  
  
1.  Abra un sitio de SharePoint, como http:\/\/\<system name\>\/SitePages\/Home.aspx, en un explorador web.  
  
2.  En la barra de inicio rápido, elija **CompartidoDocumentos**.  
  
3.  Elija **Biblioteca** en la cinta de opciones de **Herramientas de biblioteca** y elija el botón de **Cree la columna** en la cinta de opciones para crear una nueva columna.  
  
4.  Llame al estado de documento de la columna, establezca su tipo en **Opción \(menú del que elegir\)**, especifique las tres opciones siguientes, y elija el botón de **Aceptar** :  
  
    -   **Revisión necesaria**  
  
    -   **Revisión completada**  
  
    -   **Cambios solicitados**  
  
5.  Cree dos columnas más y asígneles los nombres Assignee y Review Comments.  Establezca el tipo de la columna Assignee como una línea de texto única y el tipo de la columna Review Comments como varias líneas de texto.  
  
## Permitir que los documentos se editen sin requerir la desprotección  
 Es más fácil probar la plantilla de flujo de trabajo si puede editar los documentos sin tener que desprotegerlos.  En el procedimiento siguiente, se configura el sitio de SharePoint para habilitar esa posibilidad.  
  
#### Para permitir que los documentos se editen sin desprotegerlos  
  
1.  En la barra de inicio rápido, elija el vínculo de **Documentos compartidos** .  
  
2.  En la cinta de opciones de **Herramientas de biblioteca** , elija la ficha de **Biblioteca** , y elija el botón de **Valores de biblioteca** para mostrar la página de **Configuración de la biblioteca de documentos** .  
  
3.  En la sección de **Configuración general** , elija el vínculo de **Valores de versión** para mostrar la página de **Valores de versión** .  
  
4.  Compruebe que el valor de **Solicitar que los documentos estén desprotegidos para poder modificarlos** sea **No**.  Si no, cámbiela a **No** y elija el botón de **Aceptar** .  
  
5.  Cierre el explorador.  
  
## Crear un proyecto de flujo de trabajo secuencial de SharePoint  
 Un flujo de trabajo secuencial es una sucesión de pasos que se ejecutan en orden hasta que finaliza la última actividad.  En este procedimiento, creamos un flujo de trabajo secuencial que se aplicará a nuestra lista Documentos compartidos.  El asistente de flujo de trabajo permite asociar el flujo de trabajo con la definición de sitio o la definición de lista, y le permite determinar cuando se iniciará el flujo de trabajo.  
  
#### Para crear un proyecto de flujo de trabajo secuencial de SharePoint  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En la barra de menú, elija **archivo**, **new**, **Project** para mostrar el cuadro de diálogo de **Nuevo proyecto** .  
  
3.  Expanda el nodo de **sharepoint** en **Visual C\#** o **Visual Basic**y, a continuación el nodo de **2010** .  
  
4.  En el panel de **Plantillas** , elija la plantilla de **SharePoint 2010 Project** .  
  
5.  En el cuadro de **Name** , entre en MySharePointWorkflow y elija el botón de **Aceptar** .  
  
     Aparece el **Asistente para personalización de SharePoint**.  
  
6.  En la página de **Especifique el sitio y el nivel de seguridad de la depuración** , elija el botón de opción de **Implementar como solución de granja de servidores** , y elija el botón de **Finalizar** para aceptar el sitio de nivel de confianza y predeterminado.  
  
     Este paso también establece el nivel de confianza para la solución como una solución de granja de servidores, la única opción disponible para los proyectos de flujo de trabajo.  Para obtener más información, vea [Consideraciones sobre las soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  En **Explorador de soluciones**, elija el nodo de proyecto y, a continuación, en la barra de menús, elija **Project**, **Agregar nuevo elemento**.  
  
8.  En **Visual C\#** o **Visual Basic**, expanda el nodo de **sharepoint** y, a continuación el nodo de **2010** .  
  
9. En el panel de **Plantillas** , elija la plantilla de **Flujo de trabajo secuencial \(solución de granja de servidores únicamente\)** , y elija el botón de **Add** .  
  
     Aparece el **Asistente para personalización de SharePoint**.  
  
10. En la página **Especifique el nombre del flujo de trabajo de depuración**, acepte el nombre predeterminado \(**MySharePointWorkflow \- Workflow1**\).  Mantenga el valor del tipo predeterminado de la plantilla de flujo de trabajo, **Flujo de trabajo de lista**, y elija el botón de **siguiente** .  
  
11. En la página de **¿Desea que Visual Studio asocie automáticamente el flujo de trabajo en una sesión de depuración?** , elija el botón de **siguiente** para aceptar toda la configuración predeterminada.  
  
     Este paso asocia automáticamente el flujo de trabajo a la biblioteca Documentos compartidos.  
  
12. En la página de **Especificar las condiciones que especifica cómo se inicia el flujo de trabajo** , deje seleccionadas las opciones predeterminadas en la sección de **Cómo desea que se inicie el flujo de trabajo?** y elija el botón de **Finalizar** .  
  
     Esta página permite especificar cuándo se inicia el flujo de trabajo.  De forma predeterminada, el flujo de trabajo se inicia cuando un usuario lo inicia manualmente en SharePoint o cuando se crea un elemento con el que está asociado el flujo de trabajo.  
  
## Crear actividades de flujo de trabajo  
 Los flujos de trabajo contienen una o más *actividades* que representan las acciones que se van a llevar a cabo.  Utilice el diseñador de flujo de trabajo para organizar las actividades de un flujo de trabajo.  En este procedimiento, agregaremos dos actividades al flujo de trabajo: HandleExternalEventActivity y OnWorkFlowItemChanged.  Estas actividades supervisan el estado de la revisión de documentos en la lista **Documentos compartidos**  
  
#### Para crear actividades de flujo de trabajo  
  
1.  El flujo de trabajo se debería mostrar en el diseñador de flujo de trabajo.  Si no, abra **Workflow1.cs** o **Workflow1.vb** en **Explorador de soluciones**.  
  
2.  En el diseñador, elija la actividad de **OnWorkflowActivated1** .  
  
3.  En la ventana de **Propiedades** , escriba onWorkflowActivated junto a la propiedad de **Invocado** , y elija la tecla ENTRAR.  
  
     El Editor de código se abre y un método de control de eventos denominado onWorkflowActivated se agrega al archivo de código de Workflow1.  
  
4.  Vuelva al diseñador de flujo de trabajo, abra el cuadro de herramientas y, a continuación, expanda el nodo **Windows Workflow v3.0**.  
  
5.  En el nodo de **Windows workflow v3.0** de **Cuadro de herramientas**, realice uno de los siguientes conjuntos de pasos:  
  
    1.  Abrir el menú contextual de la actividad de **Mientras** y, a continuación **copiar**.  En el diseñador de flujo de trabajo, abra el menú contextual para la línea bajo la actividad de **onWorkflowActivated1** y, a continuación **Pegar**.  
  
    2.  Arrastre la actividad de **Mientras** de **Cuadro de herramientas** el diseñador de flujo de trabajo, y conectar la actividad a la línea bajo la actividad de **onWorkflowActivated1** .  
  
6.  Elija la actividad de **WhileActivity1** .  
  
7.  En la ventana de **Propiedades** , establezca **Condición** a la condición de código.  
  
8.  Expanda la propiedad de **Condición** , escriba isWorkflowPending junto a la propiedad secundaria de **Condición** y, a continuación la tecla ENTRAR.  
  
     Se abre el Editor de código y se agrega el método isWorkflowPending al archivo de código de Workflow1.  
  
9. Vuelva al diseñador de flujo de trabajo, abra el cuadro de herramientas y, a continuación, expanda el nodo **Flujo de trabajo de SharePoint**.  
  
10. En el nodo de **Flujo de trabajo de SharePoint** de **Cuadro de herramientas**, realice uno de los siguientes conjuntos de pasos:  
  
    -   Abrir el menú contextual de la actividad de **OnWorkflowItemChanged** y, a continuación **copiar**.  En el diseñador de flujo de trabajo, abra el menú contextual para la línea dentro de la actividad de **whileActivity1** y, a continuación **Pegar**.  
  
    -   Arrastre la actividad de **OnWorkflowItemChanged** de **Cuadro de herramientas** el diseñador de flujo de trabajo, y conectar la actividad a la línea dentro de la actividad de **whileActivity1** .  
  
11. Elija la actividad de **onWorkflowItemChanged1** .  
  
12. En la ventana **Propiedades**, establezca las propiedades tal y como se indica en la tabla siguiente.  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**CorrelationToken**|**workflowToken**|  
    |**Invoked**|**onWorkflowItemChanged**|  
  
## Controlar eventos de actividad  
 Finalmente, compruebe el estado del documento en cada actividad.  Si el documento se ha revisado, el flujo de trabajo termina.  
  
#### Para controlar eventos de actividad  
  
1.  En Workflow1.cs o Workflow1.vb, agregue el campo siguiente a la parte superior de la clase `Workflow1`.  Utilizará este campo en una actividad para determinar si el flujo de trabajo ha finalizado.  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  Agregue el método siguiente a la clase `Workflow1`.  Este método comprueba el valor de la propiedad `Document Status` de la lista Documentos para determinar si el documento se ha revisado.  Si la propiedad `Document Status` está establecida en `Review Complete`, el método `checkStatus` establecerá el campo `workflowPending` en **false** para indicar que el flujo de trabajo está listo para finalizar.  
  
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
  
3.  Agregue el código siguiente a los métodos `onWorkflowActivated` y `onWorkflowItemChanged` para llamar al método `checkStatus`.  Cuando el flujo de trabajo se inicia, el método `onWorkflowActivated` llama al método `checkStatus` para determinar si ya se ha revisado el documento.  Si no se ha revisado, el flujo de trabajo continúa.  Cuando se guarda el documento, el método `onWorkflowItemChanged` llama de nuevo al método `checkStatus` para determinar si se ha revisado el documento.  Mientras el campo `workflowPending` esté establecido en **true**, el flujo de trabajo continuará ejecutándose.  
  
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
  
4.  Agregue el código siguiente al método `isWorkflowPending` para comprobar el estado de la propiedad `workflowPending`.  Cada vez que se guarda el documento, la actividad **whileActivity1** llama al método `isWorkflowPending`.  Este método examina la propiedad <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> del objeto <xref:System.Workflow.Activities.ConditionalEventArgs> para determinar si la actividad **WhileActivity1** debería continuar o finalizar.  Si la propiedad se establece en **true**, la actividad continúa.  De lo contrario, la actividad finaliza y el flujo de trabajo también finaliza.  
  
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
  
## Probar la plantilla de flujo de trabajo de SharePoint  
 Al iniciar el depurador, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] implementa la plantilla de flujo de trabajo en el servidor de SharePoint y asocia la plantilla de flujo de trabajo con la lista **Documentos compartidos**.  Para probar el flujo de trabajo, inicie una instancia de la plantilla de flujo de trabajo desde un documento de la lista **Documentos compartidos**.  
  
#### Para probar la plantilla de flujo de trabajo de SharePoint  
  
1.  En Workflow1.cs o Workflow1.vb, establezca un punto de interrupción junto al método **onWorkflowActivated**.  
  
2.  Elija la tecla F5 para compilar y ejecutar la solución.  
  
     Aparecerá el sitio de SharePoint.  
  
3.  En el panel de navegación de SharePoint, elija el vínculo de **Documentos compartidos** .  
  
4.  En la página de **Documentos compartidos** , elija el vínculo de **Documentos** en la pestaña de **Herramientas de biblioteca** , y elija el botón de **Cargar documento** .  
  
5.  En el cuadro de diálogo de **Cargar documento** , elija el botón de **Browse** , elija cualquier archivo de documento, elija el botón de **Abierta** , y elija el botón de **Aceptar** .  
  
     Esto carga el documento seleccionado en la lista **Documentos compartidos** e inicia el flujo de trabajo.  
  
6.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], compruebe que el depurador se detiene en el punto de interrupción a continuación del método `onWorkflowActivated`.  
  
7.  Elija la tecla F5 para continuar la ejecución.  
  
8.  Puede cambiar los valores del documento aquí, pero los deja en los valores predeterminados por ahora eligiendo el botón de **Guardar** .  
  
     Esto le devolverá a la página **Documentos compartidos** del sitio web predeterminado de SharePoint.  
  
9. En la página de **Documentos compartidos** , compruebe que el valor bajo la columna de **MySharePointWorkflow – Workflow1** está establecido en **En curso**.  Esto indica que el flujo de trabajo está en curso y que el documento está esperando la revisión.  
  
10. En la página de **Documentos compartidos** , elija el documento, elija la flecha que aparece, y después elija el elemento de menú de **Editar propiedades** .  
  
11. Establezca **Estado de documento** a **Revisión completada**, y elija el botón de **Guardar** .  
  
     Esto le devolverá a la página **Documentos compartidos** del sitio web predeterminado de SharePoint.  
  
12. En la página de **Documentos compartidos** , compruebe que el valor bajo la columna de **Estado de documento** está establecido en **Revisión completada**.  Actualice la página de **Documentos compartidos** y compruebe que el valor bajo la columna de **MySharePointWorkflow – Workflow1** está establecido en **Completado**.  Esto indica que el flujo de trabajo ha finalizado y que el documento se ha revisado.  
  
## Pasos siguientes  
 Puede aprender más acerca de la creación de plantillas de flujo de trabajo en estos temas:  
  
-   Para obtener más información sobre las actividades de flujo de trabajo de SharePoint, vea [Actividades de flujo de trabajo para la base de SharePoint](http://go.microsoft.com/fwlink/?LinkId=178992).  
  
-   Para obtener más información sobre las actividades de Windows Workflow Foundation, vea [Espacio de nombres de System.Workflow.Activities](http://go.microsoft.com/fwlink/?LinkId=178993).  
  
## Vea también  
 [Crear soluciones de flujo de trabajo de SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Plantillas de proyecto y de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [Compilar y depurar soluciones de SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  