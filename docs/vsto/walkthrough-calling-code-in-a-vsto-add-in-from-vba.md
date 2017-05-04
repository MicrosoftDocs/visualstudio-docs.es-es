---
title: "Tutorial: Llamar a c&#243;digo en un complemento de VSTO desde VBA | Microsoft Docs"
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
helpviewer_keywords: 
  - "VBA [desarrollo de Office en Visual Studio], llamar al código en complementos de nivel de aplicación"
  - "complementos de nivel de aplicación [desarrollo de Office en Visual Studio], llamar al código desde otras soluciones"
  - "Temas "Cómo..." de vídeo, desarrollo de Office en Visual Studio"
  - "llamar a código de complementos"
  - "complementos [desarrollo de Office en Visual Studio], llamar al código desde otras soluciones"
  - "interoperabilidad [desarrollo de Office en Visual Studio]"
  - "llamar a código desde VBA"
ms.assetid: 9c04d1df-0d93-473c-85fd-02dc2e956c9e
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Tutorial: Llamar a c&#243;digo en un complemento de VSTO desde VBA
  Este tutorial muestra cómo exponer un objeto de un complemento de VSTO a otras soluciones de Microsoft Office, incluido Visual Basic para aplicaciones \(VBA\) y complementos VSTO de COM.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Aunque este tutorial usa concretamente Excel, los conceptos que se muestran en él se pueden aplicar a cualquier plantilla de proyecto de complementos de VSTO proporcionada por Visual Studio.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Definir una clase que se puede exponer a otras soluciones de Office.  
  
-   Exponer la clase a otras soluciones de Office.  
  
-   Llamar a un método de la clase desde código VBA.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## Crear el proyecto de complemento de VSTO  
 El primer paso es crear un proyecto de complemento de VSTO para Excel.  
  
#### Para crear un nuevo proyecto  
  
1.  Cree un proyecto de complemento de VSTO para Excel con el nombre **ExcelImportData** mediante la plantilla de proyecto de complementos de VSTO para Excel. Para obtener más información, consulta [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] abre el archivo de código **ThisAddIn.cs** o **ThisAddIn.vb** y agrega el proyecto **ExcelImportData** al **Explorador de soluciones**.  
  
## Definir una clase que pueda exponer a otras soluciones de Office  
 El propósito de este tutorial es llamar a al método `ImportData` de una clase denominada `AddInUtilities` en el complemento de VSTO desde código de VBA. Este método escribe una cadena en la celda A1 de la hoja de cálculo activa.  
  
 Para exponer la clase `AddInUtilities` a otras soluciones de Office, debe hacer que la clase sea pública y visible para COM. También debe exponer la interfaz [IDispatch](http://msdn.microsoft.com/es-es/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) de la clase. El código del procedimiento siguiente muestra una manera de cumplir estos requisitos. Para obtener más información, consulta [Llamar a código en complementos de VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
#### Para definir una clase que pueda exponer a otras soluciones de Office  
  
1.  En el menú **Proyecto**, haga clic en **Agregar clase**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento**, cambie el nombre de la nueva clase a **AddInUtilities** y haga clic en **Agregar**.  
  
     El archivo **AddInUtilities.cs** o **AddInUtilities.vb** se abre en el Editor de código.  
  
3.  Agregue las instrucciones siguientes en la parte superior del archivo.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/CS/AddInUtilities.cs#2)]
     [!code-vb[Trin_AddInInteropWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/VB/AddInUtilities.vb#2)]  
  
4.  Reemplace la clase `AddInUtilities` por el siguiente código.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/CS/AddInUtilities.cs#3)]
     [!code-vb[Trin_AddInInteropWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/VB/AddInUtilities.vb#3)]  
  
     Este código hace que la clase `AddInUtilities` sea visible para COM y agrega el método `ImportData` a la clase. Para exponer la interfaz [IDispatch](http://msdn.microsoft.com/es-es/ebbff4bc-36b2-4861-9efa-ffa45e013eb5), la clase `AddInUtilities` también tiene el atributo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> e implementa una interfaz que es visible para COM.  
  
## Exponer la clase a otras soluciones de Office  
 Para exponer la clase `AddInUtilities` a otras soluciones de Office, invalide el método <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> en la clase `ThisAddIn`. Al invalidarlo, devuelva una instancia de la clase `AddInUtilities`.  
  
#### Para exponer la clase AddInUtilities a otras soluciones de Office  
  
1.  En el **Explorador de soluciones**, expanda **Excel**.  
  
2.  Haga clic con el botón secundario en el archivo **ThisAddin.cs** o **ThisAddin.vb** y, a continuación, haga clic en **Ver código**.  
  
3.  Agregue el código siguiente a la clase `ThisAddIn`.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddInInteropWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/VB/ThisAddIn.vb#1)]  
  
4.  En el menú **Compilar**, haga clic en **Compilar solución**.  
  
     Compruebe que la solución se compila sin errores.  
  
## Probar el complemento de VSTO  
 Puede llamar a la clase `AddInUtilities` desde varios tipos distintos de soluciones de Office. En este tutorial, usará el código VBA en un libro de Excel. Para obtener más información sobre los otros tipos de soluciones de Office que también puede usar, vea [Llamar a código en complementos de VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
#### Para probar el complemento de VSTO  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  En Excel, guarde el libro activo como un libro de Excel habilitado para macros \(\*.xlsm\). Guárdelo en una ubicación conveniente, como el escritorio.  
  
3.  En la cinta de opciones, haga clic en la pestaña **Desarrollador**.  
  
    > [!NOTE]  
    >  Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, consulta [Cómo: Mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  En el grupo **Código**, haga clic en **Visual Basic**.  
  
     Se abrirá el Editor de Visual Basic.  
  
5.  En la ventana **Proyecto**, haga doble clic en **ThisWorkbook**.  
  
     Se abrirá el archivo de código para el objeto `ThisWorkbook`.  
  
6.  Agregue el código VBA siguiente al archivo de código. Este código recibe primero un objeto COMAddIn que representa el complemento VSTO **ExcelImportData**. A continuación, el código usa la propiedad Object del objeto COMAddIn para llamar al método `ImportData`.  
  
    ```  
    Sub CallVSTOMethod() Dim addIn As COMAddIn Dim automationObject As Object Set addIn = Application.COMAddIns("ExcelImportData") Set automationObject = addIn.Object automationObject.ImportData End Sub  
    ```  
  
7.  Presione F5.  
  
8.  Compruebe que se ha agregado al libro la hoja nueva **Datos importados**. Compruebe también que la celda A1 contiene la cadena **This is my data**.  
  
9. Salga de Excel.  
  
## Pasos siguientes  
 Puede obtener más información acerca de la programación de complementos de VSTO en estos temas:  
  
-   Utilice la clase `ThisAddIn` para automatizar la aplicación host y realizar otras tareas en proyectos de complementos de VSTO. Para obtener más información, consulta [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Crear un panel de tareas personalizado en un complemento de VSTO. Para obtener más información, vea [Paneles de tareas personalizados](../vsto/custom-task-panes.md) y [Cómo: Agregar un panel de tareas personalizado a una aplicación](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
-   Personalizar la cinta de opciones en un complemento de VSTO. Para obtener más información, vea [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md) y [Cómo: Iniciarse en la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
## Vea también  
 [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md)   
 [Llamar a código en complementos de VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Desarrollar soluciones de Office](../vsto/developing-office-solutions.md)   
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Personalizar características de la interfaz de usuario mediante interfaces de extensibilidad](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  