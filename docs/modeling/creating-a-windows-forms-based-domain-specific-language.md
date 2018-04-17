---
title: Creación de un lenguaje específico de dominio basada en formularios de Windows | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 23fe0d582f92d5025049974ccd64357203e4845a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>Crear lenguajes específicos de dominio basados en Windows Forms
Puede usar Windows Forms para mostrar el estado de un modelo de lenguaje específico de dominio (DSL), en lugar de utilizar un diagrama DSL. Este tema explica cómo enlazar un formulario Windows Forms a un DSL, usando la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK de visualización y modelado.  
  
 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  
Una instancia DSL, que muestra una interfaz de usuario del formulario de Windows y el Explorador de modelos.  
  
## <a name="creating-a-windows-forms-dsl"></a>Crear un formulario Windows Forms DSL  
 El **mínimo diseñador WinForm** plantilla DSL crea un DSL mínimo que se puede modificar para satisfacer sus propias necesidades.  
  
#### <a name="to-create-a-minimal-winforms-dsl"></a>Para crear un DSL WinForms mínima  
  
1.  Crear un DSL desde el **mínimo diseñador WinForm** plantilla.  
  
     En este tutorial, se supone que los nombres siguientes:  
  
    |||  
    |-|-|  
    |Nombre de la solución y DSL|FarmApp|  
    |Espacio de nombres|Company.FarmApp|  
  
2.  Experimentar con el ejemplo inicial que proporciona la plantilla:  
  
    1.  Transformar todas las plantillas.  
  
    2.  Compilar y ejecutar el ejemplo (**CTRL + F5**).  
  
    3.  En la instancia experimental de Visual Studio, abra el `Sample` archivo en el proyecto de depuración.  
  
         Tenga en cuenta que se muestra en un control de formularios Windows Forms.  
  
         También puede ver los elementos del modelo que se muestra en el explorador.  
  
         Agregue algunos elementos en el formulario o en el explorador y observe que aparecen en la pantalla de otra.  
  
 En la instancia principal de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], tenga en cuenta los siguientes puntos acerca de la solución de ADSL:  
  
-   `DslDefinition.dsl` no contiene ningún elemento de diagrama. Esto es porque no usará los diagramas DSL para ver los modelos de la instancia de este DSL. En su lugar, se enlazará a un formulario Windows Forms para el modelo y los elementos en el formulario se mostrará el modelo.  
  
-   Además el `Dsl` y `DslPackage` proyectos, la solución contiene un tercer proyecto denominado `UI.` **UI** proyecto contiene la definición de un control de formularios Windows Forms. `DslPackage` depende de `UI`, y `UI` depende de `Dsl`.  
  
-   En el `DslPackage` proyecto `UI\DocView.cs` contiene el código que muestra el control de formularios Windows Forms que se define en el `UI` proyecto.  
  
-   El `UI` proyecto contiene un ejemplo funcional de un control de formulario enlazado a la línea ADSL. Sin embargo, no funcionará cuando ha cambiado la definición DSL. El `UI` proyecto contiene:  
  
    -   Una clase de Windows Forms denominada `ModelViewControl`.  
  
    -   Un archivo denominado `DataBinding.cs` que contiene una definición parcial adicional de `ModelViewControl`. Para ver su contenido, en **el Explorador de soluciones**, abra el menú contextual para el archivo y elija **ver código**.  
  
### <a name="about-the-ui-project"></a>Sobre el proyecto de la interfaz de usuario  
 Cuando se actualiza el archivo de definición DSL para definir su propios DSL, tendrá que actualizar el control en el `UI` proyecto para mostrar el ADSL. A diferencia de la `Dsl` y `DslPackage` proyectos, el ejemplo `UI` proyecto no se genera desde `DslDefinitionl.dsl`. Puede agregar .tt (archivos) para compilar el código si lo desea, aunque no se trata en este tutorial.  
  
