---
title: Personalizar la ventana Propiedades
description: Obtenga información sobre cómo personalizar la apariencia y el comportamiento de la ventana de propiedades en el lenguaje específico del dominio (DSL) en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e1bd54850264c33c5317a4395f219689a8e8634
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385804"
---
# <a name="customize-the-properties-window"></a>Personalización de la ventana Propiedades

Puede personalizar la apariencia y el comportamiento de la ventana de propiedades en el lenguaje específico del dominio (DSL) en Visual Studio. En la definición de DSL, defina las propiedades de dominio en cada clase de dominio. De forma predeterminada, al seleccionar una instancia de la clase , ya sea en un diagrama o en el Explorador de modelos, todas las propiedades de dominio se muestran en la ventana de propiedades. Esto le permite ver y editar los valores de las propiedades de dominio, incluso si no los ha asignado a campos de forma en el diagrama.

## <a name="names-descriptions-and-categories"></a>Nombres, descripciones y categorías

**Nombre y Nombre para mostrar.** En la definición de una propiedad de dominio, el nombre para mostrar de la propiedad es el nombre que aparece en tiempo de ejecución en la ventana de propiedades. Por el contrario, el nombre se usa al escribir código de programa para actualizar la propiedad . El nombre debe ser un nombre alfanumérico clr correcto, pero el nombre para mostrar puede contener espacios.

Al establecer el nombre de una propiedad en la definición de DSL, su nombre para mostrar se establece automáticamente en una copia del nombre. Si escribe un nombre con mayúsculas y minúsculas Pascal, como "FuelGauge", el nombre para mostrar contendrá automáticamente un espacio: "Medidor de combustible". Sin embargo, puede establecer explícitamente el nombre para mostrar en otro valor.

**Descripción**. La descripción de una propiedad de dominio aparece en dos lugares:

- En la parte inferior de la ventana de propiedades cuando el usuario selecciona la propiedad. Puede usarlo para explicar al usuario lo que representa la propiedad.

- En el código del programa generado. Si usa los servicios de documentación para extraer la documentación de la API, aparecerá como la descripción de esta propiedad en la API.

**Categoría**. Una categoría es un encabezado del ventana Propiedades.

## <a name="expose-style-features"></a>Exponer características de estilo

Algunas de las características dinámicas de los elementos gráficos se pueden representar o *exponer como* propiedades de dominio. Una característica que se ha expuesto de esta manera puede ser actualizada por el usuario y se puede actualizar más fácilmente mediante el código del programa.

Haga clic con el botón derecho en una clase de forma en Definición de DSL, seleccione **Agregar** expuesto y, a continuación, elija una característica.

En formas, puede exponer las propiedades **FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**, **OutlineThickness** **y FillGradientMode.** En los conectores, puede exponer las **propiedades Color** `,` **TextColor,** **DashStyle** **y Thickness.** En los diagramas puede exponer las **propiedades FillColor** **y TextColor.**

## <a name="forwarding-display-properties-of-related-elements"></a>Reenvío: mostrar propiedades de elementos relacionados

Cuando el usuario del DSL selecciona un elemento de un modelo, las propiedades de ese elemento se muestran en la ventana de propiedades. Sin embargo, también puede mostrar las propiedades de los elementos relacionados especificados. Esto resulta útil si ha definido un grupo de elementos que funcionan juntos. Por ejemplo, puede definir un elemento principal y un elemento de complemento opcional. Si el elemento principal está asignado a una forma y el otro no, resulta útil ver todas sus propiedades como si estuvieran en un elemento.

Este efecto se denomina *reenvío de propiedades* y se produce automáticamente en varios casos. En otros casos, puede lograr el reenvío de propiedades definiendo un descriptor de tipo de dominio.

### <a name="default-property-forwarding-cases"></a>Casos predeterminados de reenvío de propiedades

Cuando el usuario selecciona una forma, un conector o un elemento en el Explorador, se muestran las siguientes propiedades en el ventana Propiedades:

- Las propiedades de dominio que se definen en la clase de dominio del elemento de modelo, incluidas las que se definen en las clases base. Una excepción son las propiedades de dominio para las que ha establecido **Is Browsable** en `False` .

