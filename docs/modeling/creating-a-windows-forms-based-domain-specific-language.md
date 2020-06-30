---
title: Crear lenguajes específicos de dominio basados en Windows Forms
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57507775a03bcfd0649f4efbf8a7771fefc8e20b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547321"
---
# <a name="create-a-windows-forms-based-domain-specific-language"></a>Crear un lenguaje específico de dominio basado en Windows Forms

Puede usar Windows Forms para mostrar el estado de un modelo de lenguaje específico del dominio (DSL), en lugar de utilizar un diagrama DSL. En este tema se explica cómo enlazar un Windows Form a un DSL mediante el SDK de visualización y modelado de Visual Studio.

En la imagen siguiente se muestra una interfaz de usuario de Windows Forms y el explorador de modelos de una instancia de DSL:

![Instancia de DSL en Visual Studio](../modeling/media/dsl-wpf-2.png)

## <a name="create-a-windows-forms-dsl"></a>Creación de un Windows Forms DSL

La plantilla DSL del **Diseñador de WinForm mínima** crea un DSL mínimo que puede modificar para satisfacer sus propios requisitos.

1. Cree un DSL a partir de la plantilla del **Diseñador de WinForm mínima** .

    En este tutorial se asumen los nombres siguientes:

   | | |
   |-|-|
   | Nombre de solución y DSL | FarmApp |
   | Espacio de nombres | Company. FarmApp |

2. Experimente con el ejemplo inicial que proporciona la plantilla:

   1. Transformar todas las plantillas.

   2. Compile y ejecute el ejemplo (**Ctrl** + **F5**).

   3. En la instancia experimental de Visual Studio, abra el `Sample` archivo en el proyecto de depuración.

        Tenga en cuenta que se muestra en un control de Windows Forms.

        También puede ver los elementos del modelo que se muestran en el explorador.

        Agregue algunos elementos en el formulario o en el explorador y observe que aparecen en la otra pantalla.

   En la instancia principal de Visual Studio, tenga en cuenta los siguientes puntos acerca de la solución DSL:

- `DslDefinition.dsl`no contiene elementos de diagrama. Esto se debe a que no usará diagramas DSL para ver modelos de instancia de este DSL. En su lugar, enlazará un Windows Form al modelo y los elementos del formulario mostrarán el modelo.

- Además de los `Dsl` proyectos de y `DslPackage` , la solución contiene un tercer proyecto denominado `UI.` **UI** Project que contiene la definición de un control de Windows Forms. `DslPackage`depende de `UI` y `UI` depende de `Dsl` .

- En el `DslPackage` proyecto, `UI\DocView.cs` contiene el código que muestra el control Windows Forms que se define en el `UI` proyecto.

- El `UI` proyecto contiene un ejemplo de trabajo de un control de formulario enlazado con el DSL. Sin embargo, no funcionará cuando haya cambiado la definición de DSL. El `UI` proyecto contiene:

  - Una clase de Windows Forms denominada `ModelViewControl` .

  - Un archivo denominado `DataBinding.cs` que contiene una definición parcial adicional de `ModelViewControl` . Para ver su contenido, en **Explorador de soluciones**, abra el menú contextual del archivo y elija **Ver código**.

### <a name="about-the-ui-project"></a>Acerca del proyecto de interfaz de usuario

Al actualizar el archivo de definición de DSL para definir su propio DSL, tendrá que actualizar el control en el `UI` proyecto para mostrar el DSL. A diferencia de `Dsl` los `DslPackage` proyectos de y, el `UI` proyecto de ejemplo no se genera a partir de `DslDefinitionl.dsl` . Puede Agregar archivos. TT para generar el código si lo desea, aunque no se trata en este tutorial.

## <a name="update-the-dsl-definition"></a>Actualización de la definición de DSL

En este tutorial se usa la definición de DSL siguiente.

