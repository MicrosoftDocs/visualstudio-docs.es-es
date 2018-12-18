---
title: Controlar la visibilidad de un icono o un objeto Decorator
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: a46509fb55c3d99c3cb2920dd6088497f326ab08
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895501"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Controlar la visibilidad de un icono o un objeto Decorator
Un *decorator* es un icono o una línea de texto que aparece en una forma de un lenguaje específico de dominio (DSL). Puede que aparezca la decorador y desaparecen según el estado de las propiedades en el modelo. Por ejemplo, en una forma que representa a una persona, podría tener diferentes iconos que aparecen según el sexo de la persona, el número de elementos secundarios y así sucesivamente.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Controlar la visibilidad de un icono o un elemento decorator
 El siguiente procedimiento se da por supuesto que ya ha definido una forma y su asignación a una clase de dominio. Para obtener más información, consulte [cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Para controlar la visibilidad de un elemento decorator de icono o texto

1. En el diagrama de definición de DSL, agregue la clase shape los iconos o elementos Decorator de texto que desea que aparezca.

   1.  Haga clic en la clase shape, apunte a **agregar**y, a continuación, haga clic en el tipo de elemento decorator necesario.

   2.  Establece el decorador **posición** propiedad. Más de un elemento decorator puede tener la misma posición. Por ejemplo, podría tener iconos para hombre y mujer compartir la misma posición.

   3.  Establecer el **icono predeterminado** propiedad de un elemento decorator de icono.

2. Seleccione la asignación de elemento de diagrama, que es la línea gris entre la clase shape y la clase de dominio en el diagrama de definición de DSL.

3. En la ventana Detalles de DSL, en el **asignaciones del elemento Decorator** pestaña, seleccione un elemento decorator. Por ejemplo, el MaleDecorator.

4. Compruebe el **filtro de visibilidad** cuadro.

5. Si la propiedad de dominio que debe controlar la visibilidad está en la clase de dominio inmediato, deje **ruta de acceso a la propiedad Filter** en blanco.

    En caso contrario, haga clic en el menú desplegable y navegue a la clase donde se encuentra la propiedad o relación.

   -   Para evitar un informe de errores, debe desplazarse a través de una relación de marcado con "*" en la herramienta de exploración.

6. Establecer el **propiedad Filter** a una propiedad de dominio. Por ejemplo, el género.

7. En el **entradas de visibilidad** lista, agregue los valores de esta propiedad de dominio para el que debe estar visible el elemento decorator. Por ejemplo, hombre.

8. Repita los pasos para cada icono.

9. **Transformar todas las plantillas**, compilar y ejecutar y abrir un diagrama de pruebas.

10. Al cambiar el valor de propiedad de control, los elementos Decorator deben aparecer y desaparecer.

    Con frecuencia, desea visibilidad esté controlado por una fórmula más compleja que un simple conjunto de valores. Por ejemplo, para tener un icono dependen del número de vínculos de un tipo determinado, o para que sea dependen de una si es un número en un intervalo determinado. En ese caso, utilice el procedimiento siguiente.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Para controlar la visibilidad de un elemento decorator según una fórmula

1.  Agregue una propiedad calculada del dominio a la clase de dominio. En el **propiedades** ventana, establezca los valores siguientes:

     **IsBrowsable =**`False`**-Esto oculta la propiedad del usuario**

     **Tipo =**`Calculated`**: Esto significa que va a proporcionar código que calcula su valor**

     **Nombre** por ejemplo **DecoratorControl**

     **Tipo** = `Boolean`

     Para obtener más información, consulte [calculadas y las propiedades de almacenamiento personalizado](../modeling/calculated-and-custom-storage-properties.md).

2.  Asegúrese de controlar la visibilidad del elemento decorator la nueva propiedad.

    1.  Seleccione la asignación de elemento de diagrama, que es la línea gris de la clase de dominio a la forma. En el **detalles de DSL** ventana, abra el **DecoratorMap** ficha.

    2.  Compruebe el **filtro de visibilidad** cuadro.

    3.  En **propiedad Filter**, seleccione la propiedad de control **DecoratorControl**.

    4.  En **entradas de visibilidad**, escriba `True`.

3.  Haga clic en **Transformar todas las plantillas** en el **el Explorador de soluciones** barra de herramientas.

4.  Haga clic en **compilar solución** en el **compilar** menú.

5.  Haga doble clic en el informe de errores que ha aparecido: "*Suclase* no contiene una definición para GetDecoratorControlValue...".

     Se abrirá el editor de texto en Dsl\GeneratedCode\DomainClasses.cs. Antes del error resaltado es un comentario que se le pedirá que agregue un método.

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

     Para obtener más información acerca de cómo personalizar el modelo con el código de programa, consulte [navegar y actualizar un modelo en el código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md).

8.  Volver a generar y ejecutar la solución.

## <a name="see-also"></a>Vea también

- [Definir formas y conectores](../modeling/defining-shapes-and-connectors.md)
- [Establecer una imagen de fondo en un diagrama](../modeling/setting-a-background-image-on-a-diagram.md)
- [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)