---
title: Creación de un lenguaje específico de dominio basada en formularios de Windows | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 452318ff-8ecf-46d0-8ca0-4013d0cdafaf
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1faa3b8a7b57ddae646b55a8a17226894a5ed5d2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996288"
---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>Crear lenguajes específicos de dominio basados en Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar Windows Forms para mostrar el estado de un modelo de lenguaje específico de dominio (DSL), en lugar de usar un diagrama DSL. Este tema le guiará a través de enlazar un formulario de Windows a un DSL, utilizando el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK de visualización y modelado.  

 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  
Una instancia de DSL, que muestra una interfaz de usuario del formulario de Windows y el Explorador de modelos.  

## <a name="creating-a-windows-forms-dsl"></a>Creación de un DSL de Windows Forms  
 El **Diseñador de WinForm mínimo** plantilla DSL crea un DSL mínimo que puede modificar para adaptarlo a sus propios requisitos.  

#### <a name="to-create-a-minimal-winforms-dsl"></a>Para crear un DSL de WinForms mínima  

1. Crear un DSL desde el **Diseñador de WinForm mínimo** plantilla.  

    En este tutorial, se supone que los nombres siguientes:  


   |                       |                 |
   |-----------------------|-----------------|
   | Nombre de la solución y DSL |     FarmApp     |
   |       Espacio de nombres       | Company.FarmApp |


2. Experimentar con el ejemplo inicial que proporciona la plantilla:  

   1.  Transformar todas las plantillas.  

   2.  Compilar y ejecutar el ejemplo (**CTRL+F5**).  

   3.  En la instancia experimental de Visual Studio, abra el `Sample` archivo del proyecto de depuración.  

        Tenga en cuenta que se muestra en un control Windows Forms.  

        También puede ver los elementos del modelo que se muestra en el explorador.  

        Agregar algunos elementos en el formulario o en el explorador y observe que aparecen en la otra pantalla.  

   En la instancia principal de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], tenga en cuenta los siguientes puntos acerca de la solución de DSL:  

-   `DslDefinition.dsl` no contiene ningún elemento del diagrama. Esto es porque no usará los diagramas DSL para ver los modelos de la instancia de este DSL. En su lugar, se enlazará un formulario de Windows para el modelo y los elementos en el formulario mostrará el modelo.  

-   Además el `Dsl` y `DslPackage` proyectos, la solución contiene un tercer proyecto denominado `UI.` **UI** proyecto contiene la definición de un control Windows Forms. `DslPackage` depende de `UI`, y `UI` depende `Dsl`.  

-   En el `DslPackage` proyecto, `UI\DocView.cs` contiene el código que muestra el control de Windows Forms que se define en el `UI` proyecto.  

-   El `UI` proyecto contiene un ejemplo funcional de un control de formulario enlazado a la línea ADSL. Sin embargo, no funcionará cuando han cambiado la definición de DSL. El `UI` contiene el proyecto:  

    -   Una clase de Windows Forms denominada `ModelViewControl`.  

    -   Un archivo denominado `DataBinding.cs` que contiene una definición parcial adicional de `ModelViewControl`. Para ver su contenido, en **el Explorador de soluciones**, abra el menú contextual para el archivo y elija **ver código**.  

### <a name="about-the-ui-project"></a>Acerca del proyecto de interfaz de usuario  
 Cuando se actualiza el archivo de definición de DSL para definir su propio DSL, tendrá que actualizar el control en el `UI` proyecto para mostrar su DSL. A diferencia de la `Dsl` y `DslPackage` proyectos, el ejemplo `UI` proyecto no se genera desde `DslDefinitionl.dsl`. Puede agregar archivos .tt para generar el código si lo desea, aunque no se trata en este tutorial.  

