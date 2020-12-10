---
title: Exponer propiedades en la ventana Propiedades | Microsoft Docs
description: Obtenga información sobre las propiedades públicas de un objeto. Los cambios que realice en estas propiedades se reflejarán en el ventana Propiedades.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6f2668f8410b6e5f18b23c82202c1d33f8c67b4d
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994698"
---
# <a name="expose-properties-to-the-properties-window"></a>Exponga propiedades a la ventana Propiedades

En este tutorial se exponen las propiedades públicas de un objeto en la ventana **propiedades** . Los cambios que realice en estas propiedades se reflejarán en la ventana **propiedades** .

## <a name="prerequisites"></a>Prerrequisitos

A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="expose-properties-to-the-properties-window"></a>Exponga propiedades a la ventana Propiedades

En esta sección, creará una ventana de herramientas personalizada y mostrará las propiedades públicas del objeto panel de ventana asociado en la ventana **propiedades** .

### <a name="to-expose-properties-to-the-properties-window"></a>Para exponer propiedades a la ventana Propiedades

1. Cada extensión de Visual Studio comienza con un proyecto de implementación de VSIX, que contendrá los recursos de la extensión. Cree un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Proyecto VSIX denominado `MyObjectPropertiesExtension` . Para buscar la plantilla de Proyecto VSIX en el cuadro de diálogo **nuevo proyecto** , busque "VSIX".

2. Agregue una ventana de herramientas agregando una plantilla de elemento de ventana de herramientas personalizada denominada `MyToolWindow` . En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar**  >  **nuevo elemento**. En el **cuadro de diálogo Agregar nuevo elemento**, vaya a la extensibilidad de **elementos de Visual C#**  >   y seleccione **ventana de herramientas personalizada**. En el campo **nombre** situado en la parte inferior del cuadro de diálogo, cambie el nombre del archivo a *MyToolWindow.CS*. Para obtener más información sobre cómo crear una ventana de herramientas personalizada, vea [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Abra *MyToolWindow.CS* y agregue la siguiente instrucción using:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Ahora, agregue los siguientes campos a la `MyToolWindow` clase.

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

    La `TrackSelection` propiedad utiliza `GetService` para obtener un `STrackSelection` servicio, que proporciona una <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfaz. El `OnToolWindowCreated` controlador de eventos y el `SelectList` método juntos crean una lista de objetos seleccionados que solo contiene el propio objeto de panel de la ventana de herramientas. El `UpdateSelection` método indica a la ventana **propiedades** que muestre las propiedades públicas del panel de la ventana de herramientas.

6. Compile la solución y comience la depuración. Debería aparecer la instancia experimental de Visual Studio.

7. Si la ventana **propiedades** no está visible, ábrala presionando **F4**.

8. Abra la ventana **MyToolWindow** . Puede encontrarlo en **Ver**  >  **otras ventanas**.

    La ventana se abre y las propiedades públicas del panel de ventana aparecen en la ventana **propiedades** .

9. Cambie la propiedad **título** de la ventana **propiedades** a **mis propiedades del objeto**.

     El título de la ventana MyToolWindow cambia en consecuencia.

## <a name="expose-tool-window-properties"></a>Exponer propiedades de la ventana de herramientas

En esta sección, agregará una ventana de herramientas y expondrá sus propiedades. Los cambios que realice en las propiedades se reflejarán en la ventana **propiedades** .

### <a name="to-expose-tool-window-properties"></a>Para exponer las propiedades de la ventana de herramientas

1. Abra *MyToolWindow.CS* y agregue la propiedad booleana pública isChecked a la `MyToolWindow` clase.

    ```csharp
    [Category("My Properties")]
    [Description("MyToolWindowControl properties")]
    public bool IsChecked
    {
        get {
            if (base.Content == null)  return false;
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;
        }
        set {
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;
        }
    }
    ```

     Esta propiedad obtiene su estado de la casilla de WPF que se creará más adelante.

