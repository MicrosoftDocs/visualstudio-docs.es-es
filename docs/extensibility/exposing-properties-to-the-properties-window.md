---
title: "Expone las propiedades en la ventana Propiedades | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "propiedades [Visual Studio SDK], exponer en el Explorador de propiedades"
  - "propiedades [Visual Studio SDK]"
  - "Examinador de propiedades, exponer propiedades"
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 36
caps.handback.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
---
# Expone las propiedades en la ventana Propiedades
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tutorial muestra las propiedades públicas de un objeto a la **propiedades** ventana. Los cambios realizados a estas propiedades se reflejan en el **propiedades** ventana.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Expone las propiedades en la ventana Propiedades  
 En esta sección, creará una ventana de herramientas personalizada y mostrar las propiedades públicas del objeto de panel de ventana asociada en el **propiedades** ventana.  
  
#### Exponer propiedades a la ventana Propiedades  
  
1.  Todas las extensiones de Visual Studio se inicia con un proyecto de implementación de VSIX que contiene los activos de la extensión. Crear un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto VSIX denominado `MyObjectPropertiesExtension`. Puede encontrar la plantilla de proyecto VSIX en la **nuevo proyecto** en el cuadro de diálogo **Visual C\# \/ extensibilidad**.  
  
2.  Agregar una ventana de herramientas mediante la adición de una plantilla de elemento de ventana de herramientas personalizada denominada `MyToolWindow`. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar \/ nuevo elemento**. En el **cuadro de diálogo Agregar nuevo elemento**, vaya a **elementos de Visual C\# \/ extensibilidad** y seleccione **ventana de herramientas personalizada**. En el **nombre** campo en la parte inferior del cuadro de diálogo, cambie el nombre de archivo a `MyToolWindow.cs`. Para obtener más información sobre cómo crear una ventana de herramientas personalizada, consulte [Crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Abra MyToolWindow.cs y agregue la siguiente instrucción using:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  Ahora agregue los siguientes campos a la `MyToolWindow` clase.  
  
    ```c#  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  Agregue el código siguiente a la clase MyToolWindow.  
  
    ```c#  
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
  
     La `TrackSelection` usos de la propiedad `GetService` para obtener un `STrackSelection` servicio, que proporciona un <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfaz. El `OnToolWindowCreated` controlador de eventos y `SelectList` método juntas, crean una lista de los objetos seleccionados que contiene sólo la herramienta ventana Panel propio objeto. El `UpdateSelection` método indica el **propiedades** ventana para mostrar las propiedades públicas del panel de la ventana de herramienta.  
  
6.  Compile la solución y comience la depuración. Debe aparecer la instancia experimental de Visual Studio.  
  
7.  Si el **propiedades** ventana no está visible, ábrala presionando F4.  
  
8.  Abra la **MyToolWindow** ventana. Puede encontrarlo en **vista y otras ventanas**.  
  
     Se abre la ventana y las propiedades públicas del panel de la ventana que aparecen en la **propiedades** ventana.  
  
9. Cambiar el **título** propiedad en el **propiedades** ventana **Propiedades de mi objeto**.  
  
     Título de ventana MyToolWindow cambia en consecuencia.  
  
## Exponer propiedades de la ventana de herramienta  
 En esta sección, agregará una ventana de herramientas y exponer sus propiedades. Los cambios realizados en las propiedades se reflejan en el **propiedades** ventana.  
  
#### Exponer propiedades de la ventana de herramienta  
  
1.  Abra MyToolWindow.cs y agregue la propiedad booleana pública IsChecked a la clase MyToolWindow.  
  
    ```c#  
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
  
3.  En MyToolWindow.cs, cambie la `MyToolWindow` constructor como sigue:  
  
    ```c#  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  Cambie a la vista Diseño de MyToolWindowControl.  
  
5.  Elimine el botón y agregue una casilla de verificación de la **herramientas** a la esquina superior izquierda.  
  
6.  Agregue los eventos Checked y Unchecked. Seleccione la casilla de verificación en la vista Diseño. En el **propiedades** ventana, haga clic en el botón de controladores de eventos \(en la parte superior derecha de la **propiedades** ventana\). Buscar **Checked** y escriba **checkbox\_Checked** en el cuadro de texto, a continuación, busque **Unchecked** y escriba **checkbox\_Unchecked** en el cuadro de texto.  
  
7.  Agregue los controladores de eventos de la casilla de verificación:  
  
    ```c#  
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
  
     Buscar propiedades de la ventana en el **propiedades** ventana. El **IsChecked** propiedad aparece en la parte inferior de la ventana, en la **Propiedades de mi** categoría.  
  
10. Active la casilla de verificación de la **MyToolWindow** ventana.**IsChecked** en el **propiedades** ventana cambia a **True**. Desactive la casilla de verificación en la **MyToolWindow** ventana.**IsChecked** en el **propiedades** ventana cambia a **False**. Cambie el valor de **IsChecked** en el **propiedades** ventana. La casilla de verificación en la **MyToolWindow** ventana cambia para coincidir con el nuevo valor.  
  
    > [!NOTE]
    >  Si debe desechar un objeto que se muestra en el **propiedades** ventana, llamada `OnSelectChange` con un `null` contenedor de selección primero. Después de desechar la propiedad u objeto, puede cambiar a un contenedor de selección que se ha actualizado <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> y <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> se enumeran.  
  
## Cambiar listas de selección  
 En esta sección, agregue una lista de selección para una clase de propiedad básica y usar la interfaz de ventana de herramienta para elegir qué lista de selección para mostrar.  
  
#### Para cambiar las listas de selección  
  
1.  Abra MyToolWindow.cs y agregue una clase pública denominada `Simple`.  
  
    ```c#  
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
  
2.  Agregar una propiedad SimpleObject a la clase MyToolWindow, además de dos métodos para cambiar la **propiedades** selección de ventana entre el panel de la ventana y la `Simple` objeto.  
  
    ```c#  
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
  
3.  En MyToolWindowControl.cs, reemplace los controladores de la casilla de verificación con estas líneas de código:  
  
    ```c#  
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
  
6.  Active la casilla de verificación en la **MyToolWindow** ventana. El **propiedades** ventana muestra la `Simple` Propiedades, del objeto **SomeText** y **ReadOnly**. Desactive la casilla de verificación. Las propiedades públicas de la ventana que aparecen en la **propiedades** ventana.  
  
    > [!NOTE]
    >  El nombre para mostrar de **SomeText** es **Mi texto**.  
  
## Práctica recomendada  
 En este tutorial, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> se implementa para que la colección de objetos seleccionables y la colección de objetos seleccionados son la misma colección. Sólo el objeto seleccionado aparece en la lista del explorador de propiedades. Para una implementación de ISelectionContainer más completada, vea los ejemplos de Reference.ToolWindow.  
  
 Ventanas de herramientas de Visual Studio se conservan entre sesiones de Visual Studio. Para obtener más información sobre la conservación del estado de la ventana de herramienta, consulte <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## Vea también  
 [Extender propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)