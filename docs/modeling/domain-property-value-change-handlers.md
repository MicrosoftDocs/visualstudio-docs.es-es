---
title: "Controladores de los cambios de valor de propiedad de dominio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, invalidar controladores de eventos"
ms.assetid: 96d8f392-045e-4bc5-b165-fbaa470a3e16
caps.latest.revision: 24
caps.handback.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Controladores de los cambios de valor de propiedad de dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En un lenguaje específico de dominio de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], cuando el valor de una propiedad de dominio cambia, se llama a los métodos `OnValueChanging()` y `OnValueChanged()` en el controlador de la propiedad de dominio.  Para responder al cambio, puede invalidar estos métodos.  
  
## Invalidar los métodos del controlador de propiedad  
 Cada propiedad de dominio de su lenguaje específico de dominio es administrada por una clase que está anidada dentro de su clase de dominio primaria.  Su nombre tiene el formato *NombrePropiedad*PropertyHandler.  Puede inspeccionar esta clase de controlador de propiedad en el archivo **Dsl\\Generated Code\\DomainClasses.cs**.  En la clase, se llama a `OnValueChanging()` inmediatamente antes de que cambie el valor, y se llama a `OnValueChanged()` inmediatamente después de que cambie el valor.  
  
 Por ejemplo, supongamos que tiene una clase de dominio llamada `Comment` con una propiedad de dominio de tipo cadena llamada `Text` y una propiedad de tipo entero llamada `TextLengthCount`.  Para que `TextLengthCount` contenga siempre la longitud de la cadena `Text`, podría escribir el código siguiente en un archivo diferente del proyecto Dsl:  
  
```  
// Domain Class "Comment":  
public partial class Comment   
{  
  // Domain Property "Text":  
  partial class TextPropertyHandler  
  {  
    protected override void OnValueChanging(CommentBase element, string oldValue, string newValue)  
    {  
      base.OnValueChanging(element, oldValue, newValue);  
  
      // To update values outside the Store, write code here.  
  
      // Let the transaction manager handle undo:  
      Store store = element.Store;  
      if (store.InUndoRedoOrRollback || store.InSerializationTransaction) return;  
  
      // Update values in the Store:  
      this.TextLengthCount = newValue.Length;  
    }  
  }  
}  
  
```  
  
 Observe los siguientes aspectos sobre los controladores de propiedad:  
  
-   Se llama a ambos métodos del controlador de propiedad cuando el usuario realiza cambios en una propiedad de dominio y cuando el código de programa asigna un valor diferente a la propiedad.  
  
-   Solo se llama a los métodos cuando el valor cambia realmente.  No se invoca al controlador si el código de programa asigna un valor que es igual al valor actual.  
  
-   Las propiedades de dominio de almacenamiento calculadas y personalizadas no tienen los métodos OnValueChanged y OnValueChanging.  
  
-   No puede usar un controlador de cambios para modificar el nuevo valor.  Si quiere hacerlo, para restringir el valor de un intervalo determinado, por ejemplo, defina una `ChangeRule`.  
  
-   No puede agregar un controlador de cambios a una propiedad que represente un rol de una relación.  En su lugar, defina una `AddRule` y una `DeleteRule` en la clase de relación.  Estas reglas se desencadenan cuando se crean o se cambian vínculos.  Para obtener más información, vea [Reglas de propagan los cambios en el modelo](../modeling/rules-propagate-changes-within-the-model.md).  
  
### Cambios dentro y fuera del almacén  
 Se llama a los métodos de controlador de propiedad dentro de la transacción que inició el cambio.  Por lo tanto, puede realizar más cambios en el almacén sin abrir una nueva transacción.  Los cambios podrían provocar llamadas adicionales del controlador.  
  
 Cuando una transacción se está deshaciendo, rehaciendo o revirtiendo, no debe realizar cambios en el almacén, es decir, cambios en los elementos, relaciones, formas, conectores o diagramas del modelo, o en sus propiedades.  
  
 Además, normalmente no debería actualizar los valores cuando el modelo se está cargando desde el archivo.  
  
 Los cambios al modelo deben protegerse con una prueba como esta:  
  
```  
if (!store.InUndoRedoOrRollback   
         && !store. InSerializationTransaction)  
{ this.TextLength = ...; // in-store changes   
}  
```  
  
 En cambio, si el controlador de propiedad propaga los cambios fuera de la tienda, por ejemplo, a un archivo, una base de datos o variables que no son del almacén, siempre debe realizar estos cambios de manera que los valores externos se actualicen cuando el usuario invoque las acciones de deshacer o rehacer.  
  
