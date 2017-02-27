---
title: "Invalidar y ampliar clases generadas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, proporcionar clases que se puedan invalidar"
ms.assetid: 30baa60d-a8ea-4611-96c1-8fcc3317cf21
caps.latest.revision: 15
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 15
---
# Invalidar y ampliar clases generadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La definición de un DSL es una plataforma en la que puede compilar un conjunto eficaz de herramientas basados en un lenguaje específico.  Muchas extensiones y adaptaciones pueden hacerse reemplazando y extender las clases que se generan a partir de la definición del ADSL.  Estas clases incluyen no sólo clases de dominio que tiene definidas explícitamente en el diagrama de la definición de DSL, pero también otras clases que definen el cuadro de herramientas, explorador, serialización, etc.  
  
## Mecanismos de extensibilidad  
 Varios mecanismos se proporcionan para permitir que se extiende el código generado.  
  
### Reemplazar los métodos en una clase parcial  
 Las definiciones de clases parciales permiten que una clase está definido en más de un lugar.  Esto permite separar el código generado de código que ha escrito.  En el código manual\-escrito, puede reemplazar las clases heredadas por el código generado.  
  
 Por ejemplo, si en la definición de ADSL define una clase de dominio denominada `Book`, podría escribir código personalizado que agrega métodos de invalidación:  
  
 `public partial class Book`  
  
 `{`  
  
 `protected override void OnDeleting()`  
  
 `{`  
  
 `MessageBox.Show("Deleting book " + this.Title);`  
  
 `base.OnDeleting();`  
  
 `} }`  
  
> [!NOTE]
>  Para reemplazar métodos de una clase generada, escriba siempre el código en un archivo que se separa de los archivos generados.  Normalmente, el archivo se encuentra en una carpeta que se denomina CustomCode.  Si realiza cambios en el código generado, se perderán cuando se regenera el código de definición ADSL.  
  
 Para detectar qué métodos se puede reemplazar, el reemplazo de tipo en la clase, seguido por un espacio.  La información sobre herramientas de IntelliSense le indicará qué métodos se pueden reemplazar.  
  
### clases Doble\-Derivadas  
 La mayoría de los métodos en clases generadas se heredan de un conjunto fijo de clases de los espacios de nombres de modelado.  sin embargo, algunos métodos son definido en el código generado.  Normalmente, esto significa que no puede reemplazarlas; no se puede reemplazar en una clase parcial los métodos que se definen en otra definición parcial de la misma clase.  
  
 Sin embargo, puede reemplazar estos métodos estableciendo la marca de **genera derivado doble** para la clase de dominio.  Esto provoca dos clases que se generen, una que es una clase base abstracta de la otra.  Todos los métodos y definiciones de propiedad están en la clase base, y sólo el constructor está en la clase derivada.  
  
 Por ejemplo, en el ejemplo Library.dsl, la clase de dominio de `CirculationBook` tiene la propiedad de `Generates``Double Derived` establecida en `true`.  El código generado para esa clase de dominio contiene dos clases:  
  
-   `CirculationBookBase`, que es un resumen y que contiene todos los métodos y propiedades.  
  
-   `CirculationBook`, que es derivado de `CirculationBookBase`.  Está vacía, salvo sus constructores.  
  
 Para reemplazar un método, cree una definición parcial de la clase derivada como `CirculationBook`.  Puede invalidar los métodos generados y métodos heredados de modelado.  
  
 Puede utilizar este método con todos los tipos de elemento, incluidos los elementos de modelo, relaciones, formas, diagramas, y conectores.  También puede reemplazar métodos de otras clases generadas.  Algunas clases generadas como el ToolboxHelper siempre son doble\-derivadas.  
  
### constructores personalizados  
 No puede reemplazar un constructor.  incluso en clases doble\-derivadas, el constructor debe estar en la clase derivada.  
  
 Si desea proporcionar dispone al constructor, se puede hacer estableciendo `Has Custom Constructor` para la clase de dominio en la definición del ADSL.  Al hacer clic en **Transformar todas las plantillas**, el código generado no incluirá un constructor para esa clase.  Incluirá una llamada al constructor que falta.  Esto produce un informe de errores al compilar la solución.  Haga doble clic en el informe de errores para ver un comentario en el código generado que explica lo que debe proporcionar.  
  
 Escriba una definición de clase parcial en un archivo que es independiente de los archivos generados, y proporciona al constructor.  
  
### Puntos marcados de extensión  
 Un punto marcado de extensión es un lugar de la definición de ADSL donde puede establecer una propiedad o una casilla para indicar que proporcionará un método personalizado.  los constructores personalizados son un ejemplo.  Otros ejemplos incluyen establecer `Kind` de una propiedad de dominio al almacenamiento calculado o personalizado o establecer el indicador de **es personalizado** en un generador de la conexión.  
  
 En cada caso, cuando se establece el marcador y vuelve al código, un error de compilación se producirá.  Haga doble clic en el error para ver un comentario que explica lo que tiene que proporcionar.  
  
### Reglas  
 El administrador de transacciones le permite definir las reglas que se ejecutan antes del final de una transacción en la que un evento señalado ha producido, por ejemplo un cambio en una propiedad.  Las reglas se utilizan normalmente para mantener sincronismo entre distintos elementos en el almacén.  Por ejemplo, las reglas se utilizan para asegurarse de que el diagrama muestra el estado actual del modelo.  
  
 Las reglas son definido en función de la por\-clase, de modo que no tenga que agregar código que registre la regla para cada objeto.  Para obtener más información, vea [Reglas de propagan los cambios en el modelo](../modeling/rules-propagate-changes-within-the-model.md).  
  
### Eventos de almacén  
 El almacén de modelado proporciona un mecanismo de eventos que puede utilizar para escuchar tipos específicos de cambio en el almacén, incluida la adición y eliminación de elementos, los cambios a los valores de propiedad, etc.  Se llama a los controladores de eventos después de que el cierre de la transacción en la que se realizaron los cambios.  Normalmente, estos eventos se usan para actualizar recursos fuera del almacén.  
  
### eventos de .NET  
 Puede suscribirse a algunos eventos de las formas.  Por ejemplo, puede escuchar clic del mouse en una forma.  Tiene que escribir el código que se suscribe al evento de cada objeto.  Este código se puede escribir en un reemplazo de InitializeInstanceResources\(\).  
  
 Algunos eventos se generan en ShapeFields, que se utilizan para dibujar a decoradores de una forma.  Para obtener un ejemplo, vea [Cómo: Interceptar un clic en una forma o decorador](../Topic/How%20to:%20Intercept%20a%20Click%20on%20a%20Shape%20or%20Decorator.md).  
  
 Estos eventos no suelen dentro de una transacción.  Debe crear una transacción si desea realizar cambios en el almacén.