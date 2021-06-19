---
title: Incrustar diagramas en Windows Forms
description: Obtenga información sobre cómo insertar un diagrama de DSL en un control de Windows, que aparece en la Visual Studio anterior.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4db60267b835882a69a08c990af644b902697bad
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388989"
---
# <a name="embed-a-diagram-in-a-windows-form"></a>Insertar un diagrama en Windows Forms

Puede insertar un diagrama de DSL en un control de Windows, que aparece en la Visual Studio anterior.

## <a name="embed-a-dsl-diagram-in-a-windows-control"></a>Inserción de un diagrama dsl en un control de Windows

1. Agregue un nuevo **archivo de control de** usuario al proyecto DslPackage.

2. Agregue un control Panel al Control de usuario. Este panel contendrá el diagrama de DSL.

     Agregue otros controles que necesite.

     Establezca las propiedades Delimitador de los controles.

3. En Explorador de soluciones, haga clic con el botón derecho en el archivo de control de usuario y haga clic **en Ver código.** Agregue este constructor y variable al código:

    ```csharp
    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;
    ```

4. Agregue un nuevo archivo al proyecto DslPackage con el siguiente contenido:

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

5. Para probar el DSL, presione **F5** y abra un archivo de modelo de ejemplo. El diagrama aparece dentro del control . El cuadro de herramientas y otras características funcionan normalmente.

## <a name="update-the-form-using-store-events"></a>Actualización del formulario mediante eventos de almacén

1. En el diseñador de formularios, agregue un **ListBox** denominado `listBox1` . Se mostrará una lista de los elementos del modelo. Se sincroniza con el modelo mediante eventos *de almacén*. Para obtener más información, vea [Controladores de eventos Propagar cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2. En el archivo de código personalizado, invalide otros métodos para la clase DocView:

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

3. En el código subyacente al control de usuario, inserte métodos para escuchar los elementos agregados y quitados:

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

4. Para probar el DSL, presione **F5** y, en la instancia experimental de Visual Studio, abra un archivo de modelo de ejemplo.

     Observe que el cuadro de lista muestra una lista de los elementos del modelo y que es correcta después de cualquier adición o eliminación, y después de Deshacer y Rehacer.

## <a name="see-also"></a>Vea también

- [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
