---
title: Propiedades calculadas y de almacenamiento personalizado
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 52915f0bac2bd172daf909541ecfa86396d90a5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "76115200"
---
# <a name="calculated-and-custom-storage-properties"></a>Propiedades calculadas y de almacenamiento personalizado
Todas las propiedades de dominio en un lenguaje específico de dominio (DSL) se pueden mostrar al usuario en el diagrama y en el explorador de lenguajes, y se puede tener acceso a ellas mediante el código del programa. Sin embargo, las propiedades se diferencian en la forma en que se almacenan sus valores.

## <a name="kinds-of-domain-properties"></a>Tipos de propiedades de dominio
 En la definición de DSL, puede establecer el **tipo** de una propiedad de dominio, como se muestra en la tabla siguiente:

|Tipo de propiedad de dominio|Descripción|
|-|-|
|**Estándar** (predeterminado)|Propiedad de dominio que se guarda en el *almacén* y se serializa en el archivo.|
|**Calculadas**|Propiedad de dominio de solo lectura que no se guarda en el almacén, pero que se calcula a partir de otros valores.<br /><br /> Por ejemplo, `Person.Age` podría calcularse a partir de `Person.BirthDate` .<br /><br /> Debe proporcionar el código que realiza el cálculo. Normalmente, el valor se calcula desde otras propiedades de dominio. Sin embargo, también puede usar recursos externos.|
|**Almacenamiento personalizado**|Propiedad de dominio que no se guarda directamente en el almacén, pero que puede ser get y set.<br /><br /> Debe proporcionar los métodos que obtienen y establecen el valor.<br /><br /> Por ejemplo, `Person.FullAddress` podría almacenarse en `Person.StreetAddress` , `Person.City` y `Person.PostalCode` .<br /><br /> También puede tener acceso a recursos externos, por ejemplo, para obtener y establecer los valores de una base de datos.<br /><br /> El código no debe establecer valores en el almacén cuando `Store.InUndoRedoOrRollback` es true. Vea [transacciones y establecedores personalizados](#setters).|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Proporcionar el código para una propiedad de almacenamiento calculada o personalizada
 Si establece el tipo de una propiedad de dominio en almacenamiento calculado o personalizado, tiene que proporcionar métodos de acceso. Al compilar la solución, un informe de errores le indicará lo que es necesario.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Para definir una propiedad de almacenamiento calculada o personalizada

1. En DslDefinition. DSL, seleccione la propiedad de dominio en el diagrama o en el **Explorador de DSL**.

2. En la ventana **propiedades** , establezca el campo **Kind** en almacenamiento **calculado** o **personalizado**.

     Asegúrese de que también ha establecido su **tipo** en lo que desea.

3. Haga clic en **transformar todas las plantillas** en la barra de herramientas de **Explorador de soluciones**.

4. En el menú **Compilar**, haga clic en **Compilar solución**.

     Recibe el mensaje de error siguiente: "*YourClass* no contiene una definición para Get*supropiedad*".

5. Haga doble clic en el mensaje de error.

     Se abre Dsl\GeneratedCode\DomainClasses.cs o DomainRelationships.cs. Encima de la llamada al método resaltado, un comentario le pide que proporcione una implementación para Get*supropiedad*().

    > [!NOTE]
    > Este archivo se genera a partir de DslDefinition. DSL. Si edita este archivo, los cambios se perderán la próxima vez que haga clic en **transformar todas las plantillas**. En su lugar, agregue el método requerido en un archivo independiente.

6. Cree o abra un archivo de clase en una carpeta independiente, por ejemplo, CustomCode \\ *YourDomainClass*. cs.

     Asegúrese de que el espacio de nombres es el mismo que en el código generado.

7. En el archivo de clase, escriba una implementación parcial de la clase de dominio. En la clase, escriba una definición para el `Get` método que falta, similar al ejemplo siguiente:

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8. Si establece **Kind** en el **almacenamiento personalizado**, también tendrá que proporcionar un `Set` método. Por ejemplo:

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     El código no debe establecer valores en el almacén cuando `Store.InUndoRedoOrRollback` es true. Vea [transacciones y establecedores personalizados](#setters).

9. Compile y ejecute la solución.

10. Pruebe la propiedad. Asegúrese de intentar **Deshacer** y **rehacer**.

## <a name="transactions-and-custom-setters"></a><a name="setters"></a> Transacciones y establecedores personalizados
 En el método Set de la propiedad de almacenamiento personalizado, no es necesario abrir una transacción, porque normalmente se llama al método dentro de una transacción activa.

 Sin embargo, también se podría llamar al método Set si el usuario invoca deshacer o rehacer, o si se revierte una transacción. Cuando <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> es true, el método Set debe comportarse de la siguiente manera:

- No debe realizar cambios en el almacén, como la asignación de valores a otras propiedades de dominio. El administrador de deshacer establecerá sus valores.

- Sin embargo, debe actualizar los recursos externos, como el contenido de la base de datos o del archivo, u objetos fuera del almacén. Esto garantizará que se mantienen en synchronism con los valores del almacén.

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

 Para obtener más información acerca de las transacciones, vea [navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Consulte también

- [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Propiedades de las propiedades de dominio](../modeling/properties-of-domain-properties.md)
- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)
