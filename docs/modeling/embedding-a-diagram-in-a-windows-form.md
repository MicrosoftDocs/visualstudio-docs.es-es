---
title: Incrustar diagramas en Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b2ed12175e986178d43ffe5e3da8b85e2ab22e5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044698"
---
# <a name="embed-a-diagram-in-a-windows-form"></a>Insertar un diagrama en Windows Forms

Puede insertar un diagrama DSL en un control de Windows, que aparece en la ventana de Visual Studio.

## <a name="embed-a-dsl-diagram-in-a-windows-control"></a>Incrustar un diagrama DSL en un control de Windows

1. Agregue un nuevo **Control de usuario** archivo al proyecto DslPackage.

2. Agregue un control de Panel para el Control de usuario. Este panel contendrá el diagrama DSL.

     Agregue otros controles que necesite.

     Establecer las propiedades de delimitador de los controles.

3. En el Explorador de soluciones, haga clic en el archivo de control de usuario y haga clic en **ver código**. Agregue este constructor y la variable en el código:

    ```csharp
    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;
    ```

4. Agregue un nuevo archivo al proyecto DslPackage, con el siguiente contenido:

    ```csharp
    using System.Windows.Forms;
    namespace Company.MyDSL
    {
      partial class MyDSLDocView
      {
        private UserControl1 container;
        public override IWin32Window Window
        {
          get
          {
            if (container == null)
            {
              // Put our own form inside the DSL window:
              container = new UserControl1(this,
                (Control)base.Window);
            }
            return container;
    } } } }
    ```

5. Para probar el DSL, presione **F5** y abrir un archivo de modelo de ejemplo. El diagrama aparece dentro del control. El cuadro de herramientas y otras características funcionan con normalidad.

## <a name="update-the-form-using-store-events"></a>Actualizar el formulario con el almacén de eventos

1. En el Diseñador de formularios, agregue un **ListBox** denominado `listBox1`. Esto mostrará una lista de los elementos del modelo. Que se sincronice con el modelo mediante *almacenar eventos*. Para obtener más información, consulte [controladores propagar los cambios fuera el modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2. En el archivo de código personalizado, invalide aún más métodos a la clase DocView:

    ```csharp
    partial class MyDSLDocView
    {
     /// <summary>
     /// Register store event listeners.
     /// This method is called when the model and diagram
     /// have completed loading.
     /// </summary>
     protected override bool LoadView()
      {
        bool result = base.LoadView();
        Store store = this.DocData.Store;
        EventManagerDirectory emd = store.EventManagerDirectory;
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));

        // Do the initial parts list:
        container.SetUpFormFromModel();
        return result;
      }
     /// <summary>
     /// Listener method called on creation of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void AddElement(object sender, ElementAddedEventArgs e)
     {
       container.Add(e.ModelElement as ExampleElement);
     }
     /// <summary>
     /// Listener method called after deletion of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void RemoveElement(object sender, ElementDeletedEventArgs e)
     {
       container.Remove(e.ModelElement as ExampleElement);
     }
    ```

3. En el código subyacente del control de usuario, inserte los métodos para realizar escuchas para los elementos agregados y quitados:

    ```csharp
    public partial class UserControl1 : UserControl { ...

    private ExampleModel modelRoot;

    internal void Add(ExampleElement e) { UpdatePartsList(); }
    internal void Remove(ExampleElement e) { UpdatePartsList(); }

    internal void SetUpFormFromModel()
    {
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      UpdatePartsList();
    }

    private void UpdatePartsList()
    {
      StringBuilder builder = new StringBuilder();
      listBox1.Items.Clear();
      foreach (ExampleElement c in modelRoot.Elements)
      {
        listBox1.Items.Add(c.Name);
      }
    }
    ```

4. Para probar el DSL, presione **F5** y en la instancia experimental de Visual Studio, abra un archivo de modelo de ejemplo.

     Tenga en cuenta que el cuadro de lista muestra una lista de los elementos en el modelo y que es correcta después de cualquier adición o eliminación y deshacer y rehacer.

## <a name="see-also"></a>Vea también

- [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