## <a name="updating-the-dsl-definition"></a>Actualizar la definición de DSL  
 Lo siguiente en que la definición de DSL se usa en este tutorial.  

 ![DSL&#45;Wpf&#45;1](../modeling/media/dsl-wpf-1.png "DSL-Wpf-1")  

#### <a name="to-update-the-dsl-definition"></a>Para actualizar la definición de DSL  

1.  Abra DslDefinition.dsl en el diseñador DSL.  

2.  Eliminar **ExampleElement**  

3.  Cambiar el nombre de la **ExampleModel** clase de dominio `Farm`.  

     Asígnele propiedades de dominio adicional denominadas `Size` de tipo **Int32**, y `IsOrganic` de tipo **booleano**.  

    > [!NOTE]
    >  Si elimina la clase de dominio raíz y, a continuación, crear una nueva raíz, tendrá que restablecer la propiedad de la clase raíz del Editor. En **DSL Explorer**, seleccione **Editor**. A continuación, en la ventana Propiedades, establezca **clase raíz** a `Farm`.  

4.  Use la **la clase de dominio denominado** herramienta para crear las clases de dominio siguientes:  

    -   `Field` – A darle una propiedad de dominio adicional denominada `Size`.  

    -   `Animal` En la ventana Propiedades, establezca **modificador de herencia** a **abstracta**.  

5.  Use la **la clase de dominio** herramienta para crear las clases siguientes:  

    -   `Sheep`  

    -   `Goat`  

6.  Use la **herencia** herramienta para realizar `Goat` y `Sheep` heredar `Animal`.  

7.  Use la **Embedding** herramienta incrustar `Field` y `Animal` en `Farm`.  

8.  Es posible que desee ordenar el diagrama. Para reducir el número de elementos duplicados, use el **poner aquí subárbol** comando en el menú contextual de elementos hoja.  

9. **Transformar todas las plantillas** en la barra de herramientas del explorador de soluciones.  

10. Compilar el **Dsl** proyecto.  

    > [!NOTE]
    >  En esta fase, los otros proyectos no se compilarán sin errores. Sin embargo, deseamos crear el proyecto Dsl para que su ensamblado esté disponible para el Asistente para orígenes de datos.  

## <a name="updating-the-ui-project"></a>Actualización del proyecto de interfaz de usuario  
 Ahora puede crear un nuevo control de usuario que se mostrará la información que se almacena en el modelo de DSL. Para conectar el control de usuario con el modelo más sencillo es a través de enlaces de datos. El tipo de adaptador con el nombre de enlace de datos **ModelingBindingSource** está diseñado específicamente para conectar el DSL con interfaces no VMSDK.  

#### <a name="to-define-your-dsl-model-as-a-data-source"></a>Para definir el modelo DSL como un origen de datos  

1.  En el **datos** menú, elija **Mostrar orígenes de datos**.  

     Se abre la ventana **Orígenes de datos**.  

     Elija **Agregar nuevo origen de datos**. Se abrirá el **Asistente para configuración de orígenes de datos**.  

2.  Elija **objeto**, **siguiente**.  

     Expanda **Dsl**, **Company.FarmApp**y seleccione **granja**, que es la clase raíz del modelo. Elija **Finalizar**.  

     En el Explorador de soluciones, el **UI** proyecto ahora contiene **Properties\DataSources\Farm.datasource**  

     Las propiedades y relaciones de la clase de modelo aparecen en la ventana de orígenes de datos.  

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png "DslWpf-3")  

#### <a name="to-connect-your-model-to-a-form"></a>Para conectar el modelo a un formulario  

1. En el **UI** del proyecto, elimine todos los archivos .cs existentes.  

2. Agregue un nuevo **Control de usuario** archivo denominado `FarmControl` a la **UI** proyecto.  

3. En el **orígenes de datos** ventana, en el menú desplegable **granja**, elija **detalles**.  

    Deje los valores predeterminados para las demás propiedades.  

4. Abra FarmControl.cs en la vista Diseño.  

    Arrastre **granja** desde la ventana Orígenes de datos hasta FarmControl.  

    Aparece un conjunto de controles, uno para cada propiedad. Las propiedades de relación no generan los controles.  

5. Eliminar **farmBindingNavigator**. Esto también se genera automáticamente en el `FarmControl` diseñador, pero no es útil para esta aplicación.  

6. Con el cuadro de herramientas, cree dos instancias de **DataGridView**y asígneles el nombre `AnimalGridView` y `FieldGridView`.  

   > [!NOTE]
   >  Un paso alternativo es arrastrar los elementos de los animales y los campos desde la ventana Orígenes de datos hasta el control. Esta acción crea automáticamente las cuadrículas de datos y enlaces entre la vista de cuadrícula y el origen de datos. Sin embargo, este enlace no funciona correctamente para el DSL. Por lo tanto, es mejor crear cuadrículas de datos y enlaces manualmente.  

7. Si el cuadro de herramientas no contiene el **ModelingBindingSource** herramienta, agréguela. En el menú contextual de la **datos** ficha, elija **elegir elementos**. En el **elegir elementos del cuadro de herramientas** cuadro de diálogo, seleccione **ModelingBindingSource** desde el **ficha .NET Framework**.  

8. Con el cuadro de herramientas, cree dos instancias de **ModelingBindingSource**y asígneles el nombre `AnimalBinding` y `FieldBinding`.  

9. Establecer el **DataSource** propiedad de cada uno **ModelingBindingSource** a **farmBindingSource**.  

     Establecer el **DataMember** propiedad **animales** o **campos**.  

10. Establecer el **DataSource** propiedades de `AnimalGridView` a `AnimalBinding`y de `FieldGridView` a `FieldBinding`.  

