---
title: "Personalizar la ventana Propiedades | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, Propiedades (ventana)"
ms.assetid: b6658de5-4e85-4628-93b2-5cc12f63d25b
caps.latest.revision: 20
caps.handback.revision: 20
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Personalizar la ventana Propiedades
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede personalizar el aspecto y el comportamiento de la ventana propiedades en el lenguaje específico \(DSL\) en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  En la definición de DSL, se definen las propiedades de dominio en cada clase de dominio.  De forma predeterminada, al seleccionar una instancia de la clase, en un diagrama o en el Explorador del modelo, cada propiedad de dominio se muestra en la ventana propiedades.  Esto permite ver y editar los valores de las propiedades de dominio, incluso si no se ha asignado para formar campos en el diagrama.  
  
## nombres, descripciones, y categorías  
 **nombre y nombre para mostrar**.  En la definición de una propiedad de dominio, el nombre para mostrar de la propiedad es el nombre que aparece en tiempo de ejecución en la ventana propiedades.  Por el contrario, se utiliza el nombre al escribir código de programa para actualizar la propiedad.  El nombre debe ser un nombre alfanumérico correcto de CLR, aunque el nombre para mostrar puede contener espacios.  
  
 Cuando se establece el nombre de una propiedad en la definición de DSL, su nombre para mostrar establecen en una copia del nombre.  Si escribe un nombre ha Pascal como “FuelGauge”, el nombre para mostrar contendrá automáticamente un espacio: “Marcador de la gasolina”.  Sin embargo, puede establecer el nombre para mostrar de forma explícita a otro valor.  
  
 **Description**.  La descripción de una propiedad de dominio aparece en dos lugares:  
  
-   El fondo de la ventana propiedades cuando el usuario selecciona la propiedad.  Puede utilizarlo para explicar el usuario lo que representa la propiedad.  
  
-   en el código de programa generado.  Si utiliza las funciones de la documentación para extraer la documentación de la API, aparecerá como la descripción de esta propiedad en la API.  
  
 **Category**.  una categoría es un encabezado en la ventana Propiedades.  
  
## Exponer las características de estilo  
 Algunas de las características dinámicas de elementos gráficos se pueden representar o *exponer* como propiedades del dominio.  Una característica que se ha expuesto de esta manera se puede actualizar por el usuario y se resultará más fácil actualizar por código de programa.  
  
 Haga clic con el botón secundario en una clase shape en la definición de DSL, elija **agregue expuesto**, y elija una característica.  
  
 En las formas puede exponer **color de relleno**, las propiedades de **OutlineColor**, de **TextColor**, de **OutlineDashStyle**, de **OutlineThickness** y de **FillGradientMode** .  En los conectores puede exponer **Color**`,`**TextColor**, **DashStyle**, y las propiedades de **grosor** .  En diagramas puede exponer **color de relleno** y las propiedades de **TextColor** .  
  
## El reenvío: Mostrar propiedades de los elementos relacionados  
 Cuando el usuario ADSL selecciona un elemento en un modelo, las propiedades del elemento se muestran en la ventana propiedades.  Sin embargo, también puede mostrar las propiedades de elementos relacionados especificados.  Esto resulta útil si tiene definido un grupo de elementos que funcionen conjuntamente.  Por ejemplo, puede definir un elemento principal y un elemento de complemento opcional.  Si el elemento principal se asigna a una forma y el otro no, es útil ver todas sus propiedades como si fueran en un elemento.  
  
 Este efecto se denomina *propiedad que reenvía*, y se produce automáticamente en varios casos.  En otros casos, puede obtener la propiedad que reenvía definiendo un descriptor de dominio.  
  
### Propiedad predeterminada que reenvía los casos  
 Cuando el usuario selecciona una forma o un conector, o un elemento del Explorador, las propiedades siguientes se muestran en la ventana Propiedades:  
  
-   Las propiedades del dominio que se definen en la clase de dominio del elemento de modelo, incluidos los que se definen en las clases base.  Una excepción son propiedades de dominio para las que ha establecido **Es modificable** a `False`.  
  
-   Los nombres de los elementos vinculados con las relaciones que tienen una multiplicidad de 0..1.  Esto proporciona un método cómodo para ver elementos opcionalmente vinculados, incluso si no define una asignación de conector para la relación.  
  
-   Propiedades del dominio de la relación de incrustación destinado al elemento.  Dado que inserta relaciones no se muestran generalmente explícitamente, esto permite al usuario ver sus propiedades.  
  
-   Propiedades del dominio que se definen en la forma o el conector seleccionado.  
  
### El reenvío de la propiedad de suma  
 Para reenviar una propiedad, se define un descriptor de dominio.  Si tiene una relación de dominio entre dos clases de dominio, puede utilizar un descriptor de dominio para establecer una propiedad de dominio en la primera clase al valor de una propiedad de dominio en la segunda clase de dominio.  Por ejemplo, si tiene una relación entre una clase de dominio book y una clase de dominio author, puede utilizar un descriptor de dominio para que la propiedad Name del autor de un libro aparece en la ventana Propiedades cuando el usuario selecciona el bloc de notas.  
  
