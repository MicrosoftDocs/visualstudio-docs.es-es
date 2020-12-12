---
title: Personalizar campos de texto y de imagen
description: Obtenga información sobre cómo personalizar archivos de texto e imagen. También sepa que cuando se define un decorador de texto en una forma, se representa mediante un TextField.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6effda90580a184bb8ebfb8c4f4830dc6cb844d5
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362865"
---
# <a name="customizing-text-and-image-fields"></a>Personalizar campos de texto y de imagen
Al definir un decorador de texto en una forma, se representa mediante un TextField. Para obtener ejemplos de la inicialización de TextFields y otros ShapeFields, inspeccione Dsl\GeneratedCode\Shapes.cs en la solución DSL.

 Un TextField es un objeto que administra un área dentro de una forma, como el espacio asignado a una etiqueta. Una instancia de TextField se comparte entre muchas formas de la misma clase. La instancia de TextField no almacena el texto de la etiqueta por separado para cada instancia: en su lugar, el `GetDisplayText(ShapeElement)` método toma la forma como parámetro y puede buscar el texto en función del estado actual de la forma y su elemento de modelo.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Cómo se determina la apariencia de un campo de texto
 `DoPaint()`Se llama al método para mostrar el campo en la pantalla. Puede invalidar el valor predeterminado `DoPaint(),` o puede invalidar algunos de los métodos a los que llama. La siguiente versión simplificada de los métodos predeterminados puede ayudarle a entender cómo invalidar el comportamiento predeterminado:

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

 Hay varios otros pares de `Get` métodos y `Default` propiedades, como `DefaultMultipleLine/GetMultipleLine()` . Puede asignar un valor a la propiedad predeterminada para cambiar el valor de todas las instancias del campo de forma. Para que el valor varíe de una instancia de forma a otra, o depende del estado de la forma o su elemento de modelo, invalide el `Get` método.

## <a name="static-customizations"></a>Personalizaciones estáticas
 Si desea cambiar todas las instancias de este campo de forma, averigüe primero si puede establecer la propiedad en la definición de DSL. Por ejemplo, puede establecer el tamaño y el estilo de la fuente en el ventana Propiedades.

 Si no es así, invalide el `InitializeShapeFields` método de la clase de forma y asigne un valor a la `Default...` propiedad adecuada del campo de texto.

> [!WARNING]
> Para invalidar `InitializeShapeFields()` , debe establecer la propiedad **Generate Double derived** de la clase Shape en `true` en la definición de DSL.

 En este ejemplo, una forma tiene un campo de texto que se usará para los comentarios de los usuarios. Queremos usar la fuente de comentarios estándar. Dado que es una fuente estándar del conjunto de estilos, se puede establecer el identificador de fuente predeterminado:

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
 Para que la apariencia varíe en función del estado de una forma o de su elemento de modelo, derive su propia subclase de `TextField` e invalide uno o más `Get...` métodos. También debe invalidar el método InitializeShapeFields de la forma y reemplazar la instancia del TextField por una instancia de su propia clase.

 En el ejemplo siguiente se hace que la fuente de un campo de texto dependa del estado de una propiedad de dominio booleana del elemento de modelo de la forma.

 Para ejecutar este código de ejemplo, cree una nueva solución de DSL con la plantilla de idioma mínima. Agregue una propiedad de dominio booleana `AlternateState` a la clase de dominio ExampleElement. Agregue un elemento Decorator de icono a la clase ExampleShape y establezca su imagen en un archivo de mapa de bits. Haga clic en **transformar todas las plantillas**. Agregue un nuevo archivo de código en el proyecto DSL e inserte el código siguiente.

 Para probar el código, presione F5 y, en la solución de depuración, abra un diagrama de ejemplo. Debería aparecer el estado predeterminado del icono. Seleccione la forma y, en el ventana Propiedades, cambie el valor de la propiedad **AlternateState** . La fuente del nombre del elemento debe cambiar.

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

