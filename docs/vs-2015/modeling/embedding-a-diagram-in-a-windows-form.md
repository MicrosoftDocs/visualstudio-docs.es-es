---
title: Incrustación de un diagrama en un formulario de Windows | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 440b60697d4ab1e88f535b6c5ef824bc74e19c48
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203420"
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Incrustar diagramas en Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede insertar un diagrama DSL en un Control de Windows, que aparece en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ventana.  
  
## <a name="embedding-a-diagram"></a>Incrustación de un diagrama  
  
#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Para incrustar un diagrama DSL en un Control de Windows  
  
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
    private MyDSLDSLDocView docView;  
  
    ```  
  
4. Agregue un nuevo archivo al proyecto DslPackage, con el siguiente contenido:  
  
    ```  
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
  
5. Para probar el DSL, presione F5 y abrir un archivo de modelo de ejemplo. El diagrama aparece dentro del control. El cuadro de herramientas y otras características funcionan con normalidad.  
  
#### <a name="updating-the-form-using-store-events"></a>Actualizar el formulario con los eventos de Store  
  
1. En el Diseñador de formularios, agregue un **ListBox** denominado `listBox1`. Esto mostrará una lista de los elementos del modelo. Se conservará en synchronism con el modelo mediante *almacenar eventos*. Para obtener más información, consulte [controladores propagar los cambios fuera el modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
2. En el archivo de código personalizado, invalide aún más métodos a la clase DocView:  
  
    ```  
  
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
  
    ```  
  
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
  
4. Para probar el DSL, presione F5 y, en la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], abra un archivo de modelo de ejemplo.  
  
     Tenga en cuenta que el cuadro de lista muestra una lista de los elementos en el modelo y que es correcta después de cualquier adición o eliminación y deshacer y rehacer.  
  
## <a name="see-also"></a>Vea también  
 [Navegar y actualizar un modelo en el código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