![DSL&#45;WPF&#45;1](../modeling/media/dsl-wpf-1.png)

1. Abra DslDefinition. DSL en el diseñador de DSL.

2. Eliminar **ExampleElement**

3. Cambie el nombre de la clase de dominio **ExampleModel** a `Farm` .

     Proporcione propiedades de dominio adicionales denominadas `Size` de tipo **Int32**y `IsOrganic` de tipo **Boolean**.

    > [!NOTE]
    > Si elimina la clase de dominio raíz y, a continuación, crea una nueva raíz, tendrá que restablecer la propiedad de clase raíz del editor. En el **Explorador de DSL**, seleccione **Editor**. A continuación, en el ventana Propiedades, establezca la **clase raíz** en `Farm` .

4. Use la herramienta de **clase de dominio con nombre** para crear las clases de dominio siguientes:

    - `Field`: Proporcione una propiedad de dominio adicional denominada `Size` .

    - `Animal`-En el ventana Propiedades, establezca el **modificador de herencia** en **abstract**.

5. Use la herramienta de **clase de dominio** para crear las clases siguientes:

    - `Sheep`

    - `Goat`

6. Use la herramienta **herencia** para crear `Goat` y `Sheep` heredar de `Animal` .

7. Use la herramienta de **incrustación** para insertar `Field` y `Animal` debajo de `Farm` .

8. Tal vez desee ordenar el diagrama. Para reducir el número de elementos duplicados, use el comando **traer subárbol aquí** en el menú contextual de los elementos hoja.

9. **Transformar todas las plantillas** en la barra de herramientas de explorador de soluciones.

10. Compile el proyecto **DSL** .

    > [!NOTE]
    > En esta fase, los demás proyectos no se compilarán sin errores. Sin embargo, deseamos compilar el proyecto DSL para que el ensamblado esté disponible para el Asistente para orígenes de datos.

## <a name="update-the-ui-project"></a>Actualizar el proyecto de interfaz de usuario

Ahora puede crear un nuevo control de usuario que mostrará la información que se almacena en el modelo de DSL. La forma más fácil de conectar el control de usuario al modelo es a través de los enlaces de datos. El tipo de adaptador de enlace de datos denominado **ModelingBindingSource** está diseñado específicamente para conectar DSL a interfaces que no son de VMSDK.

### <a name="define-your-dsl-model-as-a-data-source"></a>Definir el modelo de DSL como un origen de datos

1. En el menú **datos** , elija **Mostrar orígenes de datos**.

     Se abre la ventana **Orígenes de datos**.

     Elija **Agregar nuevo origen de datos**. Se abre el **Asistente para la configuración de orígenes de datos** .

2. Elija **objeto**, **siguiente**.

     Expanda **DSL**, **Company. FarmApp**y seleccione **granja**, que es la clase raíz del modelo. Elija **Finalizar**.

     En Explorador de soluciones, el proyecto de la **interfaz de usuario** contiene ahora **Properties\DataSources\Farm.DataSource**

     Las propiedades y las relaciones de la clase de modelo aparecen en la ventana orígenes de datos.

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png)

### <a name="connect-your-model-to-a-form"></a>Conectar el modelo a un formulario

1. En el proyecto de **interfaz de usuario** , elimine todos los archivos. CS existentes.

2. Agregue un nuevo archivo de **control de usuario** denominado `FarmControl` al proyecto de **IU** .

3. En la ventana **orígenes de datos** , en el menú desplegable de la granja de **servidores**, elija **detalles**.

    Deje la configuración predeterminada para las demás propiedades.

4. Abra FarmControl.cs en la vista de diseño.

    Arrastre **Farm** desde la ventana orígenes de datos hasta FarmControl.

    Aparece un conjunto de controles, uno para cada propiedad. Las propiedades de la relación no generan controles.

5. Elimine **farmBindingNavigator**. También se genera automáticamente en el `FarmControl` Diseñador, pero no es útil para esta aplicación.

6. Mediante el cuadro de herramientas, cree dos instancias de **DataGridView**y asígneles un nombre `AnimalGridView` y `FieldGridView` .

   > [!NOTE]
   > Un paso alternativo es arrastrar los elementos animales y campos desde la ventana orígenes de datos hasta el control. Esta acción crea automáticamente cuadrículas de datos y enlaces entre la vista de cuadrícula y el origen de datos. Sin embargo, este enlace no funciona correctamente para los DSL. Por lo tanto, es mejor crear manualmente las cuadrículas de datos y los enlaces.

7. Si el cuadro de herramientas no contiene la herramienta **ModelingBindingSource** , agréguela. En el menú contextual de la pestaña **datos** , elija **elegir elementos**. En el cuadro de diálogo **elegir elementos del cuadro de herramientas** , seleccione **ModelingBindingSource** en la pestaña **.NET Framework** .

8. Mediante el cuadro de herramientas, cree dos instancias de **ModelingBindingSource**y asígneles un nombre `AnimalBinding` y `FieldBinding` .

9. Establezca la propiedad **DataSource** de cada **ModelingBindingSource** en **farmBindingSource**.

     Establezca la propiedad **DataMember** en **animales** o **campos**.

