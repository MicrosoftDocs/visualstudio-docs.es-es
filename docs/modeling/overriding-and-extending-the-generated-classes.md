---
title: Reemplazar y ampliar las clases generadas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, providing overridable classes
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 568fc8c53ea7a7be79d8f8169c964f1ec7e02c0a
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="overriding-and-extending-the-generated-classes"></a>Invalidar y ampliar clases generadas
La definición DSL es una plataforma en la que puede crear un conjunto eficaz de herramientas que se basan en un lenguaje específico de dominio. Muchas de las extensiones y las adaptaciones pueden realizarse por reemplazar y ampliar las clases que se generan a partir de la definición DSL. Estas clases incluyen no solo las clases de dominio que haya definido explícitamente en el diagrama de definición DSL, sino también otras clases que definen el cuadro de herramientas, explorador, serialización y así sucesivamente.  
  
## <a name="extensibility-mechanisms"></a>Mecanismos de extensibilidad  
 Se proporcionan varios mecanismos para que pueda extender el código generado.  
  
### <a name="overriding-methods-in-a-partial-class"></a>Reemplazar métodos en una clase parcial  
 Definiciones de clase parcial permitir que una clase que deben definirse en más de un lugar. Esto le permite separar el código generado del código que es usted quien escribe. En el código escrito manualmente, puede invalidar las clases heredadas por el código generado.  
  
 Por ejemplo, si en su definición DSL define una clase de dominio denominada `Book`, puede escribir código personalizado que agrega métodos de invalidación:  
  
 `public partial class Book`  
  
 `{`  
  
 `protected override void OnDeleting()`  
  
 `{`  
  
 `MessageBox.Show("Deleting book " + this.Title);`  
  
 `base.OnDeleting();`  
  
 `} }`  
  
> [!NOTE]
>  Para invalidar los métodos en una clase generada, siempre que escribir el código en un archivo que está separado de los archivos generados. Normalmente, el archivo se encuentra en una carpeta que se denomina CustomCode. Si realiza cambios en el código generado, perderán cuando vuelva a generar el código de la definición DSL.  
  
 Para descubrir qué métodos se puede invalidar, escriba **invalidar** en la clase, seguido por un espacio. La información sobre herramientas de IntelliSense le indicará qué métodos se pueden reemplazar.  
  
### <a name="double-derived-classes"></a>Clases derivadas de doble  
 La mayoría de los métodos de las clases generadas se hereda de un conjunto fijo de clases en los espacios de nombres de modelado. Sin embargo, algunos métodos se definen en el código generado. Normalmente, esto significa que no se puede reemplazar no se puede invalidar en una clase parcial de los métodos que se definen en otra definición parcial de la misma clase.  
  
 No obstante, puede invalidar estos métodos estableciendo la **genera derivados dobles** marca para la clase de dominio. Este causas dos clases que se genere, uno que se va a una clase base abstracta de la otra. Todas las definiciones de método y propiedad están en la clase base, y sólo el constructor está en la clase derivada.  
  
 Por ejemplo, en el ejemplo Library.dsl, el `CirculationBook` clase de dominio tiene la `Generates``Double Derived` propiedad establecida en `true`. El código generado para esa clase de dominio contiene dos clases:  
  
-   `CirculationBookBase`, que es una clase abstracta y que contiene todos los métodos y propiedades.  
  
-   `CirculationBook`, que se deriva de `CirculationBookBase`. Está vacío, salvo por sus constructores.  
  
 Para invalidar cualquier método, se crea una definición parcial de la clase derivada como `CirculationBook`. Puede invalidar los métodos generados y los métodos heredados de la plataforma de modelado.  
  
 Puede utilizar este método con todos los tipos de elemento, incluidos los conectores, relaciones, formas, diagramas y elementos del modelo. También puede invalidar los métodos de otras clases generadas. Algunas clases generan como la ToolboxHelper siempre se deriva de doble.  
  
### <a name="custom-constructors"></a>Constructores personalizados  
 No se puede reemplazar un constructor. Incluso en clases derivadas de doble, el constructor debe estar en la clase derivada.  
  
 Si desea proporcionar su propio constructor, puede hacerlo estableciendo `Has Custom Constructor` para la clase de dominio en la definición DSL. Al hacer clic en **Transformar todas las plantillas**, el código generado no incluirá un constructor para esa clase. Se incluyen una llamada al constructor que faltan. Esto hace que un informe de errores al compilar la solución. Haga doble clic en el informe de errores para ver un comentario en el código generado que explica lo que debe proporcionar.  
  
 Escribir una definición de clase parcial en un archivo que es independiente de los archivos generados y proporcionan el constructor.  
  
### <a name="flagged-extension-points"></a>Puntos de extensión de marcado  
 Un punto de la extensión marcado es un lugar en la definición de DSL donde puede establecer una propiedad o una casilla de verificación para indicar que va a proporcionar un método personalizado. Constructores personalizados son un ejemplo. Otros ejemplos incluyen la configuración del `Kind` de una propiedad de dominio a calculado o almacenamiento personalizado o configuración el **personalizado es** marca en el generador de una conexión.  
  
 En cada caso, cuando se establece la marca y volver a generar el código, se producirá un error de compilación. Haga doble clic en el error para ver un comentario que explica lo que tendrá que proporcionar.  
  
### <a name="rules"></a>Reglas  
 El Administrador de transacciones permite definir reglas que se ejecutan antes del final de una transacción en el que designado se ha producido un evento, como un cambio en una propiedad. Reglas se usan normalmente para mantener synchronism entre diferentes elementos en el almacén. Por ejemplo, las reglas se utilizan para asegurarse de que el diagrama muestra el estado actual del modelo.  
  
 Las reglas se definen según una clase por clase, por lo que no tiene que tener código que registra la regla para cada objeto. Para obtener más información, consulte [propagar los cambios en el modelo de reglas de](../modeling/rules-propagate-changes-within-the-model.md).  
  
### <a name="store-events"></a>Eventos de almacén  
 El almacén de modelado proporciona un mecanismo de evento que puede usar para realizar escuchas de determinados tipos de cambio en la tienda, incluida la adición y eliminación de elementos, cambios en los valores de propiedad y así sucesivamente. Los controladores de eventos se denominan después del cierre de la transacción en el que se realizaron los cambios. Normalmente, estos eventos se usan para actualizar los recursos fuera de la tienda.  
  
### <a name="net-events"></a>Eventos de .NET  
 Puede suscribirse a algunos eventos sobre las formas. Por ejemplo, puede escuchar clics del mouse en una forma. Tendrá que escribir código que se suscribe al evento para cada objeto. Puede escribir este código en un reemplazo del InitializeInstanceResources().  
  
 Algunos eventos se generan en ShapeFields, que se usan para dibujar decoradores en una forma. Para obtener un ejemplo, vea [Cómo: interceptar al hacer clic en una forma o un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).  
  
 Normalmente estos eventos no se producen dentro de una transacción. Debe crear una transacción si desea realizar cambios en el almacén.