11. Ajustar el diseño del control de conjunto de servidores a su gusto.  

    El **ModelingBindingSource** es un adaptador que realiza varias funciones que son específicas de DSL:  

- Las actualizaciones ajusta en una transacción de VMSDK Store.  

   Por ejemplo, cuando el usuario elimina una fila de la cuadrícula de vista de datos, un enlace normal daría como resultado una excepción de transacción.  

- Se asegura de que, cuando el usuario selecciona una fila, la ventana Propiedades muestra las propiedades del elemento del modelo correspondiente, en lugar de la fila de la cuadrícula de datos.  

  ![DslWpf4](../modeling/media/dslwpf4.png "DslWpf4")  
  Esquema de los vínculos entre los orígenes de datos y vistas.  

#### <a name="to-complete-the-bindings-to-the-dsl"></a>Para completar los enlaces para el DSL  

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

2.  En el **DslPackage** del proyecto, edite **DslPackage\DocView.tt** para actualizar la definición de variable siguiente:  

    ```csharp  
    string viewControlTypeName = "FarmControl";  
    ```  

## <a name="testing-the-dsl"></a>Probar el DSL  
 La solución de DSL ahora puede compilar y ejecutar, aunque es posible que desee agregar aún más las mejoras más adelante.  

#### <a name="to-test-the-dsl"></a>Para probar el DSL  

1.  Compile y ejecute la solución.  

2.  En la instancia experimental de Visual Studio, abra el **ejemplo** archivo.  

3.  En el **FarmApp Explorer**, abra el menú contextual en el **granja** nodo raíz y elija **agregar nueva cabras**.  

     `Goat1` aparece en el **animales** vista.  

    > [!WARNING]
    >  Debe usar el menú contextual en el **granja** nodo, no el **animales** nodo.  

4.  Seleccione el **granja** nodo raíz y ver sus propiedades.  

     En la vista de formulario, cambie el **nombre** o **tamaño** de la granja de servidores.  

     Cuando se desplaza fuera de cada campo en el formulario, los cambios de propiedad correspondiente en la ventana Propiedades.  

## <a name="enhancing-the-dsl"></a>Mejorar el DSL  

#### <a name="to-make-the-properties-update-immediately"></a>Para hacer que las propiedades se actualice inmediatamente  

1.  En la vista de diseño de FarmControl.cs, seleccione un campo sencillo como nombre, tamaño o IsOrganic.  

2.  En la ventana Propiedades, expanda **DataBindings** y abra **(avanzado)**.  

     En el **formato y enlace de datos avanzado** cuadro de diálogo, en **modo de actualización del origen de datos**, elija **OnPropertyChanged**.  

3.  Compile y ejecute la solución.  

     Compruebe que al cambiar el contenido del campo, la propiedad correspondiente del inmediatamente los cambios del modelo de conjunto de servidores.  

#### <a name="to-provide-add-buttons"></a>Para proporcionar botones para agregar  

1. En la vista de diseño de FarmControl.cs, use el cuadro de herramientas para crear un botón en el formulario.  

    Edite el nombre y el texto del botón, por ejemplo, para `New Sheep`.  

2. Abra el código detrás del botón (por ejemplo, haciendo doble clic en él).  

    Editar como sigue:  

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

    También necesitará insertar la siguiente directiva:  

   ```csharp  

   using Microsoft.VisualStudio.Modeling;  

   ```  

3. Agregar los botones similares de cabras y campos.  

4. Compile y ejecute la solución.  

5. Compruebe que el nuevo botón agrega un elemento. El nuevo elemento debe aparecer en el explorador FarmApp y en la vista de cuadrícula de datos adecuado.  

    Puede editar el nombre del elemento en la vista de cuadrícula de datos. También puede eliminar a partir de ahí.  

   ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  

### <a name="about-the-code-to-add-an-element"></a>Acerca del código para agregar un elemento  
 Para los nuevos botones de elemento, el siguiente código alternativo es ligeramente más sencillo.  

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

 Sin embargo, este código no establece un nombre predeterminado para el nuevo elemento. No se ejecuta cualquier combinación personalizada que haya definido en el **directivas de combinación de elementos** del DSL, y no se ejecuta cualquier código personalizado de mezcla que se han definido.  

 Por lo tanto, recomendamos que use <xref:Microsoft.VisualStudio.Modeling.ElementOperations> para crear nuevos elementos. Para obtener más información, consulte [personalizar la creación de elemento y el movimiento](../modeling/customizing-element-creation-and-movement.md).  

## <a name="see-also"></a>Vea también  
 [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)   
 [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Modelar el SDK de Visual Studio: lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