## <a name="style-sets"></a>Conjuntos de estilos
 En el ejemplo anterior se muestra cómo se puede cambiar el campo de texto a cualquier fuente que esté disponible. Sin embargo, un método preferible es cambiarlo a uno de un conjunto de estilos que está asociado con la forma o con la aplicación. Para ello, invalide <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> o GetTextBrushId ().

 Como alternativa, considere la posibilidad de cambiar el conjunto de estilos de la forma invalidando <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A> . Esto tiene el efecto de cambiar las fuentes y los pinceles de todos los campos de forma.

## <a name="customizing-image-fields"></a>Personalizar campos de imagen
 Al definir un decorador de imagen en una forma, y al definir una forma de imagen, el área en la que se muestra la forma se administra mediante un ImageField. Para obtener ejemplos de la inicialización de ImageFields y otros ShapeFields, revise Dsl\GeneratedCode\Shapes.cs en la solución DSL.

 Un ImageField es un objeto que administra un área dentro de una forma, como el espacio asignado a un elemento Decorator. Una instancia de ImageField se comparte entre muchas formas de la misma clase Shape. La instancia de ImageField no almacena una imagen independiente para cada forma: en su lugar, el `GetDisplayImage(ShapeElement)` método toma la forma como parámetro y puede buscar la imagen en función del estado actual de la forma y su elemento de modelo.

 Si desea un comportamiento especial, como una imagen variable, puede crear su propia clase derivada de ImageField.

#### <a name="to-create-a-subclass-of-imagefield"></a>Para crear una subclase de ImageField

1. Establezca la propiedad **genera Double derived** de la clase de forma primaria en la definición de DSL.

2. Invalide el `InitializeShapeFields` método de la clase Shape.

    - Cree un nuevo archivo de código en el proyecto DSL y escriba una definición de clase parcial para la clase Shape. Invalide la definición de método.

3. Inspeccione el código de `InitializeShapeFields` en DSL\GeneratedCode\Shapes.cs.

     En el método de invalidación, llame al método base y, a continuación, cree una instancia de su propia clase de campo de imagen. Úselo para reemplazar el campo de imagen normal de la `shapeFields` lista.

## <a name="dynamic-icons"></a>Iconos dinámicos
 En este ejemplo se realiza un cambio de icono que depende del estado del elemento de modelo de la forma.

> [!WARNING]
> En este ejemplo se muestra cómo crear un decorador de imagen dinámica. Pero si solo desea cambiar entre una o dos imágenes en función del estado de una variable de modelo, es más fácil crear varios decoradores de imagen, ubicarlos en la misma posición en la forma y, a continuación, establecer el filtro de visibilidad para que dependa de valores específicos de la variable de modelo. Para establecer este filtro, seleccione el mapa de formas en la definición de DSL, abra la ventana de detalles de DSL y haga clic en la pestaña decoradores.

 Para ejecutar este código de ejemplo, cree una nueva solución de DSL con la plantilla de idioma mínima. Agregue una propiedad de dominio booleana `AlternateState` a la clase de dominio ExampleElement. Agregue un elemento Decorator de icono a la clase ExampleShape y establezca su imagen en un archivo de mapa de bits. Haga clic en **transformar todas las plantillas**. Agregue un nuevo archivo de código en el proyecto DSL e inserte el código siguiente.

 Para probar el código, presione F5 y, en la solución de depuración, abra un diagrama de ejemplo. Debería aparecer el estado predeterminado del icono. Seleccione la forma y, en el ventana Propiedades, cambie el valor de la propiedad **AlternateState** . El icono debería aparecer girado hasta 90 grados, en esa forma.

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

## <a name="see-also"></a>Consulta también

- [Definir formas y conectores](../modeling/defining-shapes-and-connectors.md)
- [Establecer una imagen de fondo en un diagrama](../modeling/setting-a-background-image-on-a-diagram.md)
- [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)