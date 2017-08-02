---
title: "Creación de un lenguaje específico de dominio basada en formularios de Windows | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 452318ff-8ecf-46d0-8ca0-4013d0cdafaf
caps.latest.revision: 17
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c9caf1da3e6e9d065a94e6b12b7699cd5a381ea2
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>Crear lenguajes específicos de dominio basados en Windows Forms
Puede utilizar los formularios Windows Forms para mostrar el estado de un modelo de lenguaje específico de dominio (DSL), en lugar de utilizar un diagrama DSL. Este tema le guiará a través de enlazar un formulario Windows Forms a un DSL, usando la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK de visualización y modelado.  
  
 ![2 de Wpf de DSL](~/docs/modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  
Una instancia DSL, que muestra una interfaz de usuario del formulario de Windows y el Explorador de modelos.  
  
## <a name="creating-a-windows-forms-dsl"></a>Crear un DSL de Windows Forms  
 El **Diseñador de WinForm mínimo** plantilla DSL crea un DSL mínimo que puede modificar para satisfacer sus propias necesidades.  
  
#### <a name="to-create-a-minimal-winforms-dsl"></a>Para crear un DSL de WinForms mínima  
  
1.  Crear un DSL desde el **Diseñador de WinForm mínimo** plantilla.  
  
     En este tutorial se supone que los nombres siguientes:  
  
    |||  
    |-|-|  
    |Nombre de la solución y DSL|FarmApp|  
    |Espacio de nombres|Company.FarmApp|  
  
2.  Experimentar con el ejemplo inicial que proporciona la plantilla:  
  
    1.  Transformar todas las plantillas.  
  
    2.  Compilar y ejecutar el ejemplo (**CTRL+F5**).  
  
    3.  En la instancia experimental de Visual Studio, abra el `Sample` archivo del proyecto de depuración.  
  
         Observe que se muestra en un control de formularios Windows Forms.  
  
         También puede ver los elementos del modelo que se muestra en el explorador.  
  
         Agregar algunos elementos en el formulario o en el explorador y observe que aparecen en la otra pantalla.  
  
 En la instancia principal de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], tenga en cuenta los siguientes puntos acerca de la solución de DSL:  
  
-   `DslDefinition.dsl`no contiene ningún elemento del diagrama. Esto es porque no usará los diagramas DSL para ver los modelos de la instancia de este DSL. En su lugar, se enlaza un formulario Windows Forms con el modelo y los elementos en el formulario mostrarán el modelo.  
  
-   Además el `Dsl` y `DslPackage` proyectos, la solución contiene un tercer proyecto denominado `UI.` **UI** proyecto contiene la definición de un control de formularios Windows Forms. `DslPackage`depende de `UI`, y `UI` depende de `Dsl`.  
  
-   En el `DslPackage` proyecto `UI\DocView.cs` contiene el código que muestra el control de formularios Windows Forms que se define en el `UI` proyecto.  
  
-   El `UI` proyecto contiene un ejemplo funcional de un control de formulario enlazado a la línea ADSL. Sin embargo, no funcionará cuando ha cambiado la definición de DSL. El `UI` proyecto contiene:  
  
    -   Una clase de formularios Windows Forms denominada `ModelViewControl`.  
  
    -   Un archivo denominado `DataBinding.cs` que contiene una definición parcial adicional de `ModelViewControl`. Para ver su contenido en **el Explorador de soluciones**, abra el menú contextual para el archivo y elija **ver código**.  
  
### <a name="about-the-ui-project"></a>Acerca del proyecto de la interfaz de usuario  
 Cuando se actualiza el archivo de definición de DSL para definir su propio DSL, tendrá que actualizar el control en el `UI` proyecto para mostrar su DSL. A diferencia de la `Dsl` y `DslPackage` proyectos, el ejemplo `UI` proyecto no se genera desde `DslDefinitionl.dsl`. Puede agregar .tt (archivos) para generar el código si lo desea, aunque no se trata en este tutorial.  
  
## <a name="updating-the-dsl-definition"></a>Actualice la definición de DSL  
 La siguiente que definición de DSL se utiliza en este tutorial.  
  
 ![DSL-Wpf-1](~/docs/modeling/media/dsl-wpf-1.png "DSL-Wpf-1")  
  