> [!NOTE]
>  El reenvío de la propiedad sólo afecta a la ventana Propiedades cuando el usuario edita un modelo.  No define una propiedad de dominio en la clase receptora.  Si desea tener acceso a la propiedad reenviada de dominio en otras partes de la definición de DSL o en código de programa, debe tener acceso al elemento de reenvío.  
  
 El procedimiento siguiente supone que ha creado ADSL.  los primeros pasos resumen los requisitos previos.  
  
##### para reenviar una propiedad de otro elemento  
  
1.  Cree una solución de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] que contiene al menos dos clases, que en este ejemplo se denominan Book y autor.  Debe haber una relación de cualquiera tipo entre el control y el autor.  
  
     La multiplicidad del rol del origen \(el rol en el lado book\) debe ser 0..1 o 1..1, de modo que cada libro tiene un autor.  
  
2.  En **Explorador ADSL**, haga clic con el botón secundario en la clase de dominio book, y haga clic en **Agregue un nuevo DomainTypeDescriptor**.  
  
     Un nodo denominado **Rutas de descriptores personalizados de propiedad** aparece bajo el nodo de **Descriptor de tipos personalizado** .  
  
3.  Haga clic con el botón secundario en el nodo de **Descriptor de tipos personalizado** , y haga clic en **Agregar nuevo PropertyPath**.  
  
     Una nueva ruta de acceso de propiedad aparece bajo el nodo de **Rutas de descriptores personalizados de propiedad** .  
  
4.  Seleccione la nueva ruta de acceso de la propiedad y, en la ventana de **Propiedades** , establezca **Ruta de acceso a la propiedad** a la ruta de acceso de elemento modelo adecuado.  
  
     Puede modificar el trazado en una vista de árbol haciendo clic en la flecha abajo a la derecha de esta propiedad.  Para obtener más información sobre las rutas de dominio, vea [Sintaxis de las rutas de dominio](../modeling/domain-path-syntax.md).  Cuando se ha editado, la ruta debe ser similar a **BookReferencesAuthor.Author\/\!Author**.  
  
5.  Establezca **Propiedad** a la propiedad del dominio de **Name** author.  
  
6.  Establezca **Nombre para mostrar** al nombre de autor.  
  
7.  Transformar Todas las plantillas, compile y ejecute ADSL.  
  
8.  En un diagrama del modelo, cree un libro, autor, y vínculo mediante la relación de referencia.  Seleccione el elemento de libro y, en la ventana Propiedades debería ver el nombre del autor además de las propiedades del libro.  Cambie el nombre de autor vinculado, o enlace el libro a otro autor, y observe que el nombre del autor del libro.  
  
## editores de propiedades personalizados  
 La ventana propiedad proporciona una experiencia predeterminada de edición correcta para el tipo de cada propiedad de dominio.  Por ejemplo, para un tipo enumerado, el usuario ve una lista desplegable, y para una propiedad numérica, el usuario puede escribir dígitos.  Esto solo es aplicable para los tipos integrados.  Si especifica un tipo externo, el usuario podrá ver los valores de propiedad, pero no modificarlos.  
  
 Sin embargo, puede especificar los editores y los tipos siguientes:  
  
1.  otro editor que se utiliza con un tipo estándar.  Por ejemplo, podría especificar un editor de ruta de acceso para una propiedad de cadena.  
  
2.  Un externo con tipo de la propiedad de dominio, y un editor para él.  
  
3.  Un editor de .NET como el editor de la ruta de acceso, o puede crear dispone del editor de propiedades personalizado.  
  
     Una conversión entre un tipo externo y un tipo como string, que tiene un editor predeterminado.  
  
 En DSL, *un tipo externo* es cualquier tipo que no es uno de los tipos simples \(como boolean o Int32\) o de cadena.  
  
#### Para definir una propiedad de dominio que tiene un tipo externo  
  
1.  En **Explorador de soluciones**, agregue una referencia al ensamblado \(DLL\) que contiene el tipo externo, en el proyecto de **Dsl** .  
  
     El ensamblado puede ser un ensamblado.NET, o un ensamblado proporcionado por el usuario.  
  
2.  Agregue el tipo a la lista de **Tipos de dominio** , a menos que tenga ya hecho.  
  
    1.  Abra DslDefinition.dsl y, en **Explorador ADSL**, haga clic con el botón secundario en el nodo raíz, y haga clic en **Agregue el nuevo tipo externo**.  
  
         Aparece una nueva entrada bajo el nodo de **Tipos de dominio** .  
  
        > [!WARNING]
        >  El elemento de menú está en el nodo raíz ADSL, no el nodo de **Tipos de dominio** .  
  
    2.  Especifique el nombre y el espacio de nombres del nuevo tipo en la ventana Propiedades.  
  
