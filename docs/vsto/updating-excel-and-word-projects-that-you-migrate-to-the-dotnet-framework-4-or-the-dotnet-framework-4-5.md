---
title: Actualizar proyecto de Excel o Word migrado a .NET Framework 4,5
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 06f4742317e3702273c5fe7c91ccc76a153c1b3e
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584417"
---
# <a name="update-excel-and-word-projects-that-you-migrate-to-the-net-framework-45"></a>Actualizar proyectos de Excel y Word que se migran al .NET Framework 4,5
  Si tiene un proyecto de Word o Excel que use cualquiera de las siguientes características, debe modificar el código si se cambia el marco de trabajo de destino a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior:

- [Métodos GetVstoObject y HasVstoObject](#GetVstoObject)

- [Clases generadas en proyectos de nivel de documento](#generatedclasses)

- [Controles de Windows Forms en documentos](#winforms)

- [Eventos de los controles de contenido de Word](#ccevents)

- [Clases OLEObject y OLEControl](#ole)

- [Propiedad Controls.Item(Object)](#itemproperty)

- [Colecciones que derivan de CollectionBase](#collections)

  También debe quitar las `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` referencias y a la `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` clase de proyectos de Excel que se redestinan a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores. Visual Studio no quita este atributo ni la referencia a la clase.

## <a name="remove-the-excellocale1033-attribute-from-excel-projects"></a>Quitar el atributo ExcelLocale1033 de proyectos de Excel
 Se ha `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` quitado de la parte de Visual Studio 2010 Tools para Office Runtime que se usa para las soluciones que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores. El Common Language Runtime (CLR) de [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y versiones posteriores siempre pasa el identificador de configuración regional 1033 al modelo de objetos de Excel y ya no puede usar este atributo para deshabilitar este comportamiento. Para obtener más información, vea [globalización and Localization of Excel Solutions](../vsto/globalization-and-localization-of-excel-solutions.md).

### <a name="to-remove-the-excellocale1033attribute"></a>Para quitar el ExcelLocale1033Attribute

1. Con el proyecto abierto en Visual Studio, abra el **Explorador de soluciones**.

2. En el nodo **Propiedades** (en C#) o **Mi proyecto** (en Visual Basic), haga doble clic en el archivo de código AssemblyInfo para abrirlo en el editor de código.

    > [!NOTE]
    > Para ver el archivo de código AssemblyInfo en los proyectos de Visual Basic, haga clic en el botón **Mostrar todos los archivos** del **Explorador de soluciones** .

3. Busque `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` y quítelo del archivo o márquelo como comentario.

    ```vb
    <Assembly: ExcelLocale1033Proxy(True)>
    ```

    ```csharp
    [assembly: ExcelLocale1033Proxy(true)]
    ```

## <a name="remove-a-reference-to-the-excellocal1033proxy-class"></a>Quitar una referencia a la clase ExcelLocal1033Proxy
 Los proyectos que se crearon con Microsoft Visual Studio 2005 Tools para Microsoft Office System crean una instancia del objeto <xref:Microsoft.Office.Interop.Excel.Application> de Excel mediante el uso de la clase `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy`. Esta clase se ha quitado de la parte de Visual Studio 2010 Tools para Office Runtime que se usa para las soluciones que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores. Por lo tanto, debe quitar la línea de código que hace referencia a esta clase o marcarla como comentario.

### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>Para quitar la referencia a la clase ExcelLocal1033Proxy

1. Abra el proyecto en Visual Studio y, a continuación, abra el **Explorador de soluciones**.

2. En **Explorador de soluciones**, abra el menú contextual de *ThisAddIn.CS* (para C#) o *ThisAddin. VB* (para Visual Basic) y, a continuación, elija **Ver código**.

3. En el Editor de código, en la región `VSTO generated code` , quite o marque como comentario la siguiente línea de código.

    ```vb
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)

    ```

    ```csharp
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);

    ```

## <a name="update-code-that-uses-the-getvstoobject-and-hasvstoobject-methods"></a><a name="GetVstoObject"></a> Actualizar código que usa los métodos HasVstoObject y GetVstoObject
 En los proyectos que tienen como destino .NET Framework 3.5, los métodos `GetVstoObject` o `HasVstoObject` están disponibles como métodos de extensión en uno de los siguientes objetos nativos del proyecto: <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet> o <xref:Microsoft.Office.Interop.Excel.ListObject>. Al llamar a estos métodos, no es necesario pasar un parámetro. En el ejemplo de código siguiente se muestra cómo usar el método GetVstoObject en un complemento de VSTO de Word que tiene como destino el .NET Framework 3,5.

```vb
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()
```

```csharp
Microsoft.Office.Tools.Word.Document vstoDocument =
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();
```

 En los proyectos que tengan como destino la versión [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior, debe modificar el código para acceder a estos métodos de una de las siguientes maneras:

- Seguirá pudiendo acceder a estos métodos como métodos de extensión en objetos <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>o <xref:Microsoft.Office.Interop.Excel.ListObject> . Sin embargo, ahora debe pasar el objeto devuelto por la propiedad `Globals.Factory` a estos métodos.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);
  ```

- También puede acceder a estos métodos en el objeto devuelto por la propiedad `Globals.Factory`. Si accede a estos métodos de esta manera, debe pasar el objeto nativo que desee extender al método.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);
  ```

  Para obtener más información, vea [ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="update-code-that-uses-instances-of-the-generated-classes-in-document-level-projects"></a><a name="generatedclasses"></a> Actualizar el código que usa las instancias de las clases generadas en los proyectos de nivel de documento
 En los proyectos de nivel de documento que tengan como destino .NET Framework 3.5, las clases generadas en los proyectos se derivan de las siguientes clases en el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>

- `Sheet`*n*:<xref:Microsoft.Office.Tools.Excel.Worksheet>

- `Chart`*n*:<xref:Microsoft.Office.Tools.Excel.ChartSheet>

  En los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, los tipos en [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] enumerados anteriormente son interfaces en lugar de clases. Las clases generadas en proyectos que tengan como destino la versión [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior derivan de las siguientes clases nuevas en [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>

- `Sheet`*n*:<xref:Microsoft.Office.Tools.Excel.WorksheetBase>

- `Chart`*n*:<xref:Microsoft.Office.Tools.Excel.ChartSheetBase>

  Si el código del proyecto hace referencia a una instancia de una de las clases generadas como la clase base de la que se deriva, debe modificar el código.

  Por ejemplo, en un proyecto de libro de Excel que tenga como destino .NET Framework 3.5, podría tener un método del asistente que realizase algún trabajo en las instancias de las clases `Sheet`*n* generadas en su proyecto.

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

- Modificar cualquier código que llame al método `DoSomethingToSheet` para pasar la propiedad <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> de un objeto <xref:Microsoft.Office.Tools.Excel.WorksheetBase> de su proyecto. Esta propiedad devuelve un objeto <xref:Microsoft.Office.Tools.Excel.Worksheet> .

    ```vb
    DoSomethingToSheet(Globals.Sheet1.Base)
    ```

    ```csharp
    DoSomethingToSheet(Globals.Sheet1.Base);
    ```

- Modificar el parámetro de método `DoSomethingToSheet` para que, en su lugar, espere un objeto <xref:Microsoft.Office.Tools.Excel.WorksheetBase> .

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

## <a name="update-code-that-uses-windows-forms-controls-on-documents"></a><a name="winforms"></a> Actualizar código que usa controles de Windows Forms en documentos
 Debe agregar una instrucción **using** (C#) o **Imports** (Visual Basic) para <xref:Microsoft.Office.Tools.Excel> el <xref:Microsoft.Office.Tools.Word> espacio de nombres o en la parte superior de cualquier archivo de código que utilice la propiedad Controls para agregar Windows Forms controles al documento o la hoja de cálculo mediante programación.

 En proyectos que tengan como destino .NET Framework 3.5, los métodos que agregan controles de Windows Forms (como el método `AddButton`) se definen en las clases <xref:Microsoft.Office.Tools.Excel.ControlCollection> y <xref:Microsoft.Office.Tools.Word.ControlCollection>.

 En los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, estos métodos son métodos de extensión que están disponibles en la propiedad Controls. Para usar estos métodos de extensión, el archivo de código en el que usa los métodos debe tener una instrucción **using** o **Imports** para el espacio de nombres <xref:Microsoft.Office.Tools.Excel> o <xref:Microsoft.Office.Tools.Word> . Esta instrucción se genera automáticamente en los nuevos proyectos que tengan como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior. Sin embargo, esta instrucción no se agrega automáticamente en los proyectos que tienen como destino la versión .NET Framework 3.5, por lo que debe agregarla al cambiar el destino del proyecto.

 Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="update-code-that-handles-word-content-control-events"></a><a name="ccevents"></a> Actualizar el código que controla los eventos de control de contenido de Word
 En los proyectos que tengan como destino .NET Framework 3.5, el delegado <xref:System.EventHandler%601> genérico controla los eventos de los controles de contenido de Word. En los proyectos que tengan como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, otros delegados controlan estos eventos.

 En la siguiente tabla se enumeran los eventos de control de contenido de Word y los delegados asociados a ellos en proyectos que tengan como destino la versión [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior.

|Evento|Delegado a usar en proyectos de la versión [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y posterior|
|-----------| - |
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|

## <a name="update-code-that-uses-the-oleobject-and-olecontrol-classes"></a><a name="ole"></a> Actualizar el código que usa las clases OLEObject y OLEControl
 En los proyectos que tengan como destino .NET Framework 3.5, puede agregar controles personalizados (como controles de usuario de Windows Forms) a un documento o una hoja de cálculo mediante el uso de las clases `Microsoft.Office.Tools.Excel.OLEObject` y `Microsoft.Office.Tools.Word.OLEControl`.

 En los proyectos que tengan como destino la versión [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior, estas clases se han reemplazado por las interfaces <xref:Microsoft.Office.Tools.Excel.ControlSite> y <xref:Microsoft.Office.Tools.Word.ControlSite> . Debe modificar el código que hace referencia a `Microsoft.Office.Tools.Excel.OLEObject` y `Microsoft.Office.Tools.Word.OLEControl` para que en su lugar haga referencia a <xref:Microsoft.Office.Tools.Excel.ControlSite> y <xref:Microsoft.Office.Tools.Word.ControlSite>. Salvo los nuevos nombres, estos controles se comportan de la misma manera que lo hacen en los proyectos que tienen como destino .NET Framework 3.5.

 Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="update-code-that-uses-the-controlsitemobject-property"></a><a name="itemproperty"></a> Actualizar el código que usa la propiedad Controls. Item (Object)
 En los proyectos que tienen como destino la .NET Framework 3,5, puede usar la propiedad Item (Object) del Microsoft.Office.Tools.Word.Document. Controles o `Microsoft.Office.Tools.Excel.Worksheet.Controls` colección para determinar si un documento o una hoja de cálculo tiene un control especificado.

 En los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, se ha quitado la propiedad Item (Object) de estas colecciones. Para determinar si un documento o una hoja de cálculo contiene un control especificado, utilice en su lugar el método Contains (System. Object) de la <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> colección o.

 Para obtener más información sobre la colección de controles de documentos y hojas de cálculo, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="update-code-that-uses-collections-that-derive-from-collectionbase"></a><a name="collections"></a> Actualizar el código que usa colecciones que derivan de CollectionBase
 En los proyectos que tienen como destino la .NET Framework 3,5, varios tipos de colección de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] derivan de la <xref:System.Collections.CollectionBase> clase, como `Microsoft.Office.Tools.SmartTagCollection` , `Microsoft.Office.Tools.Excel.ControlCollection` y `Microsoft.Office.Tools.Word.ControlCollection` .

 Ahora, en los proyectos que tienen como destino la versión [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, estos tipos de colección son interfaces que no se derivan de <xref:System.Collections.CollectionBase>. Algunos miembros ya no están disponibles en estos tipos de colección, como <xref:System.Collections.CollectionBase.Capacity%2A>, <xref:System.Collections.CollectionBase.List%2A>y <xref:System.Collections.CollectionBase.InnerList%2A>.

## <a name="see-also"></a>Vea también
- [Migrar soluciones de Office al .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Controles de contenido](../vsto/content-controls.md)
- [Ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
