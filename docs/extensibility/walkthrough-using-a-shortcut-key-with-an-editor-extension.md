---
title: "Tutorial: Usar una tecla de m&#233;todo abreviado con una extensi&#243;n del Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] nuevo: vínculo pulsaciones de teclas a comandos"
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 32
caps.handback.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
---
# Tutorial: Usar una tecla de m&#233;todo abreviado con una extensi&#243;n del Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede responder a teclas de método abreviado en el editor de la extensión. El siguiente tutorial muestra cómo agregar un elemento de gráfico de la vista a una vista de texto mediante una tecla de método abreviado. En este tutorial se basa en la plantilla del editor de elementos gráficos de ventanilla, y permite agregar el elemento de gráfico utilizando el carácter \+.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Crear un proyecto de Managed Extensibility Framework \(MEF\)  
  
1.  Cree un proyecto de VSIX de C\#. \(En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C\# \/ extensibilidad**, a continuación, **proyecto VSIX**.\) El nombre de la solución `KeyBindingTest`.  
  
2.  Agregar una plantilla de elemento de elemento de gráfico de Editor texto al proyecto y asígnele el nombre `KeyBindingTest`. Para obtener más información, consulta [Crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Agregue las siguientes referencias y establezca **CopyLocal** a `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
 En el archivo de clase KeyBindingTest, cambie el nombre de clase a PurpleCornerBox. Utilice la luz que aparece en el margen izquierdo para realizar otros cambios adecuados. Dentro del constructor, cambie el nombre de la capa de elementos gráficos de **KeyBindingTest** a **PurpleCornerBox**:  
  
```c#  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## Definir el filtro de comandos  
 El filtro de comandos es una implementación de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, que controla el comando creando una instancia del elemento de gráfico.  
  
1.  Agregue un archivo de clase y asígnele el nombre `KeyBindingCommandFilter`.  
  
2.  Agregue las siguientes instrucciones de uso.  
  
    ```c#  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  La clase denominada KeyBindingCommandFilter debe heredar de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
    ```c#  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Agregue campos privados para la vista de texto, el comando siguiente en la cadena de comando y un indicador para representar si ya se ha agregado el filtro de comandos.  
  
    ```c#  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  Agregue un constructor que establece la vista de texto.  
  
    ```c#  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  Implemente el `QueryStatus()` método como sigue.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Implemente el `Exec()` método por lo que TI agrega un cuadro de color púrpura a la vista si un \+ carácter se escribe.  
  
    ```c#  
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
  
## Agregar el filtro de comandos  
 El proveedor del elemento gráfico debe agregar un filtro de comandos a la vista de texto. En este ejemplo, el proveedor implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> para escuchar los eventos de creación de la vista de texto. Este proveedor de elemento gráfico también exporta el nivel del elemento gráfico, que define el orden Z del elemento gráfico.  
  
1.  En el archivo KeyBindingTestTextViewCreationListener, agregue las siguientes instrucciones using:  
  
    ```c#  
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
  
2.  En la definición de nivel de elemento gráfico, cambiar el nombre de la AdornmentLayer de **KeyBindingTest** a **PurpleCornerBox**.  
  
    ```c#  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  Para obtener el adaptador de vista de texto, debe importar el <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```c#  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4.  Cambiar el <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> método por lo que agrega el `KeyBindingCommandFilter`.  
  
    ```c#  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5.  El `AddCommandFilter` controlador obtiene el adaptador de vista de texto y se agrega el filtro de comandos.  
  
    ```c#  
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
  
## Realizar el elemento de gráfico aparecen en cada línea.  
 El elemento de gráfico original aparece en todos los caracteres 'a' en un archivo de texto. Ahora que hemos cambiado el código para agregar el elemento de gráfico en respuesta al carácter '\+', agrega el elemento de gráfico sólo en la línea donde el signo ' \+' se ha escrito. Podemos cambiar el código del elemento gráfico para que aparezca el elemento de gráfico una vez más en cada 'a'.  
  
 En el archivo KeyBindingTest.cs, cambie el método CreateVisuals\(\) para recorrer en iteración todas las líneas en la vista para decorar el carácter 'a'.  
  
```c#  
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
  
## Compilar y probar el código  
  
1.  Compile la solución KeyBindingTest y ejecútelo en la instancia experimental.  
  
2.  Cree o abra un archivo de texto. Escriba algunas palabras que contengan el carácter 'a' y, a continuación, escriba \+ en cualquier parte de la vista de texto.  
  
     Un cuadrado de color púrpura debe aparecer en cada carácter 'a' en el archivo.