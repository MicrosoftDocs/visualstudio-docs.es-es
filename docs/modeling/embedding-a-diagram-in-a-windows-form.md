---
title: Incrustar un diagrama en un formulario Windows Forms | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: a19aef7cc11e7db1e04a6f54e4438f74227a55ee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Incrustar diagramas en Windows Forms
Puede incrustar un diagrama DSL de un Control de Windows, que aparece en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ventana.  
  
## <a name="embedding-a-diagram"></a>Incrustar un diagrama  
  
#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Para incrustar un diagrama DSL en un Control de Windows  
  
1.  Agregue un nuevo **Control de usuario** archivo al proyecto de DslPackage.  
  
2.  Agregar un control Panel para el Control de usuario. Este panel contiene el diagrama de DSL.  
  
     Agregar otros controles que necesite.  
  
     Establecer las propiedades de anclaje de los controles.  
  
3.  En el Explorador de soluciones, haga clic en el archivo de control de usuario y haga clic en **ver código**. Agregue este constructor y la variable en el código:  
  
    ```csharp  
  
    internal UserControl1(MyDSLDocView docView, Control content)  
      : this()  
    {  
      panel1.Controls.Add(content);  
      this.docView = docView;  
    }  
    private MyDSLDSLDocView docView;  
  
    ```  
  
4.  Agregue un nuevo archivo al proyecto DslPackage, con el siguiente contenido:  
  
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
  
5.  Para probar el ADSL, presione F5 y abrir un archivo de modelo de ejemplo. El diagrama aparece dentro del control. El cuadro de herramientas y otras características funcionan con normalidad.  
  
#### <a name="updating-the-form-using-store-events"></a>Actualizar el formulario con el almacén de eventos  
  
1.  En el Diseñador de formularios, agregar un **ListBox** denominado `listBox1`. Se mostrará una lista de los elementos en el modelo. Se mantendrán en synchronism con el modelo con *almacenar eventos*. Para obtener más información, consulte [controladores propagar cambios fuera el modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
2.  En el archivo de código personalizado, invalide más métodos a la clase DocView:  
  
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
  
3.  En el código subyacente del control de usuario, inserte métodos para realizar escuchas de los elementos agregados y quitados:  
  
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
  
4.  Para probar el ADSL, presione F5 y en la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], abra un archivo de modelo de ejemplo.  
  
     Observe que el cuadro de lista muestra una lista de los elementos en el modelo, y que es correcta tras cualquier adición o eliminación y después de deshacer y rehacer.  
  
## <a name="see-also"></a>Vea también  
 [Navegar y actualizar un modelo de código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)