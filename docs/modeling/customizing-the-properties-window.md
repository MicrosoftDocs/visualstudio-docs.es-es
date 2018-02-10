---
title: "Personalización de la ventana de propiedades | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 545c8181cdaa3f13d2de04f13101d2678f9fd0ab
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="customizing-the-properties-window"></a>Personalizar la ventana Propiedades
Puede personalizar la apariencia y el comportamiento de la ventana Propiedades de su lenguaje específico de dominio (DSL) en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En la definición DSL, debe definir propiedades de dominio en cada clase de dominio. De forma predeterminada, cuando se selecciona una instancia de la clase, ya sea en un diagrama o en el Explorador de modelos, todas las propiedades de dominio se muestran en la ventana Propiedades. Esto permite ver o editar los valores de propiedades del dominio, incluso si no se ha asignado a los campos de la forma en el diagrama.  
  
## <a name="names-descriptions-and-categories"></a>Nombres, descripciones y categorías  
 **Nombre y nombre para mostrar**. En la definición de una propiedad de dominio, el nombre para mostrar de la propiedad es el nombre que aparece en tiempo de ejecución en la ventana Propiedades. Por el contrario, el nombre se usa al escribir código de programa para actualizar la propiedad. El nombre debe ser un nombre alfanumérico de CLR correcto, pero el nombre para mostrar puede contener espacios.  
  
 Cuando se establece el nombre de una propiedad en la definición DSL, su nombre para mostrar se establece automáticamente en una copia del nombre. Si escribe un nombre de mayúsculas y minúsculas Pascal como "FuelGauge", el nombre para mostrar automáticamente contendrá un espacio: "Indicador de combustible". Sin embargo, puede establecer explícitamente el nombre para mostrar con otro valor.  
  
 **Descripción**. La descripción de una propiedad de dominio aparece en dos lugares:  
  
-   En la parte inferior de la ventana Propiedades cuando el usuario selecciona la propiedad. Puede usarlo para explicar al usuario la propiedad que representa.  
  
-   En el código de programa generado. Si utiliza las funciones de documentación para extraer la documentación de API, aparecerá como la descripción de esta propiedad en la API.  
  
 **Categoría**. Una categoría es un encabezado en la ventana Propiedades.  
  
## <a name="exposing-style-features"></a>Exponer las características de estilo  
 Algunas de las características de elementos gráficos dinámicos se pueden representar o *expone* como propiedades del dominio. Una característica que se haya expuesto de esta manera puede actualizarse por el usuario y más fácilmente se pueden actualizar mediante código del programa.  
  
 Haga clic en una clase de la forma de definición DSL, seleccione **agregar expone**y, a continuación, elige una característica.  
  
 En las formas puede exponer el **color de relleno**, **OutlineColor**, **TextColor**, **OutlineDashStyle**,  **OutlineThickness** y **FillGradientMode** propiedades. En los conectores puede exponer el **Color**`,`**TextColor**, **DashStyle**, y **grosor** propiedades. En los diagramas pueden exponer el **color de relleno** y **TextColor** propiedades.  
  
## <a name="forwarding-displaying-properties-of-related-elements"></a>Reenvío: Muestre las propiedades de elementos relacionados  
 Cuando el usuario del ADSL selecciona un elemento en un modelo, las propiedades de ese elemento se muestran en la ventana Propiedades. Sin embargo, también puede mostrar las propiedades de elementos relacionados especificados. Esto es útil si ha definido un grupo de elementos que funciona juntos. Por ejemplo, podría definir un elemento principal y un elemento opcional del complemento. Si el elemento principal se asigna a una forma y el otro no, es útil ver todas sus propiedades como si estuvieran en un elemento.  
  
 Este efecto se denomina *reenvío de la propiedad*, y realiza automáticamente en varios casos. En otros casos, puede lograr propiedad reenvío mediante la definición de un descriptor de tipo de dominio.  
  
