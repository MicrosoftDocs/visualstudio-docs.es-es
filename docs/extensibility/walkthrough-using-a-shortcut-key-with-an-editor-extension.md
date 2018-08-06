---
title: 'Tutorial: Usar una tecla de método abreviado con una extensión del Editor | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cb4788e872e18d5db9c6d7c4452defc415290188
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566569"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Tutorial: Usar una tecla de método abreviado con una extensión del editor
Puede responder a teclas de método abreviado en la extensión del editor. El siguiente tutorial muestra cómo agregar un elemento de gráfico de vista a una vista de texto mediante una tecla de método abreviado. En este tutorial se basa en la plantilla del editor de elemento gráfico de área de visualización, y permite agregar el elemento de gráfico con el carácter +.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Ha incluido como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-managed-extensibility-framework-mef-project"></a>Crear un proyecto de Managed Extensibility Framework (MEF)  
  
1.  Cree un proyecto de VSIX de C#. (En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C# / extensibilidad**, a continuación, **proyecto VSIX**.) Nombre de la solución `KeyBindingTest`.  
  
2.  Agregar una plantilla de elemento gráfico de texto del Editor de elementos al proyecto y asígnele el nombre `KeyBindingTest`. Para obtener más información, consulte [crear una extensión con una plantilla de elementos de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Agregue las siguientes referencias y establezca **CopyLocal** a `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
 En el archivo de clase KeyBindingTest, cambie el nombre de clase a PurpleCornerBox. Usar la bombilla que aparece en el margen izquierdo para realizar otros cambios adecuados. Dentro del constructor, cambie el nombre de la capa de elemento gráfico desde **KeyBindingTest** a **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  

En el archivo de clase KeyBindingTestTextViewCreationListener.cs, cambiar el nombre de la AdornmentLayer de **KeyBindingTest** a **PurpleCornerBox**:
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  

## <a name="handle-typechar-command"></a>Controlar el comando TYPECHAR
Antes de Visual Studio 2017 versión 15.6, la única manera de controlar los comandos en una extensión del editor se implementa un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> en función de filtro de comandos. Visual Studio 2017 versión 15.6 introdujo un enfoque simplificado moderno basado en controladores de comandos del editor. Las dos secciones siguientes muestran cómo controlar un comando usando tanto el enfoque heredado y moderno.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Definir el filtro de comandos (antes Visual Studio 2017 versión 15.6)

 El filtro de comandos es una implementación de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, que controla el comando al crear una instancia del elemento gráfico.  
  
1.  Agregue un archivo de clase y asígnele el nombre `KeyBindingCommandFilter`.  
  
2.  Agregue las siguientes instrucciones de uso.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  La clase denominada KeyBindingCommandFilter debe heredar de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Agregue los campos privados de la vista de texto, el comando siguiente en la cadena de comandos y una marca para representar si ya se ha agregado el filtro de comandos.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  Agregue un constructor que establece la vista de texto.  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  Implemente el `QueryStatus()` método tal como se indica a continuación.  
  
    ```csharp  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Implemente el `Exec()` método por lo que TI agrega un cuadro de color púrpura en la vista si un signo más (**+**) se escribe el carácter.  
  
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
  
## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Agregue el filtro de comando (antes Visual Studio 2017 versión 15.6)
 El proveedor del elemento gráfico debe agregar un filtro de comando a la vista de texto. En este ejemplo, el proveedor implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> para escuchar los eventos de creación de la vista de texto. Este proveedor de elemento gráfico también exporta el nivel del elemento gráfico, que define el orden Z del elemento gráfico.  
  
1.  En el archivo KeyBindingTestTextViewCreationListener, agregue las siguientes instrucciones using:  
  
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
  
2.  Para obtener el adaptador de vista de texto, debe importar el <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
3.  Cambiar el <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> método por lo que TI agrega el `KeyBindingCommandFilter`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
4.  El `AddCommandFilter` controlador obtiene el adaptador de vista de texto y agrega el filtro de comandos.  
  
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

En primer lugar, actualice las referencias del proyecto Nuget para hacer referencia a la API de editor más reciente:

1. Haga doble clic en el proyecto y seleccione **administrar paquetes de Nuget**.

2. En **Administrador de paquetes de Nuget**, seleccione el **actualizaciones** ficha, seleccione el **seleccione todos los paquetes** casilla de verificación y, a continuación, seleccione **actualización**.

El controlador de comandos es una implementación de <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>, que controla el comando al crear una instancia del elemento gráfico.  
  
1.  Agregue un archivo de clase y asígnele el nombre `KeyBindingCommandHandler`.  
  
2.  Agregue las siguientes instrucciones de uso.  
  
    ```csharp  
    using Microsoft.VisualStudio.Commanding;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
    using Microsoft.VisualStudio.Utilities;
    using System.ComponentModel.Composition;   
    ```  
  
3.  Debe heredar la clase denominada KeyBindingCommandHandler `ICommandHandler<TypeCharCommandArgs>`y expórtelo como <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>:
  
    ```csharp  
    [Export(typeof(ICommandHandler))]
    [ContentType("text")]
    [Name("KeyBindingTest")]
    internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>  
    ```  
  
4.  Agregue un nombre para mostrar del controlador de comando:  
  
    ```csharp  
    public string DisplayName => "KeyBindingTest";
    ```  
    
5.  Implemente el `GetCommandState()` método tal como se indica a continuación. Puesto que este controlador de comandos controla el comando TYPECHAR de editor de núcleo, puede delegar habilitar el comando para el editor básico.
  
    ```csharp  
    public CommandState GetCommandState(TypeCharCommandArgs args)
    {
        return CommandState.Unspecified;
    } 
    ```  
  
6.  Implemente el `ExecuteCommand()` método por lo que TI agrega un cuadro de color púrpura en la vista si un signo más (**+**) se escribe el carácter. 
  
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
 7. Copie la definición de la capa de elemento gráfico de *KeyBindingTestTextViewCreationListener.cs* del archivo a la *KeyBindingCommandHandler.cs* y, a continuación, eliminar  *KeyBindingTestTextViewCreationListener.cs* archivo:
 
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

## <a name="make-the-adornment-appear-on-every-line"></a>Hacer que el elemento gráfico aparezca en todas las líneas  

El elemento de gráfico original aparece en todos los caracteres 'a' en un archivo de texto. Ahora que hemos cambiado el código para agregar el elemento de gráfico en respuesta a la **+** caracteres, agrega el elemento de gráfico sólo en la línea donde el **+** escribe el carácter. Podemos cambiar el código del elemento gráfico para que aparezca el elemento de gráfico una vez más en cada 'a'.  
  
En el *KeyBindingTest.cs* de archivo, cambie el `CreateVisuals()` método para recorrer en iteración todas las líneas en la vista para decorar el carácter 'a'.  
  
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
  
## <a name="build-and-test-the-code"></a>Compilar y probar el código  
  
1.  Compile la solución KeyBindingTest y ejecútelo en la instancia experimental.  
  
2.  Cree o abra un archivo de texto. Escriba algunas palabras que contengan el carácter 'a' y, a continuación, escriba **+** en cualquier parte de la vista de texto.  
  
     Debería aparecer un cuadrado de color púrpura en cada carácter 'a' en el archivo.
