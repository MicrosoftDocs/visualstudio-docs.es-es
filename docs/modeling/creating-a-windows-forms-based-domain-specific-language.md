---
title: Crear un lenguaje específico de dominio basado en Windows Forms
description: Proporciona información sobre cómo usar Windows Forms para mostrar el estado de un modelo de lenguaje específico del dominio.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 9a77a22b7ed888b28f12154974d735213952899c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389545"
---
# <a name="create-a-windows-forms-based-domain-specific-language"></a>Creación de un Windows Forms basado en Domain-Specific lenguaje

Puede usar Windows Forms mostrar el estado de un modelo de lenguaje específico de dominio (DSL), en lugar de usar un diagrama DSL. Este tema le guiará a través del enlace de windows Form a un DSL mediante Visual Studio SDK de visualización y modelado.

En la imagen siguiente se muestra una interfaz de usuario de Windows Form y el explorador de modelos para una instancia de DSL:

![Instancia de DSL en Visual Studio](../modeling/media/dsl-wpf-2.png)

## <a name="create-a-windows-forms-dsl"></a>Creación de una Windows Forms DSL

La plantilla de DSL mínimo de **WinForm Designer** crea un DSL mínimo que se puede modificar para satisfacer sus propios requisitos.

1. Cree un DSL a partir de la **plantilla De diseñador mínimo de WinForm.**

    En este tutorial, se asumen los siguientes nombres:

    - Nombre de la solución y DSL: `FarmApp`
    - Espacio de nombres: `Company.FarmApp`

2. Experimente con el ejemplo inicial que proporciona la plantilla:

   1. Transformar todas las plantillas.

   2. Compile y ejecute el ejemplo (**Ctrl** + **F5**).

   3. En la instancia experimental de Visual Studio, abra el `Sample` archivo en el proyecto de depuración.

        Observe que se muestra en un control Windows Forms control .

        También puede ver los elementos del modelo que se muestran en el Explorador.

        Agregue algunos elementos en el formulario o en el Explorador y observe que aparecen en la otra pantalla.

   En la instancia principal de Visual Studio, observe los siguientes puntos sobre la solución DSL:

- `DslDefinition.dsl` no contiene elementos de diagrama. Esto se debe a que no usará diagramas DSL para ver los modelos de instancia de este DSL. En su lugar, enlazará un formulario Windows Form al modelo y los elementos del formulario mostrarán el modelo.

- Además de los proyectos y , la solución contiene un tercer proyecto denominado proyecto de interfaz de usuario que contiene `Dsl` `DslPackage` la `UI.`  definición de un control Windows Forms. `DslPackage` depende de `UI` y `UI` depende de `Dsl` .

- En el `DslPackage` proyecto, `UI\DocView.cs` contiene el código que muestra el control Windows Forms que se define en el `UI` proyecto.

- El `UI` proyecto contiene un ejemplo de trabajo de un control de formulario enlazado al DSL. Sin embargo, no funcionará cuando haya cambiado la definición de DSL. El `UI` proyecto contiene:

  - Una Windows Forms denominada `ModelViewControl` .

  - Un archivo denominado `DataBinding.cs` que contiene una definición parcial adicional de `ModelViewControl` . Para ver su contenido, en **Explorador de soluciones**, abra el menú contextual del archivo y elija **Ver código.**

### <a name="about-the-ui-project"></a>Acerca del proyecto de interfaz de usuario

Al actualizar el archivo de definición de DSL para definir su propio DSL, tendrá que actualizar el control en el proyecto `UI` para mostrar el DSL. A diferencia `Dsl` de los proyectos y , el proyecto de ejemplo no se genera a partir de `DslPackage` `UI` `DslDefinitionl.dsl` . Puede agregar archivos .tt para generar el código si lo desea, aunque no se trata en este tutorial.

## <a name="update-the-dsl-definition"></a>Actualización de la definición de DSL

La siguiente imagen es la definición de DSL que se usa en este tutorial.

![Definición de DSL](../modeling/media/dsl-wpf-1.png)

1. Abra DslDefinition.dsl en el diseñador DSL.

2. Eliminar **ExampleElement**

3. Cambie el nombre de la clase de dominio **ExampleModel** a `Farm` .

     Asíétele propiedades de dominio `Size` adicionales denominadas **de tipo Int32** y `IsOrganic` de tipo **booleano**.

    > [!NOTE]
    > Si elimina la clase de dominio raíz y, a continuación, crea una nueva raíz, tendrá que restablecer la propiedad Clase raíz del editor. En **el Explorador de DSL,** seleccione **Editor**. A continuación, en ventana Propiedades, establezca **Clase raíz** en `Farm` .

