---
title: Invalidar y ampliar clases generadas
description: Obtenga información sobre cómo la definición de DSL es una plataforma en la que puede crear un conjunto eficaz de herramientas basadas en un lenguaje específico del dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 07c44e7ff7a603f339ec268b06bd78cc84cd6be2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390950"
---
# <a name="override-and-extend-the-generated-classes"></a>Invalidación y extensión de las clases generadas

La definición de DSL es una plataforma en la que puede crear un conjunto eficaz de herramientas basadas en un lenguaje específico del dominio. Muchas extensiones y adaptaciones se pueden realizar invalidando y ampliando las clases que se generan a partir de la definición de DSL. Estas clases incluyen no solo las clases de dominio que se han definido explícitamente en el diagrama de definición de DSL, sino también otras clases que definen el cuadro de herramientas, el explorador, la serialización, y así sucesivamente.

## <a name="extensibility-mechanisms"></a>Mecanismos de extensibilidad

Se proporcionan varios mecanismos para que pueda ampliar el código generado.

### <a name="override-methods-in-a-partial-class"></a>Invalidar métodos en una clase parcial

Las definiciones de clase parciales permiten definir una clase en más de un lugar. Esto le permite separar el código generado del código que escribe usted mismo. En el código escrito manualmente, puede invalidar las clases heredadas por el código generado.

Por ejemplo, si en la definición de DSL define una clase de dominio denominada , podría escribir código personalizado `Book` que agrega métodos de invalidación:

```csharp
public partial class Book
{
   protected override void OnDeleting()
   {
      MessageBox.Show("Deleting book " + this.Title);
      base.OnDeleting();
   }
}
```

> [!NOTE]
> Para invalidar los métodos de una clase generada, escriba siempre el código en un archivo que esté separado de los archivos generados. Normalmente, el archivo se encuentra en una carpeta denominada CustomCode. Si realiza cambios en el código generado, se perderán al volver a generar el código a partir de la definición de DSL.

Para detectar qué métodos puede invalidar, escriba **override** en la clase , seguido de un espacio. La información sobre herramientas de IntelliSense le mostrará qué métodos se pueden invalidar.

### <a name="double-derived-classes"></a>Double-Derived clases

La mayoría de los métodos de las clases generadas se heredan de un conjunto fijo de clases en los espacios de nombres de modelado. Sin embargo, algunos métodos se definen en el código generado. Normalmente, esto significa que no se pueden invalidar; no puede invalidar en una clase parcial los métodos definidos en otra definición parcial de la misma clase.

No obstante, puede invalidar estos métodos estableciendo la **marca Generates Double Derived** para la clase de dominio. Esto hace que se generen dos clases, una es una clase base abstracta de la otra. Todas las definiciones de método y propiedad están en la clase base y solo el constructor está en la clase derivada.

Por ejemplo, en el archivo Library.dsl de ejemplo, la `CirculationBook` clase de dominio tiene la propiedad establecida en `Generates``Double Derived` `true` . El código generado para esa clase de dominio contiene dos clases:

- `CirculationBookBase`, que es un abstracto y que contiene todos los métodos y propiedades.

- `CirculationBook`, que se deriva de `CirculationBookBase` . Está vacío, excepto para sus constructores.

Para invalidar cualquier método, cree una definición parcial de la clase derivada, como `CirculationBook` . Puede invalidar los métodos generados y los métodos heredados del marco de modelado.

Puede usar este método con todos los tipos de elementos, incluidos los elementos del modelo, las relaciones, las formas, los diagramas y los conectores. También puede invalidar los métodos de otras clases generadas. Algunas clases generadas, como ToolboxHelper, siempre se derivan doblemente.

### <a name="custom-constructors"></a>Constructores personalizados

No se puede invalidar un constructor. Incluso en clases derivadas dobles, el constructor debe estar en la clase derivada.

Si desea proporcionar su propio constructor, puede hacerlo estableciendo para la `Has Custom Constructor` clase de dominio en la definición de DSL. Al hacer clic **en Transformar todas las plantillas**, el código generado no incluirá un constructor para esa clase. Incluirá una llamada al constructor que falta. Esto provoca un informe de errores al compilar la solución. Haga doble clic en el informe de errores para ver un comentario en el código generado que explica lo que debe proporcionar.

Escriba una definición de clase parcial en un archivo que sea independiente de los archivos generados y proporcione el constructor .

### <a name="flagged-extension-points"></a>Puntos de extensión marcados

Un punto de extensión marcado es un lugar en la definición de DSL donde puede establecer una propiedad o una casilla para indicar que va a proporcionar un método personalizado. Los constructores personalizados son un ejemplo. Otros ejemplos incluyen establecer el de una propiedad de dominio en Almacenamiento calculado o Personalizado o establecer `Kind` la marca Is **Custom** en un generador de conexiones.

En cada caso, al establecer la marca y volver a generar el código, se producirá un error de compilación. Haga doble clic en el error para ver un comentario que explique lo que tiene que proporcionar.

### <a name="rules"></a>Reglas

El administrador de transacciones permite definir reglas que se ejecutan antes del final de una transacción en la que se ha producido un evento designado, como un cambio en una propiedad. Normalmente, las reglas se usan para mantener la sincronización entre los distintos elementos del almacén. Por ejemplo, las reglas se usan para asegurarse de que el diagrama muestra el estado actual del modelo.

Las reglas se definen por clase, por lo que no es necesario tener código que registre la regla para cada objeto. Para obtener más información, vea [Reglas propagar cambios dentro del modelo](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="store-events"></a>Almacenar eventos

El almacén de modelado proporciona un mecanismo de eventos que puede usar para escuchar tipos específicos de cambios en el almacén, incluida la adición y eliminación de elementos, los cambios en los valores de propiedad, y así sucesivamente. Se llama a los controladores de eventos después del cierre de la transacción en la que se realizaron los cambios. Normalmente, estos eventos se usan para actualizar recursos fuera del almacén.

### <a name="net-events"></a>Eventos de .NET

Puede suscribirse a algunos eventos en formas. Por ejemplo, puede escuchar los clics del mouse en una forma. Tiene que escribir código que se suscribe al evento para cada objeto. Este código se puede escribir en una invalidación de InitializeInstanceResources().

Algunos eventos se generan en ShapeFields, que se usan para dibujar decoradores en una forma. Para obtener un ejemplo, [vea Cómo: Interceptar un clic en una forma o decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

Normalmente, estos eventos no se producen dentro de una transacción. Debe crear una transacción si desea realizar cambios en el almacén.
