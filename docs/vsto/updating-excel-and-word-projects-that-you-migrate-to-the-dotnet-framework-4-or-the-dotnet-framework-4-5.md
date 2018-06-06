---
title: Actualizar los proyectos de Excel y Word para migrarlos a .NET Framework 4 o .NET Framework 4.5
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 38734366f5b7d19ef0780c8ef998efb19e50a46f
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767535"
---
# <a name="update-excel-and-word-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Actualizar los proyectos de Excel y Word para migrarlos a .NET Framework 4 o .NET Framework 4.5
  Si tiene un proyecto de Word o Excel que use cualquiera de las siguientes características, debe modificar el código si se cambia el marco de trabajo de destino a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior:  
  
-   [Métodos GetVstoObject y HasVstoObject](#GetVstoObject)  
  
-   [Clases generadas en proyectos de nivel de documento](#generatedclasses)  
  
-   [Controles de Windows Forms en documentos](#winforms)  
  
-   [Eventos de los controles de contenido de Word](#ccevents)  
  
-   [Clases OLEObject y OLEControl](#ole)  
  
-   [Propiedad Controls.Item(Object)](#itemproperty)  
  
-   [Colecciones que derivan de CollectionBase](#collections)  
  
 También debe quitar la `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` y las referencias a la `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` clase a partir de los proyectos de Excel que se redestinan a la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior. Visual Studio no quita este atributo o la referencia de clase por usted.  
  
## <a name="remove-the-excellocale1033-attribute-from-excel-projects"></a>Quite el atributo ExcelLocale1033 de proyectos de Excel  
 El `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` se ha quitado de la parte de Visual Studio 2010 Tools para Office runtime que se usa para soluciones que tienen como destino la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior. El Common Language Runtime (CLR) de [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y versiones posteriores siempre pasa el identificador de configuración regional 1033 al modelo de objetos de Excel y ya no puede usar este atributo para deshabilitar este comportamiento. Para obtener más información, consulte [globalización y localización de soluciones de Excel](../vsto/globalization-and-localization-of-excel-solutions.md).  
  
### <a name="to-remove-the-excellocale1033attribute"></a>Para quitar el ExcelLocale1033Attribute  
  
1.  Con el proyecto abierto en Visual Studio, abra el **Explorador de soluciones**.  
  
2.  En el nodo **Propiedades** (en C#) o **Mi proyecto** (en Visual Basic), haga doble clic en el archivo de código AssemblyInfo para abrirlo en el editor de código.  
  
    > [!NOTE]  
    >  Para ver el archivo de código AssemblyInfo en los proyectos de Visual Basic, haga clic en el botón **Mostrar todos los archivos** del **Explorador de soluciones** .  
  
3.  Busque `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` y quítelo del archivo o márquelo como comentario.  
  
    ```vb  
    <Assembly: ExcelLocale1033Proxy(True)>  
    ```  
  
    ```csharp  
    [assembly: ExcelLocale1033Proxy(true)]  
    ```  
  
## <a name="remove-a-reference-to-the-excellocal1033proxy-class"></a>Quitar una referencia a la clase ExcelLocal1033Proxy  
 Los proyectos que se crearon con Microsoft Visual Studio 2005 Tools para Microsoft Office System crean una instancia del objeto <xref:Microsoft.Office.Interop.Excel.Application> de Excel mediante el uso de la clase `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy`. Esta clase se ha quitado de la parte de Visual Studio 2010 Tools para Office runtime que se usa para soluciones que tienen como destino la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior. Por lo tanto, debe quitar la línea de código que hace referencia a esta clase o marcarla como comentario.  
  
### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>Para quitar la referencia a la clase ExcelLocal1033Proxy  
  
1.  Abra el proyecto en Visual Studio y, a continuación, abra el **Explorador de soluciones**.  
  
2.  En **el Explorador de soluciones**, abra el menú contextual para *ThisAddin.cs* (en C#) o *ThisAddin.vb* (en Visual Basic) y, a continuación, elija **ver código**.  
  
3.  En el Editor de código, en la región `VSTO generated code` , quite o marque como comentario la siguiente línea de código.  
  
    ```vb  
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)  
  
    ```  
  
    ```csharp  
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);  
  
    ```  
  
##  <a name="GetVstoObject"></a> Actualizar código que utiliza los métodos HasVstoObject y GetVstoObject  
 En los proyectos que tienen como destino .NET Framework 3.5, los métodos `GetVstoObject` o `HasVstoObject` están disponibles como métodos de extensión en uno de los siguientes objetos nativos del proyecto: <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet> o <xref:Microsoft.Office.Interop.Excel.ListObject>. Al llamar a estos métodos, no es necesario pasar un parámetro. En el ejemplo de código siguiente se muestra cómo utilizar el método GetVstoObject en un complemento de VSTO de Word que tenga como destino .NET Framework 3.5.  
  
```vb  
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()  
```  
  
```csharp  
Microsoft.Office.Tools.Word.Document vstoDocument =   
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();  
```  
  
 En los proyectos que tengan como destino la versión [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior, debe modificar el código para acceder a estos métodos de una de las siguientes maneras:  
  
-   Seguirá pudiendo acceder a estos métodos como métodos de extensión en objetos <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>o <xref:Microsoft.Office.Interop.Excel.ListObject> . Sin embargo, ahora debe pasar el objeto devuelto por la propiedad `Globals.Factory` a estos métodos.  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
        Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument =   
        Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);  
    ```  
  
-   También puede acceder a estos métodos en el objeto devuelto por la propiedad `Globals.Factory`. Si accede a estos métodos de esta manera, debe pasar el objeto nativo que desee extender al método.  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
        Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument =   
        Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);  
    ```  
  
 Para obtener más información, consulte [documentos de Word extender y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
##  <a name="generatedclasses"></a> Actualizar código que use instancias de las clases generadas en proyectos de nivel de documento  
 En los proyectos de nivel de documento que tengan como destino .NET Framework 3.5, las clases generadas en los proyectos se derivan de las siguientes clases en el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
 En los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, los tipos en [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] enumerados anteriormente son interfaces en lugar de clases. Las clases generadas en proyectos que tengan como destino la versión [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior derivan de las siguientes clases nuevas en [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheetBase>  
  
 Si el código del proyecto hace referencia a una instancia de una de las clases generadas como la clase base de la que se deriva, debe modificar el código.  
  
 Por ejemplo, en un proyecto de libro de Excel que tenga como destino .NET Framework 3.5, podría tener un método auxiliar que realizase algún trabajo en las instancias de las clases `Sheet`*n* generadas en su proyecto.  
  
```vb  
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet)  
    ' Do something to the worksheet object.  
End Sub  
```  
  
```csharp  
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet)  
{  
    // Do something to the worksheet object.  
}  
```  
  
 Si vuelve a establecer el destino del proyecto en [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, debe realizar uno de los siguientes cambios en el código:  
  
-   Modificar cualquier código que llame al método `DoSomethingToSheet` para pasar la propiedad <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> de un objeto <xref:Microsoft.Office.Tools.Excel.WorksheetBase> de su proyecto. Esta propiedad devuelve un objeto <xref:Microsoft.Office.Tools.Excel.Worksheet> .  
  
    ```vb  
    DoSomethingToSheet(Globals.Sheet1.Base)  
    ```  
  
    ```csharp  
    DoSomethingToSheet(Globals.Sheet1.Base);  
    ```  
  
-   Modificar el parámetro de método `DoSomethingToSheet` para que, en su lugar, espere un objeto <xref:Microsoft.Office.Tools.Excel.WorksheetBase> .  
  
    ```vb  
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase)  
        ' Do something to the worksheet object.  
    End Sub  
    ```  
  
    ```csharp  
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet)  
    {  
        // Do something to the worksheet object.  
    }  
    ```  
  
##  <a name="winforms"></a> Actualizar código que usa controles de formularios Windows Forms en documentos  
 Debe agregar una **con** (C#) o **importaciones** instrucción (Visual Basic) para la <xref:Microsoft.Office.Tools.Excel> o <xref:Microsoft.Office.Tools.Word> espacio de nombres a la parte superior de cualquier archivo de código que usa la propiedad de controles para agregar Windows Forms controles al documento u hoja de cálculo mediante programación.  
  
 En proyectos que tengan como destino .NET Framework 3.5, los métodos que agregan controles de Windows Forms (como el método `AddButton`) se definen en las clases <xref:Microsoft.Office.Tools.Excel.ControlCollection> y <xref:Microsoft.Office.Tools.Word.ControlCollection>.  
  
 En los proyectos que tienen como destino la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, estos métodos son métodos de extensión que están disponibles en la propiedad de los controles. Para usar estos métodos de extensión, el archivo de código en el que usa los métodos debe tener una instrucción **using** o **Imports** para el espacio de nombres <xref:Microsoft.Office.Tools.Excel> o <xref:Microsoft.Office.Tools.Word> . Esta instrucción se genera automáticamente en los nuevos proyectos que tengan como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior. Sin embargo, esta instrucción no se agrega automáticamente en los proyectos que tienen como destino la versión .NET Framework 3.5, por lo que debe agregarla al cambiar el destino del proyecto.  
  
 Para obtener más información, consulte [agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="ccevents"></a> Actualizar código que controla los eventos de control de contenido de Word  
 En los proyectos que tengan como destino .NET Framework 3.5, el delegado <xref:System.EventHandler%601> genérico controla los eventos de los controles de contenido de Word. En los proyectos que tengan como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, otros delegados controlan estos eventos.  
  
 En la siguiente tabla se enumeran los eventos de control de contenido de Word y los delegados asociados a ellos en proyectos que tengan como destino la versión [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior.  
  
|evento|Delegado a usar en proyectos de la versión [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y posterior|  
|-----------|---------------------------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|  
  
##  <a name="ole"></a> Actualizar código que utiliza las clases OLEObject y OLEControl  
 En los proyectos que tengan como destino .NET Framework 3.5, puede agregar controles personalizados (como controles de usuario de Windows Forms) a un documento o una hoja de cálculo mediante el uso de las clases `Microsoft.Office.Tools.Excel.OLEObject` y `Microsoft.Office.Tools.Word.OLEControl`.  
  
 En los proyectos que tengan como destino la versión [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior, estas clases se han reemplazado por las interfaces <xref:Microsoft.Office.Tools.Excel.ControlSite> y <xref:Microsoft.Office.Tools.Word.ControlSite>. Debe modificar el código que hace referencia a `Microsoft.Office.Tools.Excel.OLEObject` y `Microsoft.Office.Tools.Word.OLEControl` para que en su lugar haga referencia a <xref:Microsoft.Office.Tools.Excel.ControlSite> y <xref:Microsoft.Office.Tools.Word.ControlSite>. Salvo los nuevos nombres, estos controles se comportan de la misma manera que lo hacen en los proyectos que tienen como destino .NET Framework 3.5.  
  
 Para obtener más información, consulte [agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="itemproperty"></a> Actualizar código que usa la propiedad Controls.Item (Object)  
 En los proyectos que tienen como destino .NET Framework 3.5, puede usar la propiedad Item (Object) de la Microsoft.Office.Tools.Word.Document.Controls o `Microsoft.Office.Tools.Excel.Worksheet.Controls` colección para determinar si un documento u hoja de cálculo tiene un control especificado.  
  
 En los proyectos que tienen como destino la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, la propiedad Item (Object) se ha quitado de estas colecciones. Para determinar si un documento u hoja de cálculo contiene un control especificado, use el método Contains(System.Object) de la <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> o <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> colección en su lugar.  
  
 Para obtener más información acerca de la colección de controles de documentos y hojas de cálculo, consulte [agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="collections"></a> Actualizar código que usa colecciones que derivan de CollectionBase  
 En los proyectos que tienen como destino .NET Framework 3.5, varios tipos de colección en el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] derivan de la <xref:System.Collections.CollectionBase> de la clase, como `Microsoft.Office.Tools.SmartTagCollection`, `Microsoft.Office.Tools.Excel.ControlCollection`, y `Microsoft.Office.Tools.Word.ControlCollection`.  
  
 Ahora, en los proyectos que tienen como destino la versión [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, estos tipos de colección son interfaces que no se derivan de <xref:System.Collections.CollectionBase>. Algunos miembros ya no están disponibles en estos tipos de colección, como <xref:System.Collections.CollectionBase.Capacity%2A>, <xref:System.Collections.CollectionBase.List%2A>y <xref:System.Collections.CollectionBase.InnerList%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Migrar soluciones de Office para .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Controles de contenido](../vsto/content-controls.md)   
 [Ampliar documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  