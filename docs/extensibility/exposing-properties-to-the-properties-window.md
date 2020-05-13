---
title: Exponer propiedades a la ventana Propiedades ? Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f84962628ae550676e2c2eeb10c0f3baeca1bb58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711827"
---
# <a name="expose-properties-to-the-properties-window"></a>Exponer propiedades a la ventana Propiedades

Este tutorial expone las propiedades públicas de un objeto a la **propiedades** ventana. Los cambios realizados en estas propiedades se reflejan en la ventana **Propiedades.**

## <a name="prerequisites"></a>Prerrequisitos

A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="expose-properties-to-the-properties-window"></a>Exponer propiedades a la ventana Propiedades

En esta sección, creará una ventana de herramientas personalizada y mostrará las propiedades públicas del objeto de panel de ventana asociado en la ventana **Propiedades.**

### <a name="to-expose-properties-to-the-properties-window"></a>Para exponer propiedades a la ventana Propiedades

1. Cada extensión de Visual Studio comienza con un proyecto de implementación de VSIX, que contendrá los activos de extensión. Cree [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un proyecto `MyObjectPropertiesExtension`VSIX denominado . Puede encontrar la plantilla de proyecto VSIX en el cuadro de diálogo **Nuevo proyecto** buscando "vsix".

2. Agregue una ventana de herramientas agregando `MyToolWindow`una plantilla de elemento de ventana de herramientas personalizada denominada . En el **Explorador**de soluciones , haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar** > **nuevo elemento**. En el cuadro de **diálogo Agregar nuevo elemento**, vaya a**Extensibilidad** de elementos > de **Visual C.** y seleccione Ventana de **herramientas personalizadas**. En el campo **Nombre** en la parte inferior del cuadro de diálogo, cambie el nombre del archivo a *MyToolWindow.cs*. Para obtener más información sobre cómo crear una ventana de herramientas personalizada, consulte [Crear una extensión con una ventana](../extensibility/creating-an-extension-with-a-tool-window.md)de herramientas .

3. Abra *MyToolWindow.cs* y agregue la siguiente instrucción using:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Ahora agregue los siguientes `MyToolWindow` campos a la clase.

   ```csharp
   private ITrackSelection trackSel;
   private SelectionContainer selContainer;

   ```

5. Agregue el siguiente código a la clase `MyToolWindow` .

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

   public void UpdateSelection()
   {
       ITrackSelection track = TrackSelection;
       if (track != null)
           track.OnSelectChange((ISelectionContainer)selContainer);
   }

   public void SelectList(ArrayList list)
   {
       selContainer = new SelectionContainer(true, false);
       selContainer.SelectableObjects = list;
       selContainer.SelectedObjects = list;
       UpdateSelection();
   }

   public override void OnToolWindowCreated()
   {
       ArrayList listObjects = new ArrayList();
       listObjects.Add(this);
       SelectList(listObjects);
   }
   ```

    La `TrackSelection` propiedad `GetService` se `STrackSelection` utiliza para obtener <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> un servicio, que proporciona una interfaz. El `OnToolWindowCreated` controlador `SelectList` de eventos y el método juntos crean una lista de objetos seleccionados que contiene solo el propio objeto de panel de la ventana de herramientas. El `UpdateSelection` método indica a la ventana **Propiedades** que muestre las propiedades públicas del panel de la ventana de herramientas.

6. Compile la solución y comience la depuración. Debería aparecer la instancia experimental de Visual Studio.

7. Si la ventana **Propiedades** no está visible, ábrala pulsando **F4**.

8. Abra la ventana **MyToolWindow.** Puede encontrarlo en **Ver** > **otras ventanas**.

    Se abre la ventana y las propiedades públicas del panel de la ventana aparecen en la ventana **Propiedades.**

9. Cambie la propiedad **Título** de la ventana **Propiedades** a **Propiedades de mi objeto**.

     El título de la ventana MyToolWindow cambia en consecuencia.

## <a name="expose-tool-window-properties"></a>Exponer las propiedades de la ventana de herramientas

En esta sección, agregará una ventana de herramientas y expone sus propiedades. Los cambios realizados en las propiedades se reflejan en la ventana **Propiedades.**

### <a name="to-expose-tool-window-properties"></a>Para exponer las propiedades de la ventana de herramientas

1. Abra *MyToolWindow.cs*y agregue la propiedad booleana pública IsChecked a la `MyToolWindow` clase.

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

     Esta propiedad obtiene su estado de la casilla de verificación WPFque creará más adelante.

2. Abra *MyToolWindowControl.xaml.cs* y reemplace el constructor MyToolWindowControl por el código siguiente.

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     Esto `MyToolWindowControl` da acceso `MyToolWindow` al panel.

3. En *MyToolWindow.cs*, `MyToolWindow` cambie el constructor de la siguiente manera:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. Cambie a la vista de diseño de MyToolWindowControl.

5. Elimine el botón y agregue una casilla de verificación del Cuadro de **herramientas** a la esquina superior izquierda.

6. Agregue los eventos Checked y Unchecked. Seleccione la casilla de verificación en la vista de diseño. En la ventana **Propiedades,** haga clic en el botón Controladores de eventos (en la parte superior derecha de la ventana **Propiedades).** Busque **Checked** y escriba **checkbox_Checked** en el cuadro de texto y, a continuación, busque **Unchecked** y escriba **checkbox_Unchecked** en el cuadro de texto.

7. Agregue los controladores de eventos de casilla de verificación:

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

8. Compile la solución y comience la depuración.

9. En la instancia experimental, abra la ventana **MyToolWindow.**

     Busque las propiedades de la ventana en la ventana **Propiedades.** La propiedad **IsChecked** aparece en la parte inferior de la ventana, en la categoría **Mis propiedades.**

10. Active la casilla de verificación en la ventana **MyToolWindow.** **IsChecked** en la ventana **Propiedades** cambia a **True**. Desactive la casilla de verificación de la ventana **MyToolWindow.** **IsChecked** en la ventana **Propiedades** cambia a **False**. Cambie el valor de **IsChecked** en la ventana **Propiedades.** La casilla de verificación de la ventana **MyToolWindow** cambia para que coincida con el nuevo valor.

    > [!NOTE]
    > Si debe eliminar un objeto que se muestra en `OnSelectChange` la `null` ventana **Propiedades,** llame primero con un contenedor de selección. Después de desechar la propiedad u objeto, <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> puede <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> cambiar a un contenedor de selección que se haya actualizado y enumera.

## <a name="change-selection-lists"></a>Cambiar listas de selección

 En esta sección, agregará una lista de selección para una clase de propiedad básica y utilizará la interfaz de la ventana de herramientas para elegir la lista de selección que desea mostrar.

### <a name="to-change-selection-lists"></a>Para cambiar las listas de selección

1. Abra *MyToolWindow.cs* y agregue `Simple`una clase pública denominada .

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

2. Agregue `SimpleObject` una propiedad `MyToolWindow` a la clase, además de dos métodos para cambiar la selección de la ventana **Propiedades** entre el panel de la ventana y el `Simple` objeto.

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

3. En *MyToolWindowControl.cs*, reemplace los controladores de casilla de verificación por estas líneas de código:

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

4. Compile la solución y comience la depuración.

5. En la instancia experimental, abra la ventana **MyToolWindow.**

6. Active la casilla de verificación en la ventana **MyToolWindow.** La **Properties** ventana Propiedades `Simple` muestra las propiedades del objeto, **SomeText** y **ReadOnly**. Desactive la casilla. Las propiedades públicas de la ventana aparecen en la ventana **Propiedades.**

    > [!NOTE]
    > El nombre para mostrar de **SomeText** es **Mi texto**.

## <a name="best-practice"></a>Procedimiento recomendado

En este <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> tutorial, se implementa para que la colección de objetos seleccionables y la colección de objetos seleccionados sean la misma colección. Solo el objeto seleccionado aparece en la lista Navegador de propiedades. Para obtener una implementación más completa de ISelectionContainer, vea el Reference.ToolWindow ejemplos.

Las ventanas de herramientas de Visual Studio persisten entre sesiones de Visual Studio. Para obtener más información sobre cómo <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>conservar el estado de la ventana de herramientas, consulte .

## <a name="see-also"></a>Vea también

- [Extender propiedades y la ventana Propiedad](../extensibility/extending-properties-and-the-property-window.md)