2. Abra *MyToolWindowControl.Xaml.CS* y reemplace el constructor MyToolWindowControl por el código siguiente.

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     Esto proporciona `MyToolWindowControl` acceso al `MyToolWindow` panel.

3. En *MyToolWindow.CS*, cambie el `MyToolWindow` constructor de la siguiente manera:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. Cambie a la vista de diseño de MyToolWindowControl.

5. Elimine el botón y agregue una casilla de verificación del **cuadro de herramientas** a la esquina superior izquierda.

6. Agregue los eventos Checked y Unchecked. Active la casilla en la vista de diseño. En la ventana **propiedades** , haga clic en el botón controladores de eventos (en la parte superior derecha de la ventana **propiedades** ). Busque **activada** y escriba **checkbox_Checked** en el cuadro de texto, busque **desactivada** y escriba **checkbox_Unchecked** en el cuadro de texto.

7. Agregue los controladores de eventos de casilla:

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

9. En la instancia experimental, abra la ventana **MyToolWindow** .

     Busque las propiedades de la ventana en la ventana **propiedades** . La propiedad **isChecked** aparece en la parte inferior de la ventana, en la categoría **mis propiedades** .

10. Active la casilla en la ventana **MyToolWindow** . **IsChecked** en la ventana **propiedades** cambia a **true**. Desactive la casilla de la ventana **MyToolWindow** . **IsChecked** en la ventana **propiedades** cambia a **false**. Cambie el valor de **isChecked** en la ventana **propiedades** . La casilla de la ventana **MyToolWindow** cambia para que coincida con el nuevo valor.

    > [!NOTE]
    > Si debe desechar un objeto que se muestra en la ventana **propiedades** , llame `OnSelectChange` primero a con un `null` contenedor de selección. Después de desechar la propiedad o el objeto, puede cambiar a un contenedor de selección que tenga actualizadas <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> y <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> listas.

## <a name="change-selection-lists"></a>Cambiar listas de selección

 En esta sección, agregará una lista de selección para una clase de propiedad básica y utilizará la interfaz de la ventana de herramientas para elegir la lista de selección que se va a mostrar.

### <a name="to-change-selection-lists"></a>Para cambiar las listas de selección

1. Abra *MyToolWindow.CS* y agregue una clase pública denominada `Simple` .

    ```csharp
    public class Simple
    {
        private string someText = "";

        [Category("My Properties")]
        [Description("Simple Properties")]
        [DisplayName("My Text")]
        public string SomeText
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

2. Agregue una `SimpleObject` propiedad a la `MyToolWindow` clase, además de dos métodos para cambiar la selección de la ventana **propiedades** entre el panel de ventana y el `Simple` objeto.

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

3. En *MyToolWindowControl.CS*, reemplace los controladores de casilla por estas líneas de código:

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

5. En la instancia experimental, abra la ventana **MyToolWindow** .

6. Active la casilla en la ventana **MyToolWindow** . La ventana **propiedades** muestra las `Simple` propiedades del objeto, **SomeText** y **ReadOnly**. Desactive la casilla. Las propiedades públicas de la ventana aparecen en la ventana **propiedades** .

    > [!NOTE]
    > El nombre para mostrar de **SomeText** es **mi texto**.

## <a name="best-practice"></a>Procedimiento recomendado

En este tutorial, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> se implementa de forma que la colección de objetos seleccionable y la colección de objetos seleccionada sean la misma colección. Solo aparece el objeto seleccionado en la lista de exploradores de propiedades. Para obtener una implementación de ISelectionContainer más completa, vea los ejemplos de Reference. ToolWindow.

Las ventanas de herramientas de Visual Studio se conservan entre las sesiones de Visual Studio. Para obtener más información sobre cómo conservar el estado de la ventana de herramientas, vea <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> .

## <a name="see-also"></a>Consulte también

- [Extender propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)