- Nombres de elementos vinculados a través de relaciones que tienen una multiplicidad de 0..1. Esto proporciona un método práctico para ver elementos vinculados opcionalmente, incluso si no se ha definido una asignación de conector para la relación.

- Propiedades de dominio de la relación de inserción que tiene como destino el elemento . Dado que las relaciones de inserción normalmente no se muestran explícitamente, esto permite al usuario ver sus propiedades.

- Propiedades de dominio que se definen en la forma o conector seleccionados.

### <a name="add-property-forwarding"></a>Agregar reenvío de propiedades

Para reenviar una propiedad, defina un descriptor de tipo de dominio. Si tiene una relación de dominio entre dos clases de dominio, puede usar un descriptor de tipo de dominio para establecer una propiedad de dominio de la primera clase en el valor de una propiedad de dominio de la segunda clase de dominio. Por ejemplo, si tiene una relación entre una clase de dominio **Book** y una  clase de dominio **Author,** puede usar un descriptor de tipo de dominio para que la propiedad Nombre de un autor de libro aparezca en el ventana Propiedades cuando el usuario seleccione el libro. 

> [!NOTE]
> El reenvío de propiedades solo afecta al ventana Propiedades cuando el usuario está editando un modelo. No define una propiedad de dominio en la clase receptora. Si desea tener acceso a la propiedad de dominio reenviado en otras partes de la definición de DSL o en el código del programa, debe tener acceso al elemento de reenvío.

En el procedimiento siguiente se da por supuesto que ha creado un DSL. En los primeros pasos se resumen los requisitos previos.

#### <a name="forward-a-property-from-another-element"></a>Reenviar una propiedad desde otro elemento

1. Cree una solución que contenga al menos dos clases, que en [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] este ejemplo se **denominan Book** y **Author**. Debe haber una relación de cualquier tipo entre **Book** y **Author**.

    La multiplicidad del rol de origen  (el rol en el lado del libro) debe ser 0...1 o 1..1, de modo que cada libro tenga un **autor.** 

2. En **el Explorador dsl**, haga clic con el botón derecho en la clase de dominio **Book** y, a continuación, haga clic en Agregar **nuevo domainTypeDescriptor**.

    Aparece un nodo denominado **Rutas de acceso de descriptores de propiedad personalizados** en el **nodo Descriptor de tipo** personalizado.

3. Haga clic con el botón derecho **en el nodo Descriptor de tipo personalizado y,** a continuación, haga clic en Agregar nuevo **propertyPath**.

    Aparece una nueva ruta de acceso de propiedad en el **nodo Rutas de acceso de descriptores de propiedad personalizados.**

4. Seleccione la nueva ruta de acceso de propiedad y, en la ventana **Propiedades,** establezca Ruta de acceso en **Propiedad** en la ruta de acceso del elemento de modelo adecuado.

    Puede editar la ruta de acceso en una vista de árbol haciendo clic en la flecha abajo situada a la derecha de esta propiedad. Para obtener más información sobre las rutas de acceso de dominio, vea [Sintaxis de ruta de acceso de dominio.](../modeling/domain-path-syntax.md) Cuando lo haya editado, la ruta de acceso debe ser **similar a BookReferencesAuthor.Author/! Cree**.

5. Establezca **Propiedad en** la propiedad **de** dominio Nombre del **autor.**

6. Establezca **Display Name (Nombre para mostrar)** **en Author Name (Nombre del autor).**

7. Transformar todas las plantillas, compilar y ejecutar el DSL.

8. En un diagrama de modelos, cree un libro, un autor y vincóquelos mediante la relación de referencia. Seleccione el elemento book y, en la ventana Propiedades debería ver Author Name (Nombre del autor), además de las propiedades del libro. Cambie el nombre del autor vinculado o vincule el libro a otro autor y observe que cambia el nombre del autor del libro.

## <a name="custom-property-editors"></a>Editores de propiedades personalizados

La ventana de propiedades proporciona una experiencia de edición predeterminada adecuada para el tipo de cada propiedad de dominio. Por ejemplo, para un tipo enumerado, el usuario ve una lista desplegable y, para una propiedad numérica, el usuario puede escribir dígitos. Esto solo se aplica a los tipos integrados. Si especifica un tipo externo, el usuario podrá ver los valores de la propiedad, pero no editarlo.

