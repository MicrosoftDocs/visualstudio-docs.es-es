---
title: Personalizar y ampliar lenguajes específicos de dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8383e82091ec9cc62f5b08dcc89f1e1e74239030
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60096795"
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Personalizar y ampliar lenguajes específicos de dominio
Visual Studio de modelado y visualización SDK (VMSDK) proporciona varios niveles en el que puede definir las herramientas de modelado:

1. Definir lenguajes específicos de dominio (DSL) mediante el diagrama de definición de DSL. Puede crear rápidamente un DSL con una notación en forma de diagrama, un formato XML legible y las herramientas básicas que se necesitan para generar código y otros artefactos.

     Para obtener más información, consulte [cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md).

2. Ajuste el DSL mediante el uso de características más avanzadas de la definición de DSL. Por ejemplo, puede establecer vínculos adicionales aparecen cuando el usuario crea un elemento. Estas técnicas se logran principalmente en la definición de DSL, y algunas requieren unas pocas líneas de código de programa.

3. Amplíe sus herramientas de modelado mediante el uso de código de programa. VMSDK está diseñado específicamente para facilitar la integración de las extensiones con el código que se genera a partir de la definición de DSL.  Para obtener más información, consulte [escribir código para personalizar un lenguaje específico de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md).

> [!NOTE]
>  Si ha actualizado el archivo de definiciones de DSL, no olvide hacer clic en **Transformar todas las plantillas** en la barra de herramientas del explorador de soluciones antes de volver a generar la solución.

## <a name="customShapes"></a> En esta sección

