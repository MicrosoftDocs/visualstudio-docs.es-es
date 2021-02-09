---
title: 'Tutorial: agregar una página de aplicación a un flujo de trabajo | Microsoft Docs'
description: En este tutorial, agregue una página de aplicación a una solución de flujo de trabajo de SharePoint. Modifique el código de flujo de trabajo. Cree, codifique y pruebe la página de la aplicación.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d07b5272a31a0c649e12f353aefaa7c63c335eb5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882666"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>Tutorial: Adición de una página de aplicación a un flujo de trabajo
  En este tutorial se muestra cómo agregar una página de aplicación que muestra los datos derivados de un flujo de trabajo a un proyecto de flujo de trabajo. Se basa en el proyecto descrito en el tema [Tutorial: creación de un flujo de trabajo con formularios de asociación e iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

 En este tutorial se muestran las siguientes tareas:

- Agregar una página de aplicación ASPX a un proyecto de flujo de trabajo de SharePoint.

- Obtener datos del proyecto de flujo de trabajo y manipularlos.

- Mostrar datos en una tabla de la página de la aplicación.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint.

- Visual Studio.

- También tiene que completar el proyecto en el tema [Tutorial: creación de un flujo de trabajo con formularios de asociación e iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

## <a name="amend-the-workflow-code"></a>Corregir el código del flujo de trabajo
 En primer lugar, agregue una línea de código al flujo de trabajo para establecer el valor de la columna resultado en la cantidad del informe de gastos. Este valor se usa más adelante en el cálculo de resumen del informe de gastos.

#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>Para establecer el valor de la columna de resultados en el flujo de trabajo

1. Cargue el proyecto completado del tema [Tutorial: creación de un flujo de trabajo con formularios de asociación e iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Abra el código para *Workflow1.CS* o *Workflow1. VB* (dependiendo del lenguaje de programación).

3. `createTask1_MethodInvoking`Agregue el código siguiente al final del método:

    ```vb
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =
      workflowProperties.InitiationData
    ```

    ```csharp
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =
      workflowProperties.InitiationData;
    ```

## <a name="create-an-application-page"></a>Crear una página de aplicación
 A continuación, agregue un formulario ASPX al proyecto. Este formulario mostrará los datos obtenidos del proyecto de flujo de trabajo del informe de gastos. Para ello, agregará una página de aplicación. Una página de aplicación utiliza la misma página maestra que otras páginas de SharePoint, lo que significa que se asemejará a otras páginas del sitio de SharePoint.

#### <a name="to-add-an-application-page-to-the-project"></a>Para agregar una página de aplicación al proyecto

1. Elija el proyecto ExpenseReport y, a continuación, en la barra de menús, elija **proyecto**  >  **Agregar nuevo elemento**.

2. En el panel **plantillas** , elija la plantilla **Página de aplicación** , use el nombre predeterminado para el elemento de proyecto (**ApplicationPage1. aspx**) y elija el botón **Agregar** .

3. En [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] de ApplicationPage1. aspx, reemplace la `PlaceHolderMain` sección por lo siguiente:

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

4. Agregue un título a la página de la aplicación reemplazando la `PlaceHolderPageTitleInTitleArea` sección por lo siguiente:

    ```aspx-csharp
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >
        Expense Report Summary
    </asp:Content>
    ```

## <a name="code-the-application-page"></a>Código de la página de la aplicación
 A continuación, agregue código a la página de la aplicación Resumen del informe de gastos. Al abrir la página, el código examina la lista de tareas de SharePoint en busca de gastos que superan el límite de gasto asignado. El informe muestra cada elemento junto con la suma de los gastos.

#### <a name="to-code-the-application-page"></a>Para codificar la página de la aplicación

1. Elija el nodo **ApplicationPage1. aspx** y, a continuación, en la barra de menús, elija **Ver**  >  **código** para mostrar el código subyacente de la página de la aplicación.

2. Reemplace las instrucciones **using** o **Import** (dependiendo del lenguaje de programación) en la parte superior de la clase con lo siguiente:

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

3. Agregue el código siguiente al método `Page_Load`:

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
    > Asegúrese de reemplazar "TestServer" en el código por el nombre de un servidor válido que ejecute SharePoint.

## <a name="test-the-application-page"></a>Probar la página de aplicación
 A continuación, determine si la página de la aplicación muestra los datos de gastos correctamente.

#### <a name="to-test-the-application-page"></a>Para probar la página de aplicación

1. Elija la tecla **F5** para ejecutar e implementar el proyecto en SharePoint.

2. Elija el botón **Inicio** y, a continuación, elija el vínculo **documentos compartidos** en la barra Inicio rápido para mostrar la lista Documentos compartidos en el sitio de SharePoint.

3. Para representar informes de gastos en este ejemplo, cargue algunos nuevos documentos en la lista documentos. para ello, elija el vínculo **documentos** en la pestaña **LibraryTools** de la parte superior de la página y, a continuación, elija el botón **cargar documento** en la cinta de opciones de herramientas.

4. Después de cargar algunos documentos, cree una instancia del flujo de trabajo; para ello, elija el vínculo **biblioteca** en la pestaña **LibraryTools** de la parte superior de la página y, a continuación, elija el botón configuración de la biblioteca en la cinta de **Opciones** de herramientas.

5. En la página Configuración de la **biblioteca de documentos** , elija el vínculo configuración de flujo de **trabajo** en la sección **permisos y administración** .

6. En la página **configuración del flujo de trabajo** , elija el vínculo **Agregar un flujo de trabajo** .

7. En la página **Agregar un flujo de trabajo** , elija el flujo de trabajo **ExpenseReport-Workflow1** , escriba un nombre para el flujo de trabajo, como **ExpenseTest**, y, a continuación, elija el botón **siguiente** .

    Aparece el formulario de Asociación de flujo de trabajo. Úselo para informar del importe del límite de gastos.

8. En el formulario de asociación, escriba **1000** en el cuadro **límite de aprobación automática** y, a continuación, elija el botón **asociar flujo de trabajo** .

9. Elija el botón **Inicio** para volver a la Página principal de SharePoint.

10. Elija el vínculo **documentos compartidos** en la barra de inicio rápido.

11. Elija uno de los documentos cargados para mostrar una flecha desplegable, elíjalo y, a continuación, elija el elemento **flujos de trabajo** .

12. Elija la imagen situada junto a ExpenseTest para mostrar el formulario de inicio del flujo de trabajo.

13. En el cuadro de texto **total de gastos** , especifique un valor mayor que 1000 y, a continuación, elija el botón **Iniciar flujo de trabajo** .

     Cuando un gasto informado supera el importe del gasto asignado, se agrega una tarea a la Lista de tareas. Una columna denominada **ExpenseTest** con el valor **completado** también se agrega al elemento de informe de gastos en la lista Documentos compartidos.

14. Repita los pasos del 11-13 con otros documentos de la lista Documentos compartidos. (El número exacto de documentos no es importante).

15. Muestre la página de la aplicación de resumen del informe de gastos abriendo la siguiente dirección URL en un explorador Web: **http://**<em>SystemName</em>**/_layouts/expensereport/applicationpage1.aspx**.

     En la página Resumen del informe de gastos se enumeran todos los informes de gastos que superaron la cantidad asignada, la cantidad en la que se excedieron y la cantidad total de todos los informes.

## <a name="next-steps"></a>Pasos siguientes
 Para obtener más información acerca de las páginas de aplicación de SharePoint, vea [crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

 Puede obtener más información sobre cómo diseñar el contenido de una página de SharePoint mediante el diseñador web visual de Visual Studio de estos temas:

- [Crear elementos Web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Crear controles reutilizables para elementos Web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Vea también

- [Tutorial: Creación de un flujo de trabajo con formularios de asociación e iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Cómo: para crear una página de aplicación](../sharepoint/how-to-create-an-application-page.md)
- [Creación de páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)