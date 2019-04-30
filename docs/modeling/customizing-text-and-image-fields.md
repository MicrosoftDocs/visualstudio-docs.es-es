---
title: Personalizar campos de texto y de imagen
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 607809b05688931b139b27fec1803719b928dfea
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445822"
---
# <a name="customizing-text-and-image-fields"></a>Personalizar campos de texto y de imagen
Al definir un elemento decorator de texto en una forma, se representa mediante un campo de texto. Para obtener ejemplos de la inicialización de TextFields y otros ShapeFields, inspeccionar Dsl\GeneratedCode\Shapes.cs en su solución de DSL.

 Un campo de texto es un objeto que administra un área dentro de una forma, como el espacio asignado a una etiqueta. Una instancia de TextField se comparte entre las muchas formas de la misma clase. La instancia de TextField no almacena el texto de la etiqueta por separado para cada instancia: en su lugar, el `GetDisplayText(ShapeElement)` toma la forma como un parámetro de método y puede buscar el texto que depende el estado actual de la forma y su elemento de modelo.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Cómo se determina la apariencia de un campo de texto
 El `DoPaint()` se llama al método muestra el campo en la pantalla. O bien puede invalidar el valor predeterminado `DoPaint(),` o puede invalidar algunos de los métodos que llama. La siguiente versión simplificada de los métodos predeterminados puede ayudarle a entender cómo invalidar el comportamiento predeterminado:

```csharp
// Simplified version:
public override void DoPaint(DiagramPaintEventArgs e, ShapeElement parentShape)
{
  string text = GetDisplayText(shape);
  StringFormat format = GetStringFormat(parentShape);
  Brush brush = GetTextBrush(e.View, shape);
  using (Font font = GetFont(shape))
  {
    e.Graphics.DrawString(text, font, brush, format);
  }
}
// StringFormat determines whether the string is centered etc.
// To customize statically for all instances of this shape field,
// assign to DefaultStringFormat.
// To customize dynamically or per shape, override this:
public virtual StringFormat GetStringFormat(ShapeElement shape)
{ return DefaultStringFormat; }

// Override to customize the displayed string:
public virtual string GetDisplayText(ShapeElement shape)
{ return this.GetValue(shape).ToString(); }

// Brush determines the text color.
// To change the brush for every field, change the shape's styleset.
// To customize to a brush in the style set, override GetTextBrushId.
// To change the brush to non-standard color, override this.
// Should take account of whether selected.
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }

// Brush ID selects a brush from a StyleSet.
// Either return a member of DiagramBrushes
// or add your own brush to the shape or application's styleset.
// Override this to change dynamically or per instance.
// To change statically, just assign to default values.
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;
}

// Font determines the shape and size of the text.
// To change the font for every field, change the shape's styleset.
// To customize to a font in the style set, override GetFontId.
// To change the font to a non-standard font, override this.
public virtual Font GetFont(ShapeElement shape)
{ return shape.StyleSet.GetFont(GetFontId(shape)); }

// Selects a font from a styleset.
// Either return a member of DiagramFonts or
// add your own font to the shape or application's styleset.
// To change statically for all instances of this field,
// assign to DefaultFontId.
// To change per shape or dynamically, override this.
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)
{ return DefaultFontId; }
```

 Hay varios otros pares de `Get` métodos y `Default` propiedades, como `DefaultMultipleLine/GetMultipleLine()`. Puede asignar un valor a la propiedad para cambiar el valor para todas las instancias del campo de forma predeterminada. Para que el valor variar con respecto a la instancia de una forma a otra o dependiente del estado de la forma o su elemento de modelo, invalidar el `Get` método.

## <a name="static-customizations"></a>Personalizaciones estáticas
 Si desea cambiar todas las instancias de este campo de forma, en primer lugar, averigüe si se puede establecer la propiedad en la definición de DSL. Por ejemplo, puede establecer el tamaño de fuente y estilo en la ventana Propiedades.

 Si no, a continuación, invalide el `InitializeShapeFields` método de la clase shape y asignarle un valor adecuado `Default...` propiedad del campo de texto.

> [!WARNING]
> Para invalidar `InitializeShapeFields()`, debe establecer el **genera doble derivada** propiedad de la clase shape para `true` en la definición de DSL.

 En este ejemplo, una forma tiene un campo de texto que se usará para los comentarios del usuario. Deseamos usar la fuente estándar de comentario. Dado que es una fuente estándar en el conjunto de estilos, podemos establecer el identificador de fuente predeterminado:

