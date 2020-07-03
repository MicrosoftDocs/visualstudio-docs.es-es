---
title: 'Tutorial: Mostrar sugerencias de bombillas | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 153eda065b9a6e845a39c35aaae34bbe1745f7a8
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904992"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Tutorial: Mostrar sugerencias de bombillas
Las bombillas son iconos en el editor de Visual Studio que se expanden para mostrar un conjunto de acciones, por ejemplo, correcciones de problemas identificados por los analizadores de código integrados o la refactorización de código.

 En los editores de Visual C# y Visual Basic, también puede usar el .NET Compiler Platform ("Roslyn") para escribir y empaquetar sus propios analizadores de código con acciones que muestren las bombillas automáticamente. Para obtener más información, consulte:

- [Cómo: escribir una corrección de código y diagnóstico de C#](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [Cómo: escribir un diagnóstico de Visual Basic y corrección de código](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  Otros lenguajes como C++ también proporcionan bombillas para algunas acciones rápidas, como, una sugerencia para crear una implementación de código auxiliar de esa función.

  Este es el aspecto de una bombilla. En un proyecto de Visual Basic o Visual C#, aparece un subrayado ondulado de color rojo bajo un nombre de variable cuando no es válido. Si se sitúa el mouse sobre el identificador no válido, aparece una bombilla cerca del cursor.

  ![bombilla](../extensibility/media/lightbulb.png "Bombilla")

  Si hace clic en la flecha abajo por la bombilla, aparece un conjunto de acciones sugeridas junto con una vista previa de la acción seleccionada. En este caso, muestra los cambios que se realizan en el código si se ejecuta la acción.

  ![vista previa de bombilla](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  Puede usar bombillas para proporcionar sus propias acciones sugeridas. Por ejemplo, puede proporcionar acciones para mover las llaves de apertura a una nueva línea o moverlas al final de la línea anterior. En el siguiente tutorial se muestra cómo crear una bombilla que aparece en la palabra actual y tiene dos acciones sugeridas: **convertir a** mayúsculas y **convertir a**minúsculas.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Crear un proyecto Managed Extensibility Framework (MEF)

1. Cree un proyecto VSIX en C#. (En el cuadro de diálogo **nuevo proyecto** , seleccione **Visual C#/extensibilidad**y, a continuación, **Proyecto VSIX**). Asigne a la solución el nombre `LightBulbTest` .

2. Agregue una plantilla de elemento **clasificador de editor** al proyecto. Para obtener más información, vea [crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Elimine los archivos de clase existentes.

4. Agregue la siguiente referencia al proyecto y establezca **copia local** en `False` :

     *Microsoft.VisualStudio.Language.Intellisense*

5. Agregue un nuevo archivo de clase y asígnele el nombre **LightBulbTest**.

6. Agregue lo siguiente mediante directivas:

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

## <a name="implement-the-light-bulb-source-provider"></a>Implementación del proveedor de origen de bombillas

1. En el archivo de clase *LightBulbTest.CS* , elimine la clase LightBulbTest. Agregue una clase denominada **TestSuggestedActionsSourceProvider** que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> . Expórtelo con un nombre de **prueba sugerida de acciones** y un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto".

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. Dentro de la clase de proveedor de origen, importe <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> y agréguelo como una propiedad.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> método para devolver un <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> objeto. El origen se describe en la sección siguiente.

    ```csharp
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)
    {
        if (textBuffer == null || textView == null)
        {
            return null;
        }
        return new TestSuggestedActionsSource(this, textView, textBuffer);
    }
    ```

## <a name="implement-the-isuggestedactionsource"></a>Implementación de ISuggestedActionSource
 El origen de la acción sugerida es responsable de recopilar el conjunto de acciones sugeridas y agregarlas en el contexto correcto. En este caso, el contexto es la palabra actual y las acciones sugeridas son **UpperCaseSuggestedAction** y **LowerCaseSuggestedAction**, que se describe en la sección siguiente.

1. Agregue una clase **TestSuggestedActionsSource** que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. Agregue campos privados de solo lectura para el proveedor de origen de acción sugerido, el búfer de texto y la vista de texto.

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

4. Agregue un método privado que devuelva la palabra que está actualmente bajo el cursor. El método siguiente examina la ubicación actual del cursor y pide al explorador de la estructura de texto la extensión de la palabra. Si el cursor está en una palabra, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> se devuelve en el parámetro out; de lo contrario, el `out` parámetro es `null` y el método devuelve `false` .

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

5. Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>. El editor llama a este método para averiguar si se va a mostrar la bombilla. Esta llamada se realiza a menudo, por ejemplo, cada vez que el cursor se mueve de una línea a otra, o cuando el mouse se desplaza sobre un error ondulado. Es asincrónica con el fin de permitir que otras operaciones de la interfaz de usuario se lleven a cabo mientras este método funciona. En la mayoría de los casos, este método debe realizar algún análisis y análisis de la línea actual, por lo que el procesamiento puede tardar algún tiempo.

     En esta implementación, obtiene de forma asincrónica el <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> y determina si la extensión es significativa, como en, si tiene algún texto distinto del espacio en blanco.

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

6. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> método, que devuelve una matriz de <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> objetos que contienen los diferentes <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> objetos. Se llama a este método cuando se expande la bombilla.

    > [!WARNING]
    > Debe asegurarse de que las implementaciones de `HasSuggestedActionsAsync()` y `GetSuggestedActions()` son coherentes; es decir, si `HasSuggestedActionsAsync()` devuelve `true` , `GetSuggestedActions()` debe haber algunas acciones que mostrar. En muchos casos, `HasSuggestedActionsAsync()` se llama justo antes `GetSuggestedActions()` , pero no siempre es así. Por ejemplo, si el usuario invoca las acciones de bombilla presionando (**Ctrl +** .) solo `GetSuggestedActions()` se llama a.

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

7. Defina un `SuggestedActionsChanged` evento.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. Para completar la implementación, agregue implementaciones para los `Dispose()` `TryGetTelemetryId()` métodos y. No quiere realizar la telemetría, así que solo tiene que devolver `false` y establecer el GUID en `Empty` .

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

## <a name="implement-light-bulb-actions"></a>Implementar acciones de bombillas

1. En el proyecto, agregue una referencia a *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* y establezca **copia local** en `False` .

2. Cree dos clases, la primera llamada `UpperCaseSuggestedAction` y la segunda llamada `LowerCaseSuggestedAction`. Ambas clases implementan <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Ambas clases son iguales, salvo que una llama a <xref:System.String.ToUpper%2A> y la otra llama a <xref:System.String.ToLower%2A>. Los siguientes pasos abarcan solo la clase de acción de mayúsculas, pero debe implementar ambas clases. Siga los pasos para implementar la acción de mayúsculas como un modelo para implementar la acción de minúsculas.

3. Agregue las siguientes directivas Using para estas clases:

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

6. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> método para que muestre la vista previa de la acción.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> método para que devuelva una <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> enumeración vacía.

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
    > No se espera que el método de **invocación** de la acción de bombilla muestre la interfaz de usuario. Si la acción hace que aparezca la nueva interfaz de usuario (por ejemplo, un cuadro de diálogo de vista previa o de selección), no muestre la interfaz de usuario directamente desde el método de **invocación** , sino que programe para mostrar la interfaz de usuario después de volver de **invocar**.

10. Para completar la implementación, agregue los `Dispose()` `TryGetTelemetryId()` métodos y.

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

11. No se olvide de hacer lo mismo para `LowerCaseSuggestedAction` cambiar el texto que se muestra a "convertir" a minúsculas {0} "y la llamada <xref:System.String.ToUpper%2A> a <xref:System.String.ToLower%2A> .

## <a name="build-and-test-the-code"></a>Compilar y probar el código
 Para probar este código, compile la solución LightBulbTest y ejecútela en la instancia experimental.

1. Compile la solución.

2. Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

3. Cree un archivo de texto y escriba algún texto. Debería ver una bombilla a la izquierda del texto.

     ![probar la bombilla](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. Señale la bombilla. Debería ver una flecha hacia abajo.

5. Al hacer clic en la bombilla, deben mostrarse dos acciones sugeridas, junto con la vista previa de la acción seleccionada.

     ![probar la bombilla, expandida](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6. Si hace clic en la primera acción, todo el texto de la palabra actual se debe convertir en mayúsculas. Si hace clic en la segunda acción, todo el texto se debe convertir a minúsculas.
