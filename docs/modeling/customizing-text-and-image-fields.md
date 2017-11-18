---
title: Personalizar campos de imagen y de texto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7259fc0-5afa-4356-b27e-5641e01628a9
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: c551b368ba695f4d78fbe7a885f3896160fa93ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="customizing-text-and-image-fields"></a>Personalizar campos de texto y de imagen
Cuando se define un decorador de texto en una forma, se representa mediante un campo de texto. Para obtener ejemplos de la inicialización de TextFields y otros ShapeFields, inspeccionar Dsl\GeneratedCode\Shapes.cs en la solución DSL.  
  
 Un campo de texto es un objeto que administra un área dentro de una forma, por ejemplo, el espacio asignado a una etiqueta. Una instancia de campo de texto se comparte entre las muchas formas de la misma clase. La instancia del campo de texto no almacena el texto de la etiqueta por separado para cada instancia de: en su lugar, el `GetDisplayText(ShapeElement)` método toma la forma como un parámetro y puede buscar el texto que depende del estado actual de la forma y su elemento de modelo.  
  
## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Cómo se determina la apariencia de un campo de texto  
 El `DoPaint()` método se llama para mostrar el campo en la pantalla. O bien puede invalidar el valor predeterminado `DoPaint(),` o puede invalidar algunos de los métodos que llama. La siguiente versión simplificada de los métodos predeterminados puede ayudarle a entender cómo invalidar el comportamiento predeterminado:  
  
```  
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
  
 Hay varios otros pares de `Get` métodos y `Default` propiedades, como `DefaultMultipleLine/GetMultipleLine()`. Puede asignar un valor a la propiedad predeterminada para cambiar el valor para todas las instancias del campo forma. Para que el valor variar con respecto a la instancia de una forma a otro, o depende del estado de la forma o su elemento de modelo, invalide el `Get` método.  
  
## <a name="static-customizations"></a>Personalizaciones estáticas  
 Si desea cambiar todas las instancias de este campo de forma, averiguar si puede establecer la propiedad en la definición DSL en primer lugar. Por ejemplo, puede establecer el tamaño de fuente y estilo en la ventana Propiedades.  
  
 Si no es así, a continuación, invalidar la `InitializeShapeFields` método de la clase shape y asignar un valor a la correspondiente `Default...` propiedad del campo de texto.  
  
> [!WARNING]
>  Para invalidar `InitializeShapeFields()`, debe establecer el **genera derivados dobles** propiedad de la clase de forma que `true` en la definición DSL.  
  
 En este ejemplo, una forma tiene un campo de texto que se usará para los comentarios del usuario. Debe usar la fuente de comentario estándar. Dado que es una fuente estándar desde el conjunto de estilos, podemos establecer el identificador de fuente predeterminado:  
  
```  
  
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
 Para hacer la apariencia varían dependa del estado de una forma o su elemento de modelo, derive su propia subclase de `TextField` y reemplazar uno o varios `Get...` métodos. También debe invalidar el método de InitializeShapeFields de la forma y reemplazar la instancia del campo de texto con una instancia de su propia clase.  
  
 En el ejemplo siguiente se pasa a la fuente de un campo de texto dependiente del estado de una propiedad de dominio booleano del elemento de modelo de la forma.  
  
 Para ejecutar este código de ejemplo, cree una nueva solución DSL mediante la plantilla de idioma mínima. Agregar una propiedad de dominio booleano `AlternateState` a la clase de dominio ExampleElement. Agregue un elemento decorator de icono a la clase ExampleShape y establezca su imagen de un archivo de mapa de bits. Haga clic en **Transformar todas las plantillas de**. Agregue un nuevo archivo de código en el proyecto DSL e inserte el código siguiente.  
  
 Para probar el código, presione F5 y, en la solución de depuración, abra un diagrama de ejemplo. Debería aparecer el estado predeterminado del icono. Seleccione la forma y en la ventana Propiedades, cambie el valor de la **AlternateState** propiedad. Debe cambiar la fuente del nombre del elemento.  
  
```  
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
 El ejemplo anterior muestra cómo se puede cambiar el campo de texto para cualquier fuente que está disponible. Sin embargo, un método preferible consiste en cambiar a uno de un conjunto de estilos que está asociado con la forma o a la aplicación. Para ello, invalide <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> o GetTextBrushId().  
  
 Como alternativa, considere la posibilidad de cambiar el conjunto de estilo de la forma mediante la invalidación <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>. Esto tiene el efecto de cambiar las fuentes y los pinceles para todos los campos de la forma.  
  
## <a name="customizing-image-fields"></a>Personalizar campos de imagen  
 Cuando se define un decorador de imagen en una forma, y cuando se define una forma de imagen, un ImageField administra el área en la que se muestra la forma. Para obtener ejemplos de la inicialización de ImageFields y otros ShapeFields, inspeccionar Dsl\GeneratedCode\Shapes.cs en la solución DSL.  
  
 Un ImageField es un objeto que administra un área dentro de una forma, por ejemplo, el espacio asignado a un decorador. Una instancia de ImageField se comparte entre las muchas formas de la misma clase de forma. La instancia de ImageField no almacena una imagen independiente para cada forma: en su lugar, el `GetDisplayImage(ShapeElement)` método toma la forma como un parámetro y puede buscar la imagen depende del estado actual de la forma y su elemento de modelo.  
  
 Si desea un comportamiento especial, como una imagen de variable, puede crear su propia clase derivada de ImageField.  
  
#### <a name="to-create-a-subclass-of-imagefield"></a>Para crear una subclase de ImageField  
  
1.  Establecer el **genera derivados dobles** propiedad de la clase de forma primaria en la definición DSL.  
  
2.  Invalidar el `InitializeShapeFields` método de la clase de forma.  
  
    -   Cree un nuevo archivo de código en el proyecto DSL y escribir una definición de clase parcial para la clase shape. Reemplazar la definición de método no existe.  
  
3.  Inspeccionar el código de `InitializeShapeFields` en DSL\GeneratedCode\Shapes.cs.  
  
     En el método de invalidación, llame al método base y, a continuación, cree una instancia de su propia clase de campo de imagen. Utilícelo para reemplazar el campo de imagen normal en el `shapeFields` lista.  
  
## <a name="dynamic-icons"></a>Iconos dinámicos  
 Este ejemplo convierte un icono Cambiar dependen del estado del elemento de modelo de la forma.  
  
> [!WARNING]
>  Este ejemplo muestra cómo hacer que un elemento decorator de imagen dinámica. Pero si solo desea cambiar entre una o dos imágenes según el estado de una variable de modelo, resulta más fácil crear varias decoradores de imagen, encontrarlos en la misma posición en la forma y, a continuación, configure el filtro de visibilidad para dependen de los valores específicos del modelo variable. Para establecer este filtro, seleccione el mapa de formas en la definición DSL, abra la ventana de detalles de DSL y haga clic en la pestaña decoradores.  
  
 Para ejecutar este código de ejemplo, cree una nueva solución DSL mediante la plantilla de idioma mínima. Agregar una propiedad de dominio booleano `AlternateState` a la clase de dominio ExampleElement. Agregue un elemento decorator de icono a la clase ExampleShape y establezca su imagen de un archivo de mapa de bits. Haga clic en **Transformar todas las plantillas de**. Agregue un nuevo archivo de código en el proyecto DSL e inserte el código siguiente.  
  
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
 [Definir formas y conectores](../modeling/defining-shapes-and-connectors.md)   
 [Configuración de una imagen de fondo en un diagrama](../modeling/setting-a-background-image-on-a-diagram.md)   
 [Navegar y actualizar un modelo de código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)