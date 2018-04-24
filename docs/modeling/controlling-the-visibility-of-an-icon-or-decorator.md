---
title: Controlar la visibilidad de un icono o un objeto Decorator
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 070f49b09086d463a13470f389a4857225b7add9
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Controlar la visibilidad de un icono o un objeto Decorator
A *decorador* es un icono o una línea de texto que aparece en una forma de un lenguaje específico de dominio (DSL). Puede que aparezca la decorador y desaparecen según el estado de las propiedades en el modelo. Por ejemplo, en una forma que representa a una persona, podría tener diferentes iconos que aparecen según el sexo de la persona, número de elementos secundarios y así sucesivamente.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Controlar la visibilidad de un icono o elemento decorator
 El siguiente procedimiento se supone que ya se han definido una forma y su asignación a una clase de dominio. Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Para controlar la visibilidad de un elemento decorator de icono o texto

1.  En el diagrama de definición DSL, agregue a la clase de forma los iconos o decoradores de texto que desea que aparezca.

    1.  Haga clic en la clase shape, seleccione **agregar**y, a continuación, haga clic en el tipo de elemento decorator necesario.

    2.  Establecer el decorador **posición** propiedad. Más de un elemento decorator puede tener la misma posición que él. Por ejemplo, podría tener iconos para hombre y mujer compartir la misma posición que él.

    3.  Establecer el **icono predeterminado** propiedad de un elemento decorator de icono.

2.  Seleccione la asignación de elemento de diagrama, que es la línea gris entre la clase shape y la clase de dominio en el diagrama de definición DSL.

3.  En la ventana Detalles de DSL, en la **decorador mapas** ficha, seleccione un decorador. Por ejemplo, el MaleDecorator.

4.  Compruebe el **filtro de visibilidad** cuadro.

5.  Si la propiedad de dominio que debe controlar la visibilidad está en la clase de dominio inmediato, deje **ruta de acceso a la propiedad Filter** en blanco.

     En caso contrario, haga clic en el menú desplegable y navegue a la clase donde se encuentra la propiedad o relación.

    -   Para evitar un informe de errores, no debe navegar a través de una relación marcada con "*" en la herramienta de exploración.

6.  Establecer el **propiedad Filter** a una propiedad de dominio. Por ejemplo, sexo.

7.  En el **entradas de visibilidad** lista, agregue los valores de esta propiedad de dominio para el que el elemento decorator debería estar visible. Por ejemplo, hombre.

8.  Repita los pasos para cada icono.

9. **Transformar todas las plantillas**, compilar y ejecutar y abrir un diagrama de pruebas.

10. Cuando se cambia el valor de la propiedad de control, el decoradores deben aparecen y desaparecen.

 Con frecuencia, desea visibilidad esté controlada por una fórmula más compleja de un sencillo conjunto de valores. Por ejemplo, para tener un icono dependen del número de vínculos de un tipo determinado, o para facilitar dependen de un si es un número en un intervalo determinado. En ese caso, utilice el procedimiento siguiente.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Para controlar la visibilidad de un elemento decorator según una fórmula

1.  Agregar una propiedad de dominio calculada a la clase de dominio. En el **propiedades** ventana, establezca los siguientes valores:

     **IsBrowsable =**`False`**-Esto oculta la propiedad del usuario** 

     **Tipo =**`Calculated`**-Esto significa que se va a proporcionar código que calcula su valor** 

     **Nombre** como **DecoratorControl**

     **tipo de** = `Boolean`

     Para obtener más información, consulte [calculadas y las propiedades de almacenamiento personalizada](../modeling/calculated-and-custom-storage-properties.md).

2.  Asegúrese de controlar la visibilidad decorador la nueva propiedad.

    1.  Seleccione la asignación de elemento de diagrama, que es la línea gris de la clase de dominio a la forma. En el **detalles de DSL** ventana, abra el **DecoratorMap** ficha.

    2.  Compruebe el **filtro de visibilidad** cuadro.

    3.  En **propiedad Filter**, seleccione la propiedad de control **DecoratorControl**.

    4.  En **visibilidad entradas**, escriba `True`.

3.  Haga clic en **Transformar todas las plantillas** en la barra de herramientas del explorador de soluciones.

4.  Haga clic en **generar solución** en el **generar** menú.

5.  Haga doble clic en el informe de errores que ha aparecido: "*YourClass* no contiene ninguna definición para GetDecoratorControlValue...".

     Se abrirá el editor de texto en Dsl\GeneratedCode\DomainClasses.cs. Antes del error resaltado es un comentario que le pedirá que agregue un método.

6.  Tenga en cuenta el espacio de nombres, clase y método que faltan.  Por ejemplo, Company.FamilyTree.Person.GetDecoratorControlValue().

7.  En un archivo de código independiente, escribir una definición de clase parcial que contiene el método que falta. Por ejemplo:

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     Para obtener más información acerca de cómo personalizar el modelo de código de programa, consulte [navegar y actualizar un modelo de código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md).

8.  Volver a generar y ejecutar la solución.

## <a name="see-also"></a>Vea también

- [Definir formas y conectores](../modeling/defining-shapes-and-connectors.md)
- [Establecer una imagen de fondo en un diagrama](../modeling/setting-a-background-image-on-a-diagram.md)
- [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)