### <a name="default-property-forwarding-cases"></a>Casos de reenvío de propiedad predeterminados  
 Cuando el usuario selecciona una forma o conector o un elemento en el explorador, las siguientes propiedades se muestran en la ventana Propiedades:  
  
-   Las propiedades del dominio que se definen en la clase de dominio del elemento del modelo, los que se definen en las clases base incluidos. Una excepción es propiedades del dominio para el que ha establecido **es examinable** a `False`.  
  
-   Los nombres de elementos que están vinculados a través de relaciones que tienen una multiplicidad de 0.. 1. Esto proporciona un método práctico para ver si lo desea vincula elementos, incluso si no ha definido una asignación de conector para la relación.  
  
-   Propiedades del dominio de la relación de incrustación que tenga como destino el elemento. Dado que las relaciones de incrustación normalmente no se muestran explícitamente, esto permite al usuario ver sus propiedades.  
  
-   Propiedades del dominio que se definen en la forma seleccionada o el conector.  
  
### <a name="adding-property-forwarding"></a>Agregar propiedad reenvío  
 Para reenviar una propiedad, defina un descriptor de tipo de dominio. Si tiene una relación de dominio entre dos clases de dominio, puede usar un descriptor de tipo de dominio para establecer una propiedad de dominio en la primera clase en el valor de una propiedad de dominio en la segunda clase de dominio. Por ejemplo, si tiene una relación entre un **libreta** clase de dominio y un **autor** clase de dominio, puede usar un descriptor de tipo de dominio para realizar la **nombre** propiedad de un Del libro **autor** aparecen en la ventana Propiedades cuando el usuario selecciona el libro.  
  
> [!NOTE]
>  Reenvío de propiedad afecta a solo la ventana Propiedades cuando el usuario está editando un modelo. No se define una propiedad de dominio en la clase receptora. Si desea tener acceso a la propiedad de dominio reenviados en otras partes de la definición de DSL o en el código de programa, debe tener acceso al elemento de reenvío.  
  
 El siguiente procedimiento se supone que ha creado un DSL. Los primeros pasos resumen los requisitos previos.  
  
##### <a name="to-forward-a-property-from-another-element"></a>Para reenviar una propiedad de otro elemento  
  
1.  Crear un [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] solución que contenga al menos dos clases, que en este ejemplo se denominan **libreta** y **autor**. Debe haber una relación de cualquier tipo entre **libreta** y **autor**.  
  
     La multiplicidad de la función de origen (el rol en el **libreta** lado) debe ser de 0.. 1 o 1.. 1, para que cada **libreta** tiene uno **autor**.  
  
2.  En **DSL explorador**, haga clic en el **libreta** clase de dominio y, a continuación, haga clic en **agregar nueva DomainTypeDescriptor**.  
  
     Un nodo denominado **las rutas de acceso de descriptores de propiedad personalizada** aparece bajo la **Descriptor de tipos personalizado** nodo.  
  
3.  Haga clic en el **Descriptor de tipos personalizado** nodo y, a continuación, haga clic en **agregar nueva PropertyPath**.  
  
     Aparece una nueva ruta de acceso de propiedad en el **las rutas de acceso de descriptores de propiedad personalizada** nodo.  
  
4.  Seleccione la nueva ruta de acceso de propiedad y en el **propiedades** ventana, establezca **ruta de acceso a la propiedad** a la ruta de acceso del elemento del modelo adecuado.  
  
     Puede editar la ruta de acceso en una vista de árbol, haga clic en la flecha hacia abajo a la derecha de esta propiedad. Para obtener más información acerca de las rutas de acceso de dominio, consulte [sintaxis de ruta de acceso de dominio](../modeling/domain-path-syntax.md). Cuando se la ha editado, la ruta de acceso debe ser similar a **BookReferencesAuthor.Author/! Autor**.  
  
5.  Establecer **propiedad** a la **nombre** propiedad de dominio de **autor**.  
  
6.  Establecer **nombre para mostrar** a **crear nombre**.  
  
7.  Transformar todas las plantillas, compile y ejecute el ADSL.  
  
