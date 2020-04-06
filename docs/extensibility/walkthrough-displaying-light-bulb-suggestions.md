---
title: 'Tutorial: Visualización de sugerencias de bombillas de luz Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09773e2be81ce51971709db590a07ca9960104fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697472"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Tutorial: Mostrar sugerencias de bombillas
Las bombillas son iconos en el editor de Visual Studio que se expanden para mostrar un conjunto de acciones, por ejemplo, correcciones de problemas identificados por los analizadores de código integrados o la refactorización de código.

 En los editores de Visual C y Visual Basic, también puede usar la plataforma de compilador de .NET ("Roslyn") para escribir y empaquetar sus propios analizadores de código con acciones que muestran bombillas automáticamente. Para obtener más información, consulte:

- [Cómo: Escribir una corrección de diagnóstico y código de C-](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [Cómo: Escribir un diagnóstico de Visual Basic y una corrección de código](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  Otros lenguajes como C++ también proporcionan bombillas para algunas acciones rápidas, como, una sugerencia para crear una implementación de código auxiliar de esa función.

  Así es como se ve una bombilla. En un proyecto de Visual Basic o Visual C, aparece un ondulado rojo bajo un nombre de variable cuando no es válido. Si pasa el ratón sobre el identificador no válido, aparecerá una bombilla cerca del cursor.

  ![bombilla](../extensibility/media/lightbulb.png "Bombilla")

  Si hace clic en la flecha hacia abajo junto a la bombilla, aparecerá un conjunto de acciones sugeridas, junto con una vista previa de la acción seleccionada. En este caso, muestra los cambios realizados en el código si ejecuta la acción.

  ![vista previa de bombilla](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  Puede utilizar bombillas para proporcionar sus propias acciones sugeridas. Por ejemplo, podría proporcionar acciones para mover llaves de apertura a una nueva línea o moverlas al final de la línea anterior. En el siguiente tutorial se muestra cómo crear una bombilla que aparece en la palabra actual y tiene dos acciones sugeridas: **Convertir a mayúsculas** y **Convertir a minúsculas**.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Crear un proyecto de Managed Extensibility Framework (MEF)

1. Cree un proyecto de VSIX de C. (En el cuadro de diálogo **Nuevo proyecto** , seleccione **Visual C/ Extensibilidad**y, a continuación, **Proyecto VSIX**.) Asigne un `LightBulbTest`nombre a la solución .

2. Agregue una plantilla de elemento **Clasificador** de editor al proyecto. Para obtener más información, consulte Crear una extensión con una plantilla de elemento de [editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Elimine los archivos de clase existentes.

4. Agregue la siguiente referencia al proyecto y `False`establezca Copiar **local** en:

     *Microsoft.VisualStudio.Language.Intellisense*

5. Agregue un nuevo archivo de clase y **asíse: LightBulbTest**.

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

## <a name="implement-the-light-bulb-source-provider"></a>Implementar el proveedor de fuente de bombilla

1. En el *LightBulbTest.cs* archivo de clase, elimine la clase LightBulbTest. Agregue una clase denominada **TestSuggestedActionsSourceProvider** que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Expórtelo con un nombre <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de **acciones sugeridas** de prueba y un de "texto".

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. Dentro de la clase <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> de proveedor de origen, importe y agréguelo como una propiedad.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> para devolver un objeto. La fuente se describe en la siguiente sección.

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

## <a name="implement-the-isuggestedactionsource"></a>Implementar el ISuggestedActionSource
 La fuente de acción sugerida es responsable de recopilar el conjunto de acciones sugeridas y agregarlas en el contexto correcto. En este caso, el contexto es la palabra actual y las acciones sugeridas son **UpperCaseSuggestedAction** y **LowerCaseSuggestedAction**, que se describe en la sección siguiente.

1. Agregue una clase **TestSuggestedActionsSource** que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. Agregue campos privados de solo lectura para el proveedor de origen de acciones sugerido, el búfer de texto y la vista de texto.

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

4. Agregue un método privado que devuelva la palabra que está actualmente debajo del cursor. El siguiente método examina la ubicación actual del cursor y solicita al navegador de estructura de texto la extensión de la palabra. Si el cursor está en <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> una palabra, se devuelve en el parámetro out; de lo `out` contrario, el parámetro es `null` y el método devuelve `false`.

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

5. Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>. El editor llama a este método para averiguar si se debe mostrar la bombilla. Esta llamada se realiza a menudo, por ejemplo, cada vez que el cursor se mueve de una línea a otra, o cuando el ratón se desplaza sobre un error ondulando. Es asíncrono para permitir que otras operaciones de interfaz de usuario continúen mientras este método funciona. En la mayoría de los casos, este método necesita realizar algún análisis y análisis de la línea actual, por lo que el procesamiento puede tardar algún tiempo.

     En esta implementación, obtiene <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> de forma asincrónica y determina si la extensión es significativa, como en, si tiene algún texto que no sea espacios en blanco.

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

6. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> el método, que <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> devuelve una matriz <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> de objetos que contienen los diferentes objetos. Este método se llama cuando se expande la bombilla.

    > [!WARNING]
    > Debe asegurarse de que `HasSuggestedActionsAsync()` las `GetSuggestedActions()` implementaciones de y son coherentes; es decir, `HasSuggestedActionsAsync()` `true`si `GetSuggestedActions()` devuelve , entonces debe tener algunas acciones para mostrar. En muchos `HasSuggestedActionsAsync()` casos, se `GetSuggestedActions()`llama justo antes, pero esto no siempre es el caso. Por ejemplo, si el usuario invoca las acciones de bombilla `GetSuggestedActions()` presionando (**CTRL+** .) sólo se llama.

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

7. Defina `SuggestedActionsChanged` un evento.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. Para completar la implementación, `Dispose()` agregue `TryGetTelemetryId()` implementaciones para los métodos y. No desea realizar la telemetría, por `false` lo que `Empty`solo tiene que devolver y establecer el GUID en .

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

## <a name="implement-light-bulb-actions"></a>Implementar acciones de bombilla

1. En el proyecto, agregue una referencia a *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* y establezca **Copy Local** en `False`.

2. Cree dos clases, la primera llamada `UpperCaseSuggestedAction` y la segunda llamada `LowerCaseSuggestedAction`. Ambas clases implementan <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Ambas clases son iguales, salvo que una llama a <xref:System.String.ToUpper%2A> y la otra llama a <xref:System.String.ToLower%2A>. Los siguientes pasos abarcan solo la clase de acción de mayúsculas, pero debe implementar ambas clases. Siga los pasos para implementar la acción de mayúsculas como un modelo para implementar la acción de minúsculas.

3. Agregue las siguientes directivas using para estas clases:

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

6. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> el método para que muestre la vista previa de la acción.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> el método para que <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> devuelva una enumeración vacía.

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
    > No se espera que el método **Invoke** de la acción de bombilla muestre la interfaz de usuario. Si la acción abre una nueva interfaz de usuario (por ejemplo, una vista previa o un cuadro de diálogo de selección), no muestre la interfaz de usuario directamente desde el método **Invoke,** sino que programe la visualización de la interfaz de usuario después de volver desde **Invoke**.

10. Para completar la implementación, agregue los `Dispose()` métodos y. `TryGetTelemetryId()`

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

11. No se olvide de hacer `LowerCaseSuggestedAction` lo mismo para cambiar{0}el texto de visualización <xref:System.String.ToUpper%2A> <xref:System.String.ToLower%2A>a "Convertir ' a minúsculas" y la llamada a .

## <a name="build-and-test-the-code"></a>Compile y pruebe el código
 Para probar este código, compile la solución LightBulbTest y ejecútela en la instancia experimental.

1. Compile la solución.

2. Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

3. Cree un archivo de texto y escriba algún texto. Debería ver una bombilla a la izquierda del texto.

     ![probar la bombilla](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. Apunte a la bombilla. Deberías ver una flecha hacia abajo.

5. Al hacer clic en la bombilla, deben mostrarse dos acciones sugeridas, junto con la vista previa de la acción seleccionada.

     ![probar la bombilla, expandida](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6. Si hace clic en la primera acción, todo el texto de la palabra actual debe convertirse a mayúsculas. Si hace clic en la segunda acción, todo el texto debe convertirse a minúsculas.
