---
title: 'Tutorial: Uso de una tecla de acceso directo con una extensión de editor . Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651598c0dbe746a9a26a6d60ce72b02853f98d47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697151"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Tutorial: Use una tecla de método abreviado con una extensión de editor
Puede responder a las teclas de método abreviado en la extensión del editor. En el siguiente tutorial se muestra cómo agregar un adorno de vista a una vista de texto mediante una tecla de método abreviado. Este tutorial se basa en la plantilla del editor de adornos de la ventana gráfica y le permite agregar el adorno mediante el carácter +.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Crear un proyecto de managed Extensibility Framework (MEF)

1. Cree un proyecto de VSIX de C. (En el cuadro de diálogo **Nuevo proyecto** , seleccione **Visual C/ Extensibilidad**y, a continuación, **Proyecto VSIX**.) Asigne un `KeyBindingTest`nombre a la solución .

2. Agregue una plantilla de elemento Adornment de `KeyBindingTest`texto del editor al proyecto y asísaber. Para obtener más información, vea [Crear una extensión con una plantilla](../extensibility/creating-an-extension-with-an-editor-item-template.md)de elemento de editor .

3. Agregue las siguientes referencias y `false`establezca **CopyLocal** en:

    Microsoft.VisualStudio.Editor

    Microsoft.VisualStudio.OLE.Interop

    Microsoft.VisualStudio.Shell.14.0

    Microsoft.VisualStudio.TextManager.Interop

   En el keyBindingTest archivo de clase, cambie el nombre de clase a PurpleCornerBox. Utilice la bombilla que aparece en el margen izquierdo para realizar los demás cambios apropiados. Dentro del constructor, cambie el nombre de la capa de adorno de **KeyBindingTest** a **PurpleCornerBox**:

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

En el archivo de clase KeyBindingTestTextViewCreationListener.cs, cambie el nombre de AdornmentLayer de **KeyBindingTest** a **PurpleCornerBox**:

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>Comando Handle TYPECHAR
Antes de Visual Studio 2017 versión 15.6, la única <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> manera de controlar comandos en una extensión de editor era implementar un filtro de comandos basado. Visual Studio 2017 versión 15.6 introdujo un enfoque simplificado moderno basado en controladores de comandos del editor. Las dos secciones siguientes muestran cómo controlar un comando mediante el enfoque heredado y moderno.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Definir el filtro de comandos (antes de Visual Studio 2017 versión 15.6)

 El filtro de comandos es una implementación de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, que controla el comando creando una instancia del adorno.

1. Agregue un archivo de clase y asígnele el nombre `KeyBindingCommandFilter`.

2. Agregue las siguientes directivas using.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. La clase denominada KeyBindingCommandFilter <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>debe heredar de .

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. Agregue campos privados para la vista de texto, el siguiente comando de la cadena de comandos y una marca para representar si el filtro de comandos ya se ha agregado.

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
    ```

5. Agregue un constructor que establezca la vista de texto.

    ```csharp
    public KeyBindingCommandFilter(IWpfTextView textView)
    {
        m_textView = textView;
        m_adorned = false;
    }
    ```

6. Implemente `QueryStatus()` el método de la siguiente manera.

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7. Implemente `Exec()` el método para que agregue un cuadro morado**+** a la vista si se escribe un carácter de signo más ( ).

    ```csharp
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)
    {
        if (m_adorned == false)
        {
            char typedChar = char.MinValue;

            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)
            {
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);
                if (typedChar.Equals('+'))
                {
                    new PurpleCornerBox(m_textView);
                    m_adorned = true;
                }
            }
        }
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);
    }

    ```

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Agregue el filtro de comandos (antes de Visual Studio 2017 versión 15.6)
 El proveedor de adornos debe agregar un filtro de comandos a la vista de texto. En este ejemplo, el <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> proveedor implementa para escuchar eventos de creación de vistas de texto. Este proveedor de adornos también exporta la capa de adorno, que define el orden Z del adorno.

1. En el archivo KeyBindingTestTextViewCreationListener, agregue las siguientes directivas using:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio.Utilities;
    using Microsoft.VisualStudio.Editor;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.TextManager.Interop;

    ```

2. Para obtener el adaptador de vista <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>de texto, debe importar el archivo .

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. Cambie <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> el método para que `KeyBindingCommandFilter`agregue el archivo .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. El `AddCommandFilter` controlador obtiene el adaptador de vista de texto y agrega el filtro de comandos.

    ```csharp
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)
    {
        if (commandFilter.m_added == false)
        {
            //get the view adapter from the editor factory
            IOleCommandTarget next;
            IVsTextView view = editorFactory.GetViewAdapter(textView);

            int hr = view.AddCommandFilter(commandFilter, out next);

            if (hr == VSConstants.S_OK)
            {
                commandFilter.m_added = true;
                 //you'll need the next target for Exec and QueryStatus
                if (next != null)
                commandFilter.m_nextTarget = next;
            }
        }
    }
    ```

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Implementar un controlador de comandos (a partir de Visual Studio 2017 versión 15.6)

