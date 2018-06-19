---
title: 'Tutorial: Usar una tecla de método abreviado con una extensión del Editor | Documentos de Microsoft'
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
ms.openlocfilehash: f8f8a310832f0691b4bc4056baddeb1fbbad78f8
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704030"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Tutorial: Usar una tecla de método abreviado con una extensión del Editor
Puede responder a teclas de método abreviado de la extensión del editor. En el siguiente tutorial muestra cómo agregar un elemento de gráfico de la vista a una vista de texto mediante una tecla de método abreviado. En este tutorial se basa en la plantilla del editor de elementos gráficos de área de visualización y permite agregar el elemento de gráfico utilizando el carácter +.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Crear un proyecto de Managed Extensibility Framework (MEF)  
  
1.  Cree un proyecto de C# VSIX. (En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C# / extensibilidad**, a continuación, **proyecto VSIX**.) Llame a la solución `KeyBindingTest`.  
  
2.  Agregar una plantilla de elementos de elemento de gráfico de Editor texto al proyecto y asígnele el nombre `KeyBindingTest`. Para obtener más información, consulte [crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Agregue las siguientes referencias y establezca **CopyLocal** a `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
 En el archivo de clase KeyBindingTest, cambie el nombre de clase para PurpleCornerBox. Use la bombilla que aparece en el margen izquierdo para realizar otros cambios adecuados. Dentro del constructor, cambie el nombre de la capa de elementos gráficos desde **KeyBindingTest** a **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  

En el archivo de clase KeyBindingTestTextViewCreationListener.cs, cambie el nombre de la AdornmentLayer de **KeyBindingTest** a **PurpleCornerBox**:
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  

## <a name="handling-typechar-command"></a>Control de comando TYPECHAR
Antes de la versión 15.6 era la implementación de la única manera de controlar comandos en una extensión del editor de Visual Studio 2017 un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> en función de filtro de comandos. Visual Studio 2017 versión 15.6 introdujo un enfoque simplificado moderno en función de los controladores de comandos de editor. Las dos secciones siguientes muestran cómo controlar un comando, usando tanto el enfoque heredado y moderno.

## <a name="defining-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Definir el filtro de comandos (anterior a Visual Studio 2017 versión 15.6)

 El filtro de comandos es una implementación de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, que controla el comando de creación de instancias de los elementos de gráficos.  
  
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
  
4.  Agregue campos privados para la vista de texto, el comando siguiente en la cadena de comando y un indicador para representar si ya se ha agregado el filtro de comandos.  
  
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
  
7.  Implemente el `Exec()` método por lo que TI agrega un cuadro de color púrpura a la vista si un + carácter se escribe.  
  
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
  
## <a name="adding-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Agregar el filtro de comandos (anterior a Visual Studio 2017 versión 15.6)
 El proveedor de elementos gráficos debe agregar un filtro de comandos a la vista de texto. En este ejemplo, el proveedor implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> para escuchar los eventos de creación de vista de texto. Este proveedor de elementos gráficos también exporta la capa de elementos gráficos, que define el orden Z de los elementos de gráficos.  
  
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

2. En **Administrador de paquetes de Nuget**, seleccione la **actualizaciones** ficha, seleccione la **seleccionar todos los paquetes** casilla de verificación y, a continuación, seleccione **actualización**.

El controlador de comandos es una implementación de <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>, que controla el comando de creación de instancias de los elementos de gráficos.  
  
1.  Agregue un archivo de clase y asígnele el nombre `KeyBindingCommandHandler`.  
  
2.  Agregue las siguientes instrucciones de uso.  
  
    ```csharp  
    using Microsoft.VisualStudio.Commanding;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
    using Microsoft.VisualStudio.Utilities;
    using System.ComponentModel.Composition;   
    ```  
  
3.  La clase denominada KeyBindingCommandHandler debe heredar de `ICommandHandler<TypeCharCommandArgs>`y se exporta como <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>:
  
    ```csharp  
    [Export(typeof(ICommandHandler))]
    [ContentType("text")]
    [Name("KeyBindingTest")]
    internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>  
    ```  
  
4.  Agregue un nombre para mostrar del controlador de comandos:  
  
    ```csharp  
    public string DisplayName => "KeyBindingTest";
    ```  
    
5.  Implemente el `GetCommandState()` método tal como se indica a continuación. Puesto que este controlador de comandos controla el comando TYPECHAR de núcleo editor, puede delegar habilitar el comando en el editor principal.
  
    ```csharp  
    public CommandState GetCommandState(TypeCharCommandArgs args)
    {
        return CommandState.Unspecified;
    } 
    ```  
  
6.  Implemente el `ExecuteCommand()` método por lo que TI agrega un cuadro de color púrpura a la vista si un + carácter se escribe. 
  
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
 7. Copiar la definición de la capa de elementos gráficos del archivo de KeyBindingTestTextViewCreationListener.cs en el KeyBindingCommandHandler.cs y, a continuación, elimine el archivo de KeyBindingTestTextViewCreationListener.cs:
 
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

## <a name="making-the-adornment-appear-on-every-line"></a>Hacer que los elementos de gráficos que aparecen en cada línea  

El elemento de gráfico original aparece en todos los caracteres "a" en un archivo de texto. Ahora que hemos cambiado el código para agregar el elemento de gráfico en respuesta a los caracteres '+', agrega el elemento de gráfico solo en la línea donde el '+' se ha escrito. Podemos cambiar el código del elemento gráfico para que aparezca el elemento de gráfico una vez más en cada 'a'.  
  
En el archivo KeyBindingTest.cs, cambie el método CreateVisuals() para recorrer en iteración todas las líneas en la vista para decorar el carácter 'a'.  
  
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
  
## <a name="building-and-testing-the-code"></a>Compilar y probar el código  
  
1.  Compile la solución KeyBindingTest y ejecútelo en la instancia experimental.  
  
2.  Cree o abra un archivo de texto. Escriba algunas palabras que contengan el carácter 'a' y, a continuación, escriba + en cualquier parte de la vista de texto.  
  
     Debe aparecer un cuadrado de color púrpura en cada carácter 'a' en el archivo.