|Para lograr este efecto|En este tema, consulte|
|-|-|
|Permite al usuario establecer las propiedades de estilo y color de una forma.|Haga clic en la clase de forma o conector, seleccione **agregar expuestos**y haga clic en un elemento.<br /><br /> Consulte [personalizar la presentación en el diagrama](../modeling/customizing-presentation-on-the-diagram.md).|
|Las distintas clases de elemento de modelo un aspecto similares en el diagrama, compartir propiedades como el alto inicial y el ancho, el color, información sobre herramientas.|Usar la herencia entre las formas o clases de conector. Las asignaciones entre las formas derivadas y clases de dominio derivadas heredan los detalles de asignación de los elementos primarios.<br /><br /> O bien, asignar clases de dominio diferente a la misma clase shape.|
|Los contextos de distintas formas, se muestra una clase de elemento de modelo.|Asignar más de una clase de forma a la misma clase de dominio. Cuando se compila la solución, siga el informe de errores y proporciona el código solicitado para decidir qué forma que desee usar.|
|Color de una forma u otras características como fuente indican el estado actual.|Consulte [actualizar formas y conectores para reflejar el modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Cree una regla que actualiza las propiedades expuestas. Consulte [las reglas propagan los cambios en el modelo](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> O bien, use OnAssociatedPropertyChanged() para actualizar no exponen características como flechas de vínculo o la fuente.|
|Icono en forma cambia para indicar el estado.|Establecer la visibilidad de la asignación de decorator en la ventana Detalles de DSL. Busque varios elementos Decorator de imagen en la misma posición. Consulte [actualizar formas y conectores para reflejar el modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> O bien, invalidar `ImageField.GetDisplayImage()`. Vea el ejemplo de <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.|
|Establecer una imagen de fondo en cualquier forma|Invalidar InitializeInstanceResources() para agregar un anclado ImageField. Consulte [personalizar la presentación en el diagrama](../modeling/customizing-presentation-on-the-diagram.md).|
|Anidar formas a cualquier profundidad|Configure una recursiva incrustación de árbol. Defina el elemento BoundsRules para contener las formas. Consulte [personalizar la presentación en el diagrama](../modeling/customizing-presentation-on-the-diagram.md).|
|Adjuntar conectores en puntos fijos en límites de un elemento.|Definir elementos terminales incrustados, representados por pequeños puertos en el diagrama. Use el elemento BoundsRules para corregir los puertos en su lugar. Vea el ejemplo de diagrama de circuito en [SDK de visualización y modelado](http://go.microsoft.com/fwlink/?LinkID=186128).|
|Campo de texto muestra un valor derivado de otros valores.|Asignar el elemento decorator de texto a una propiedad de dominio Calculated o almacenamiento personalizado. Para obtener más información, consulte [calculadas y las propiedades de almacenamiento personalizado](../modeling/calculated-and-custom-storage-properties.md).|
|Propagar los cambios entre los elementos del modelo, o entre formas|Consulte [validación en los lenguajes específicos de dominio](../modeling/validation-in-a-domain-specific-language.md).|
|Propagar los cambios a los recursos como otras extensiones de Visual Studio fuera de la tienda.|Consulte [controladores de eventos propagan cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).|
|Ventana de propiedades muestra las propiedades de un elemento relacionado.|Configure la propiedad de reenvío. Consulte [personalizar la ventana propiedades](../modeling/customizing-the-properties-window.md).|
|Categorías de propiedades|La ventana Propiedades se divide en secciones denominadas categorías. Establecer el **categoría** de las propiedades de dominio. Las propiedades con el mismo nombre de categoría aparecerá en la misma sección. También puede establecer el **categoría** de un rol de relación.|
|Controlar el acceso a las propiedades de dominio|Establecer **es examinable** false para impedir que una propiedad de dominio que aparecen en la ventana Propiedades en tiempo de ejecución. Todavía puede asignarla a los elementos Decorator de texto.<br /><br /> **Es de sólo lectura de la interfaz de usuario** impide que los usuarios cambiar una propiedad de dominio.<br /><br /> Acceso al programa en la propiedad de dominio no se ve afectado.|
|Cambiar el nombre, el icono y la visibilidad de los nodos en el Explorador de modelos de su DSL.|Consulte [personalizar el Explorador de modelos](../modeling/customizing-the-model-explorer.md).|
|Habilitar copiar, cortar y pegar|Establecer el **habilitar copiar pegar** propiedad de la **Editor** nodo en el Explorador de DSL.|
|Copie sus objetivos y los vínculos de referencia cada vez que se copia un elemento. Por ejemplo, copie los comentarios adjuntos a un elemento.|Establecer el **Propagates Copy** propiedad del rol de origen (representado por la línea a un lado de la relación de dominio en el diagrama de definición de DSL).<br /><br /> Escribir código para invalidar ProcessOnCopy para lograr efectos más complejos.<br /><br /> Consulte [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).|
|Eliminar, cambiar el valor primario o volver a vincular los elementos relacionados cuando se elimina un elemento.|Establecer el **propaga eliminar** valor de un rol de relación. Para efectos más complejos, invalidar `ShouldVisitRelationship` y `ShouldVisitRolePlayer` métodos en el `MyDslDeleteClosure` (clase), definido en **DomainModel.cs**.|
|Conservar el diseño de la forma y la apariencia en la copia y arrastrar y colocar.|Agregar las formas y conectores a copiado `ElementGroupPrototype`. Es el método más cómodo para invalidar `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Consulte [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).|
|Pegar formas en la ubicación elegida, como la posición actual del cursor.|Invalidar `ClipboardCommandSet.ProcessOnCopy()` para usar la versión específica de la ubicación de `ElementOperations.Merge().` vea [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).|
|Crear vínculos adicionales al pegar|Override ClipboardCommandSet.ProcessOnPasteCommand()|
|Habilitar arrastrar y colocar en este diagrama, otros lenguajes DSL y Windows elementos|Vea [Cómo: Agregar un controlador para arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|Permitir que una forma o la herramienta y se puedan arrastrar una forma secundaria, como un puerto, como si se arrastró el elemento primario.|Definir una directiva de mezcla de elementos en la clase de objeto de destino, para reenviar el objeto colocado con el elemento primario. Consulte [personalizar la creación de elemento y movimiento](../modeling/customizing-element-creation-and-movement.md).|
|Permiten una forma o una herramienta que se puedan arrastrar una forma y hacer que los vínculos adicionales o los objetos creados. Por ejemplo, para permitir un comentario que se pueden colocar en un elemento al que está vinculado.|Definir una directiva de mezcla de elementos en la clase de dominio de destino y definir los vínculos que se genere. En casos complejos, puede agregar código personalizado. Consulte [personalizar la creación de elemento y movimiento](../modeling/customizing-element-creation-and-movement.md).|
|Cree un grupo de elementos con una herramienta. Por ejemplo, un componente con un conjunto fijo de puertos.|Invalide el método de inicialización del cuadro de herramientas de ToolboxHelper.cs. Crear un prototipo de grupo del elemento (EGP) que contiene los elementos y sus vínculos de relación. Consulte [personalizar las herramientas y el cuadro de herramientas](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Incluya las formas de entidad de seguridad y el puertos en el EGP o definir elemento BoundsRules para colocar las formas de puerto cuando se crea una instancia de EGP.|
|Usar una herramienta de conexión para crear instancias de varios tipos de relación.|Agregar directivas de conectar vínculo (LCD) a la que se invoca mediante la herramienta Generador de conexiones. Los paneles LCD determinan el tipo de la relación entre los tipos de los dos elementos. Para facilitar esta dependen de los Estados de los elementos, puede agregar código personalizado. Consulte [personalizar las herramientas y el cuadro de herramientas](../modeling/customizing-tools-and-the-toolbox.md).|
|Herramientas rápidas - el usuario hacer doble clic en cualquier herramienta para crear muchas formas o conectores en sucesión.|En el Explorador de DSL, seleccione el `Editor` nodo. En la ventana Propiedades, establezca **usa elementos de cuadro de herramientas rápidas**.|
|Definir comandos de menú|Vea [Cómo: Modificar comandos de menú estándar](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|Restringir el modelo con las reglas de validación|Consulte [validación en los lenguajes específicos de dominio](../modeling/validation-in-a-domain-specific-language.md)|
|Generar código, archivos de configuración o documentos desde un DSL.|[Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)|
|Personalizar cómo los modelos se guardan en el archivo.|Consulte [personalizar el almacenamiento de archivo y la serialización XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Guardar modelos en las bases de datos u otro medio.|Invalidar *Sulenguaje*DocData<br /><br /> Consulte [personalizar el almacenamiento de archivo y la serialización XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Integrar varios DSL para que funcionen como parte de una aplicación.|Consulte [integrar modelos utilizando Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|
|Permitir que su DSL sea ampliada por terceros y la extensión de control.|[Ampliar DSL mediante MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Compartir clases entre DSL mediante una biblioteca DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definir una directiva de bloqueo para crear segmentos de solo lectura](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>Vea también

- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Escribir código para personalizar un lenguaje específico de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modelar el SDK de Visual Studio: lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