## <a name="updating-the-dsl-definition"></a>Actualización de la definición de DSL  
 Los siguientes que la definición DSL se utiliza en este tutorial.  
  
 ![DSL&#45;Wpf&#45;1](../modeling/media/dsl-wpf-1.png "DSL-Wpf-1")  
  
#### <a name="to-update-the-dsl-definition"></a>Para actualizar la definición de DSL  
  
1.  Abra DslDefinition.dsl en el diseñador DSL.  
  
2.  Eliminar **ExampleElement**  
  
3.  Cambiar el nombre de la **ExampleModel** clase de dominio para `Farm`.  
  
     Asígnele propiedades de dominio adicional denominados `Size` de tipo **Int32**, y `IsOrganic` de tipo **booleano**.  
  
    > [!NOTE]
    >  Si elimina la clase de dominio raíz y, a continuación, crear una nueva raíz, tendrá que restablecer la propiedad de clase de raíz del Editor. En **DSL explorador**, seleccione **Editor**. A continuación, en la ventana Propiedades, establezca **clase raíz** a `Farm`.  
  
4.  Use la **clase con el nombre de dominio** herramienta para crear las clases de dominio siguientes:  
  
    -   `Field` -Conseguir una propiedad de dominio adicional denominada `Size`.  
  
    -   `Animal` -En la ventana Propiedades, establezca **modificador de herencia** a **abstracta**.  
  
5.  Use la **clase dominio** herramienta para crear las clases siguientes:  
  
    -   `Sheep`  
  
    -   `Goat`  
  
6.  Use la **herencia** herramienta para realizar `Goat` y `Sheep` heredar de `Animal`.  
  
7.  Use la **Embedding** herramienta incrustar `Field` y `Animal` en `Farm`.  
  
8.  Puede ordenar el diagrama. Para reducir el número de elementos duplicados, use la **poner el subárbol aquí** comando en el menú contextual de elementos de la hoja.  
  
9. **Transformar todas las plantillas** en la barra de herramientas del explorador de soluciones.  
  
10. Compilar el **Dsl** proyecto.  
  
    > [!NOTE]
    >  En esta fase, los demás proyectos no se compilarán sin errores. Sin embargo, debe compilar el proyecto de Dsl para que su ensamblado está disponible en el Asistente para orígenes de datos.  
  
## <a name="updating-the-ui-project"></a>Actualizar el proyecto de interfaz de usuario  
 Ahora puede crear un nuevo control de usuario que se mostrará la información que se almacena en un modelo DSL. La forma más sencilla de conectar el control de usuario con el modelo es a través de enlaces de datos. El tipo de adaptador con el nombre de enlace de datos **ModelingBindingSource** está diseñado específicamente para conectar DSL a las interfaces no VMSDK.  
  
#### <a name="to-define-your-dsl-model-as-a-data-source"></a>Para definir el modelo DSL como un origen de datos  
  
1.  En el **datos** menú, elija **Mostrar orígenes de datos**.  
  
     El **orígenes de datos** abre la ventana.  
  
     Elija **Agregar nuevo origen de datos**. El **Asistente para configuración de orígenes de datos** se abre.  
  
2.  Elija **objeto**, **siguiente**.  
  
     Expanda **Dsl**, **Company.FarmApp**y seleccione **granja**, que es la clase raíz del modelo. Elija **Finalizar**.  
  
     En el Explorador de soluciones, la **UI** proyecto ahora contiene **Properties\DataSources\Farm.datasource**  
  
     Las propiedades y relaciones de la clase del modelo aparecen en la ventana de orígenes de datos.  
  
     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png "DslWpf-3")  
  
#### <a name="to-connect-your-model-to-a-form"></a>Para conectar el modelo a un formulario  
  
1.  En el **UI** proyecto de equipo y elimine todos los archivos .cs existente.  
  
2.  Agregue un nuevo **Control de usuario** archivo denominado `FarmControl` a la **UI** proyecto.  
  
3.  En el **orígenes de datos** ventana, en el menú desplegable **granja**, elija **detalles**.  
  
     Deje la configuración predeterminada para las demás propiedades.  
  
4.  Abra FarmControl.cs en la vista Diseño.  
  
     Arrastre **granja** desde la ventana de orígenes de datos a FarmControl.  
  
     Aparece un conjunto de controles, uno para cada propiedad. Las propiedades de relación no generan controles.  
  
5.  Eliminar **farmBindingNavigator**. Esto también se genera automáticamente en el `FarmControl` diseñador, pero no es útil para esta aplicación.  
  
6.  Usar el cuadro de herramientas, cree dos instancias de **DataGridView**y asignarles un nombre `AnimalGridView` y `FieldGridView`.  
  
    > [!NOTE]
    >  Un paso alternativo es arrastrar los elementos de animales y campos de la ventana de orígenes de datos en el control. Esta acción crea automáticamente cuadrículas de datos y los enlaces entre la vista de cuadrícula y el origen de datos. Sin embargo, este enlace no funciona correctamente para DSL. Por lo tanto, es mejor crear las cuadrículas de datos y los enlaces manualmente.  
  
7.  Si el cuadro de herramientas no contiene el **ModelingBindingSource** herramienta, agréguela. En el menú contextual de la **datos** ficha, elija **elegir elementos**. En el **elegir elementos del cuadro de herramientas** cuadro de diálogo, seleccione **ModelingBindingSource** desde el **.NET Framework (ficha)**.  
  
8.  Usar el cuadro de herramientas, cree dos instancias de **ModelingBindingSource**y asignarles un nombre `AnimalBinding` y `FieldBinding`.  
  
9. Establecer el **DataSource** propiedad de cada **ModelingBindingSource** a **farmBindingSource**.  
  
     Establecer el **DataMember** propiedad **animales** o **campos**.  
  
10. Establecer el **DataSource** propiedades de `AnimalGridView` a `AnimalBinding`y de `FieldGridView` a `FieldBinding`.  
  
11. Ajustar el diseño del control de granja de servidores a su gusto.  
  
 El **ModelingBindingSource** es un adaptador que realiza varias funciones que son específicas de DSL:  
  
