---
title: 'Tutorial: usar una tecla de método abreviado con una extensión de editor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5c9cb20bafa552c47a2f599d12e6b66fdb2bde59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201942"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Tutorial: Uso de una tecla de método abreviado con una extensión del editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede responder a las teclas de método abreviado en la extensión del editor. En el siguiente tutorial se muestra cómo agregar un elemento gráfico de vista a una vista de texto mediante una tecla de método abreviado. Este tutorial se basa en la plantilla del editor de elementos gráficos de la ventanilla y permite agregar el elemento gráfico mediante el carácter +.  
  
## <a name="prerequisites"></a>Prerrequisitos  
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Crear un proyecto de Managed Extensibility Framework (MEF)  
  
1. Cree un proyecto VSIX en C#. (En el cuadro de diálogo **nuevo proyecto** , seleccione **Visual C#/extensibilidad**y, a continuación, **Proyecto VSIX**). Asigne a la solución el nombre `KeyBindingTest` .  
  
2. Agregue una plantilla de elemento de gráfico de texto del editor al proyecto y asígnele el nombre `KeyBindingTest` . Para obtener más información, vea [crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Agregue las referencias siguientes y establezca **CopyLocal** en `false` :  
  
    Microsoft. VisualStudio. Editor  
  
    Microsoft.VisualStudio.OLE.Interop  
  
    Microsoft. VisualStudio. Shell. 14.0  
  
    Microsoft. VisualStudio. TextManager. Interop  
  
   En el archivo de clase KeyBindingTest, cambie el nombre de la clase a PurpleCornerBox. Use la bombilla que aparece en el margen izquierdo para realizar los demás cambios apropiados. Dentro del constructor, cambie el nombre de la capa de elemento gráfico de **KeyBindingTest** a **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>Definir el filtro de comandos  
 El filtro de comandos es una implementación de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , que controla el comando mediante la creación de instancias del elemento gráfico.  
  
1. Agregue un archivo de clase y asígnele el nombre `KeyBindingCommandFilter`.  
  
2. Agregue las siguientes instrucciones de uso.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3. La clase denominada KeyBindingCommandFilter debe heredar de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4. Agregue campos privados para la vista de texto, el siguiente comando de la cadena de comandos y una marca que represente si ya se ha agregado el filtro de comandos.  
  
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
  
6. Implemente el `QueryStatus()` método como se indica a continuación.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7. Implemente el `Exec()` método para que agregue un cuadro púrpura a la vista si se escribe un carácter +.  
  
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
  
## <a name="adding-the-command-filter"></a>Agregar el filtro de comandos  
 El proveedor de elementos gráficos debe agregar un filtro de comandos a la vista de texto. En este ejemplo, el proveedor implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> para escuchar los eventos de creación de la vista de texto. Este proveedor de elementos gráficos también exporta la capa de elementos gráficos, que define el orden Z del elemento gráfico.  
  
1. En el archivo KeyBindingTestTextViewCreationListener, agregue las siguientes instrucciones Using:  
  
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
  
2. En la definición de la capa de adornos, cambie el nombre del AdornmentLayer de **KeyBindingTest** a **PurpleCornerBox**.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3. Para obtener el adaptador de vista de texto, debe importar el <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> .  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4. Cambie el <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> método para que agregue la `KeyBindingCommandFilter` .  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5. El `AddCommandFilter` controlador obtiene el adaptador de vista de texto y agrega el filtro de comandos.  
  
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
  
## <a name="making-the-adornment-appear-on-every-line"></a>La forma en que el elemento gráfico aparece en cada línea  
 El elemento gráfico original aparecía en cada carácter "a" en un archivo de texto. Ahora que hemos cambiado el código para agregar el elemento gráfico en respuesta al carácter ' + ', agrega el elemento gráfico solo en la línea donde se escribe ' + '. Podemos cambiar el código de elemento gráfico para que el elemento gráfico aparezca una vez más en cada ' a '.  
  
 En el archivo KeyBindingTest.cs, cambie el método CreateVisuals () para recorrer en iteración todas las líneas de la vista para decorar el carácter "a".  
  
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
  
1. Compile la solución KeyBindingTest y ejecútela en la instancia experimental.  
  
2. Cree o abra un archivo de texto. Escriba algunas palabras que contengan el carácter "a" y, a continuación, escriba + en cualquier parte de la vista de texto.  
  
     Debe aparecer un cuadrado púrpura en cada carácter ' a ' del archivo.