```csharp

 partial class ExampleShape
{   protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Find and update comment field:
      TextField commentField = ShapeElement.FindShapeField(shapeFields, "CommentDecorator") as TextField;
      // Use the standard font for comments:
      commentField.DefaultFontId = DiagramFonts.CommentText;
```

## <a name="dynamic-customizations"></a>Personalizaciones dinámicas
 Para hacer que la apariencia varían depende del estado de una forma o su elemento de modelo, derive su propia subclase de `TextField` y reemplazar uno o varios `Get...` métodos. También debe invalidar el método de InitializeShapeFields de la forma y reemplazar la instancia de TextField con una instancia de su propia clase.

 El ejemplo siguiente pone la fuente de un campo de texto dependiente del estado de una propiedad de dominio booleano de la forma elemento de modelo.

 Para ejecutar este código de ejemplo, cree una nueva solución DSL con la plantilla de lenguaje mínimo. Agregar una propiedad de dominio booleano `AlternateState` a la clase de dominio ExampleElement. Agregue un elemento decorator de icono a la clase ExampleShape y establezca su imagen a un archivo de mapa de bits. Haga clic en **Transformar todas las plantillas**. Agregue un nuevo archivo de código en el proyecto DSL e inserte el código siguiente.

 Para probar el código, presione F5 y, en la solución de depuración, abra un diagrama de ejemplo. Debería aparecer el estado predeterminado del icono. Seleccione la forma y en la ventana Propiedades, cambie el valor de la **AlternateState** propiedad. Debe cambiar la fuente del nombre del elemento.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...

  partial class ExampleShape
  {
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Replace the text field for NameDecorator:
      TextField oldField = ShapeElement.FindShapeField(shapeFields, "NameDecorator") as TextField;
      shapeFields.Remove(oldField);
      // Replace with my text field based on DSL Definition values:
      MyTextField newField = new MyTextField(oldField);
      shapeFields.Add(newField);
    }
  }
  /// <summary>
  /// Dynamic font depends on state of model element.
  /// </summary>
  public class MyTextField : TextField
  {
    public MyTextField(TextField prototype)
      : base(prototype.Name)
    {
      DefaultText = prototype.DefaultText;
      DefaultFocusable = prototype.DefaultFocusable;
      DefaultAutoSize = prototype.DefaultAutoSize;
      AnchoringBehavior.MinimumHeightInLines = prototype.AnchoringBehavior.MinimumHeightInLines;
      AnchoringBehavior.MinimumWidthInCharacters = prototype.AnchoringBehavior.MinimumWidthInCharacters;
      DefaultAccessibleState = prototype.DefaultAccessibleState;
    }

    public override System.Drawing.Font GetFont(ShapeElement parentShape)
    {
      // Access the Boolean domain property of the model element:
      if ((parentShape.ModelElement as ExampleElement).AlternateState)
        return new System.Drawing.Font("Callisto", 14.0f,
               System.Drawing.FontStyle.Italic |
               System.Drawing.FontStyle.Bold);
      else
        return base.GetFont(parentShape);
    }

  }