3.  Agregue una propiedad de dominio a una clase de dominio de la forma habitual.  
  
     En la ventana Propiedades, seleccione el tipo externo de la lista desplegable del campo de **tipo** .  
  
 En esta fase, los usuarios pueden ver los valores de propiedad, pero no pueden editarla.  Los valores mostrados se obtienen de la función de `ToString()` .  Podría escribir código de programa que establece el valor de la propiedad, como en un comando o una regla.  
  
### establecer un editor de propiedades  
 Agregue un atributo de CLR a la propiedad de dominio, con el siguiente formato:  
  
```  
[System.ComponentModel.Editor (  
   typeof(AnEditor),  
   typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 Puede establecer el atributo en una propiedad utilizando la entrada de **atributo personalizado** en la ventana Propiedades.  
  
 El tipo de `AnEditor` debe derivarse del tipo especificado en el segundo parámetro.  el segundo parámetro debe ser <xref:System.Drawing.Design.UITypeEditor> o <xref:System.ComponentModel.ComponentEditor>.  Para obtener más información, vea <xref:System.ComponentModel.EditorAttribute>.  
  
 Puede especificar dispone del editor, o un editor proporcionado en [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], como <xref:System.Windows.Forms.Design.FileNameEditor> o <xref:System.Drawing.Design.ImageEditor>.  Por ejemplo, utilice el siguiente procedimiento para tener una propiedad en la que el usuario puede especificar un nombre de archivo.  
  
##### Para definir una propiedad de dominio filename  
  
1.  Agregue una propiedad de dominio a una clase de dominio en la definición del ADSL.  
  
2.  Seleccione la nueva propiedad.  En el campo de **atributo personalizado** en la ventana Propiedades, escriba el siguiente atributo.  Para especificar este atributo, haga clic en los puntos suspensivos **\[...\]** y escriba el nombre de atributo y los parámetros por separado:  
  
    ```  
    [System.ComponentModel.Editor (  
       typeof(System.Windows.Forms.Design.FileNameEditor)  
       , typeof(System.Drawing.Design.UITypeEditor))]  
  
    ```  
  
3.  Deje el tipo de la propiedad de dominio en la configuración predeterminada de **Cadena**.  
  
4.  Para probar el editor, compruebe que los usuarios pueden abrir el editor de nombre de archivo para modificar la propiedad del dominio.  
  
    1.  Presione CTRL\+F5 o F5.  En la solución de depuración, abra un archivo de prueba.  Cree un elemento de la clase de dominio y selecciónelo.  
  
    2.  En la ventana Propiedades, seleccione la propiedad del dominio.  El campo Valor muestra puntos suspensivos **\[...\]**.  
  
    3.  Haga clic en los puntos suspensivos.  un cuadro de diálogo de archivos aparece.  Seleccione un archivo y cerrar el cuadro de diálogo.  La ruta de acceso es ahora el valor de la propiedad del dominio.  
  
### definición poseer el editor de propiedades  
 Puede definir dispone del editor.  Debe hacer esto para permitir que el usuario o editar un tipo que tiene definido, o editar un tipo estándar de una manera especial.  Por ejemplo, podría permitir al usuario que escriba una cadena que representa una fórmula.  
  
 Define un editor escribiendo una clase que se deriva de <xref:System.Drawing.Design.UITypeEditor>.  la clase debe reemplazar:  
  
-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, interactuar con el usuario y actualizar el valor de propiedad.  
  
-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, especificar si el editor abrirá un cuadro de diálogo o proporcionará un menú desplegable.  
  
 También puede proporcionar una representación gráfica del valor de propiedad que se mostrarán en la cuadrícula de propiedades.  Para ello, reemplace `GetPaintValueSupported`, y `PaintValue`.  Para obtener más información, vea <xref:System.Drawing.Design.UITypeEditor>.  
  
> [!NOTE]
>  Agregue el código en un archivo de código independiente en el proyecto de **Dsl** .  
  
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
  
 Para utilizar este editor, establezca **atributo personalizado** de una propiedad de dominio:  
  
```  
[System.ComponentModel.Editor (  
   typeof(MyNamespace.TextFileNameEditor)  
   , typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 Para obtener más información, vea <xref:System.Drawing.Design.UITypeEditor>.  
  
## Proporcionar una lista desplegable de valores  
 Puede proporcionar una lista de valores de un usuario elija.  
  
> [!NOTE]
>  Esta técnica proporciona una lista de valores que pueden cambiar en tiempo de ejecución.  Si desea proporcionar una lista que no cambia, considere en lugar de utilizar un tipo enumerado como el tipo de la propiedad de dominio.  
  
 Para definir una lista de valores estándar, se agregan a la propiedad de dominio un atributo CLR que tiene el formato siguiente:  
  
```  
[System.ComponentModel.TypeConverter   
(typeof(MyTypeConverter))]  
  
```  
  
 Defina una clase que se derive de <xref:System.ComponentModel.TypeConverter>.  agregue el código en un archivo independiente en el proyecto de **Dsl** .  Por ejemplo:  
  
```c#  
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
  
## Vea también  
 [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)