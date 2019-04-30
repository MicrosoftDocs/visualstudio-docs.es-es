---
title: Controladores de cambio de valor de propiedad de dominio | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
ms.assetid: 96d8f392-045e-4bc5-b165-fbaa470a3e16
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c8dac5a999b4f11fb066edfc1b1d4c057a999bae
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442986"
---
# <a name="domain-property-value-change-handlers"></a>Controladores de los cambios de valor de propiedad de dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En un lenguaje específico de dominio de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], cuando el valor de una propiedad de dominio cambia, se llama a los métodos `OnValueChanging()` y `OnValueChanged()` en el controlador de la propiedad de dominio. Para responder al cambio, puede invalidar estos métodos.  
  
## <a name="overriding-the-property-handler-methods"></a>Invalidar los métodos del controlador de propiedad   
 Cada propiedad de dominio de su lenguaje específico de dominio es administrada por una clase que está anidada dentro de su clase de dominio primaria. Su nombre sigue el formato *PropertyName*PropertyHandler. Puede inspeccionar esta clase de controlador de propiedad en el archivo **Dsl\Generated Code\DomainClasses.cs**. En la clase, se llama a `OnValueChanging()` inmediatamente antes de que cambie el valor, y se llama a `OnValueChanged()` inmediatamente después de que cambie el valor.  
  
 Por ejemplo, suponga que tiene una clase de dominio denominada `Comment` que tiene una propiedad de dominio de cadena denominada `Text` y una propiedad de entero denominada `TextLengthCount`. Para hacer que `TextLengthCount` siempre para contener la longitud de la `Text` cadena, podría escribir el código siguiente en un archivo independiente en el proyecto Dsl:  
  
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
  
- Se llama a ambos métodos del controlador de propiedad cuando el usuario realiza cambios en una propiedad de dominio y cuando el código de programa asigna un valor diferente a la propiedad.  
  
- Solo se llama a los métodos cuando el valor cambia realmente. No se invoca al controlador si el código de programa asigna un valor que es igual al valor actual.  
  
- Las propiedades de dominio de almacenamiento calculadas y personalizadas no tienen los métodos OnValueChanged y OnValueChanging.  
  
- No puede usar un controlador de cambios para modificar el nuevo valor. Si quiere hacerlo, para restringir el valor de un intervalo determinado, por ejemplo, defina una `ChangeRule`.  
  
- No puede agregar un controlador de cambios a una propiedad que represente un rol de una relación. En su lugar, defina una `AddRule` y una `DeleteRule` en la clase de relación. Estas reglas se desencadenan cuando se crean o se cambian vínculos. Para obtener más información, consulte [propagar cambios en el modelo de reglas de](../modeling/rules-propagate-changes-within-the-model.md).  
  
### <a name="changes-in-and-out-of-the-store"></a>Cambios dentro y fuera del almacén  
 Se llama a los métodos de controlador de propiedad dentro de la transacción que inició el cambio. Por lo tanto, puede realizar más cambios en el almacén sin abrir una nueva transacción. Los cambios podrían provocar llamadas adicionales del controlador.  
  
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
  
### <a name="canceling-a-change"></a>Cancelar un cambio  
 Si quiere evitar un cambio, puede revertir la transacción actual. Por ejemplo, quizás quiera asegurarse de que una propiedad está dentro de un intervalo específico.  
  
```  
if (newValue > 10)   
{ store.TransactionManager.CurrentTransaction.Rollback();  
  System.Windows.Forms.MessageBox.Show("Value must be less than 10");  
}  
  
```  
  
### <a name="alternative-technique-calculated-properties"></a>Técnica alternativa: propiedades calculadas  
 El ejemplo anterior muestra cómo se puede usar OnValueChanged() para propagar los valores de una propiedad de dominio a otra. Cada propiedad tiene su propio valor almacenado.  
  
 En su lugar, podría considerar la posibilidad de definir la propiedad derivada como una propiedad calculada. En ese caso, la propiedad no tiene su propio almacenamiento y su función de definición se evalúa siempre que se necesita su valor. Para obtener más información, consulte [calculadas y las propiedades de almacenamiento personalizado](../modeling/calculated-and-custom-storage-properties.md).  
  
 En lugar del ejemplo anterior, puede establecer el **tipo** campo de `TextLengthCount` sea **Calculated** en la definición de DSL. Desea proporcionar su propia **obtener** método para esta propiedad de dominio. El **obtener** método devolvería la longitud actual de la `Text` cadena.  
  
 Sin embargo, un posible inconveniente de las propiedades calculadas es que la expresión se evalúa cada vez que se usa el valor, lo que podría suponer un problema de rendimiento. Además, las propiedades calculadas no tienen ningún método OnValueChanging() y OnValueChanged().  
  
### <a name="alternative-technique-change-rules"></a>Técnica alternativa: reglas de cambio  
 Si define una regla de cambio, se ejecuta al final de una transacción en la que cambia el valor de una propiedad.  Para obtener más información, consulte [propagar cambios en el modelo de reglas de](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Si se realizan varios cambios en una transacción, la regla de cambio se ejecuta cuando se completan todos. Por el contrario, los métodos OnValue... se ejecutan cuando algunos de los cambios no se han realizado. Según lo que quiera lograr, una regla de cambio podría ser más apropiada.  
  
 También puede usar una regla de cambio para ajustar el nuevo valor de la propiedad para que esté dentro de un rango específico.  
  
> [!WARNING]
> Si una regla realiza cambios en el contenido del almacén, se podrían desencadenar otras reglas y controladores de propiedad. Si una regla cambia la propiedad que la desencadenó, se llamará de nuevo. Debe asegurarse de que las definiciones de regla no producen un desencadenamiento infinito.  
  
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
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 En el ejemplo siguiente se invalida el controlador de propiedad de una propiedad de dominio y notifica al usuario cuando una propiedad de la clase de dominio `ExampleElement` ha cambiado.  
  
### <a name="code"></a>Código  
  
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
