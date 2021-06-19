---
title: Personalizar campos de texto y de imagen
description: Obtenga información sobre cómo personalizar archivos de texto e imagen. Aprenda también que, al definir un decorador de texto en una forma, se representa mediante un elemento TextField.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f52c4deda5b934a9b55c5ecfeec95ca633edf15e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389272"
---
# <a name="customizing-text-and-image-fields"></a>Personalizar campos de texto y de imagen
Cuando se define un decorador de texto en una forma, se representa mediante un elemento TextField. Para obtener ejemplos de la inicialización de TextFields y otros ShapeFields, inspeccione Dsl\GeneratedCode\Shapes.cs en la solución DSL.

 TextField es un objeto que administra un área dentro de una forma, como el espacio asignado a una etiqueta. Una instancia de TextField se comparte entre muchas formas de la misma clase. La instancia de TextField no almacena el texto de la etiqueta por separado para cada instancia: en su lugar, el método toma la forma como parámetro y puede buscar el texto que depende del estado actual de la forma y su elemento de `GetDisplayText(ShapeElement)` modelo.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Cómo se determina la apariencia de un campo de texto
 Se `DoPaint()` llama al método para mostrar el campo en la pantalla. Puede invalidar el valor predeterminado `DoPaint(),` o puede invalidar algunos de los métodos a los que llama. La siguiente versión simplificada de los métodos predeterminados puede ayudarle a entender cómo invalidar el comportamiento predeterminado:

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

 Hay otros pares de `Get` métodos y `Default` propiedades, como `DefaultMultipleLine/GetMultipleLine()` . Puede asignar un valor a la propiedad Default para cambiar el valor de todas las instancias del campo de forma. Para que el valor varíe de una instancia de forma a otra, o dependa del estado de la forma o de su elemento de modelo, invalide el `Get` método .

## <a name="static-customizations"></a>Personalizaciones estáticas
 Si desea cambiar todas las instancias de este campo de forma, primero debe averiguar si puede establecer la propiedad en la definición de DSL. Por ejemplo, puede establecer el estilo y el tamaño de fuente en el ventana Propiedades.

 Si no es así, invalide el método de la clase de forma y asigne un valor `InitializeShapeFields` a la propiedad adecuada del campo de `Default...` texto.

> [!WARNING]
> Para invalidar `InitializeShapeFields()` , debe establecer la propiedad **Generates Double Derived de** la clase de forma en en la `true` definición de DSL.

 En este ejemplo, una forma tiene un campo de texto que se usará para los comentarios del usuario. Queremos usar la fuente de comentario estándar. Dado que es una fuente estándar del conjunto de estilos, podemos establecer el identificador de fuente predeterminado:

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
 Para que la apariencia dependa del estado de una forma o de su elemento de modelo, derive su propia subclase de e `TextField` invalide uno o varios `Get...` métodos. También debe invalidar el método InitializeShapeFields de la forma y reemplazar la instancia de TextField por una instancia de su propia clase.

 En el ejemplo siguiente se hace que la fuente de un campo de texto dependa del estado de una propiedad de dominio booleano del elemento de modelo de la forma.

 Para ejecutar este código de ejemplo, cree una nueva solución DSL mediante la plantilla Lenguaje mínimo. Agregue una propiedad de dominio `AlternateState` booleano a la clase de dominio ExampleElement. Agregue un decorador de icono a la clase ExampleShape y establezca su imagen en un archivo de mapa de bits. Haga clic **en Transformar todas las plantillas.** Agregue un nuevo archivo de código en el proyecto DSL e inserte el código siguiente.

 Para probar el código, presione F5 y, en la solución de depuración, abra un diagrama de ejemplo. Debe aparecer el estado predeterminado del icono. Seleccione la forma y, en la ventana Propiedades, cambie el valor de la **propiedad AlternateState.** La fuente del nombre del elemento debe cambiar.

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
 En el ejemplo anterior se muestra cómo puede cambiar el campo de texto a cualquier fuente que esté disponible. Sin embargo, un método preferible es cambiarlo a uno de un conjunto de estilos asociado a la forma o a la aplicación. Para ello, invalide <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> o GetTextBrushId().

 Como alternativa, considere la posibilidad de cambiar el conjunto de estilos de la forma reemplazando <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A> . Esto tiene el efecto de cambiar las fuentes y pinceles de todos los campos de forma.

## <a name="customizing-image-fields"></a>Personalización de campos de imagen
 Al definir un decorador de imagen en una forma y al definir una forma de imagen, el área en la que se muestra la forma se administra mediante un objeto ImageField. Para obtener ejemplos de la inicialización de ImageFields y otros ShapeFields, inspeccione Dsl\GeneratedCode\Shapes.cs en la solución DSL.

 ImageField es un objeto que administra un área dentro de una forma, como el espacio asignado a un decorador. Una instancia de ImageField se comparte entre muchas formas de la misma clase de forma. La instancia imageField no almacena una imagen independiente para cada forma: en su lugar, el método toma la forma como parámetro y puede buscar la imagen dependiente del estado actual de la forma y su elemento `GetDisplayImage(ShapeElement)` de modelo.

 Si desea un comportamiento especial, como una imagen de variable, puede crear su propia clase derivada de ImageField.

#### <a name="to-create-a-subclass-of-imagefield"></a>Para crear una subclase de ImageField

1. Establezca la **propiedad Generates Double Derived de** la clase de forma primaria en la definición de DSL.

2. Invalide `InitializeShapeFields` el método de la clase de forma.

    - Cree un nuevo archivo de código en el proyecto DSL y escriba una definición de clase parcial para la clase de forma. Invalide la definición del método allí.

3. Inspeccione el código de `InitializeShapeFields` en DSL\GeneratedCode\Shapes.cs.

     En el método de invalidación, llame al método base y, a continuación, cree una instancia de su propia clase de campo de imagen. Use esta opción para reemplazar el campo de imagen normal de la `shapeFields` lista.

## <a name="dynamic-icons"></a>Iconos dinámicos
 Este ejemplo hace que un cambio de icono dependa del estado del elemento de modelo de la forma.

> [!WARNING]
> En este ejemplo se muestra cómo crear un decorador de imágenes dinámico. Pero si solo desea cambiar entre una o dos imágenes en función del estado de una variable de modelo, es más sencillo crear varios decoradores de imágenes, buscarlos en la misma posición en la forma y, a continuación, establecer el filtro Visibilidad para que dependa de valores específicos de la variable de modelo. Para establecer este filtro, seleccione el mapa de formas en la definición de DSL, abra la ventana Detalles de DSL y haga clic en la pestaña Decorators (Decoradores).

 Para ejecutar este código de ejemplo, cree una nueva solución DSL mediante la plantilla Lenguaje mínimo. Agregue una propiedad de dominio `AlternateState` booleano a la clase de dominio ExampleElement. Agregue un decorador de icono a la clase ExampleShape y establezca su imagen en un archivo de mapa de bits. Haga clic **en Transformar todas las plantillas.** Agregue un nuevo archivo de código en el proyecto DSL e inserte el código siguiente.

 Para probar el código, presione F5 y, en la solución de depuración, abra un diagrama de ejemplo. Debe aparecer el estado predeterminado del icono. Seleccione la forma y, en la ventana Propiedades, cambie el valor de la **propiedad AlternateState.** A continuación, el icono debería aparecer girado hasta 90 grados, en esa forma.

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