---
title: "Tutorial: Mostrar sugerencias de bombilla | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Tutorial: Mostrar sugerencias de bombilla
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las bombillas son iconos que se utilizan en el editor de Visual Studio que se expanden para mostrar un conjunto de acciones, por ejemplo correcciones para problemas identificados por los analizadores de código integrados o la refactorización de código.  
  
 En los editores de Visual C\# y Visual Basic, también puede usar .NET Compiler Platform \(«Roslyn»\) para escribir y empaquetar sus propios analizadores de código con las acciones que se muestran las bombillas automáticamente. Para obtener más información, consulte:  
  
-   [Cómo: Escribir un diagnóstico de C\# y la revisión de código](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [Cómo: Escribir un diagnóstico de Visual Basic y la corrección de código](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 Otros lenguajes como C\+\+ también proporcionan las bombillas para algunas acciones rápidas, como una sugerencia para crear una implementación de código auxiliar de esa función.  
  
 Este es el aspecto de una bombilla. En un proyecto de Visual Basic o Visual C\#, un subrayado ondulado de color rojo aparece bajo un nombre de variable cuando no es válido. Cuando desplaza el mouse sobre el identificador no válido, se muestra una bombilla cerca del cursor.  
  
 ![light bulb](~/extensibility/media/lightbulb.png "LightBulb")  
  
 Si hace clic en la flecha hacia abajo por la bombilla, se muestra un conjunto de acciones sugeridas, junto con una vista previa de la acción seleccionada. En este caso, muestra los cambios que se realizaron en el código si se ejecuta la acción.  
  
 ![light bulb preview](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 Puede usar bombillas para proporcionar sus propias acciones sugeridas. Por ejemplo, podría proporcionar acciones para mover abrir las llaves para una nueva línea o al final de la línea anterior. El siguiente tutorial muestra cómo crear una bombilla que aparece en la palabra actual y le sugiere dos acciones: **convertir a mayúsculas** y **convertir a minúsculas**.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Crear un proyecto de Managed Extensibility Framework \(MEF\)  
  
1.  Cree un proyecto de VSIX de C\#. \(En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C\# \/ extensibilidad**, a continuación, **proyecto VSIX**.\) El nombre de la solución `LightBulbTest`.  
  
2.  Agregar un **clasificador Editor** plantilla de elemento para el proyecto. Para obtener más información, consulta [Crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
4.  Agregue la siguiente referencia al proyecto y establezca **copia Local** a `False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  Agregue un nuevo archivo de clase y asígnele el nombre **LightBulbTest**.  
  
6.  Agregue las siguientes instrucciones using:  
  
    ```c#  
    using System;  
    using System.Linq;  
    using System.Collections.Generic;  
    using System.Threading.Tasks;  
    using Microsoft.VisualStudio.Language.Intellisense;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Utilities;  
    using System.ComponentModel.Composition;  
    using System.Threading;  
  
    ```  
  
## Implementar un proveedor de origen de luz  
  
1.  En el archivo de clase LightBulbTest.cs, elimine la clase LightBulbTest. Agregue una clase denominada **TestSuggestedActionsSourceProvider** que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Exportación con el nombre de **acciones recomendadas de prueba** y un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto".  
  
    ```c#  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  En la clase de proveedor de origen, importe la <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> y se agrega como una propiedad.  
  
    ```c#  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> para devolver un <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> objeto. Trataremos el origen en la sección siguiente.  
  
    ```c#  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null && textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## Implementar el ISuggestedActionSource  
 El origen de la acción sugerida es responsable de recopilar el conjunto de acciones sugeridas y agregarlos en el contexto adecuado. En este caso, el contexto es la palabra actual y las acciones sugeridas son **UpperCaseSuggestedAction** y **LowerCaseSuggestedAction**, que se tratan en la sección siguiente.  
  
1.  Agregue una clase **TestSuggestedActionsSource** que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
    ```c#  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  Agregue campos privados de sólo lectura para el proveedor de código fuente de la acción sugerida, el búfer de texto y la vista de texto.  
  
    ```c#  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  Agregue un constructor que establece los campos privados.  
  
    ```c#  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  Agregue un método privado que devuelve la palabra que está bajo el cursor. El siguiente método busca en la ubicación actual del cursor y pide el navegador de estructura de texto de la extensión de la palabra. Si el cursor está en una palabra, el <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> devueltos en el parámetro out; de lo contrario el `out` parámetro es `null` y el método devuelve `false`.  
  
    ```c#  
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)  
    {  
        ITextCaret caret = m_textView.Caret;  
        SnapshotPoint point;  
  
        if (caret.Position.BufferPosition > 0)  
        {  
            point = caret.Position.BufferPosition - 1;  
        }  
        else  
        {  
            wordExtent = default(TextExtent);  
            return false;  
        }  
  
        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);  
  
        wordExtent = navigator.GetExtentOfWord(point);  
        return true;  
    }  
    ```  
  
5.  Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>. El editor llama a este método para averiguar si se debe mostrar la bombilla. Esta llamada se realiza con bastante frecuencia, por ejemplo, cuando el cursor se mueve de una línea a otra, o cuando se desplaza el mouse sobre un subrayado ondulado de error. Es asincrónica para permitir que otras operaciones de interfaz de usuario de ejercer mientras está trabajando en este método. En la mayoría de los casos que este método tiene que realizar algunos análisis y análisis de la línea actual, por lo que el procesamiento puede tardar algún tiempo.  
  
     En nuestra implementación obtiene de forma asincrónica el <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> y determina si la extensión es significativa, es decir, si tiene algún texto que no sea un espacio en blanco.  
  
    ```c#  
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        return Task.Factory.StartNew(() =>  
        {  
            TextExtent extent;  
            if (TryGetWordUnderCaret(out extent))  
            {  
                // don't display the action if the extent has whitespace  
                return extent.IsSignificant;  
              }  
            return false;  
        });  
    }  
    ```  
  
6.  Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> método, que devuelve una matriz de <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> objetos que contienen las distintas <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> objetos. Este método se llama cuando se expande la bombilla.  
  
    > [!WARNING]
    >  Debe asegurarse de que las implementaciones de `HasSuggestedActionsAsync()` y `GetSuggestedActions()` son coherente; es, si `HasSuggestedActionsAsync()` devuelve `true`, a continuación, `GetSuggestedActions()` debería tener algunas acciones para mostrar. En muchos casos `HasSuggestedActionsAsync()` se llama justo antes `GetSuggestedActions()`, pero no siempre es así. Por ejemplo, si el usuario invoca las acciones de bombilla presionando \(CTRL \+.\) sólo `GetSuggestedActions()` se llama.  
  
    ```c#  
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        TextExtent extent;  
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)  
        {  
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);  
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);  
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);  
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };  
        }  
        return Enumerable.Empty<SuggestedActionSet>();  
    }   
    ```  
  
7.  Definir una `SuggestedActionsChanged` eventos.  
  
    ```c#  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  Para completar la implementación, agregue las implementaciones para los `Dispose()` y `TryGetTelemetryId()` métodos. No queremos no telemetría, así que puede devolver false y establezca el GUID vacío.  
  
    ```c#  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample provider and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
## Implementar las acciones de bombilla  
  
1.  En el proyecto, agregue una referencia a Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll y establezca **copia Local** a `False`.  
  
2.  Crear dos clases, la primera llamada `UpperCaseSuggestedAction` y la segunda se denomina `LowerCaseSuggestedAction`. Ambas clases implementan <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.  
  
    ```c#  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Ambas clases son iguales, salvo que uno llama <xref:System.String.ToUpper%2A> y las demás llamadas <xref:System.String.ToLower%2A>. Los siguientes pasos abarcan solo la clase de acción de mayúsculas, pero debe implementar ambas clases. Siga los pasos para implementar la acción de mayúsculas como un modelo para implementar la acción de minúsculas.  
  