Sin embargo, puede especificar los siguientes editores y tipos:

1. Otro editor que se usa con un tipo estándar. Por ejemplo, podría especificar un editor de rutas de acceso de archivo para una propiedad de cadena.

2. Un tipo externo para la propiedad de dominio y un editor para ella.

3. Un editor de .NET, como el editor de rutas de acceso de archivo, o bien puede crear su propio editor de propiedades personalizado.

   Conversión entre un tipo externo y un tipo como String, que tiene un editor predeterminado.

   En un DSL, un *tipo externo* es cualquier tipo que no sea uno de los tipos simples (como Boolean o Int32) o String.

### <a name="define-a-domain-property-that-has-an-external-type"></a>Definición de una propiedad de dominio que tenga un tipo externo

1. En **Explorador de soluciones**, agregue una referencia al ensamblado (DLL) que contiene el tipo externo, en el **proyecto Dsl.**

    El ensamblado puede ser un ensamblado de .NET o un ensamblado proporcionado por usted.

2. Agregue el tipo a la **lista Tipos de** dominio, a menos que ya lo haya hecho.

   1. Abra DslDefinition.dsl y, en el **Explorador de DSL,** haga clic con el botón derecho en el nodo raíz y, a continuación, haga clic **en Agregar nuevo tipo externo**.

        Aparece una nueva entrada en el nodo **Tipos de** dominio.

       > [!WARNING]
       > El elemento de menú está en el nodo raíz dsl, no en el **nodo Tipos de** dominio.

   2. Establezca el nombre y el espacio de nombres del nuevo tipo en el ventana Propiedades.

3. Agregue una propiedad de dominio a una clase de dominio de la manera habitual.

    En la ventana Propiedades, seleccione el tipo externo en la lista desplegable del **campo** Tipo.

   En esta fase, los usuarios pueden ver los valores de la propiedad, pero no pueden editarlos. Los valores mostrados se obtienen de la `ToString()` función . Puede escribir código de programa que establece el valor de la propiedad, por ejemplo, en un comando o regla.

### <a name="set-a-property-editor"></a>Establecimiento de un editor de propiedades

Agregue un atributo CLR a la propiedad de dominio con el formato siguiente:

```csharp
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]
```

Puede establecer el atributo en una propiedad mediante la entrada **Atributo** personalizado de la ventana Propiedades.

El tipo de `AnEditor` debe derivarse del tipo especificado en el segundo parámetro. El segundo parámetro debe ser <xref:System.Drawing.Design.UITypeEditor> o <xref:System.ComponentModel.ComponentEditor> . Para más información, consulte <xref:System.ComponentModel.EditorAttribute>.

Puede especificar su propio editor o un editor de .NET, como <xref:System.Windows.Forms.Design.FileNameEditor> o <xref:System.Drawing.Design.ImageEditor> . Por ejemplo, use el procedimiento siguiente para tener una propiedad en la que el usuario pueda escribir un nombre de archivo.

#### <a name="define-a-file-name-domain-property"></a>Definición de una propiedad de dominio de nombre de archivo

1. Agregue una propiedad de dominio a una clase de dominio en la definición de DSL.