#### <a name="to-update-the-dsl-definition"></a>Para actualizar la definición de DSL  
  
1.  Abra DslDefinition.dsl en el diseñador DSL.  
  
2.  Eliminar **ExampleElement**  
  
3.  Cambiar el nombre de la **ExampleModel** clase de dominio `Farm`.  
  
     Proporcionar propiedades de dominio adicional denominados `Size` de tipo **Int32**, y `IsOrganic` de tipo **booleano**.  
  
    > [!NOTE]
    >  Si elimina la clase de dominio raíz y, a continuación, crear una nueva raíz, tendrá que restablecer la propiedad de clase de raíz del Editor. En **DSL Explorer**, seleccione **Editor**. A continuación, en la ventana Propiedades, establezca **clase raíz** a `Farm`.  
  
4.  Utilice la **con el nombre de clase de dominio** herramienta para crear las clases de dominio siguientes:  
  
    -   `Field`– Ponerle una propiedad de dominio adicional denominada `Size`.  
  
    -   `Animal`En la ventana Propiedades, establezca **modificador de herencia** a **abstracta**.  
  
5.  Utilice la **clase de dominio** herramienta para crear las clases siguientes:  
  
    -   `Sheep`  
  
    -   `Goat`  
  
6.  Utilice la **herencia** herramienta para realizar `Goat` y `Sheep` heredan de `Animal`.  
  
7.  Utilice la **Embedding** herramienta incrustar `Field` y `Animal` en `Farm`.  
  
8.  Puede ordenar el diagrama. Para reducir el número de elementos duplicados, utilice la **poner aquí subárbol** comando en el menú contextual de elementos de la hoja.  
  
9. **Transformar todas las plantillas** en la barra de herramientas del explorador de soluciones.  
  
10. Generar el **Dsl** proyecto.  
  
    > [!NOTE]
    >  En esta fase, los otros proyectos no compilará sin errores. Sin embargo, deseamos compilar el proyecto de Dsl para que su ensamblado está disponible para el Asistente para orígenes de datos.  
  
## <a name="updating-the-ui-project"></a>Actualización del proyecto de la interfaz de usuario  
 Ahora puede crear un nuevo control de usuario que se mostrará la información que se almacena en el modelo DSL. Para conectar el control de usuario con el modelo más sencillo es a través de enlaces de datos. El tipo de adaptador con el nombre de enlace de datos **ModelingBindingSource** diseñado específicamente para conectar DSL con interfaces no VMSDK.  
  
#### <a name="to-define-your-dsl-model-as-a-data-source"></a>Para definir el modelo DSL como origen de datos  
  
1.  En el **datos** menú, elija **Mostrar orígenes de datos**.  
  
     El **orígenes de datos** se abre la ventana.  
  
     Elija **Agregar nuevo origen de datos**. El **Asistente de configuración de origen de datos** se abre.  
  
2.  Elija **objeto**, **siguiente**.  
  
     Expanda **Dsl**, **Company.FarmApp**y seleccione **granja**, que es la clase raíz del modelo. Elija **finalizar**.  
  
     En el Explorador de soluciones, el **UI** proyecto contiene ahora **Properties\DataSources\Farm.datasource**  
  
     Las propiedades y relaciones de la clase de modelo aparecen en la ventana de orígenes de datos.  
  
     ![3 DslWpf](~/docs/modeling/media/dslwpf-3.png "DslWpf&3;")  
  
#### <a name="to-connect-your-model-to-a-form"></a>Para conectar el modelo a un formulario  
  
1.  En el **UI** project, elimine todos los archivos .cs existente.  
  
2.  Agregue un nuevo **Control de usuario** archivo denominado `FarmControl` a la **UI** proyecto.  
  
3.  En el **orígenes de datos** ventana, en el menú desplegable **granja**, elija **detalles**.  
  
     Deje la configuración predeterminada para las demás propiedades.  
  
4.  Abra FarmControl.cs en la vista Diseño.  
  
     Arrastre **granja** desde la ventana Orígenes de datos a FarmControl.  
  
     Aparece un conjunto de controles, uno para cada propiedad. Las propiedades de relación no generar controles.  
  
