---
title: Exponer propiedades a la ventana Propiedades | Microsoft Docs
description: Obtenga información sobre las propiedades públicas de un objeto . Los cambios realizados en estas propiedades se reflejan en el ventana Propiedades.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5f932772b031332d7df2a2487c70576f49407ba1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898742"
---
# <a name="expose-properties-to-the-properties-window"></a>Exponer propiedades a la ventana Propiedades

En este tutorial se exponen las propiedades públicas de un objeto en la **ventana** Propiedades. Los cambios realizados en estas propiedades se reflejan en la **ventana** Propiedades.

## <a name="prerequisites"></a>Requisitos previos

A partir Visual Studio 2015, no se instala el SDK Visual Studio desde el centro de descarga. Se incluye como una característica opcional en Visual Studio configuración. También puede instalar el SDK de VS después. Para más información, consulte [Instalación del SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="expose-properties-to-the-properties-window"></a>Exponer propiedades a la ventana Propiedades

En esta sección, creará una ventana de herramientas personalizada y mostrará las propiedades públicas del objeto de panel de ventana asociado en la **ventana** Propiedades.

### <a name="to-expose-properties-to-the-properties-window"></a>Para exponer propiedades a la ventana Propiedades

1. Cada Visual Studio extensión comienza con un proyecto de implementación de VSIX, que contendrá los recursos de extensión. Cree un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto VSIX denominado `MyObjectPropertiesExtension` . Puede encontrar la plantilla de proyecto VSIX en el **cuadro de diálogo Nuevo** proyecto buscando "vsix".

2. Agregue una ventana de herramientas agregando una plantilla de elemento de ventana de herramientas personalizada denominada `MyToolWindow` . En la **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto y **seleccione Agregar** nuevo  >  **elemento**. En el **cuadro de diálogo Agregar nuevo elemento**, vaya a Extensibilidad de elementos de Visual **C#**  >   y seleccione Ventana de **herramientas personalizadas**. En el **campo** Nombre de la parte inferior del cuadro de diálogo, cambie el nombre de archivo a *MyToolWindow.cs.* Para obtener más información sobre cómo crear una ventana de herramientas personalizada, vea [Crear una extensión con una ventana de herramientas.](../extensibility/creating-an-extension-with-a-tool-window.md)

3. Abra *MyToolWindow.cs y* agregue la siguiente instrucción using:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Ahora agregue los campos siguientes a la `MyToolWindow` clase .

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

    La `TrackSelection` propiedad usa para obtener un `GetService` `STrackSelection` servicio, que proporciona una interfaz <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> . El `OnToolWindowCreated` controlador de eventos y el método crean `SelectList` juntos una lista de objetos seleccionados que contiene solo el propio objeto del panel de ventana de herramientas. El `UpdateSelection` método indica a la **ventana** Propiedades que muestre las propiedades públicas del panel de la ventana de herramientas.

6. Compile la solución y comience la depuración. La instancia experimental de Visual Studio debe aparecer.

7. Si la **ventana** Propiedades no está visible, ábrala presionando **F4**.

8. Abra la **ventana MyToolWindow.** Puede encontrarlo en **Ver**  >  **otras ventanas.**

    Se abre la ventana y las propiedades públicas del panel de ventana aparecen en la **ventana** Propiedades.

9. Cambie la **propiedad Caption** de la **ventana Propiedades** a Propiedades de **mi objeto**.

     El título de la ventana MyToolWindow cambia en consecuencia.

## <a name="expose-tool-window-properties"></a>Exponer las propiedades de la ventana de herramientas

En esta sección, agregará una ventana de herramientas y expondrá sus propiedades. Los cambios realizados en las propiedades se reflejan en la **ventana** Propiedades.

### <a name="to-expose-tool-window-properties"></a>Para exponer las propiedades de la ventana de herramientas

1. Abra *MyToolWindow.cs* y agregue la propiedad booleana pública IsChecked a la `MyToolWindow` clase .

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

     Esta propiedad obtiene su estado de la casilla WPF que creará más adelante.

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

     Esto proporciona `MyToolWindowControl` acceso al `MyToolWindow` panel.

3. En *MyToolWindow.cs,* cambie el `MyToolWindow` constructor de la siguiente manera:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. Cambie a la vista de diseño de MyToolWindowControl.

5. Elimine el botón y agregue una casilla del Cuadro de **herramientas** a la esquina superior izquierda.

6. Agregue los eventos Checked y Unchecked. Active la casilla en la vista de diseño. En la **ventana** Propiedades, haga clic en el botón controladores de eventos (en la parte superior derecha de la **ventana** Propiedades). Busque Checked **(Activado) y escriba checkbox_Checked** en el cuadro de texto y, a continuación, busque **Unchecked** **(Desactivado) y escriba checkbox_Unchecked** en el cuadro de texto. 

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

9. En la instancia experimental, abra la **ventana MyToolWindow.**

     Busque las propiedades de la ventana en la **ventana** Propiedades. La **propiedad IsChecked** aparece en la parte inferior de la ventana, en la **categoría Mis** propiedades.

10. Active la casilla en la **ventana MyToolWindow.** **IsChecked en** la **ventana Propiedades** cambia a **True.** Desactive la casilla en la **ventana MyToolWindow.** **IsChecked en** la **ventana Propiedades** cambia a **False.** Cambie el valor de **IsChecked en** la **ventana** Propiedades. La casilla de la **ventana MyToolWindow** cambia para que coincida con el nuevo valor.

    > [!NOTE]
    > Si debe eliminar un objeto que se muestra en la ventana **Propiedades,** llame `OnSelectChange` primero a con un contenedor de `null` selección. Después de eliminar la propiedad u objeto, puede cambiar a un contenedor de selección que haya actualizado <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> las listas y <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> .

## <a name="change-selection-lists"></a>Cambiar listas de selección

 En esta sección, agregará una lista de selección para una clase de propiedad básica y usará la interfaz de la ventana de herramientas para elegir la lista de selección que se va a mostrar.

### <a name="to-change-selection-lists"></a>Para cambiar las listas de selección

1. Abra *MyToolWindow.cs y* agregue una clase pública denominada `Simple` .

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

2. Agregue una propiedad a la clase , más dos métodos para cambiar la selección de la ventana `SimpleObject` Propiedades entre el panel de ventana y el objeto `MyToolWindow`  `Simple` .

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

3. En *MyToolWindowControl.cs,* reemplace los controladores de casilla por estas líneas de código:

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

5. En la instancia experimental, abra la **ventana MyToolWindow.**

6. Active la casilla en la **ventana MyToolWindow.** La **ventana** Propiedades muestra las `Simple` propiedades del objeto, **SomeText** y **ReadOnly.** Desactive la casilla. Las propiedades públicas de la ventana aparecen en la **ventana** Propiedades.

    > [!NOTE]
    > El nombre para mostrar **de SomeText** es **My Text**.

## <a name="best-practice"></a>Procedimiento recomendado

En este tutorial, se implementa para que la colección de objetos seleccionables y la colección de objetos <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> seleccionados sean la misma colección. Solo el objeto seleccionado aparece en la lista Explorador de propiedades. Para obtener una implementación más completa de ISelectionContainer, vea los ejemplos de Reference.ToolWindow.

Visual Studio ventanas de herramientas persistentes entre Visual Studio sesión. Para obtener más información sobre cómo conservar el estado de la ventana de herramientas, vea <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> .

## <a name="see-also"></a>Consulta también

- [Extensión de las propiedades y la ventana Propiedad](../extensibility/extending-properties-and-the-property-window.md)