4. Use la **herramienta Clase de dominio** con nombre para crear las siguientes clases de dominio:

    - `Field` - Asítele una propiedad de dominio adicional denominada `Size` .

    - `Animal` - En la ventana Propiedades, establezca **Modificador de herencia en** **Abstract**.

5. Use la **herramienta Clase de** dominio para crear las clases siguientes:

    - `Sheep`

    - `Goat`

6. Use la **herramienta Herencia** para crear `Goat` y `Sheep` heredar de `Animal` .

7. Use la **herramienta de inserción** para insertar `Field` y en `Animal` `Farm` .

8. Es posible que desee ordenar el diagrama. Para reducir el número de elementos duplicados, use el comando **Bring Subtree Here** (Traer subárbol aquí) en el menú contextual de los elementos hoja.

9. **Transformar todas las plantillas** en la barra de herramientas de Explorador de soluciones.

10. Compile el **proyecto dsl.**

    > [!NOTE]
    > En esta fase, los demás proyectos no se compilarán sin errores. Sin embargo, queremos compilar el proyecto dsl para que su ensamblado esté disponible para el Asistente para orígenes de datos.

## <a name="update-the-ui-project"></a>Actualización del proyecto de interfaz de usuario

Ahora puede crear un nuevo control de usuario que mostrará la información almacenada en el modelo DSL. La manera más fácil de conectar el control de usuario al modelo es a través de enlaces de datos. El tipo de adaptador de enlace de datos **denominado ModelingBindingSource** está diseñado específicamente para conectar las DSL a interfaces que no son de VMSDK.

### <a name="define-your-dsl-model-as-a-data-source"></a>Definición del modelo DSL como origen de datos

1. En el **menú Datos,** elija **Mostrar orígenes de datos.**

     Se abre la ventana **Orígenes de datos**.

     Elija **Agregar nuevo origen de datos.** Se **abre el Asistente para configuración del origen de** datos.

2. Elija **Objeto**, **Siguiente.**

     Expanda **Dsl**, **Company.FarmApp** y **seleccione Farm**, que es la clase raíz del modelo. Elija **Finalizar**.

     En Explorador de soluciones, el proyecto **de interfaz de** usuario ahora contiene **Properties\DataSources\Farm.datasource**

     Las propiedades y relaciones de la clase de modelo aparecen en la ventana Orígenes de datos.

     ![Ventana Orígenes de datos](../modeling/media/dslwpf-3.png)

### <a name="connect-your-model-to-a-form"></a>Conexión del modelo a un formulario

1. En el proyecto **de interfaz** de usuario, elimine todos los archivos .cs existentes.

2. Agregue un nuevo archivo **de Control de** usuario denominado al proyecto de interfaz `FarmControl` **de** usuario.

3. En la **ventana Orígenes de** datos, en el menú desplegable de **granja,** elija **Detalles.**

    Deje la configuración predeterminada para las demás propiedades.

4. Abra FarmControl.cs en la vista de diseño.

    Arrastre **Farm desde** la ventana Orígenes de datos a FarmControl.

    Aparece un conjunto de controles, uno para cada propiedad. Las propiedades de relación no generan controles.

5. Elimine **farmBindingNavigator.** Esto también se genera automáticamente en el `FarmControl` diseñador, pero no es útil para esta aplicación.

6. Con el cuadro de herramientas, cree dos instancias de **DataGridView,** así como el nombre y `AnimalGridView` `FieldGridView` .

   > [!NOTE]
   > Un paso alternativo consiste en arrastrar los elementos Animales y Campos desde la ventana Orígenes de datos al control . Esta acción crea automáticamente cuadrículas de datos y enlaces entre la vista de cuadrícula y el origen de datos. Sin embargo, este enlace no funciona correctamente para las DSL. Por lo tanto, es mejor crear las cuadrículas de datos y los enlaces manualmente.

7. Si el cuadro de herramientas no contiene la **herramienta ModelingBindingSource,** agrégrela. En el menú contextual de la **pestaña Datos,** elija **Elegir elementos.** En el **cuadro de diálogo Elegir elementos del** cuadro de herramientas, seleccione **ModelingBindingSource** **en .NET Framework** pestaña.

8. Con el Cuadro de herramientas, cree dos instancias de **ModelingBindingSource** y así mismo denles `AnimalBinding` el nombre y `FieldBinding` .

9. Establezca la **propiedad DataSource** de cada **ModelingBindingSource** en **farmBindingSource.**

     Establezca la **propiedad DataMember** en **Animales o** **Campos.**

10. Establezca las **propiedades DataSource** `AnimalGridView` de en y de en `AnimalBinding`  `FieldGridView` `FieldBinding` .

