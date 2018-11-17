---
title: Exponer propiedades a la ventana Propiedades | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 026e7de7d56cb907682be52db2dbd32782822d9f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756910"
---
# <a name="exposing-properties-to-the-properties-window"></a>Exposición de las propiedades en la ventana de propiedades
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial expone las propiedades públicas de un objeto para el **propiedades** ventana. Los cambios que realice para estas propiedades se reflejan en el **propiedades** ventana.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="exposing-properties-to-the-properties-window"></a>Exposición de las propiedades en la ventana de propiedades  
 En esta sección, creará una ventana de herramientas personalizada y mostrar las propiedades públicas del objeto de panel de ventana asociada en el **propiedades** ventana.  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>Para exponer las propiedades de la ventana Propiedades  
  
1.  Todas las extensiones de Visual Studio se inicia con un proyecto de implementación de VSIX que contendrá los recursos de extensión. Crear un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proyecto VSIX denominado `MyObjectPropertiesExtension`. Puede encontrar la plantilla de proyecto VSIX en el **nuevo proyecto** en el cuadro de diálogo **Visual C# / extensibilidad**.  
  
2.  Agregar una ventana de herramientas mediante la adición de una plantilla de elemento de la ventana de herramientas personalizada denominada `MyToolWindow`. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**. En el **cuadro de diálogo Agregar nuevo elemento**, vaya a **elementos de Visual C# / extensibilidad** y seleccione **ventana de herramientas personalizada**. En el **nombre** campo en la parte inferior del cuadro de diálogo, cambie el nombre de archivo a `MyToolWindow.cs`. Para obtener más información sobre cómo crear una ventana de herramientas personalizada, vea [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Abra MyToolWindow.cs y agregue la siguiente instrucción using:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  Ahora agregue los campos siguientes a la `MyToolWindow` clase.  
  
    ```csharp  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  Agregue el código siguiente a la clase MyToolWindow.  
  
    ```csharp  
    private ITrackSelection TrackSelection  
    {  
        get  
        {  
            if (trackSel == null)  
                trackSel =  
                   GetService(typeof(STrackSelection)) as ITrackSelection;  
            return trackSel;  
        }  
    }  
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     El `TrackSelection` propiedad usa `GetService` para obtener un `STrackSelection` service, que proporciona un <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfaz. El `OnToolWindowCreated` controlador de eventos y `SelectList` método juntos crean una lista de los objetos seleccionados que contiene solo la herramienta ventana Panel propio objeto. El `UpdateSelection` método indica la **propiedades** ventana para mostrar las propiedades públicas del panel de ventana de herramientas.  
  
6.  Compile la solución y comience la depuración. Debería aparecer la instancia experimental de Visual Studio.  
  
7.  Si el **propiedades** ventana no está visible, ábrala presionando F4.  
  
8.  Abra el **MyToolWindow** ventana. Puede encontrarlo en **vista / Windows otros**.  
  
     Se abre la ventana y las propiedades públicas del panel de ventana aparecen en la **propiedades** ventana.  
  
9. Cambiar el **título** propiedad en el **propiedades** ventana para **propiedades de mi objeto**.  
  
     El título de ventana MyToolWindow cambia en consecuencia.  
  
## <a name="exposing-tool-window-properties"></a>Expone las propiedades de ventana de herramienta  
 En esta sección, agregará una ventana de herramientas y exponer sus propiedades. Los cambios realizados en las propiedades se reflejan en el **propiedades** ventana.  
  
#### <a name="to-expose-tool-window-properties"></a>Para exponer propiedades de la ventana de herramienta  
  
1.  Abra MyToolWindow.cs y agregue la propiedad booleana pública IsChecked a la clase MyToolWindow.  
  
    ```csharp  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     Esta propiedad obtiene su estado de la casilla de verificación WPF que creará más adelante.  
  
2.  Abra MyToolWindowControl.xaml.cs y reemplace el constructor de MyToolWindowControl con el código siguiente.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     Esto proporciona `MyToolWindowControl` el acceso a la `MyToolWindow` panel.  
  
3.  En MyToolWindow.cs, cambie el `MyToolWindow` constructor como sigue:  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  Cambie a la vista de diseño de MyToolWindowControl.  
  
5.  El botón Eliminar y agregar una casilla de verificación de la **cuadro de herramientas** hacia la esquina superior izquierda.  
  
6.  Agregue los eventos Checked y Unchecked. Seleccione la casilla de verificación en la vista Diseño. En el **propiedades** ventana, haga clic en el botón de controladores de eventos (en la parte superior derecha de la **propiedades** ventana). Buscar **Checked** y tipo **checkbox_Checked** en el cuadro de texto, a continuación, busque **Unchecked** y tipo **checkbox_Unchecked** en el cuadro de texto.  
  
7.  Agregue los controladores de eventos de la casilla de verificación:  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = true;  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.UpdateSelection();  
    }  
    ```  
  