10. Establezca las propiedades **DataSource** de `AnimalGridView` en `AnimalBinding` y de `FieldGridView` en `FieldBinding` .

11. Ajuste el diseño del control de la granja de servidores a su gusto.

    **ModelingBindingSource** es un adaptador que realiza varias funciones que son específicas de los DSL:

- Encapsula las actualizaciones en una transacción de almacén VMSDK.

   Por ejemplo, cuando el usuario elimina una fila de la cuadrícula de la vista de datos, un enlace normal produciría una excepción de transacción.

- Garantiza que, cuando el usuario selecciona una fila, el ventana Propiedades muestra las propiedades del elemento de modelo correspondiente, en lugar de la fila de la cuadrícula de datos.

  ![DslWpf4 ](../modeling/media/dslwpf4.png) esquema de vínculos entre orígenes de datos y vistas.

### <a name="complete-the-bindings-to-the-dsl"></a>Completar los enlaces a la DSL

1. Agregue el código siguiente en un archivo de código independiente en el proyecto de la **interfaz de usuario** :

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

2. En el proyecto **DslPackage** , edite **DslPackage\DocView.TT** para actualizar la siguiente definición de variable:

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="test-the-dsl"></a>Prueba del DSL

La solución DSL ahora se puede compilar y ejecutar, aunque es posible que desee agregar más mejoras más adelante.

1. Compile y ejecute la solución.

2. En la instancia experimental de Visual Studio, abra el archivo de **ejemplo** .

3. En el **Explorador de FarmApp**, abra el menú contextual en el nodo raíz de la **granja de servidores** y elija **Agregar nuevo caprino**.

     `Goat1`aparece en la vista **animales** .

    > [!WARNING]
    > Debe utilizar el menú contextual en el nodo de la **granja** , no en el nodo **animales** .

4. Seleccione el nodo raíz de la **granja** y vea sus propiedades.

     En la vista de formulario, cambie el **nombre** o el **tamaño** de la granja.

     Cuando sale de cada campo del formulario, la propiedad correspondiente cambia en el ventana Propiedades.

## <a name="enhance-the-dsl"></a>Mejora del DSL

### <a name="make-the-properties-update-immediately"></a>Hacer que las propiedades se actualicen inmediatamente

1. En la vista de diseño de FarmControl.cs, seleccione un campo simple como nombre, tamaño o IsOrganic.

2. En el ventana Propiedades, expanda **DataBindings** y Abra **(avanzado)**.

     En el cuadro de diálogo **formato y enlace avanzado** , en **modo de actualización del origen de datos**, seleccione **OnPropertyChanged**.

3. Compile y ejecute la solución.

     Compruebe que, al cambiar el contenido del campo, la propiedad correspondiente del modelo de granja de servidores cambia inmediatamente.

### <a name="provide-add-buttons"></a>Proporcionar botones para agregar

1. En la vista de diseño de FarmControl.cs, use el cuadro de herramientas para crear un botón en el formulario.

    Edite el nombre y el texto del botón, por ejemplo, a `New Sheep` .

2. Abra el código subyacente del botón (por ejemplo, haciendo doble clic en él).

    Edítelo de la siguiente manera:

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

    También tendrá que insertar la siguiente directiva:

   ```csharp

   using Microsoft.VisualStudio.Modeling;
   ```

3. Agregue botones similares para caprinos y campos.

4. Compile y ejecute la solución.

5. Compruebe que el botón nuevo agrega un elemento. El nuevo elemento debe aparecer en el explorador de FarmApp y en la vista de cuadrícula de datos adecuada.

    Debe poder editar el nombre del elemento en la vista de cuadrícula de datos. También puede eliminarlo de ahí.

   ![DSL&#45;WPF&#45;2](../modeling/media/dsl-wpf-2.png)

### <a name="about-the-code-to-add-an-element"></a>Acerca del código para agregar un elemento

En el caso de los botones nuevo elemento, el siguiente código alternativo es ligeramente más sencillo.

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

Sin embargo, este código no establece un nombre predeterminado para el nuevo elemento. No ejecuta ninguna combinación personalizada que haya definido en las directivas de combinación de **elementos** del DSL y no ejecuta ningún código de combinación personalizado que pueda haberse definido.

Por lo tanto, se recomienda utilizar <xref:Microsoft.VisualStudio.Modeling.ElementOperations> para crear nuevos elementos. Para obtener más información, vea [personalizar la creación y el movimiento](../modeling/customizing-element-creation-and-movement.md)de los elementos.

## <a name="see-also"></a>Consulte también

- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modelar el SDK de Visual Studio: lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