-   Las actualizaciones se ajusta en una transacción de almacén de VMSDK.  
  
     Por ejemplo, cuando el usuario elimina una fila de la cuadrícula de la vista de datos, un enlace regular produciría una excepción de transacción.  
  
-   Garantiza que, cuando el usuario selecciona una fila, la ventana Propiedades muestra las propiedades del elemento del modelo correspondiente, en lugar de la fila de cuadrícula de datos.  
  
 ![DslWpf4](../modeling/media/dslwpf4.png "DslWpf4")  
Esquema de vínculos entre los orígenes de datos y vistas.  
  
#### <a name="to-complete-the-bindings-to-the-dsl"></a>Para completar los enlaces a la línea ADSL  
  
1.  Agregue el código siguiente en un archivo de código independiente en el **UI** proyecto:  
  
    ```csharp  
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
  
2.  En el **DslPackage** proyecto de equipo y editar **DslPackage\DocView.tt** para actualizar la definición de variable siguiente:  
  
    ```csharp  
    string viewControlTypeName = "FarmControl";  
    ```  
  
## <a name="testing-the-dsl"></a>Pruebas de DSL  
 La solución DSL ahora puede compilar y ejecutar, aunque quizás quiera agregar más mejoras más adelante.  
  
#### <a name="to-test-the-dsl"></a>Para probar la DSL  
  
1.  Compile y ejecute la solución.  
  
2.  En la instancia experimental de Visual Studio, abra el **ejemplo** archivo.  
  
3.  En el **FarmApp Explorer**, abra el menú contextual en el **granja** nodo raíz y elija **agregar nueva cabra**.  
  
     `Goat1` aparece en el **animales** vista.  
  
    > [!WARNING]
    >  Debe usar el menú contextual en el **granja** nodo, no el **animales** nodo.  
  
4.  Seleccione el **granja** nodo raíz y ver sus propiedades.  
  
     En la vista de formulario, cambie el **nombre** o **tamaño** de la granja de servidores.  
  
     Cuando se desplaza fuera de cada campo en el formulario, los cambios de propiedad correspondientes en la ventana Propiedades.  
  
## <a name="enhancing-the-dsl"></a>Mejorar la DSL  
  
#### <a name="to-make-the-properties-update-immediately"></a>Para hacer que las propiedades actualizar de forma inmediata  
  
1.  En la vista de diseño de FarmControl.cs, seleccione un campo simple como el nombre, tamaño o IsOrganic.  
  
2.  En la ventana Propiedades, expanda **DataBindings** y abra **(avanzado)**.  
  
     En el **formato y enlace de datos avanzado** cuadro de diálogo, en **modo de actualización del origen de datos**, elija **OnPropertyChanged**.  
  
3.  Compile y ejecute la solución.  
  
     Compruebe que al cambiar el contenido del campo, la propiedad correspondiente de inmediatamente los cambios del modelo de granja de servidores.  
  
#### <a name="to-provide-add-buttons"></a>Para que proporcione agregar botones  
  
1.  En la vista de diseño de FarmControl.cs, utilice el cuadro de herramientas para crear un botón en el formulario.  
  
     Edite el nombre y el texto del botón, por ejemplo, al `New Sheep`.  
  
2.  Abra el código detrás del botón (por ejemplo, doble clic en él).  
  
     Edite como sigue:  
  
    ```csharp  
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
  
    ```csharp  
  
    using Microsoft.VisualStudio.Modeling;  
  
    ```  
  
3.  Agregar los botones similares de caprinos y los campos.  
  
4.  Compile y ejecute la solución.  
  
5.  Compruebe que el nuevo botón agrega un elemento. El nuevo elemento debe aparecer en el Explorador de FarmApp y en la vista de cuadrícula de datos adecuado.  
  
     Puede modificar el nombre del elemento en la vista de cuadrícula de datos. También puede eliminar desde allí.  
  
 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  
  
### <a name="about-the-code-to-add-an-element"></a>Acerca del código para agregar un elemento  
 Para los nuevos botones de elemento, el siguiente código alternativo es un poco más simple.  
  
```csharp  
private void NewSheepButton_Click(object sender, EventArgs e)  
{  
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))  
  {  
    farm.Animals.Add(new Sheep(farm.Partition)); ;  
    t.Commit();  
  }  
}  
  
```  
  
 Sin embargo, este código no establece un nombre predeterminado para el nuevo elemento. No se ejecuta cualquier combinación personalizada que haya definido en el **elemento mezcla directivas** de DSL, y no se ejecuta cualquier código personalizado de mezcla que se han definido.  
  
 Por lo tanto, recomendamos que use <xref:Microsoft.VisualStudio.Modeling.ElementOperations> para crear nuevos elementos. Para obtener más información, consulte [personalizar la creación de elemento y movimiento](../modeling/customizing-element-creation-and-movement.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md)   
 [Escribir código para personalizar un lenguaje específico de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Modelar el SDK de Visual Studio: lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)