3.  Agregue las siguientes instrucciones using para estas clases:  
  
    ```c#  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  Declare un conjunto de campos privados.  
  
    ```c#  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  Agregue un constructor que establezca los campos.  
  
    ```c#  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> método por lo que muestra la vista previa de la acción.  
  
    ```c#  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> método para que devuelva una cadena vacía <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> \(enumeración\).  
  
    ```c#  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  Implemente las propiedades de la siguiente manera:  
  
    ```c#  
    public bool HasActionSets  
    {  
        get { return false; }  
    }  
    public string DisplayText  
    {  
        get { return m_display; }  
    }  
    public ImageMoniker IconMoniker  
    {  
       get { return default(ImageMoniker); }  
    }  
    public string IconAutomationText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public string InputGestureText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public bool HasPreview  
    {  
        get { return true; }  
    }  
    ```  
  
9. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> método reemplazando el texto en el intervalo con su equivalente en mayúsculas.  
  
    ```c#  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  La acción de bombilla **Invoke** no se espera el método para mostrar la interfaz de usuario.  Si su acción de poner en funcionamiento la nueva interfaz de usuario \(por ejemplo una vista previa o selección de cuadro de diálogo\), no mostrar la interfaz de usuario directamente desde el **Invoke** método pero en su lugar programar para mostrar la interfaz de usuario después de volver de **Invoke**.  
  
10. Para completar la implementación, agregue el `Dispose()` y `TryGetTelemetryId()` métodos.  
  
    ```c#  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample action and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
11. No se olvide de hacer lo mismo para `LowerCaseSuggestedAction` cambiar el texto "Convertir '{0}' en minúsculas" y la llamada <xref:System.String.ToUpper%2A> a <xref:System.String.ToLower%2A>.  
  
## Compilar y probar el código  
 Para probar este código, compile la solución LightBulbTest y ejecútelo en la instancia Experimental.  
  
1.  Compile la solución.  
  
2.  Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
3.  Cree un archivo de texto y escriba algún texto. Debería ver una bombilla a la izquierda del texto.  
  
     ![test the light bulb](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  Apuntar a la bombilla. Debería ver una flecha hacia abajo.  
  
5.  Al hacer clic en la bombilla, deberían mostrarse dos acciones sugeridas, junto con la vista previa de la acción seleccionada.  
  
     ![test light bulb, expanded](~/extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  Si hace clic en la primera acción, todo el texto de la palabra actual se debe convertir a mayúsculas. Si hace clic en la segunda acción, todo el texto de la palabra actual se debe convertir a minúsculas.