11. Ajuste el diseño del control Farm a su gusto.

    **ModelingBindingSource es** un adaptador que realiza varias funciones específicas de las DSL:

- Encapsula las actualizaciones en una transacción de almacén de VMSDK.

   Por ejemplo, cuando el usuario elimina una fila de la cuadrícula de vistas de datos, un enlace normal produciría una excepción de transacción.

- Garantiza que, cuando el usuario selecciona una fila, el ventana Propiedades muestra las propiedades del elemento de modelo correspondiente, en lugar de la fila de cuadrícula de datos.

  ![Esquema del enlace DSL](../modeling/media/dslwpf4.png)
  
  Esquema de vínculos entre orígenes de datos y vistas.

### <a name="complete-the-bindings-to-the-dsl"></a>Completar los enlaces al DSL

1. Agregue el código siguiente en un archivo de código independiente en el proyecto **de interfaz de** usuario:

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

2. En el **proyecto DslPackage,** edite **DslPackage\DocView.tt** para actualizar la siguiente definición de variable:

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="test-the-dsl"></a>Prueba del DSL

La solución DSL ahora se puede compilar y ejecutar, aunque es posible que quiera agregar más mejoras más adelante.

1. Compile y ejecute la solución.

2. En la instancia experimental de Visual Studio, abra el **archivo de** ejemplo.

3. En el **Explorador de FarmApp,** abra el menú contextual en el nodo raíz **De** granja y elija Agregar **nueva granja.**

     `Goat1`aparece en la **vista Animales.**

    > [!WARNING]
    > Debe usar el menú contextual del nodo **Granja,** no el **nodo Animales.**

4. Seleccione el nodo raíz **Farm** (Granja) y vea sus propiedades.

     En la vista de formulario, cambie **el nombre** o **el tamaño** de la granja.

     Al salir de cada campo del formulario, la propiedad correspondiente cambia en el ventana Propiedades.

## <a name="enhance-the-dsl"></a>Mejora del DSL

### <a name="make-the-properties-update-immediately"></a>Hacer que las propiedades se actualicen inmediatamente

1. En la vista de diseño de FarmControl.cs, seleccione un campo simple como Nombre, Tamaño o IsOrganic.

2. En el ventana Propiedades, expanda **DataBindings** y abra **(Avanzado).**

     En el **cuadro de diálogo Formato y enlace** avanzado, en Modo de actualización del origen de **datos,** **elija OnPropertyChanged**.

3. Compile y ejecute la solución.

     Compruebe que, al cambiar el contenido del campo, la propiedad correspondiente del modelo farm cambia inmediatamente.

### <a name="provide-add-buttons"></a>Proporcionar botones Agregar

1. En la vista de diseño de FarmControl.cs, use el cuadro de herramientas para crear un botón en el formulario.

    Edite el nombre y el texto del botón, por ejemplo, en `New Sheep` .

2. Abra el código detrás del botón (por ejemplo, haciendo doble clic en él).

    Edite esta opción de la siguiente manera:

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

    También deberá insertar la siguiente directiva:

   ```csharp

   using Microsoft.VisualStudio.Modeling;
   ```

3. Agregue botones similares para Las marchas y los campos.

4. Compile y ejecute la solución.

5. Compruebe que el nuevo botón agrega un elemento. El nuevo elemento debe aparecer en FarmApp Explorer y en la vista de cuadrícula de datos adecuada.

    Debería poder editar el nombre del elemento en la vista de cuadrícula de datos. También puede eliminarlo desde allí.

   ![Vista de cuadrícula de datos de ejemplo](../modeling/media/dsl-wpf-2.png)

### <a name="about-the-code-to-add-an-element"></a>Acerca del código para agregar un elemento

Para los nuevos botones de elemento, el código alternativo siguiente es ligeramente más sencillo.

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

Sin embargo, este código no establece un nombre predeterminado para el nuevo elemento. No ejecuta ninguna combinación personalizada que pueda haber definido en las directivas **de** combinación de elementos del DSL y no ejecuta ningún código de combinación personalizado que se haya definido.

Por lo tanto, se recomienda usar <xref:Microsoft.VisualStudio.Modeling.ElementOperations> para crear nuevos elementos. Para obtener más información, vea [Personalización de la creación y el movimiento de elementos.](../modeling/customizing-element-creation-and-movement.md)

## <a name="see-also"></a>Vea también

- [Definición de un Domain-Specific language](../modeling/how-to-define-a-domain-specific-language.md)
- [Escribir código para personalizar un Domain-Specific language](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modelar el SDK de Visual Studio: lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
