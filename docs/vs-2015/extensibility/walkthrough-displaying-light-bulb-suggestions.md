---
title: 'Tutorial: Mostrar sugerencias de bombilla | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 32d567ab4c71bdf4716a4c61464e1ee4ba6ecfa4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099785"
---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>Tutorial: Mostrar sugerencias de bombilla
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las bombillas son iconos que se usan en el editor de Visual Studio que se expanden para mostrar un conjunto de acciones, por ejemplo correcciones para problemas identificados por los analizadores de código integrados o refactorización de código.  
  
 En los editores de Visual C# y Visual Basic, también se puede usar .NET Compiler Platform («Roslyn») para escribir y empaquetar sus propios analizadores de código con las acciones que se muestran automáticamente las bombillas. Para obtener más información, consulte:  
  
- [Cómo: Escribir una corrección de código y el diagnóstico de C#](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
- [Cómo: Escribir una corrección de código y el diagnóstico de Visual Basic](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
  Otros lenguajes como C++ también proporcionan bombillas para algunas acciones rápidas, como una sugerencia para crear una implementación de código auxiliar de esa función.  
  
  Este es el aspecto de una bombilla. En un proyecto de Visual Basic o Visual C#, un subrayado ondulado rojo aparece bajo un nombre de variable cuando no es válido. Cuando mueva el mouse sobre el identificador no válido, se muestra una bombilla junto al cursor.  
  
  ![bombilla](../extensibility/media/lightbulb.png "bombilla")  
  
  Si hace clic en la flecha hacia abajo por la bombilla, se muestra un conjunto de acciones sugeridas, junto con una vista previa de la acción seleccionada. En este caso, muestra los cambios que se realizarán en el código al ejecutar la acción.  
  
  ![vista previa de bombilla](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
  Puede usar bombillas para proporcionar sus propias acciones sugeridas. Por ejemplo, podría proporcionar acciones para mover la apertura de las llaves para una nueva línea o moverlos al final de la línea anterior. El siguiente tutorial muestra cómo crear una bombilla que aparece en la palabra actual y le sugiere dos acciones: **Convertir a mayúsculas** y **convertir a minúsculas**.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Crear un proyecto de Managed Extensibility Framework (MEF)  
  
1. Cree un proyecto de VSIX de C#. (En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C# / extensibilidad**, a continuación, **proyecto VSIX**.) Asigne a la solución el nombre `LightBulbTest`.  
  
2. Agregar un **clasificador de Editor** plantilla de elemento al proyecto. Para obtener más información, consulte [crear una extensión con una plantilla de elementos de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Elimine los archivos de clase existentes.  
  
4. Agregue la siguiente referencia al proyecto y establezca **Copy Local** a `False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5. Agregue un nuevo archivo de clase y asígnele el nombre **LightBulbTest**.  
  
6. Agregue las siguientes instrucciones using:  
  
    ```csharp  
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
  
## <a name="implementing-the-light-bulb-source-provider"></a>Implementar el proveedor de código fuente de luz  
  
1. En el archivo de clase LightBulbTest.cs, elimine la clase LightBulbTest. Agregue una clase denominada **TestSuggestedActionsSourceProvider** que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Expórtelo con el nombre de **acciones sugeridas de prueba** y un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "text".  
  
    ```csharp  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2. En la clase de proveedor de origen, importe el <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> y agréguela como una propiedad.  
  
    ```csharp  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> método devuelva un <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> objeto. Trataremos el origen en la sección siguiente.  
  
    ```csharp  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null && textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implementing-the-isuggestedactionsource"></a>Implementar el ISuggestedActionSource  
 El origen de la acción sugerida es responsable de recopilar el conjunto de acciones sugeridas y agregarlos en el contexto adecuado. En este caso, el contexto es la palabra actual y las acciones sugeridas son **UpperCaseSuggestedAction** y **LowerCaseSuggestedAction**, que se describirá en la sección siguiente.  
  
1. Agregue una clase **TestSuggestedActionsSource** que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2. Agregue los campos privados de solo lectura para el proveedor de código fuente de la acción sugerida, el búfer de texto y la vista de texto.  
  
    ```csharp  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3. Agregue un constructor que establezca los campos privados.  
  
    ```csharp  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4. Agregue un método privado que devuelve la palabra que se encuentra actualmente bajo el cursor. El siguiente método busca en la ubicación actual del cursor y solicita el navegador de estructura de texto para la extensión de la palabra. Si el cursor está en una palabra, el <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> en el parámetro de salida; de lo contrario el `out` parámetro es `null` y el método devuelve `false`.  
  
    ```csharp  
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
  
5. Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>. El editor de llama a este método para averiguar si se debe mostrar la bombilla. Esta llamada se realiza con bastante frecuencia, por ejemplo, cada vez que el cursor se mueve de una línea a otra, o cuando se mantiene el mouse sobre un subrayado ondulado de error. Es asincrónica para permitir que otras operaciones de la interfaz de usuario a cabo mientras está trabajando en este método. En la mayoría de los casos que este método necesita realizar algún análisis y el análisis de la línea actual, por lo que el procesamiento puede tardar algún tiempo.  
  
     En nuestra implementación obtiene de forma asincrónica el <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> y determina si la extensión es significativa, es decir, si tiene algún texto que no sea espacio en blanco.  
  
    ```csharp  
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
  
6. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> método, que devuelve una matriz de <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> objetos que contienen las distintas <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> objetos. Este método se llama cuando se expande la bombilla.  
  
    > [!WARNING]
    >  Debe asegurarse de que las implementaciones de `HasSuggestedActionsAsync()` y `GetSuggestedActions()` son coherente; es, si `HasSuggestedActionsAsync()` devuelve `true`, a continuación, `GetSuggestedActions()` debe tener algunas acciones para mostrar. En muchos casos `HasSuggestedActionsAsync()` se llama justo antes `GetSuggestedActions()`, pero no siempre es el caso. Por ejemplo, si el usuario invoca la bombilla de acciones presionando (CTRL +.) solo `GetSuggestedActions()` se llama.  
  
    ```csharp  
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
  
7. Definir un `SuggestedActionsChanged` eventos.  
  
    ```csharp  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8. Para completar la implementación, agregue las implementaciones para el `Dispose()` y `TryGetTelemetryId()` métodos. No queremos hacer telemetría, así que solo devuelva false y establece el GUID en vacío.  
  
    ```csharp  
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
  
## <a name="implementing-light-bulb-actions"></a>Implementación de bombilla de acciones  
  
1. En el proyecto, agregue una referencia a Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll y conjunto **Copy Local** a `False`.  
  
2. Cree dos clases, la primera llamada `UpperCaseSuggestedAction` y la segunda llamada `LowerCaseSuggestedAction`. Ambas clases implementan <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Ambas clases son iguales, salvo que una llama a <xref:System.String.ToUpper%2A> y la otra llama a <xref:System.String.ToLower%2A>. Los siguientes pasos abarcan solo la clase de acción de mayúsculas, pero debe implementar ambas clases. Siga los pasos para implementar la acción de mayúsculas como un modelo para implementar la acción de minúsculas.  
  
3. Agregue las siguientes instrucciones using para estas clases:  
  
    ```csharp  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4. Declare un conjunto de campos privados.  
  
    ```csharp  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5. Agregue un constructor que establezca los campos.  
  
    ```csharp  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> método por lo que muestra la vista previa de la acción.  
  
    ```csharp  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> método para que devuelva un valor vacío <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> enumeración.  
  
    ```csharp  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8. Implemente las propiedades de la siguiente manera:  
  
    ```csharp  
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
  
9. Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> reemplazando el texto en el intervalo por su equivalente en mayúsculas.  
  
    ```csharp  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  La acción de bombilla **Invoke** no se espera el método para mostrar la interfaz de usuario.  Si la acción aparezca la nueva interfaz de usuario (por ejemplo una vista previa o selección de cuadro de diálogo), no mostrar la interfaz de usuario directamente desde el **Invoke** método pero en su lugar, programar para mostrar la interfaz de usuario después de volver de **Invoke**.  
  
10. Para completar la implementación, agregue el `Dispose()` y `TryGetTelemetryId()` métodos.  
  
    ```csharp  
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
  
11. No se olvide de hacer lo mismo `LowerCaseSuggestedAction` cambiar el texto a "convertir '{0}' a minúsculas" y la llamada <xref:System.String.ToUpper%2A> a <xref:System.String.ToLower%2A>.  
  
## <a name="building-and-testing-the-code"></a>Compilar y probar el código  
 Para probar este código, compile la solución LightBulbTest y ejecútelo en la instancia Experimental.  
  
1. Compile la solución.  
  
2. Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
3. Cree un archivo de texto y escriba algún texto. Debería ver una bombilla a la izquierda del texto.  
  
     ![probar la bombilla](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4. Punto en la bombilla. Debería ver una flecha hacia abajo.  
  
5. Al hacer clic en la bombilla, deben mostrarse dos acciones sugeridas, junto con la versión preliminar de la acción seleccionada.  
  
     ![probar la bombilla, expandida](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6. Si hace clic en la primera acción, todo el texto de la palabra actual se debe convertir a mayúsculas. Si hace clic en la segunda acción, todo el texto de la palabra actual se debe convertir a minúsculas.