5.  Eliminar **farmBindingNavigator**. Esto también se genera automáticamente en el `FarmControl` diseñador, pero no es útil para esta aplicación.  
  
6.  Mediante el cuadro de herramientas, cree dos instancias de **DataGridView**y asignarles nombre `AnimalGridView` y `FieldGridView`.  
  
    > [!NOTE]
    >  Una alternativa consiste en arrastrar los elementos de los animales y los campos desde la ventana Orígenes de datos en el control. Esta acción crea automáticamente los enlaces entre la vista de cuadrícula y el origen de datos y cuadrículas de datos. Sin embargo, este enlace no funciona correctamente para DSL. Por lo tanto, es mejor crear cuadrículas de datos y enlaces manualmente.  
  
7.  Si el cuadro de herramientas no contiene la **ModelingBindingSource** de la herramienta, agréguelo. En el menú contextual de la **datos** , elija la ficha **elegir elementos**. En el **elegir elementos del cuadro de herramientas** cuadro de diálogo, seleccione **ModelingBindingSource** desde el **ficha .NET Framework**.  
  
8.  Mediante el cuadro de herramientas, cree dos instancias de **ModelingBindingSource**y asignarles nombre `AnimalBinding` y `FieldBinding`.  
  
9. Establecer el **DataSource** propiedad de cada **ModelingBindingSource** a **farmBindingSource**.  
  
     Establecer el **DataMember** propiedad **animales** o **campos**.  
  
10. Establecer el **DataSource** propiedades de `AnimalGridView` a `AnimalBinding`y de `FieldGridView` a `FieldBinding`.  
  
11. Ajustar el diseño del control de granja de servidores a su gusto.  
  
 El **ModelingBindingSource** es un adaptador que realiza varias funciones que son específicas de DSL:  
  
-   Encapsula las actualizaciones en una transacción de almacén de VMSDK.  
  
     Por ejemplo, cuando el usuario elimina una fila de la cuadrícula de la vista de datos, un enlace normal generará una excepción de transacción.  
  
-   Garantiza que, cuando el usuario selecciona una fila, la ventana Propiedades muestra las propiedades del elemento del modelo correspondiente, en lugar de la fila de la cuadrícula de datos.  
  
 ![DslWpf4](~/docs/modeling/media/dslwpf4.png "DslWpf4")  
Esquema de los vínculos entre los orígenes de datos y vistas.  
  
#### <a name="to-complete-the-bindings-to-the-dsl"></a>Para completar los enlaces de DSL  
  
1.  Agregue el siguiente código en un archivo de código independiente en el **UI** proyecto:  
  
    ```c#  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Design;  
  
    namespace Company.FarmApp  
    {  
      partial class FarmControl  
      {  
        public IContainer Components { get { return components; } }  
  
        /// <summary>Binds the WinForms data source to the DSL model.  
        /// </summary>  
        /// <param name="nodelRoot">The root element of the model.</param>  
        public void DataBind(ModelElement modelRoot)  
        {  
          WinFormsDataBindingHelper.PreInitializeDataSources(this);  
          this.farmBindingSource.DataSource = modelRoot;  
          WinFormsDataBindingHelper.InitializeDataSources(this);  
        }  
      }  
    }  
    ```  
  
2.  En el **DslPackage** proyecto, edite **DslPackage\DocView.tt** para actualizar la definición de variable siguiente:  
  
    ```c#  
    string viewControlTypeName = "FarmControl";  
    ```  
  
## <a name="testing-the-dsl"></a>Probar el DSL  
 La solución de DSL ahora puede compilar y ejecutar, aunque quizás quiera agregar más mejoras más adelante.  
  
#### <a name="to-test-the-dsl"></a>Para probar el DSL  
  
1.  Compile y ejecute la solución.  
  
2.  En la instancia experimental de Visual Studio, abra el **ejemplo** archivo.  
  
3.  En el **FarmApp Explorer**, abra el menú contextual en el **granja** nodo raíz y seleccione **Agregar nuevo cabras**.  
  
     `Goat1`aparece en la **animales** vista.  
  
    > [!WARNING]
    >  Debe usar el menú contextual en el **granja** nodo, no el **animales** nodo.  
  