8.  En un diagrama del modelo, crear un libro, un autor y vincularlas mediante la relación de referencia. Seleccione el elemento "book" y, en la ventana Propiedades debería ver el nombre del autor además de las propiedades del libro. Cambiar el nombre del autor vinculado, o vincular el libro a un autor de diferentes y observar que cambia el nombre del autor del libro.  
  
## <a name="custom-property-editors"></a>Editores de propiedades personalizadas  
 La ventana de propiedad proporciona un valor predeterminado adecuado editor asociado para el tipo de cada propiedad de dominio. Por ejemplo, para un tipo enumerado, el usuario ve una lista desplegable y, para una propiedad numérica, el usuario puede escribir dígitos. Esto es cierto solo para los tipos integrados. Si especifica un tipo externo, el usuario podrá ver los valores de propiedad, pero no editarlo.  
  
 Sin embargo, puede especificar los editores y los tipos siguientes:  
  
1.  Otro editor que se usa con un tipo estándar. Por ejemplo, puede especificar un editor de ruta de acceso de archivo para una propiedad de cadena.  
  
2.  Un tipo externo para la propiedad de dominio y un editor para él.  
  
3.  Un editor. NET, como el editor de la ruta de acceso de archivo, o puede crear sus propias propiedades personalizadas del editor.  
  
     Una conversión entre un tipo externo y un tipo como cadena, que tiene un editor predeterminado.  
  
 En un DSL, un *tipo externo* es cualquier tipo que no es uno de los tipos simples (por ejemplo, un valor booleano o Int32) o una cadena.  
  
#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>Para definir una propiedad de dominio que tenga un tipo externo  
  
1.  En **el Explorador de soluciones**, agregue una referencia al ensamblado (DLL) que contiene el tipo externo, en la **Dsl** proyecto.  
  
     El ensamblado puede ser un ensamblado .NET o un ensamblado proporcionado por el usuario.  
  
2.  Agregar el tipo para el **tipos de dominio** lista, a menos que ya lo ha hecho.  
  
    1.  Abra DslDefinition.dsl y en **DSL explorador**, haga clic en el nodo raíz y, a continuación, haga clic en **Agregar nuevo tipo externo**.  
  
         Aparece una nueva entrada en el **tipos de dominio** nodo.  
  
        > [!WARNING]
        >  El elemento de menú no está en el nodo de raíz ADSL, el **tipos de dominio** nodo.  
  
    2.  En la ventana Propiedades, establezca el nombre y el espacio de nombres del nuevo tipo.  
  
3.  Agregar una propiedad de dominio a una clase de dominio de la manera habitual.  
  
     En la ventana Propiedades, seleccione el tipo externo en la lista desplegable de la **tipo** campo.  
  
 En esta fase, los usuarios pueden ver los valores de la propiedad, pero no pueden modificarlo. Los valores mostrados se obtienen de la `ToString()` (función). Puede escribir código de programa que establece el valor de la propiedad, por ejemplo en un comando o una regla.  
  
### <a name="setting-a-property-editor"></a>Establecer un Editor de propiedades  
 Agregue un atributo CLR para la propiedad de dominio, de la forma siguiente:  
  
