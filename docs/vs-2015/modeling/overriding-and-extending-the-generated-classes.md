---
title: Reemplazar y extender las clases generadas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
ms.assetid: 30baa60d-a8ea-4611-96c1-8fcc3317cf21
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 16a09a5b0f5e534d310092036b8e7eb1d4c344d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668475"
---
# <a name="overriding-and-extending-the-generated-classes"></a>Invalidar y ampliar clases generadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La definición de DSL es una plataforma en la que se puede crear un eficaz conjunto de herramientas basadas en un lenguaje específico de dominio. Muchas extensiones y adaptaciones se pueden realizar invalidando y extendiendo las clases que se generan a partir de la definición de DSL. Estas clases no solo incluyen las clases de dominio definidas explícitamente en el diagrama de definición de DSL, sino también otras clases que definen el cuadro de herramientas, el explorador, la serialización, etc.

## <a name="extensibility-mechanisms"></a>Mecanismos de extensibilidad
 Se proporcionan varios mecanismos para que pueda extender el código generado.

### <a name="overriding-methods-in-a-partial-class"></a>Reemplazar métodos en una clase parcial
 Las definiciones de clase parcial permiten definir una clase en más de un lugar. Esto permite separar el código generado del código que se escribe. En el código escrito manualmente, puede invalidar las clases heredadas por el código generado.

 Por ejemplo, si en la definición de DSL define una clase de dominio denominada `Book`, puede escribir código personalizado que agregue métodos de invalidación:

 `public partial class Book`

 `{`

 `protected override void OnDeleting()`

 `{`

 `MessageBox.Show("Deleting book " + this.Title);`

 `base.OnDeleting();`

 `} }`

> [!NOTE]
> Para invalidar los métodos en una clase generada, escriba siempre el código en un archivo que esté separado de los archivos generados. Normalmente, el archivo se encuentra en una carpeta denominada CustomCode. Si realiza cambios en el código generado, se perderán cuando vuelva a generar el código a partir de la definición de DSL.

 Para detectar qué métodos puede invalidar, escriba **override** en la clase, seguido de un espacio. La información sobre herramientas de IntelliSense le indicará qué métodos se pueden invalidar.

### <a name="double-derived-classes"></a>Clases derivadas de Double
 La mayoría de los métodos de las clases generadas se heredan de un conjunto fijo de clases en los espacios de nombres de modelado. Sin embargo, algunos métodos se definen en el código generado. Normalmente, esto significa que no se pueden invalidar. no se puede invalidar en una clase parcial los métodos que se definen en otra definición parcial de la misma clase.

 No obstante, puede invalidar estos métodos estableciendo la marca **Generate Double derived** para la clase de dominio. Esto hace que se generen dos clases, una de las cuales es una clase base abstracta de la otra. Todas las definiciones de método y propiedad están en la clase base y solo el constructor está en la clase derivada.

 Por ejemplo, en la biblioteca de ejemplo. DSL, la clase de dominio `CirculationBook` tiene la propiedad `Generates``Double Derived` establecida en `true`. El código generado para esa clase de dominio contiene dos clases:

- `CirculationBookBase`, que es un abstracto y que contiene todos los métodos y propiedades.

- `CirculationBook`, que se deriva de `CirculationBookBase`. Está vacío, salvo por sus constructores.

  Para invalidar cualquier método, cree una definición parcial de la clase derivada, como `CirculationBook`. Puede invalidar los métodos generados y los métodos heredados del marco de modelado.

  Puede usar este método con todos los tipos de elemento, incluidos los elementos del modelo, las relaciones, las formas, los diagramas y los conectores. También puede invalidar métodos de otras clases generadas. Algunas clases generadas como ToolboxHelper siempre se derivan de Double.

### <a name="custom-constructors"></a>Constructores personalizados
 No se puede invalidar un constructor. Incluso en clases derivadas dobles, el constructor debe estar en la clase derivada.

 Si desea proporcionar su propio constructor, puede establecer `Has Custom Constructor` para la clase de dominio en la definición de DSL. Al hacer clic en **transformar todas las plantillas**, el código generado no incluirá un constructor para esa clase. Incluirá una llamada al constructor que falta. Esto genera un informe de errores al compilar la solución. Haga doble clic en el informe de errores para ver un Comentario en el código generado que explica lo que debe proporcionar.

 Escriba una definición de clase parcial en un archivo que sea independiente de los archivos generados y proporcione el constructor.

### <a name="flagged-extension-points"></a>Puntos de extensión marcados
 Un punto de extensión marcado es un lugar en la definición de DSL en el que puede establecer una propiedad o una casilla para indicar que va a proporcionar un método personalizado. Los constructores personalizados son un ejemplo. Otros ejemplos incluyen el establecimiento del `Kind` de una propiedad de dominio en el almacenamiento calculado o personalizado o el establecimiento de la marca **is Custom** en un generador de conexiones.

 En cada caso, al establecer la marca y volver a generar el código, se producirá un error de compilación. Haga doble clic en el error para ver un comentario que explica lo que debe proporcionar.

### <a name="rules"></a>Reglas
 El administrador de transacciones permite definir reglas que se ejecutan antes del final de una transacción en la que se ha producido un evento designado, como un cambio en una propiedad. Las reglas se utilizan normalmente para mantener synchronism entre distintos elementos del almacén. Por ejemplo, las reglas se usan para asegurarse de que el diagrama muestra el estado actual del modelo.

 Las reglas se definen por clase, por lo que no es necesario tener código que registre la regla para cada objeto. Para obtener más información, vea [propagar los cambios dentro del modelo](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="store-events"></a>Almacenar eventos
 El almacén de modelado proporciona un mecanismo de eventos que puede utilizar para escuchar tipos específicos de cambio en el almacén, como la adición y eliminación de elementos, cambios en los valores de propiedad, etc. Se llama a los controladores de eventos después del cierre de la transacción en la que se realizaron los cambios. Normalmente, estos eventos se utilizan para actualizar recursos fuera del almacén.

### <a name="net-events"></a>Eventos .NET
 Puede suscribirse a algunos eventos de las formas. Por ejemplo, puede escuchar los clics del mouse en una forma. Tendrá que escribir código que se suscriba al evento para cada objeto. Este código se puede escribir en una invalidación de InitializeInstanceResources ().

 Algunos eventos se generan en ShapeFields, que se usan para dibujar los decoradores en una forma. Para obtener un ejemplo, vea [Cómo: interceptar un clic en una forma o un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

 Normalmente, estos eventos no se producen dentro de una transacción. Debe crear una transacción si desea realizar cambios en el almacén.