4.  Seleccione el **granja** nodo raíz y ver sus propiedades.  
  
     En la vista formulario, cambie el **nombre** o **tamaño** de la granja de servidores.  
  
     Cuando sale de cada campo en el formulario, los cambios de propiedad correspondientes en la ventana Propiedades.  
  
## <a name="enhancing-the-dsl"></a>Mejorar el DSL  
  
#### <a name="to-make-the-properties-update-immediately"></a>Asegúrese de actualizar inmediatamente las propiedades  
  
1.  En la vista de diseño de FarmControl.cs, seleccione un campo sencillo como nombre, tamaño o IsOrganic.  
  
2.  En la ventana Propiedades, expanda **DataBindings** y abra **(avanzado)**.  
  
     En el **formato y enlace de datos avanzado** cuadro de diálogo, en **modo de actualización del origen de datos**, elija **OnPropertyChanged**.  
  
3.  Compile y ejecute la solución.  
  
     Compruebe que al cambiar el contenido del campo, la propiedad correspondiente del inmediatamente los cambios del modelo de conjunto de servidores.  
  
#### <a name="to-provide-add-buttons"></a>Para proporcionar botones para agregar  
  
1.  En la vista de diseño de FarmControl.cs, utilice el cuadro de herramientas para crear un botón en el formulario.  
  
     Editar el nombre y el texto del botón, por ejemplo, para `New Sheep`.  
  
2.  Abra el código detrás del botón (por ejemplo, haciendo doble clic).  
  
     Editar como sigue:  
  
    ```c#  
    private void NewSheepButton_Click(object sender, EventArgs e)  
    {  
      using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))  
      {  
        elementOperations.MergeElementGroup(farm,  
          new ElementGroup(new Sheep(farm.Partition)));  
        t.Commit();  
      }  
    }  
  
    // The following code is shared with other add buttons:  
    private ElementOperations operationsCache = null;  
    private ElementOperations elementOperations  
    {  
      get  
      {  
        if (operationsCache == null)  
        {  
          operationsCache = new ElementOperations(farm.Store, farm.Partition);  
        }  
        return operationsCache;  
      }  
    }  
    private Farm farm  
    {  
      get { return this.farmBindingSource.DataSource as Farm; }  
    }  
  
    ```  
  
     También debe insertar la siguiente directiva:  
  
    ```c#  
  
    using Microsoft.VisualStudio.Modeling;  
  
    ```  
  
3.  Agregar los botones similares de cabras y campos.  
  
4.  Compile y ejecute la solución.  
  
5.  Compruebe que el botón nuevo agrega un elemento. El nuevo elemento debe aparecer en el Explorador de FarmApp y en la vista de cuadrícula de datos adecuado.  
  
     Podrá modificar el nombre del elemento en la vista de cuadrícula de datos. También puede eliminar desde allí.  
  
 ![DSL-Wpf-2](~/docs/modeling/media/dsl-wpf-2.png "2 de Wpf de DSL")  
  
### <a name="about-the-code-to-add-an-element"></a>Acerca del código para agregar un elemento  
 Para los nuevos botones de elemento, el siguiente código alternativo es un poco más simple.  
  
```c#  
private void NewSheepButton_Click(object sender, EventArgs e)  
{  
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))  
  {  
    farm.Animals.Add(new Sheep(farm.Partition)); ;  
    t.Commit();  
  }  
}  
  
```  
  
 Sin embargo, este código no establece un nombre predeterminado para el nuevo elemento. No se ejecuta cualquier combinación personalizada que haya definido en el **directivas de combinación del elemento** de DSL, y no se ejecuta ningún código personalizado de mezcla que se han definido.  
  
 Por lo tanto, recomendamos que use <xref:Microsoft.VisualStudio.Modeling.ElementOperations>para crear nuevos elementos.</xref:Microsoft.VisualStudio.Modeling.ElementOperations> Para obtener más información, consulte [personalizar la creación de elemento y el movimiento](../modeling/customizing-element-creation-and-movement.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md)   
 [Escribir código para personalizar un lenguaje específico de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Modelar el SDK de Visual Studio: lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