```

## <a name="style-sets"></a>Conjuntos de estilo
 El ejemplo anterior muestra cómo puede cambiar el campo de texto para cualquier fuente que está disponible. Sin embargo, un método preferible es cámbielo a uno de un conjunto de estilos que está asociado a la forma o con la aplicación. Para ello, invalide <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> o GetTextBrushId().

 Como alternativa, considere la posibilidad de cambiar el conjunto de estilos de la forma mediante la invalidación <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>. Esto tiene el efecto de cambiar las fuentes y los pinceles de todos los campos de forma.

## <a name="customizing-image-fields"></a>Personalizar campos de imagen
 Cuando se define un decorador de imagen en una forma, y cuando se define una forma de imagen, el área en que se muestra la forma se administra mediante un ImageField. Para obtener ejemplos de la inicialización de ImageFields y otros ShapeFields, inspeccionar Dsl\GeneratedCode\Shapes.cs en su solución de DSL.

 Un ImageField es un objeto que administra un área dentro de una forma, como el espacio asignado a un objeto decorator. Una instancia de ImageField se comparte entre las muchas formas de la misma clase de forma. La instancia de ImageField no almacena una imagen independiente para cada forma: en su lugar, el `GetDisplayImage(ShapeElement)` toma la forma como un parámetro de método y puede buscar la imagen dependen del estado actual de la forma y su elemento de modelo.

 Si desea un comportamiento especial, como una imagen de la variable, puede crear su propia clase derivada de ImageField.

#### <a name="to-create-a-subclass-of-imagefield"></a>Para crear una subclase de ImageField

1. Establecer el **genera doble derivada** propiedad de la clase de la forma primaria en la definición de DSL.

2. Invalidar el `InitializeShapeFields` método de la clase shape.

    - Cree un nuevo archivo de código en el proyecto DSL y escribir una definición de clase parcial para la clase shape. Reemplazar la definición de método no existe.

3. Inspeccione el código de `InitializeShapeFields` en DSL\GeneratedCode\Shapes.cs.

     En el método de invalidación, llame al método base y, a continuación, cree una instancia de su propia clase de campo de imagen. Úselo para reemplazar el campo de imagen normal en el `shapeFields` lista.

## <a name="dynamic-icons"></a>Iconos dinámicos
 En este ejemplo hace que un icono Cambiar dependen del estado de la forma elemento de modelo.

> [!WARNING]
> En este ejemplo se muestra cómo hacer que un decorador de imagen dinámica. Pero si solo desea cambiar entre una o dos imágenes según el estado de una variable de modelo, resulta más fácil de crear varios elementos Decorator de imagen, buscarlos en la misma posición en la forma y, a continuación, establezca el filtro de visibilidad a depender de valores específicos del modelo variable. Para establecer este filtro, seleccione el mapa de formas en la definición de DSL, abra la ventana Detalles de DSL y haga clic en la pestaña elementos Decorator.

 Para ejecutar este código de ejemplo, cree una nueva solución DSL con la plantilla de lenguaje mínimo. Agregar una propiedad de dominio booleano `AlternateState` a la clase de dominio ExampleElement. Agregue un elemento decorator de icono a la clase ExampleShape y establezca su imagen a un archivo de mapa de bits. Haga clic en **Transformar todas las plantillas**. Agregue un nuevo archivo de código en el proyecto DSL e inserte el código siguiente.

 Para probar el código, presione F5 y, en la solución de depuración, abra un diagrama de ejemplo. Debería aparecer el estado predeterminado del icono. Seleccione la forma y en la ventana Propiedades, cambie el valor de la **AlternateState** propiedad. A continuación, debe aparecer el icono Girar a través de 90 grados, de esa forma.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...
partial class ExampleShape
{
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    /// <param name="shapeFields"></param>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);

      // Replace the image field:
      ShapeField oldField = ShapeElement.FindShapeField(shapeFields, "IconDecorator");
      shapeFields.Remove(oldField);
      // Must keep the same name:
      MyImageField newField = new MyImageField(oldField.Name);
      shapeFields.Add(newField);
      newField.DefaultImage = (oldField as ImageField).DefaultImage.Clone() as System.Drawing.Image;
    }
  }

  public class MyImageField : ImageField
  {
    public MyImageField(string tag) : base(tag) { }

    /// <summary>
    /// Get the image for this field in the given shape.
    /// </summary>
    public override System.Drawing.Image GetDisplayImage(ShapeElement parentShape)
    {
      ExampleElement element = parentShape.ModelElement as ExampleElement;
      if (element.AlternateState == true)
        return AlternateImage;
      else
        return base.GetDisplayImage(parentShape);
    }

    private System.Drawing.Image alternateImage;
    public System.Drawing.Image AlternateImage
    {
      get
      {
        if (alternateImage == null)
        {
          // Alternate image is a copy of the default, rotated by 90 degrees:
          alternateImage = this.DefaultImage.Clone() as System.Drawing.Image;
          alternateImage.RotateFlip(System.Drawing.RotateFlipType.Rotate90FlipNone);
        }
        return alternateImage;
      }
    }
  }
}
```

## <a name="see-also"></a>Vea también

- [Definir formas y conectores](../modeling/defining-shapes-and-connectors.md)
- [Establecer una imagen de fondo en un diagrama](../modeling/setting-a-background-image-on-a-diagram.md)
- [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)