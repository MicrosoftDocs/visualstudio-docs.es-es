---
title: Invalidar y ampliar las clases generadas | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
ms.assetid: 30baa60d-a8ea-4611-96c1-8fcc3317cf21
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a7b9733a47b4763a0f28ee4b24b54fdfd44bf066
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435002"
---
# <a name="overriding-and-extending-the-generated-classes"></a>Invalidar y ampliar clases generadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La definición de DSL es una plataforma en la que puede crear un conjunto eficaz de herramientas que se basan en un lenguaje específico de dominio. Muchas extensiones y adaptaciones pueden realizarse al invalidar y ampliar las clases que se generan a partir de la definición de DSL. Estas clases incluyen no solo las clases de dominio que ha definido explícitamente en el diagrama de definición de DSL, sino también otras clases que definen el cuadro de herramientas, el explorador, serialización y así sucesivamente.  
  
## <a name="extensibility-mechanisms"></a>Mecanismos de extensibilidad  
 Se proporcionan varios mecanismos para que pueda ampliar el código generado.  
  
### <a name="overriding-methods-in-a-partial-class"></a>Invalidar métodos en una clase parcial  
 Definiciones de clases parciales permiten una clase que se definen en más de un solo lugar. Esto le permite separar el código generado desde el código que usted escribe. En el código escrito manualmente, puede invalidar las clases heredadas por el código generado.  
  
 Por ejemplo, si en su definición de DSL define una clase de dominio denominada `Book`, podría escribir código personalizado que agrega los métodos de invalidación:  
  
 `public partial class Book`  
  
 `{`  
  
 `protected override void OnDeleting()`  
  
 `{`  
  
 `MessageBox.Show("Deleting book " + this.Title);`  
  
 `base.OnDeleting();`  
  
 `} }`  
  
> [!NOTE]
> Para invalidar métodos en una clase generada, siempre que escriba el código en un archivo que se separa de los archivos generados. Normalmente, el archivo se encuentra en una carpeta que se denomina un valor CustomCode. Si realiza cambios en el código generado, se perderán al volver a generar el código de la definición de DSL.  
  
 Para detectar qué métodos se pueden invalidar, escriba **invalidar** en la clase, seguido por un espacio. La información sobre herramientas de IntelliSense le indicará qué métodos se pueden invalidar.  
  
### <a name="double-derived-classes"></a>Clases derivadas de doble  
 La mayoría de los métodos en clases generadas se hereda de un conjunto fijo de clases en los espacios de nombres de modelado. Sin embargo, algunos métodos se definen en el código generado. Normalmente, esto significa que no se puede invalidar no se puede reemplazar en clases parciales de los métodos que se definen en otra definición parcial de la misma clase.  
  
 No obstante, puede invalidar estos métodos estableciendo el **genera doble derivada** marca para la clase de dominio. Este hace que dos clases que se genere, uno que se va a una clase base abstracta de la otra. Todas las definiciones de método y propiedad están en la clase base, y es sólo el constructor de la clase derivada.  
  
 Por ejemplo, en el ejemplo Library.dsl, el `CirculationBook` clase de dominio tiene el `Generates``Double Derived` propiedad establecida en `true`. El código generado para esa clase de dominio contiene dos clases:  
  
- `CirculationBookBase`, que es abstracta y que contiene todos los métodos y propiedades.  
  
- `CirculationBook`, que se deriva de `CirculationBookBase`. Está vacío, salvo sus constructores.  
  
  Para invalidar cualquier método, cree una definición parcial de la clase derivada como `CirculationBook`. Puede invalidar los métodos generados y los métodos heredados del marco de modelado.  
  
  Puede usar este método con todos los tipos de elemento, incluidos los conectores, relaciones, formas, diagramas y elementos del modelo. También puede invalidar los métodos de otras clases generadas. Algunas clases generan, como el ToolboxHelper siempre son doble derivada.  
  
### <a name="custom-constructors"></a>Constructores personalizados  
 No se puede reemplazar un constructor. Incluso en las clases derivadas de doble, el constructor debe estar en la clase derivada.  
  
 Si desea proporcionar su propio constructor, puede hacerlo estableciendo `Has Custom Constructor` para la clase de dominio en la definición de DSL. Al hacer clic en **Transformar todas las plantillas**, el código generado no incluirá un constructor para esa clase. Se incluyen una llamada al constructor que faltan. Esto hace que un informe de errores al compilar la solución. Haga doble clic en el informe de errores para ver un comentario en el código generado que explica lo que debe proporcionar.  
  
 Escribir una definición de clase parcial en un archivo que es independiente de los archivos generados y proporcione el constructor.  
  
### <a name="flagged-extension-points"></a>Puntos de extensión de marcado  
 Un punto de extensión marcado es un lugar en la definición de DSL, donde puede establecer una propiedad o una casilla de verificación para indicar que va a proporcionar un método personalizado. Constructores personalizados son un ejemplo. Otros ejemplos incluyen la configuración de la `Kind` de una propiedad de dominio a Calculated o almacenamiento personalizado o configuración la **Is Custom** marca en un generador de conexiones.  
  
 En cada caso, cuando se establece la marca y volver a generar el código, se producirá un error de compilación. Haga doble clic en el error para ver un comentario que explica lo que tendrá que proporcionar.  
  
### <a name="rules"></a>Reglas  
 El Administrador de transacciones permite definir reglas que se ejecutan antes del final de una transacción en el que se ha producido un evento designado, por ejemplo, un cambio en una propiedad. Las reglas se utilizan normalmente para mantener synchronism entre los distintos elementos en el almacén. Por ejemplo, las reglas se usan para asegurarse de que el diagrama muestra el estado actual del modelo.  
  
 Las reglas se definen por clase, por lo que no es necesario que el código que registra la regla para cada objeto. Para obtener más información, consulte [propagar cambios en el modelo de reglas de](../modeling/rules-propagate-changes-within-the-model.md).  
  
### <a name="store-events"></a>Eventos de Store  
 El almacén de modelado proporciona un mecanismo de eventos que puede usar para realizar escuchas para determinados tipos de cambio en la tienda, incluida la adición y eliminación de elementos, los cambios realizados en los valores de propiedad y así sucesivamente. Los controladores de eventos se denominan después del cierre de la transacción en el que se realizaron los cambios. Normalmente, estos eventos se utilizan para actualizar los recursos fuera de la tienda.  
  
### <a name="net-events"></a>Eventos de .NET  
 Puede suscribirse a algunos eventos en las formas. Por ejemplo, puede escuchar la clics del mouse en una forma. Tendrá que escribir código que se suscribe al evento para cada objeto. Este código se puede escribir en un reemplazo de InitializeInstanceResources().  
  
 Algunos eventos se generan en ShapeFields, que se usan para dibujar los elementos Decorator de una forma. Como ejemplo, vea [Cómo: Interceptar un clic en una forma o decorador](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).  
  
 Normalmente, estos eventos no se producen dentro de una transacción. Debe crear una transacción si desea realizar cambios en el almacén.