2. Seleccione la nueva propiedad. En el **campo Atributo** personalizado de la ventana Propiedades, escriba el atributo siguiente. Para escribir este atributo, haga clic en los puntos suspensivos **[...]** y, a continuación, escriba el nombre del atributo y los parámetros por separado:

    ```csharp
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3. Deje el tipo de la propiedad de dominio en su valor predeterminado de **String**.

4. Para probar el editor, compruebe que los usuarios pueden abrir el editor de nombres de archivo para editar la propiedad de dominio.

    1. Presione CTRL+F5 o F5. En la solución de depuración, abra un archivo de prueba. Cree un elemento de la clase de dominio y selecciónelo.

    2. En la ventana Propiedades, seleccione la propiedad de dominio. El campo de valor muestra un botón de puntos suspensivos **[...]**.

    3. Haga clic en los puntos suspensivos. Aparece un cuadro de diálogo de archivo. Seleccione un archivo y cierre el cuadro de diálogo. La ruta de acceso del archivo es ahora el valor de la propiedad de dominio.

### <a name="define-your-own-property-editor"></a>Definición de su propio editor de propiedades

Puede definir su propio editor. Lo haría para permitir que el usuario edite un tipo definido o edite un tipo estándar de una manera especial. Por ejemplo, podría permitir que el usuario introduzca una cadena que represente una fórmula.

Para definir un editor, escriba una clase que se derive de <xref:System.Drawing.Design.UITypeEditor> . La clase debe invalidar:

- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, para interactuar con el usuario y actualizar el valor de propiedad.

- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, para especificar si el editor abrirá un cuadro de diálogo o proporcionará un menú desplegable.

También puede proporcionar una representación gráfica del valor de la propiedad que se mostrará en la cuadrícula de propiedades. Para ello, invalide `GetPaintValueSupported` y `PaintValue` .  Para más información, consulte <xref:System.Drawing.Design.UITypeEditor>.

> [!NOTE]
> Agregue el código en un archivo de código independiente en el **proyecto dsl.**

Por ejemplo:

```csharp
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor
{
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)
  {
    base.InitializeDialog(openFileDialog);
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";
    openFileDialog.Title = "Select a text file";
  }
}
```

Para usar este editor, establezca el **atributo personalizado** de una propiedad de dominio en:

```csharp
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]
```

Para más información, consulte <xref:System.Drawing.Design.UITypeEditor>.

## <a name="provide-a-drop-down-list-of-values"></a>Proporcionar una lista desplegable de valores

Puede proporcionar una lista de valores entre los que puede elegir un usuario.

> [!NOTE]
> Esta técnica proporciona una lista de valores que pueden cambiar en tiempo de ejecución. Si desea proporcionar una lista que no cambie, considere la posibilidad de usar en su lugar un tipo enumerado como el tipo de la propiedad de dominio.

Para definir una lista de valores estándar, agregue a la propiedad de dominio un atributo CLR que tenga el formato siguiente:

```csharp
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]
```

Defina una clase que se derive de <xref:System.ComponentModel.TypeConverter>. Agregue el código en un archivo independiente en el **proyecto dsl.** Por ejemplo:

```csharp
/// <summary>
/// Type converter that provides a list of values
/// to be displayed in the property grid.
/// </summary>
/// <remarks>This type converter returns a list
/// of the names of all "ExampleElements" in the
/// current store.</remarks>
public class MyTypeConverter : System.ComponentModel.TypeConverter
{
  /// <summary>
  /// Return true to indicate that we return a list of values to choose from
  /// </summary>
  /// <param name="context"></param>
  public override bool GetStandardValuesSupported
    (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Returns true to indicate that the user has
  /// to select a value from the list
  /// </summary>
  /// <param name="context"></param>
  /// <returns>If we returned false, the user would
  /// be able to either select a value from
  /// the list or type in a value that is not in the list.</returns>
  public override bool GetStandardValuesExclusive
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Return a list of the values to display in the grid
  /// </summary>
  /// <param name="context"></param>
  /// <returns>A list of values the user can choose from</returns>
  public override StandardValuesCollection GetStandardValues
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    // Try to get a store from the current context
    // "context.Instance"  returns the element(s) that
    // are currently selected i.e. whose values are being
    // shown in the property grid.
    // Note that the user could have selected multiple objects,
    // in which case context.Instance will be an array.
    Store store = GetStore(context.Instance);

    List<string> values = new List<string>();

    if (store != null)
    {
      values.AddRange(store.ElementDirectory
        .FindElements<ExampleElement>()
        .Select<ExampleElement, string>(e =>
      {
        return e.Name;
      }));
    }
    return new StandardValuesCollection(values);
  }

  /// <summary>
  /// Attempts to get to a store from the currently selected object(s)
  /// in the property grid.
  /// </summary>
  private Store GetStore(object gridSelection)
  {
    // We assume that "instance" will either be a single model element, or
    // an array of model elements (if multiple items are selected).

    ModelElement currentElement = null;

    object[] objects = gridSelection as object[];
    if (objects != null && objects.Length > 0)
    {
      currentElement = objects[0] as ModelElement;
    }
    else
    {
        currentElement = gridSelection as ModelElement;
    }

    return (currentElement == null) ? null : currentElement.Store;
  }

}
```

## <a name="see-also"></a>Consulte también

- [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
