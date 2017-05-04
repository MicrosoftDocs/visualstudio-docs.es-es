---
title: "Tutorial: Agregar una p&#225;gina de aplicaci&#243;n a un flujo de trabajo | Microsoft Docs"
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
  - "página de aplicación [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, agregar una página de aplicaciones al flujo de trabajo"
ms.assetid: e4845d07-917b-45cb-a569-4ecdd602fbd9
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Tutorial: Agregar una p&#225;gina de aplicaci&#243;n a un flujo de trabajo
  En este tutorial se muestra cómo agregar una página de aplicación que muestre los datos derivados de un flujo de trabajo a un proyecto de flujo de trabajo.  El punto de partida es el proyecto descrito en el tema [Tutorial: Crear un flujo de trabajo con formularios de asociación y de iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Agregar una aplicación de página ASPX a un proyecto de flujo de trabajo de SharePoint.  
  
-   Obtener los datos del proyecto de flujo de trabajo y manipularlos.  
  
-   Mostrar los datos en una tabla en la página de aplicación.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   También tiene que completar el proyecto del tema [Tutorial: Crear un flujo de trabajo con formularios de asociación y de iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).  
  
## Corregir código del flujo de trabajo  
 Primero, agregue una línea de código al flujo de trabajo para establecer el valor de la columna Outcome en la cantidad del informe de gastos.  Este valor se utiliza después en el cálculo final del informe de gastos.  
  
#### Para establecer el valor de la columna Outcome en el flujo de trabajo  
  
1.  Cargue el proyecto completado del tema [Tutorial: Crear un flujo de trabajo con formularios de asociación y de iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Abra el código de Workflow1.cs o Workflow1.vb \(según cuál sea el lenguaje de programación\).  
  
3.  Agregue el código siguiente al método `createTask1_MethodInvoking`.  
  
    ```vb  
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =   
      workflowProperties.InitiationData  
    ```  
  
    ```csharp  
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =   
      workflowProperties.InitiationData;  
    ```  
  
## Crear una página de aplicación  
 A continuación, agregue un objeto complexType ASPX al proyecto.  Este formulario mostrará los datos obtenidos del proyecto de flujo de trabajo del informe de gastos.  Para hacerlo, agregará una página de aplicación.  Una página de aplicación utiliza la misma página maestra que el resto de páginas de SharePoint, lo que significa que se parece a otras páginas de sitio de SharePoint.  
  
#### Para agregar una página de aplicación al proyecto  
  
1.  Elija el proyecto ExpenseReport y, a continuación, en la barra de menú, elija **Project**, **Agregar nuevo elemento**.  
  
2.  En el panel de **Plantillas** , elija la plantilla de **Página de aplicación** , utilice el nombre predeterminado para el elemento de proyecto \(**ApplicaitonPage1.aspx**\), y elija el botón de **Add** .  
  
3.  En el código [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] de ApplicationPage1.aspx, reemplace la sección `PlaceHolderMain` por lo siguiente:  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
        <asp:Label ID="Label1" runat="server" Font-Bold="True"   
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>  
        <br />  
        <asp:Table ID="Table1" runat="server">  
        </asp:Table>  
    </asp:Content>  
    ```  
  
     Este código agrega una tabla a la página junto con un título.  
  
4.  Agregue un título a la página de aplicación reemplazando la sección `PlaceHolderPageTitleInTitleArea` por lo siguiente:  
  
    ```  
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >  
        Expense Report Summary  
    </asp:Content>  
    ```  
  
## Codificar la página de aplicación  
 A continuación, agregue el código a la página de aplicación de resumen del informe de gastos.  Al abrir la página, el código examina la lista Tareas de SharePoint para buscar los gastos que superaron el límite asignado.  El informe enumera cada elemento junto con la suma de los gastos.  
  
#### Para codificar la página de aplicación  
  
1.  Elija el nodo de **ApplicationPage1.aspx** y, a continuación, en la barra de menú, elija **Visualización**, **code** para mostrar el código subyacente de la página de aplicación.  
  
2.  Reemplace las instrucciones **Import** o **using** \(dependiendo del lenguaje de programación\) de la parte superior de la clase por el siguiente:  
  
    ```vb  
    Imports System  
    Imports Microsoft.SharePoint  
    Imports Microsoft.SharePoint.WebControls  
    Imports System.Collections  
    Imports System.Data  
    Imports System.Web.UI  
    Imports System.Web.UI.WebControls  
    Imports System.Web.UI.WebControls.WebParts  
    Imports System.Drawing  
    Imports Microsoft.SharePoint.Navigation  
    ```  
  
    ```csharp  
    using System;  
    using Microsoft.SharePoint;  
    using Microsoft.SharePoint.WebControls;  
    using System.Collections;  
    using System.Data;  
    using System.Web.UI;  
    using System.Web.UI.WebControls;  
    using System.Web.UI.WebControls.WebParts;  
    using System.Drawing;  
    using Microsoft.SharePoint.Navigation;  
    ```  
  
3.  Agregue el código siguiente al método `Page_Load`:  
  
    ```vb  
    Try  
        ' Reference the Tasks list on the SharePoint site.  
        ' Replace "TestServer" with a valid SharePoint server name.  
        Dim site As SPSite = New SPSite("http://TestServer")  
        Dim list As SPList = site.AllWebs(0).Lists("Tasks")  
        ' string text = "";  
        Dim sum As Integer = 0  
        Table1.Rows.Clear()  
        ' Add table headers.  
        Dim hr As TableHeaderRow = New TableHeaderRow  
        hr.BackColor = Color.LightBlue  
        Dim hc1 As TableHeaderCell = New TableHeaderCell  
        Dim hc2 As TableHeaderCell = New TableHeaderCell  
        hc1.Text = "Expense Report Name"  
        hc2.Text = "Amount Exceeded"  
        hr.Cells.Add(hc1)  
        hr.Cells.Add(hc2)  
        ' Add the TableHeaderRow as the first item   
        ' in the Rows collection of the table.  
        Table1.Rows.AddAt(0, hr)  
        ' Iterate through the tasks in the Task list and collect those    
        ' that have values in the "Related Content" and "Outcome" fields   
        ' - the fields written to when expense approval is required.  
        For Each item As SPListItem In list.Items  
            Dim s_relContent As String = ""  
            Dim s_outcome As String = ""  
            Try  
                ' Task has the fields - treat as expense report.  
                s_relContent = item.GetFormattedValue("Related Content")  
                s_outcome = item.GetFormattedValue("Outcome")  
            Catch erx As System.Exception  
                ' Task does not have fields - skip it.  
                Continue For  
            End Try  
            ' Convert amount to an int and keep a running total.  
            If (Not String.IsNullOrEmpty(s_relContent) And Not   
              String.IsNullOrEmpty(s_outcome)) Then  
                sum = (sum + Convert.ToInt32(s_outcome))  
                Dim relContent As TableCell = New TableCell  
                relContent.Text = s_relContent  
                Dim outcome As TableCell = New TableCell  
                outcome.Text = ("$" + s_outcome)  
                Dim dataRow2 As TableRow = New TableRow  
                dataRow2.Cells.Add(relContent)  
                dataRow2.Cells.Add(outcome)  
                Table1.Rows.Add(dataRow2)  
            End If  
        Next  
        ' Report the sum of the reports in the table footer.  
        Dim tfr As TableFooterRow = New TableFooterRow  
        tfr.BackColor = Color.LightGreen  
        ' Create a TableCell object to contain the   
        ' text for the footer.  
        Dim ftc1 As TableCell = New TableCell  
        Dim ftc2 As TableCell = New TableCell  
        ftc1.Text = "TOTAL: "  
        ftc2.Text = ("$" + Convert.ToString(sum))  
        ' Add the TableCell object to the Cells  
        ' collection of the TableFooterRow.  
        tfr.Cells.Add(ftc1)  
        tfr.Cells.Add(ftc2)  
        ' Add the TableFooterRow to the Rows  
        ' collection of the table.  
        Table1.Rows.Add(tfr)  
    Catch errx As Exception  
        System.Diagnostics.Debug.WriteLine(("Error: " + errx.ToString))  
    End Try  
    ```  
  
    ```csharp  
    try  
    {  
        // Reference the Tasks list on the SharePoint site.  
        // Replace "TestServer" with a valid SharePoint server name.  
        SPSite site = new SPSite("http://TestServer");  
        SPList list = site.AllWebs[0].Lists["Tasks"];  
  
        // string text = "";  
        int sum = 0;  
  
        Table1.Rows.Clear();  
  
        // Add table headers.  
        TableHeaderRow hr = new TableHeaderRow();  
        hr.BackColor = Color.LightBlue;  
        TableHeaderCell hc1 = new TableHeaderCell();  
        TableHeaderCell hc2 = new TableHeaderCell();  
        hc1.Text = "Expense Report Name";  
        hc2.Text = "Amount Exceeded";  
        hr.Cells.Add(hc1);  
        hr.Cells.Add(hc2);  
        // Add the TableHeaderRow as the first item   
        // in the Rows collection of the table.  
        Table1.Rows.AddAt(0, hr);  
  
        // Iterate through the tasks in the Task list and collect those   
        // that have values in the "Related Content" and "Outcome"   
        // fields - the fields written to when expense approval is   
        // required.  
        foreach (SPListItem item in list.Items)  
        {  
            string s_relContent = "";  
            string s_outcome = "";  
  
            try  
            {  
                // Task has the fields - treat as expense report.  
                s_relContent = item.GetFormattedValue("Related   
                  Content");  
                s_outcome = item.GetFormattedValue("Outcome");  
            }  
            catch  
            {  
                // Task does not have fields - skip it.  
                continue;  
            }  
  
            if (!String.IsNullOrEmpty(s_relContent) &&   
              !String.IsNullOrEmpty(s_outcome))  
            {  
                // Convert amount to an int and keep a running total.  
                sum += Convert.ToInt32(s_outcome);  
                TableCell relContent = new TableCell();  
                relContent.Text = s_relContent;  
                TableCell outcome = new TableCell();  
                outcome.Text = "$" + s_outcome;  
                TableRow dataRow2 = new TableRow();  
                dataRow2.Cells.Add(relContent);  
                dataRow2.Cells.Add(outcome);  
                Table1.Rows.Add(dataRow2);  
            }  
        }  
  
        // Report the sum of the reports in the table footer.  
           TableFooterRow tfr = new TableFooterRow();  
        tfr.BackColor = Color.LightGreen;  
  
        // Create a TableCell object to contain the   
        // text for the footer.  
        TableCell ftc1 = new TableCell();  
        TableCell ftc2 = new TableCell();  
        ftc1.Text = "TOTAL: ";  
        ftc2.Text = "$" + Convert.ToString(sum);  
  
        // Add the TableCell object to the Cells  
        // collection of the TableFooterRow.  
        tfr.Cells.Add(ftc1);  
        tfr.Cells.Add(ftc2);  
  
        // Add the TableFooterRow to the Rows  
        // collection of the table.  
        Table1.Rows.Add(tfr);  
    }  
  
    catch (Exception errx)  
    {  
        System.Diagnostics.Debug.WriteLine("Error: " + errx.ToString());  
    }  
    ```  
  
    > [!WARNING]  
    >  Asegúrese de reemplazar “TestServer” en el código con el nombre de un servidor válido que ejecute SharePoint.  
  
## Probar la página de aplicación  
 A continuación, determine si la página de aplicación muestra los datos de gastos correctamente.  
  
#### Para probar la página de aplicación  
  
1.  Elija la tecla F5 para ejecutar e implementar el proyecto en SharePoint.  
  
2.  Elija el botón de **Domicilio** , y elija el vínculo de **Documentos compartidos** en la barra de inicio rápido para mostrar documentos compartidos en el sitio de SharePoint.  
  
3.  Para representar los informes de gastos para este ejemplo, cargue algunos nuevos documentos en la lista documentos eligiendo el vínculo de **Documentos** en la pestaña de **LibraryTools** en la parte superior de la página y después elegir el botón de **Cargar documento** en la cinta de opciones de la herramienta.  
  
4.  Después de cargar algunos documentos, cree instancias del flujo de trabajo eligiendo el vínculo de **Biblioteca** en la pestaña de **LibraryTools** en la parte superior de la página y después elegir el botón de **Valores de biblioteca** en la cinta de opciones de la herramienta.  
  
5.  En la página de **Configuración de la biblioteca de documentos** , elija el vínculo de **Valores de flujo de trabajo** en la sección de **Permisos y administración** .  
  
6.  En la página de **Valores de flujo de trabajo** , elija el vínculo de **Agregue un flujo de trabajo** .  
  
7.  En la página de **Agregue un flujo de trabajo** , elija el flujo de trabajo de **ExpenseReport \- Workflow1** , escriba un nombre para el flujo de trabajo, como ExpenseTest, y elija el botón de **siguiente** .  
  
     Aparece el formulario de asociación del flujo de trabajo.  Utilícelo para notificar la cantidad de límite de gastos.  
  
8.  En el formulario de asociación, escriba en **1000** en el cuadro de **Límite auto de aprobación** , y elija el botón de **Asociar flujo de trabajo** .  
  
9. Elija el botón de **Domicilio** para volver a la página principal de SharePoint.  
  
10. Elija el vínculo de **Documentos compartidos** en la barra de inicio rápido.  
  
11. Elija uno de los documentos cargados para mostrar una flecha de lista desplegable, elija y, a continuación elija el elemento de **Flujos de trabajo** .  
  
12. Elija la imagen junto a ExpenseTest para mostrar el formulario de Iniciación de flujo de trabajo.  
  
13. En el cuadro de texto de **Total de gastos** , especifique un valor mayor que 1000, y elija el botón de **Iniciar flujo de trabajo** .  
  
     Cuando un gasto supera la cantidad de gasto asignada, se agrega una tarea a la lista Tareas.  Una columna denominada **ExpenseTest** con el valor **Completado** también se agrega al elemento de informe de gastos en la lista Documentos compartidos.  
  
14. Repita los pasos 11 a 13 con otros documentos de la lista Documentos compartidos. \(El número exacto de documentos no es importante\).  
  
15. Muestre la página de aplicación de resumen del informe de gastos abriendo la siguiente dirección URL en un explorador web: **http:\/\/***SystemName***\/\_layouts\/ExpenseReport\/ApplicationPage1.aspx**.  
  
     La página de resumen del informe de gastos enumera todos los informes de gastos que superan la cantidad asignada, la cantidad en que la superan y la cantidad total de todos los informes.  
  
## Pasos siguientes  
 Para obtener más información sobre las páginas de aplicación de SharePoint, vea [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 En los temas siguientes puede obtener más información sobre cómo diseñar el contenido de las páginas de SharePoint con el diseñador web visual en Visual Studio:  
  
-   [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## Vea también  
 [Tutorial: Crear un flujo de trabajo con formularios de asociación y de iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Cómo: Crear una página de aplicación](../sharepoint/how-to-create-an-application-page.md)   
 [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  