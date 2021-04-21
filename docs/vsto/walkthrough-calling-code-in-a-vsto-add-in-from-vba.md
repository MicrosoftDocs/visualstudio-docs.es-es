---
title: 'Tutorial: Llamada de código en un complemento de VSTO desde VBA'
description: Obtenga información sobre cómo exponer un objeto en un complemento de VSTO a otras soluciones de Microsoft Office, incluidos Visual Basic para Aplicaciones (VBA) y complementos VSTO COM.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- Video How tos, Office development in Visual Studio
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 21e0928396327911ea794c6270340c6efd27a43e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824606"
---
# <a name="walkthrough-call-code-in-a-vsto-add-in-from-vba"></a>Tutorial: Llamada de código en un complemento de VSTO desde VBA
  Este tutorial muestra cómo exponer un objeto de un complemento de VSTO a otras soluciones de Microsoft Office, incluido Visual Basic para aplicaciones (VBA) y complementos VSTO de COM.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Aunque este tutorial usa concretamente Excel, los conceptos que se muestran en él se pueden aplicar a cualquier plantilla de proyecto de complementos de VSTO proporcionada por Visual Studio.

 En este tutorial se muestran las tareas siguientes:

- Definir una clase que se puede exponer a otras soluciones de Office.

- Exponer la clase a otras soluciones de Office.

- Llamar a un método de la clase desde código VBA.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-the-vsto-add-in-project"></a>Creación del proyecto de complemento de VSTO
 El primer paso es crear un proyecto de complemento de VSTO para Excel.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de complemento de VSTO para Excel con el nombre **ExcelImportData** mediante la plantilla de proyecto de complementos de VSTO para Excel. Para obtener más información, consulta [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] abre el **archivo de código ThisAddIn.cs** o **ThisAddIn.vb** y agrega el proyecto **ExcelImportData** **a Explorador de soluciones**.

## <a name="define-a-class-that-you-can-expose-to-other-office-solutions"></a>Definir una clase que pueda exponer a otras soluciones de Office
 El propósito de este tutorial es llamar a al método `ImportData` de una clase denominada `AddInUtilities` en el complemento de VSTO desde código de VBA. Este método escribe una cadena en la celda A1 de la hoja de cálculo activa.

 Para exponer la clase `AddInUtilities` a otras soluciones de Office, debe hacer que la clase sea pública y visible para COM. También debe exponer la interfaz [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) de la clase. El código del procedimiento siguiente muestra una manera de cumplir estos requisitos. Para obtener más información, consulta [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>Para definir una clase que pueda exponer a otras soluciones de Office

1. En el menú **Proyecto** , haga clic en **Agregar clase**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , cambie el nombre de la nueva clase a **AddInUtilities** y haga clic en **Agregar**.

     El archivo **AddInUtilities.cs** o **AddInUtilities.vb** se abre en el Editor de código.

3. Agregue las siguientes directivas a la parte superior del archivo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet2":::

4. Reemplace la clase `AddInUtilities` por el siguiente código.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet3":::

     Este código hace que la clase `AddInUtilities` sea visible para COM y agrega el método `ImportData` a la clase. Para exponer la interfaz [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) , la clase `AddInUtilities` también tiene el atributo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> e implementa una interfaz que es visible para COM.

## <a name="expose-the-class-to-other-office-solutions"></a>Exposición de la clase a otras soluciones de Office
 Para exponer la clase `AddInUtilities` a otras soluciones de Office, invalide el método <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> en la clase `ThisAddIn` . Al invalidarlo, devuelva una instancia de la clase `AddInUtilities` .

### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>Para exponer la clase AddInUtilities a otras soluciones de Office

1. En el **Explorador de soluciones**, expanda **Excel**.

2. Haga clic con el botón secundario en el archivo **ThisAddin.cs** o **ThisAddin.vb** y, a continuación, haga clic en **Ver código**.

3. Agregue el siguiente código a la clase `ThisAddIn` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb" id="Snippet1":::

4. En el menú **Compilar** , haga clic en **Compilar solución**.

     Compruebe que la solución se compila sin errores.

## <a name="test-the-vsto-add-in"></a>Prueba del complemento de VSTO
 Puede llamar a la clase `AddInUtilities` desde varios tipos distintos de soluciones de Office. En este tutorial, usará el código VBA en un libro de Excel. Para obtener más información sobre los otros tipos de soluciones de Office que también puede usar, vea Llamada a código en complementos [VSTO desde otras soluciones de Office.](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)

### <a name="to-test-your-vsto-add-in"></a>Para probar el complemento de VSTO

1. Presione **F5** para ejecutar el proyecto.

2. En Excel, guarde el libro activo como un libro de Excel habilitado para macros (*.xlsm). Guárdelo en una ubicación conveniente, como el escritorio.

3. En la cinta de opciones, haga clic en la pestaña **Desarrollador** .

    > [!NOTE]
    > Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, [vea Cómo: Mostrar la pestaña del desarrollador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. En el grupo **Código** , haga clic en **Visual Basic**.

     Se abrirá el Editor de Visual Basic.

5. En la ventana **Proyecto** , haga doble clic en **ThisWorkbook**.

     Se abrirá el archivo de código para el objeto `ThisWorkbook` .

6. Agregue el código VBA siguiente al archivo de código. Este código obtiene primero un objeto COMAddIn que representa el complemento VSTO **ExcelImportData.** A continuación, el código usa la propiedad Object del objeto COMAddIn para llamar al `ImportData` método .

    ```vb
    Sub CallVSTOMethod()
        Dim addIn As COMAddIn
        Dim automationObject As Object
        Set addIn = Application.COMAddIns("ExcelImportData")
        Set automationObject = addIn.Object
        automationObject.ImportData
    End Sub
    ```

7. Presione **F5**.

8. Compruebe que se ha agregado al libro la hoja nueva **Datos importados** . Compruebe también que la celda A1 contiene la cadena **This is my data**.

9. Salga de Excel.

## <a name="next-steps"></a>Pasos siguientes
 Puede obtener más información acerca de la programación de complementos de VSTO en estos temas:

- Utilice la clase `ThisAddIn` para automatizar la aplicación host y realizar otras tareas en proyectos de complementos de VSTO. Para obtener más información, [vea Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

- Crear un panel de tareas personalizado en un complemento de VSTO. Para obtener más información, vea [Paneles de tareas personalizados](../vsto/custom-task-panes.md) y Cómo: Agregar un panel de [tareas personalizado a una aplicación.](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)

- Personalice la cinta de opciones en un complemento de VSTO. Para obtener más información, vea Información [general sobre la cinta](../vsto/ribbon-overview.md) de opciones y Cómo: Introducción a la [personalización de la cinta de opciones.](../vsto/how-to-get-started-customizing-the-ribbon.md)

## <a name="see-also"></a>Consulte también
- [Programación de complementos VSTO](../vsto/programming-vsto-add-ins.md)
- [Llamada de código en complementos de VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Desarrollo de soluciones de Office](../vsto/developing-office-solutions.md)
- [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Personalización de las características de la interfaz de usuario mediante interfaces de extensibilidad](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
