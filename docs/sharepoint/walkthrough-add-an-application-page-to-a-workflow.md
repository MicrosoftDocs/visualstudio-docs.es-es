---
title: 'Tutorial: Agregar una página de aplicación a un flujo de trabajo | Microsoft Docs'
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
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 937fb2d5b41c2fce9fb11cc683f7abd771718e89
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119467"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>Tutorial: Agregar una página de aplicación a un flujo de trabajo
  Este tutorial muestra cómo agregar una página de aplicación que muestra los datos derivados de un flujo de trabajo a un proyecto de flujo de trabajo. Basa en el proyecto que se describe en el tema [Tutorial: crear un flujo de trabajo con formularios de asociación e iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Adición de una aplicación de página ASPX a un proyecto de flujo de trabajo de SharePoint.  
  
-   Obtención de datos desde el proyecto de flujo de trabajo y manipulación de estos.  
  
-   Mostrar datos en una tabla en la página de aplicación.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint. Para obtener más información, consulte [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   También tiene que completar el proyecto en el tema [Tutorial: crear un flujo de trabajo con formularios de asociación e iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).  
  
## <a name="ammend-the-workflow-code"></a>Ammend el código de flujo de trabajo
 En primer lugar, agregue una línea de código para el flujo de trabajo para establecer el valor de la columna de resultado a la cantidad del informe de gastos. Este valor se usa más adelante en el cálculo de resumen del informe de gastos.  
  
#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>Para establecer el valor de la columna de resultado del flujo de trabajo
  
1.  Cargue el proyecto completado del tema [Tutorial: crear un flujo de trabajo con la asociación y formularios de iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Abra el código para *Workflow1.cs* o *Workflow1.vb* (dependiendo del lenguaje de programación).  
  
3.  En la parte inferior de la `createTask1_MethodInvoking` método, agregue el código siguiente:  
  
    ```vb  
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =   
      workflowProperties.InitiationData  
    ```  
  
    ```csharp  
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =   
      workflowProperties.InitiationData;  
    ```  
  
## <a name="create-an-application-page"></a>Crear una página de aplicación
 A continuación, agregue un formulario ASPX al proyecto. Este formulario mostrará los datos obtenidos desde el proyecto de flujo de trabajo de informe de gastos. Para ello, agregará una página de aplicación. Una página de aplicación utiliza la misma página maestra como otras páginas de SharePoint, lo que significa que será similar a otras páginas del sitio de SharePoint.  
  
#### <a name="to-add-an-application-page-to-the-project"></a>Para agregar una página de aplicación al proyecto  
  
1.  Elija el proyecto ExpenseReport y, a continuación, en la barra de menús, elija **proyecto** > **Agregar nuevo elemento**.  
  
2.  En el **plantillas** panel, elija el **página aplicación** plantilla, use el nombre predeterminado para el elemento de proyecto (**ApplicaitonPage1.aspx**) y elija el **Agregar** botón.  
  
3.  En el [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] de ApplicationPage1.aspx, reemplace el `PlaceHolderMain` sección con lo siguiente:  
  
    ```aspx-csharp  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
        <asp:Label ID="Label1" runat="server" Font-Bold="True"   
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>  
        <br />  
        <asp:Table ID="Table1" runat="server">  
        </asp:Table>  
    </asp:Content>  
    ```  
  
     Este código agrega una tabla a la página junto con un título.  
  
4.  Agregar un título a la página de aplicación, reemplazando el `PlaceHolderPageTitleInTitleArea` sección con lo siguiente:  
  
    ```aspx-csharp  
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >  
        Expense Report Summary  
    </asp:Content>  
    ```  
  
## <a name="code-the-application-page"></a>Código de la página de aplicación
 A continuación, agregue código a la página de aplicación de resumen del informe de gastos. Cuando se abre la página, el código examina la lista de tareas de SharePoint para los gastos que supera el límite de gasto asignado. El informe enumera cada elemento junto con la suma de los gastos.  
  
#### <a name="to-code-the-application-page"></a>En el código de la página de aplicación  
  
1.  Elija la **ApplicationPage1.aspx** nodo y, a continuación, en la barra de menús, elija **vista** > **código** para mostrar el código subyacente de la página de aplicación.  
  
2.  Reemplace el **mediante** o **importación** instrucciones (dependiendo del lenguaje de programación) en la parte superior de la clase con lo siguiente:  
  
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
    >  No olvide reemplazar "TestServer" en el código con el nombre de un servidor válido que se está ejecutando SharePoint.  
  
## <a name="test-the-application-page"></a>Probar la página de aplicación
 A continuación, determine si la página de aplicación muestra los datos de gastos correctamente.  
  
#### <a name="to-test-the-application-page"></a>Para probar la página de aplicación  
  
1.  Elija la **F5** clave ejecutar e implementar el proyecto de SharePoint.  
  
2.  Elija la **inicio** botón y, a continuación, elija el **documentos compartidos** vínculo en la barra de inicio rápido para mostrar la lista de documentos compartidos en el sitio de SharePoint.  
  
3.  Para representar los informes de gastos en este ejemplo, cargar algunos documentos nuevos en la lista de documentos eligiendo la **documentos** vincular en el **herramientas de biblioteca** ficha en la parte superior de la página y, a continuación, eligiendo el  **Cargar documento** botón en la cinta de herramientas.  
  
4.  Después de cargar algunos documentos, crear una instancia de flujo de trabajo eligiendo el **biblioteca** vincular en el **herramientas de biblioteca** ficha en la parte superior de la página y, después, elige el **configuración de la biblioteca**botón en la cinta de herramientas.  
  
5.  En el **Document Library Settings** página, elija el **Workflow Settings** vincular en el **permisos y administración** sección.  
  
6.  En el **Workflow Settings** página, elija el **agregar un flujo de trabajo** vínculo.  
  
7.  En el **agregar un flujo de trabajo** página, elija el **ExpenseReport - Workflow1** flujo de trabajo, escriba un nombre para el flujo de trabajo, como **ExpenseTest**y, a continuación, elija el **Siguiente** botón.  
  
     Aparece el formulario de asociación de flujo de trabajo. Utilícelo para informar el importe del límite de gasto.  
  
8.  En el formulario de asociación, escriba **1000** en el **límite de aprobación automática** cuadro y, a continuación, elija el **asociar el flujo de trabajo** botón.  
  
9. Elija la **principal** botón para volver a la página principal de SharePoint.  
  
10. Elija la **documentos compartidos** vínculo en la barra de inicio rápido.  
  
11. Elija uno de los documentos cargados que muestre una flecha de lista desplegable, selecciónela y, a continuación, elija el **flujos de trabajo** elemento.  
  
12. Elija una imagen junto a ExpenseTest para mostrar el formulario de iniciación de flujo de trabajo.  
  
13. En el **gasto Total** cuadro de texto, escriba un valor que es mayor que 1000 y, a continuación, elija el **iniciar flujo de trabajo** botón.  
  
     Cuando un gasto supera el importe del gasto asignada, se agrega una tarea a la lista de tareas. Una columna denominada **ExpenseTest** con el valor **completado** también se agrega al elemento de informe de gastos en la lista de documentos compartidos.  
  
14. Repita los pasos 11 a 13 con otros documentos en la lista de documentos compartidos. (El número exacto de documentos no es importante).  
  
15. Mostrar la página de aplicación de resumen del informe de gastos, abra la siguiente dirección URL en un explorador Web: **http://***SystemName***/_layouts/ExpenseReport/ApplicationPage1.aspx**.  
  
     La página de resumen del informe de gastos enumera todos los informes de gastos que superan la cantidad asignada, la cantidad que la superan y la cantidad total de todos los informes.  
  
## <a name="next-steps"></a>Pasos siguientes
 Para obtener más información acerca de las páginas de aplicación de SharePoint, vea [crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 Puede aprender más acerca de cómo diseñar el contenido de la página de SharePoint mediante Visual Web Designer en Visual Studio en los siguientes temas:  
  
-   [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## <a name="see-also"></a>Vea también
 [Tutorial: Crear un flujo de trabajo con formularios de asociación e iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Cómo: crear una página de aplicación](../sharepoint/how-to-create-an-application-page.md)   
 [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
