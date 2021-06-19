---
title: Propiedades calculadas y de almacenamiento personalizado
description: Obtenga información sobre cómo todas las propiedades de dominio de un lenguaje específico de dominio (DSL) se pueden mostrar al usuario en el diagrama y en el explorador de idiomas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f98dca6759b9e4a77e71139b6d9ec9b394d99b04
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385427"
---
# <a name="calculated-and-custom-storage-properties"></a>Propiedades calculadas y de almacenamiento personalizado
Todas las propiedades de dominio de un lenguaje específico de dominio (DSL) se pueden mostrar al usuario en el diagrama y en el explorador de idiomas, y se puede acceder a ellos mediante código de programa. Sin embargo, las propiedades difieren en la forma en que se almacenan sus valores.

## <a name="kinds-of-domain-properties"></a>Tipos de propiedades de dominio
 En la definición de DSL, puede establecer **el tipo de** una propiedad de dominio, como se muestra en la tabla siguiente:

|Tipo de propiedad de dominio|Descripción|
|-|-|
|**Estándar** (valor predeterminado)|Propiedad de dominio que se guarda en el *almacén y* se serializa en archivo.|
|**Calculadas**|Propiedad de dominio de solo lectura que no se guarda en el almacén, pero que se calcula a partir de otros valores.<br /><br /> Por ejemplo, `Person.Age` se podría calcular a partir de `Person.BirthDate` .<br /><br /> Debe proporcionar el código que realiza el cálculo. Normalmente, el valor se calcula a partir de otras propiedades de dominio. Sin embargo, también puede usar recursos externos.|
|**Almacenamiento personalizado**|Una propiedad de dominio que no se guarda directamente en el almacén, pero que se puede obtener y establecer.<br /><br /> Debe proporcionar los métodos que obtienen y establecen el valor.<br /><br /> Por ejemplo, `Person.FullAddress` podría almacenarse en `Person.StreetAddress` , y `Person.City` `Person.PostalCode` .<br /><br /> También puede acceder a recursos externos, por ejemplo, para obtener y establecer valores de una base de datos.<br /><br /> El código no debe establecer valores en el almacén cuando `Store.InUndoRedoOrRollback` es true. Vea [Transacciones y setters personalizados.](#setters)|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Proporcionar el código para una propiedad de almacenamiento calculada o personalizada
 Si establece el tipo de una propiedad de dominio en Almacenamiento calculado o Personalizado, tendrá que proporcionar métodos de acceso. Al compilar la solución, un informe de errores le mostrará lo que se necesita.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Para definir una propiedad de almacenamiento calculada o personalizada

1. En DslDefinition.dsl, seleccione la propiedad de dominio en el diagrama o en el **Explorador de DSL.**

2. En la **ventana Propiedades,** establezca el **campo Tipo** en **Almacenamiento** calculado **o Personalizado.**

     Asegúrese de que también ha establecido su **tipo** en lo que desea.

3. Haga **clic en Transformar todas las** plantillas en la barra de herramientas **Explorador de soluciones**.

4. En el menú **Compilar** , haga clic en **Compilar solución**.

     Recibirá el siguiente mensaje de error:*"YourClass* no contiene una definición de Get *YourProperty".*

5. Haga doble clic en el mensaje de error.

     Se abre Dsl\GeneratedCode\DomainClasses.cs o DomainRelationships.cs. Encima de la llamada al método resaltado, un comentario le pide que proporcione una implementación para Get *YourProperty*().

    > [!NOTE]
    > Este archivo se genera a partir de DslDefinition.dsl. Si edita este archivo, los cambios se perderán la próxima vez que haga clic en **Transformar todas las plantillas.** En su lugar, agregue el método necesario en un archivo independiente.

6. Cree o abra un archivo de clase en una carpeta independiente, por ejemplo CustomCode \\ *YourDomainClass*.cs.

     Asegúrese de que el espacio de nombres es el mismo que en el código generado.

7. En el archivo de clase, escriba una implementación parcial de la clase de dominio. En la clase , escriba una definición para el método `Get` que falta similar al ejemplo siguiente:

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8. Si establece **Kind en** Custom **Storage,** también tendrá que proporcionar un `Set` método . Por ejemplo:

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     El código no debe establecer valores en el almacén cuando `Store.InUndoRedoOrRollback` es true. Vea [Transacciones y setters personalizados.](#setters)

9. Compile y ejecute la solución.

10. Pruebe la propiedad . Asegúrese de probar Deshacer **y** **Rehacer**.

## <a name="transactions-and-custom-setters"></a><a name="setters"></a> Transacciones y setters personalizados
 En la propiedad Set method de Custom Storage, no es necesario abrir una transacción, ya que normalmente se llama al método dentro de una transacción activa.

 Sin embargo, también se podría llamar al método Set si el usuario invoca Deshacer o Rehacer, o si se revierte una transacción. Cuando <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> es true, el método Set debe comportarse como sigue:

- No debe realizar cambios en el almacén, como asignar valores a otras propiedades de dominio. El administrador de deshacer establecerá sus valores.

- Sin embargo, debe actualizar los recursos externos, como el contenido de la base de datos o el archivo, u objetos fuera del almacén. Esto garantizará que se mantienen sincronizados con los valores del almacén.

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

 Para obtener más información sobre las transacciones, vea [Navegar y actualizar un modelo en código de programa.](../modeling/navigating-and-updating-a-model-in-program-code.md)

## <a name="see-also"></a>Vea también

- [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Propiedades de las propiedades de dominio](../modeling/properties-of-domain-properties.md)
- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)