```  
[System.ComponentModel.Editor (  
   typeof(AnEditor),  
   typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 Puede establecer el atributo en una propiedad mediante el **el atributo personalizado** entrada en la ventana Propiedades.  
  
 El tipo de `AnEditor` debe derivarse del tipo especificado en el segundo parámetro. El segundo parámetro debe ser <xref:System.Drawing.Design.UITypeEditor> o <xref:System.ComponentModel.ComponentEditor>. Para obtener más información, consulta <xref:System.ComponentModel.EditorAttribute>.  
  
 Puede especificar su propio editor o un editor proporcionado en el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], como <xref:System.Windows.Forms.Design.FileNameEditor> o <xref:System.Drawing.Design.ImageEditor>. Por ejemplo, utilice el procedimiento siguiente para tener una propiedad en el que el usuario puede escribir un nombre de archivo.  
  
##### <a name="to-define-a-file-name-domain-property"></a>Para definir una propiedad de dominio del nombre de archivo  
  
1.  Agregar una propiedad de dominio a una clase de dominio en su definición DSL.  
  
2.  Seleccione la nueva propiedad. En el **el atributo personalizado** en la ventana Propiedades, escriba el siguiente atributo. Para especificar este atributo, haga clic en los puntos suspensivos **[...]**  y, a continuación, escriba el nombre del atributo y los parámetros por separado:  
  
    ```  
    [System.ComponentModel.Editor (  
       typeof(System.Windows.Forms.Design.FileNameEditor)  
       , typeof(System.Drawing.Design.UITypeEditor))]  
  
    ```  
  
3.  Deje el tipo de la propiedad de dominio en su valor predeterminado de **cadena**.  
  
4.  Para probar el editor, compruebe que los usuarios pueden abrir el editor de nombre de archivo para editar la propiedad de dominio.  
  
    1.  Presione CTRL+F5 o F5. En la solución de depuración, abra un archivo de prueba. Crear un elemento de la clase de dominio y selecciónelo.  
  
    2.  En la ventana Propiedades, seleccione la propiedad de dominio. El campo de valor muestra un botón de puntos suspensivos **[...]** .  
  
    3.  Haga clic en el botón de puntos suspensivos. Aparece un cuadro de diálogo de archivo. Seleccione un archivo y cerrar el cuadro de diálogo. La ruta de acceso de archivo es ahora el valor de la propiedad de dominio.  
  
### <a name="defining-your-own-property-editor"></a>Definir su propio editor de propiedades  
 Puede definir su propio editor. Debe realizar esta opción para permitir al usuario para editar un tipo que haya definido, o para editar un tipo estándar de una manera especial. Por ejemplo, podría permitir al usuario que escriba una cadena que representa una fórmula.  
  
 Definir un editor escribiendo una clase que se deriva de <xref:System.Drawing.Design.UITypeEditor>. La clase debe invalidar:  
  
-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, para interactuar con el usuario y actualizar el valor de propiedad.  
  
-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, para especificar si el editor se abre un cuadro de diálogo o proporcionar un menú desplegable.  
  
 También puede proporcionar una representación gráfica del valor de la propiedad que se mostrará en la cuadrícula de propiedades. Para ello, invalide `GetPaintValueSupported`, y `PaintValue`.  Para obtener más información, consulta <xref:System.Drawing.Design.UITypeEditor>.  
  
> [!NOTE]
>  Agregue el código en un archivo de código independiente en el **Dsl** proyecto.  
  
 Por ejemplo:  
  
```  
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
  
 Para utilizar este editor, establezca el **el atributo personalizado** de una propiedad de dominio para:  
  
```  
[System.ComponentModel.Editor (  
   typeof(MyNamespace.TextFileNameEditor)  
   , typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 Para obtener más información, consulta <xref:System.Drawing.Design.UITypeEditor>.  
  
## <a name="providing-a-drop-down-list-of-values"></a>Proporciona una lista desplegable de valores  
 Puede proporcionar una lista de valores para un usuario que puede elegir.  
  
> [!NOTE]
>  Esta técnica proporciona una lista de valores que pueden cambiar en tiempo de ejecución. Si desea proporcionar una lista que no cambia, considere en su lugar con un tipo enumerado como el tipo de la propiedad de dominio.  
  
 Para definir una lista de valores estándar, se agrega a la propiedad de dominio de un atributo CLR que tiene la forma siguiente:  
  
```  
[System.ComponentModel.TypeConverter   
(typeof(MyTypeConverter))]  
  
```  
  
 Defina una clase que se derive de <xref:System.ComponentModel.TypeConverter>. Agregue el código en un archivo independiente en el **Dsl** proyecto. Por ejemplo:  
  
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
  
## <a name="see-also"></a>Vea también  
 [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)