---
title: Propiedades de almacenamiento personalizados y calculados | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 153ff58e5ace618fbf9e6f0e3bb25614d21fc98a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="calculated-and-custom-storage-properties"></a>Propiedades calculadas y de almacenamiento personalizado
Todas las propiedades de dominio en un lenguaje específico de dominio (DSL) se pueden mostrar al usuario en el diagrama y en el Explorador de lenguaje y son accesibles mediante código del programa. Sin embargo, las propiedades difieren del modo en que se almacenan sus valores.  
  
## <a name="kinds-of-domain-properties"></a>Tipos de propiedades del dominio  
 En la definición DSL, puede establecer la **tipo** de una propiedad de dominio, como se muestra en la tabla siguiente:  
  
|Tipo de propiedad de dominio|Descripción|  
|--------------------------|-----------------|  
|**Estándar** (predeterminado)|Una propiedad de dominio que se guarda en el *almacenar* y serializado al archivo.|  
|**Calcula**|Una propiedad de dominio de solo lectura que no se guarda en el almacén, pero se calcula a partir de otros valores.<br /><br /> Por ejemplo, `Person.Age` se ha podido calcular desde `Person.BirthDate`.<br /><br /> Tendrá que proporcionar el código que realiza el cálculo. Normalmente, se calcula el valor de otras propiedades de dominio. Sin embargo, también puede utilizar los recursos externos.|  
|**Almacenamiento personalizado**|Una propiedad de dominio que no se guarda directamente en el almacén, pero puede ser get y set.<br /><br /> Tendrá que proporcionar los métodos que obtener y establecer el valor.<br /><br /> Por ejemplo, `Person.FullAddress` pueden almacenarse en `Person.StreetAddress`, `Person.City`, y `Person.PostalCode`.<br /><br /> También puede tener acceso a recursos externos como, por ejemplo, para obtener y establecer valores de una base de datos.<br /><br /> El código no debe establecer valores en el almacén cuando `Store.InUndoRedoOrRollback` es true. Vea [transacciones y establecedores personalizados](#setters).|  
  
## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Proporcionar el código para una propiedad calculada o personalizado de almacenamiento  
 Si establece el tipo de una propiedad de dominio calculado o almacenamiento personalizado, tendrá que proporcionar métodos de acceso. Cuando se compila una solución, un informe de errores le indicará lo que se requiere.  
  
#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Para definir un calculado o una propiedad de almacenamiento personalizado  
  
1.  En DslDefinition.dsl, seleccione la propiedad de dominio en el diagrama o en **DSL explorador**.  
  
2.  En el **propiedades** ventana, establezca el **tipo** campo **calculado** o **almacenamiento personalizado**.  
  
     Asegúrese de que ha establecido su **tipo** que desee.  
  
3.  Haga clic en **Transformar todas las plantillas** en la barra de herramientas de **el Explorador de soluciones**.  
  
4.  En el menú **Compilar** , haga clic en **Compilar solución**.  
  
     Recibirá el siguiente mensaje de error: "*YourClass* no contiene una definición de Get*YourProperty*."  
  
5.  Haga doble clic en el mensaje de error.  
  
     Se abrirá DomainRelationships.cs o Dsl\GeneratedCode\DomainClasses.cs. Por encima de la llamada de método resaltada, un comentario le solicita que proporcione una implementación de Get*YourProperty*().  
  
    > [!NOTE]
    >  Este archivo se genera a partir de DslDefinition.dsl. Si edita este archivo, los cambios se perderán la próxima vez que haga clic en **Transformar todas las plantillas**. En su lugar, agregue el método requerido en un archivo independiente.  
  
6.  Cree o abra un archivo de clase en una carpeta independiente, por ejemplo CustomCode\\*YourDomainClass*. cs.  
  
     Asegúrese de que el espacio de nombres es el mismo que el código generado.  
  
7.  En el archivo de clase, escribir una implementación parcial de la clase de dominio. En la clase, escribir una definición para el carácter que falta `Get` método que es similar al siguiente:  
  
    ```  
    namespace Company.FamilyTree  
    {  public partial class Person  
       {  int GetAgeValue()  
          { return System.DateTime.Today.Year - this.BirthYear; }  
    }  }  
    ```  
  
8.  Si establece **tipo** a **almacenamiento personalizado**, también tendrá que proporcionar un `Set` método. Por ejemplo:  
  
    ```  
    void SetAgeValue(int value)  
    { if (!Store.InUndoRedoOrRollback)  
        this.BirthYear =   
            System.DateTime.Today.Year - value; }  
    ```  
  
     El código no debe establecer valores en el almacén cuando `Store.InUndoRedoOrRollback` es true. Vea [transacciones y establecedores personalizados](#setters).  
  
9. Compile y ejecute la solución.  
  
10. Probar la propiedad. Asegúrese de que intente **deshacer** y **rehacer**.  
  
##  <a name="setters"></a> Las transacciones y establecedores personalizados  
 En el método Set de la propiedad de almacenamiento personalizado, no tendrá que abrir una transacción, ya que normalmente se llama al método dentro de una transacción activa.  
  
 Sin embargo, también se puede llamar al método conjunto si el usuario invoca la operación de deshacer o rehacer, o si se revierte una transacción. Cuando <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> es true, el método Set debe comportarse como sigue:  
  
-   No debe realizar cambios en el almacén, como asignar valores a otras propiedades de dominio. El Administrador de deshacer establece sus valores.  
  
-   Sin embargo, deben actualizar los recursos externos, como la base de datos o el contenido del archivo u objetos fuera de la tienda. Este modo se asegurará de que se mantengan en synchronism con los valores en el almacén.  
  
 Por ejemplo:  
  
```  
void SetAgeValue(int value)  
{   
  // If we are in Undo, no changes to Store objects:  
  if (!this.Store.InUndoRedoOrRollback)  
  {   
    this.BirthYear = System.DateTime.Today.Year - value;   
  }  
  // But always update external objects:  
  System.IO.File.WriteAllText(AgeFile, value);  
}  
```  
  
 Para obtener más información acerca de las transacciones, vea [navegar y actualizar un modelo de código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>Vea también  
 [Navegar y actualizar un modelo de código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Propiedades de las propiedades del dominio](../modeling/properties-of-domain-properties.md)   
 [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)