En primer lugar, actualice las referencias de Nuget del proyecto para hacer referencia a la API del editor más reciente:

1. Haga clic con el botón derecho en el proyecto y seleccione **Administrar paquetes Nuget**.

2. En **Nuget Package Manager**, seleccione la pestaña **Actualizaciones,** active la casilla **Seleccionar todos los paquetes** y, a continuación, seleccione **Actualizar**.

El controlador de comandos es una implementación de <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>, que controla el comando creando una instancia del adorno.

1. Agregue un archivo de clase y asígnele el nombre `KeyBindingCommandHandler`.

2. Agregue las siguientes directivas using.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. La clase denominada KeyBindingCommandHandler `ICommandHandler<TypeCharCommandArgs>`debe heredar <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>de , y exportarla como:

   ```csharp
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>
   ```

4. Agregue un nombre para mostrar del controlador de comandos:

   ```csharp
   public string DisplayName => "KeyBindingTest";
   ```

5. Implemente `GetCommandState()` el método de la siguiente manera. Dado que este controlador de comandos controla el comando TYPECHAR del editor principal, puede delegar la habilitación del comando en el editor principal.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. Implemente `ExecuteCommand()` el método para que agregue un cuadro morado**+** a la vista si se escribe un carácter de signo más ( ).

   ```csharp
   public bool ExecuteCommand(TypeCharCommandArgs args, CommandExecutionContext executionContext)
   {
       if (args.TypedChar == '+')
       {
           bool alreadyAdorned = args.TextView.Properties.TryGetProperty(
               "KeyBindingTextAdorned", out bool adorned) && adorned;
           if (!alreadyAdorned)
           {
               new PurpleCornerBox((IWpfTextView)args.TextView);
               args.TextView.Properties.AddProperty("KeyBindingTextAdorned", true);
           }
       }

       return false;
   }
   ```

   7. Copie la definición de capa de adorno del archivo *de KeyBindingTestTextViewCreationListener.cs* al *KeyBindingCommandHandler.cs* y, a continuación, elimine *KeyBindingTestTextViewCreationListener.cs* archivo:

   ```csharp
   /// <summary>
   /// Defines the adornment layer for the adornment. This layer is ordered
   /// after the selection layer in the Z-order.
   /// </summary>
   [Export(typeof(AdornmentLayerDefinition))]
   [Name("PurpleCornerBox")]
   [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
   private AdornmentLayerDefinition editorAdornmentLayer;
   ```

## <a name="make-the-adornment-appear-on-every-line"></a>Haz que el adorno aparezca en cada línea

El adorno original apareció en cada carácter 'a' en un archivo de texto. Ahora que hemos cambiado el código para agregar **+** el adorno en respuesta al carácter, **+** agrega el adorno solo en la línea donde se escribe el carácter. Podemos cambiar el código de adorno para que el adorno aparezca una vez más en cada 'a'.

En el archivo *KeyBindingTest.cs,* cambie el `CreateVisuals()` método para recorrer en iteración todas las líneas de la vista para decorar el carácter 'a'.

```csharp
private void CreateVisuals(ITextViewLine line)
{
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;

    foreach (ITextViewLine textViewLine in textViewLines)
    {
        if (textViewLine.ToString().Contains("a"))
        {
            // Loop through each character, and place a box around any 'a'
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)
            {
                if (this.view.TextSnapshot[charIndex] == 'a')
                {
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);
                    if (geometry != null)
                    {
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);
                        drawing.Freeze();

                        var drawingImage = new DrawingImage(drawing);
                        drawingImage.Freeze();

                        var image = new Image
                        {
                            Source = drawingImage,
                        };

                        // Align the image with the top of the bounds of the text geometry
                        Canvas.SetLeft(image, geometry.Bounds.Left);
                        Canvas.SetTop(image, geometry.Bounds.Top);

                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);
                    }
                }
            }
        }
    }
}
```

## <a name="build-and-test-the-code"></a>Compile y pruebe el código

1. Compile la solución KeyBindingTest y ejecútela en la instancia experimental.

2. Cree o abra un archivo de texto. Escriba algunas palabras que contengan **+** el carácter 'a' y, a continuación, escriba en cualquier lugar de la vista de texto.

     Un cuadrado púrpura debe aparecer en cada carácter 'a' en el archivo.