### Cancelar un cambio  
 Si quiere evitar un cambio, puede revertir la transacción actual.  Por ejemplo, quizás quiera asegurarse de que una propiedad está dentro de un intervalo específico.  
  
```  
if (newValue > 10)   
{ store.TransactionManager.CurrentTransaction.Rollback();  
  System.Windows.Forms.MessageBox.Show("Value must be less than 10");  
}  
  
```  
  
### Técnica alternativa: propiedades calculadas  
 El ejemplo anterior muestra cómo se puede usar OnValueChanged\(\) para propagar los valores de una propiedad de dominio a otra.  Cada propiedad tiene su propio valor almacenado.  
  
 En su lugar, podría considerar la posibilidad de definir la propiedad derivada como una propiedad calculada.  En ese caso, la propiedad no tiene su propio almacenamiento y su función de definición se evalúa siempre que se necesita su valor.  Para obtener más información, vea [Propiedades de almacenamiento personalizados y calculados](../modeling/calculated-and-custom-storage-properties.md).  
  
 En lugar del ejemplo anterior, podría establecer el campo **Kind** de `TextLengthCount` en **Calculated** en la definición de DSL.  Para esta propiedad de dominio, proporcionaría su propio método **Get**.  El método **Get** devolvería la longitud actual de la cadena `Text`.  
  
 Sin embargo, un posible inconveniente de las propiedades calculadas es que la expresión se evalúa cada vez que se usa el valor, lo que podría suponer un problema de rendimiento.  Además, las propiedades calculadas no tienen ningún método OnValueChanging\(\) y OnValueChanged\(\).  
  
### Técnica alternativa: reglas de cambio  
 Si define una regla de cambio, se ejecuta al final de una transacción en la que cambia el valor de una propiedad.  Para obtener más información, vea [Reglas de propagan los cambios en el modelo](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Si se realizan varios cambios en una transacción, la regla de cambio se ejecuta cuando se completan todos.  Por el contrario, los métodos OnValue...  se ejecutan cuando algunos de los cambios no se han realizado.  Según lo que quiera lograr, una regla de cambio podría ser más apropiada.  
  
 También puede usar una regla de cambio para ajustar el nuevo valor de la propiedad para que esté dentro de un rango específico.  
  
> [!WARNING]
>  Si una regla realiza cambios en el contenido del almacén, se podrían desencadenar otras reglas y controladores de propiedad.  Si una regla cambia la propiedad que la desencadenó, se llamará de nuevo.  Debe asegurarse de que las definiciones de regla no producen un desencadenamiento infinito.  
  
```  
using Microsoft.VisualStudio.Modeling;   
...  
// Change rule on the domain class Comment:  
[RuleOn(typeof(Comment), FireTime = TimeToFire.TopLevelCommit)]   
class MyCommentTrimRule : ChangeRule  
{  
  public override void   
    ElementPropertyChanged(ElementPropertyChangedEventArgs e)  
  {  
    base.ElementPropertyChanged(e);  
    Comment comment = e.ModelElement as Comment;  
  
    if (comment.Text.StartsWith(" ") || comment.Text.EndsWith(" "))  
      comment.Text = comment.Text.Trim();  
    // If changed, rule will trigger again.  
  }  
}  
  
// Register the rule:   
public partial class MyDomainModel   
{  
 protected override Type[] GetCustomDomainModelTypes()   
 { return new Type[] { typeof(MyCommentTrimRule) };   
 }  
}  
  
```  
  
## Ejemplo  
  
### Descripción  
 En el ejemplo siguiente se invalida el controlador de propiedad de una propiedad de dominio y notifica al usuario cuando una propiedad de la clase de dominio `ExampleElement` ha cambiado.  
  
### Código  
  
```  
using DslModeling = global::Microsoft.VisualStudio.Modeling;  
using DslDesign = global::Microsoft.VisualStudio.Modeling.Design;  
  
namespace msft.FieldChangeSample  
{  
  public partial class ExampleElement  
  {  
    internal sealed partial class NamePropertyHandler  
    {  
      protected override void OnValueChanged(ExampleElement element,  
         string oldValue, string newValue)  
      {  
        if (!this.Store.InUndoRedoOrRollback)  
        {  
           // make in-store changes here...  
        }  
        // This part is called even in undo:  
        System.Windows.Forms.MessageBox.Show("Value Has Changed");  
        base.OnValueChanged(element, oldValue, newValue);  
      }  
    }  
  }  
}  
```  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Modeling.DomainPropertyValueHandler%602.OnValueChanged%2A>   
 <xref:Microsoft.VisualStudio.Modeling.DomainPropertyValueHandler%602.OnValueChanging%2A>