8.  Compile la solución y comience la depuración.  
  
9. En la instancia experimental, abra el **MyToolWindow** ventana.  
  
     Busque las propiedades de la ventana en la **propiedades** ventana. El **IsChecked** propiedad aparece en la parte inferior de la ventana, en el **propiedades de mi** categoría.  
  
10. Active la casilla de verificación la **MyToolWindow** ventana. **IsChecked** en el **propiedades** ventana cambia a **True**. Desactive la casilla de verificación en la **MyToolWindow** ventana. **IsChecked** en el **propiedades** ventana cambia a **False**. Cambie el valor de **IsChecked** en el **propiedades** ventana. La casilla de verificación en la **MyToolWindow** ventana cambia para coincidir con el nuevo valor.  
  
    > [!NOTE]
    >  Si debe desechar un objeto que se muestra en el **propiedades** (ventana), llamada `OnSelectChange` con un `null` contenedor de selección primero. Después de desechar la propiedad o el objeto, puede cambiar a un contenedor de selección que se ha actualizado <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> y <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> se enumeran.  
  
## <a name="changing-selection-lists"></a>Cambiar las listas de selección  
 En esta sección, agregue una lista de selección para una clase de propiedad básico y use la interfaz de la ventana de herramienta para elegir qué lista de selección para mostrar.  
  
#### <a name="to-change-selection-lists"></a>Para cambiar las listas de selección  
  
1.  Abra MyToolWindow.cs y agregue una clase pública denominada `Simple`.  
  
    ```csharp  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
        {  
            get { return someText; }  
            set { someText = value; }  
        }  
  
        [Category("My Properties")]  
        [Description("Read-only property")]  
        public bool ReadOnly  
        {  
            get { return false; }  
        }  
    }  
    ```  
  
2.  Agregar una propiedad SimpleObject a la clase MyToolWindow, además de los dos métodos para cambiar la **propiedades** selección entre el panel de ventana de la ventana y la `Simple` objeto.  
  
    ```csharp  
    private Simple simpleObject = null;  
    public Simple SimpleObject  
    {  
        get  
        {  
            if (simpleObject == null) simpleObject = new Simple();  
            return simpleObject;  
        }  
    }  
  
    public void SelectSimpleList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(SimpleObject);  
        SelectList(listObjects);  
    }  
  
    public void SelectThisList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
3.  En MyToolWindowControl.cs, reemplace los controladores de casilla de verificación con estas líneas de código:  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
     {  
        pane.IsChecked = true;  
        pane.SelectSimpleList();  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.SelectThisList();  
        pane.UpdateSelection();  
    }  
    ```  
  
4.  Compile la solución y comience la depuración.  
  
5.  En la instancia experimental, abra el **MyToolWindow** ventana.  
  
6.  Active la casilla situada en la **MyToolWindow** ventana. El **propiedades** ventana muestra el `Simple` propiedades, del objeto **SomeText** y **ReadOnly**. Desactive la casilla de verificación. Las propiedades públicas de la ventana aparecen en la **propiedades** ventana.  
  
    > [!NOTE]
    >  El nombre para mostrar de **SomeText** es **mi texto**.  
  
## <a name="best-practice"></a>Procedimiento recomendado  
 En este tutorial, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> se implementa para que la colección de objetos seleccionables y en la colección de objetos seleccionados son la misma colección. Sólo el objeto seleccionado aparece en la lista del explorador de propiedades. Para una implementación de ISelectionContainer más completa, consulte los ejemplos de Reference.ToolWindow.  
  
 Ventanas de herramientas de Visual Studio se conservan entre sesiones de Visual Studio. Para obtener más información sobre la conservación del estado de la ventana de herramienta, consulte <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## <a name="see-also"></a>Vea también  
 [Ampliación de propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)

