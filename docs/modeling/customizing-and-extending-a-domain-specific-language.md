---
title: "Personalizar y ampliar un lenguaje específico de dominio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
ms.assetid: b155eb79-4e0a-4a99-a6f2-ca4f811fb5ca
caps.latest.revision: 48
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 00a120fc470393f8ab843636ca5d3400b004232b
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Personalizar y ampliar lenguajes específicos de dominio
Visual Studio de modelado y visualización de SDK (VMSDK) proporciona varios niveles en el que puede definir herramientas de modelado:  
  
1.  Definir un lenguaje específico de dominio (DSL) con el diagrama de la definición de DSL. Puede crear rápidamente un DSL con una notación esquemáticas, un formato XML legible y las herramientas básicas que se necesitan para generar código y otros artefactos.  
  
     Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md).  
  
2.  Ajuste el DSL mediante las características más avanzadas de la definición de DSL. Por ejemplo, puede establecer vínculos adicionales aparecen cuando el usuario crea un elemento. Estas técnicas se logran principalmente en la definición de DSL y algunas requieren unas pocas líneas de código de programa.  
  
3.  Amplíe sus herramientas de modelado mediante código del programa. VMSDK está diseñado específicamente para facilitar la integración de las extensiones con el código que se genera a partir de la definición de DSL.  Para obtener más información, consulte [escribir el código para personalizar un lenguaje específico de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
> [!NOTE]
>  Si ha actualizado el archivo de definiciones de DSL, no olvide hacer clic en **Transformar todas las plantillas** en la barra de herramientas del explorador de soluciones antes de volver a generar la solución.  
  
##  <a name="a-namecustomshapesa-in-this-section"></a><a name="customShapes"></a>En esta sección  
  
|Para lograr este efecto|Consulte este tema|  
|----------------------------|-------------------------|  
|Permitir al usuario establecer las propiedades de color y estilo de una forma.|Haga clic en la clase de forma o conector, seleccione **agregar expuestos**y haga clic en un elemento.<br /><br /> Consulte [personalizar la presentación en el diagrama](../modeling/customizing-presentation-on-the-diagram.md).|  
|Las distintas clases de elemento de modelo un aspecto similares en el diagrama, compartir propiedades como inicial alto y ancho, color, información sobre herramientas.|Utilizar la herencia entre formas o clases de conector. Las asignaciones entre las formas derivadas y clases de dominio derivadas heredan los detalles de asignación de los elementos primarios.<br /><br /> O bien, asignar clases de dominio diferente a la misma clase de forma.|  
|Contextos de distintas formas, se muestra una clase de elemento de modelo.|Asignar más de una clase de la forma a la misma clase de dominio. Cuando se compila la solución, siga el informe de errores y proporciona el código solicitado para decidir qué forma que desea utilizar.|  
|Forma y color u otras características como fuente indican el estado actual.|Consulte [actualizar formas y conectores para reflejar el modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Crear una regla que actualiza las propiedades expuestas. Consulte [reglas propagan los cambios en el modelo de](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> O bien, utilice OnAssociatedPropertyChanged() para actualizar no exponen características como flechas de vínculo o la fuente.|  
|Icono de cambia de forma para indicar el estado.|Establecer la visibilidad de la asignación del elemento decorator en la ventana Detalles de DSL. Buscar varios elementos Decorator de imagen en la misma posición. Consulte [actualizar formas y conectores para reflejar el modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> O bien, reemplazar `ImageField.GetDisplayImage()`. Vea el ejemplo en <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.</xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>|  
|Establecer una imagen de fondo en cualquier forma|Reemplazar InitializeInstanceResources() para agregar un ImageField anclado. Consulte [personalizar la presentación en el diagrama](../modeling/customizing-presentation-on-the-diagram.md).|  
|Anidar formas a cualquier profundidad|Configurar una recursiva incrustación de árbol. Definir BoundsRules para contener las formas. Consulte [personalizar la presentación en el diagrama](../modeling/customizing-presentation-on-the-diagram.md).|  
|Adjuntar conectores en puntos fijos en los límites de un elemento.|Definir elementos terminales incrustados, representados por puertos pequeño en el diagrama. Utilice BoundsRules para corregir los puertos en su lugar. Vea el ejemplo de diagrama del circuito en [SDK de visualización y modelado](http://go.microsoft.com/fwlink/?LinkID=186128).|  
|Campo de texto muestra un valor derivado de otros valores.|Asignar el elemento decorator de texto a una propiedad de dominio calculado o almacenamiento personalizado. Para obtener más información, consulte [calculado y las propiedades de almacenamiento personalizada](../modeling/calculated-and-custom-storage-properties.md).|  
|Propagar cambios entre los elementos del modelo, o entre formas|Consulte [validación en un lenguaje específico de dominio](../modeling/validation-in-a-domain-specific-language.md).|  
|Propagar los cambios a los recursos como otros [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensiones fuera de la tienda.|Consulte [controladores de eventos propagan cambios fuera el modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).|  
|Ventana de propiedades muestra las propiedades de un elemento relacionado.|Configurar la propiedad de reenvío. Consulte [personalización de la ventana propiedades](../modeling/customizing-the-properties-window.md).|  
|Categorías de propiedades|La ventana Propiedades se divide en secciones denominadas categorías. Establecer el **categoría** de las propiedades del dominio. Propiedades con el mismo nombre de categoría aparecerán en la misma sección. También puede establecer el **categoría** de un rol de relación.|  
|Controlar el acceso a las propiedades del dominio|Establecer **es examinable** false para impedir que una propiedad de dominio que aparecen en la ventana Propiedades en tiempo de ejecución. Todavía puede asignar a elementos Decorator de texto.<br /><br /> **Es de sólo lectura de interfaz de usuario** impide a los usuarios cambiar una propiedad de dominio.<br /><br /> Acceso a la propiedad de dominio no se ve afectado.|  
|Cambiar el nombre, el icono y la visibilidad de los nodos en el Explorador de modelos de su DSL.|Consulte [personalizar el Explorador de modelos](../modeling/customizing-the-model-explorer.md).|  
|Permiten copiar, cortar y pegar|Establecer el **permiten copiar pegar** propiedad de la **Editor** nodo en el Explorador de DSL.|  
|Copie sus objetivos y los vínculos de referencia cada vez que se copia un elemento. Por ejemplo, copie los comentarios adjuntos a un elemento.|Establecer el **copia propaga** propiedad de la función de origen (representada por la línea en un lado de la relación de dominio en el diagrama de la definición de DSL).<br /><br /> Escribir código para invalidar ProcessOnCopy para lograr efectos más complejas.<br /><br /> Consulte [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).|  
|Eliminar, cambiar el valor primario o volver a vincular elementos relacionados cuando se elimina un elemento.|Establecer el **propaga eliminar** valor de un rol de relación. Para efectos más complejos, invalide `ShouldVisitRelationship` y `ShouldVisitRolePlayer` métodos en el `MyDslDeleteClosure` clase, definida en **DomainModel.cs**<br /><br /> Consulte [personalizar el comportamiento de eliminación](../modeling/customizing-deletion-behavior.md)|  
|Conservar el diseño de la forma y la apariencia de copia y arrastre y coloque.|Agregar las formas y conectores a copiado `ElementGroupPrototype`. Es el método más conveniente para invalidar`ElementOperations.CreateElementGroupPrototype()`<br /><br /> Consulte [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).|  
|Pegar formas en la ubicación elegida, como la posición actual del cursor.|Invalidar `ClipboardCommandSet.ProcessOnCopy()` utilizar la versión específica de la ubicación de `ElementOperations.Merge().` vea [personalización del comportamiento de copia](../modeling/customizing-copy-behavior.md).|  
|Crear vínculos adicionales al pegar|Reemplazar ClipboardCommandSet.ProcessOnPasteCommand()|  
|Habilitar arrastrar y colocar en este diagrama, otros lenguajes DSL y Windows elementos|Vea [Cómo: agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|Permiten una forma o la herramienta de arrastrar una forma secundaria, como un puerto, como si se arrastró el elemento primario.|Definir una directiva de mezcla de elementos en la clase de objeto de destino para reenviar el objeto colocado en el elemento primario. Consulte [Personalizar movimiento y la creación del elemento](../modeling/customizing-element-creation-and-movement.md).|  
|Permitir una forma o la herramienta de arrastrar una forma y tienen vínculos adicionales u objetos creados. Por ejemplo, para permitir un comentario que se va a colocar en un elemento al que está vinculado.|Definir una directiva de mezcla de elementos de la clase de dominio de destino y definir los vínculos que se genere. En casos complejos, puede agregar código personalizado. Consulte [Personalizar movimiento y la creación del elemento](../modeling/customizing-element-creation-and-movement.md).|  
|Crear un grupo de elementos con una sola herramienta. Por ejemplo, un componente con un conjunto fijo de puertos.|Invalide el método de inicialización del cuadro de herramientas de ToolboxHelper.cs. Crear un prototipo de grupo de elementos (EGP) que contiene los elementos y sus vínculos de relación. Consulte [personalizar las herramientas y el cuadro de herramientas](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Incluya las formas de entidad de seguridad y el puertos en el EGP o definir BoundsRules para colocar las formas de puerto cuando se crea una instancia del EGP. Consulte [ubicación y tamaño formas Boundsrules](../modeling/boundsrules-constrain-shape-location-and-size.md).|  
|Usar una herramienta de conexión para crear instancias de varios tipos de relación.|Agregar vínculo conectar directivas (LCD) para el generador de conexión que se invoca mediante la herramienta. Los paneles LCD determinan el tipo de la relación entre los tipos de los dos elementos. Para hacer esto depende de los Estados de los elementos, puede agregar código personalizado. Consulte [personalizar las herramientas y el cuadro de herramientas](../modeling/customizing-tools-and-the-toolbox.md).|  
|Herramientas rápidas: el usuario hacer doble clic en cualquier herramienta para crear muchas formas o conectores en sucesión.|En el Explorador de DSL, seleccione la `Editor` nodo. En la ventana Propiedades, establezca **utiliza elementos de cuadro de herramientas rápidas**.|  
|Definir los comandos de menú|Vea [Cómo: modificar un comando de menú estándar](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|Restringir el modelo con las reglas de validación|Consulte [validación en un lenguaje específico de dominio](../modeling/validation-in-a-domain-specific-language.md)|  
|Generar código, archivos de configuración o documentos de un DSL.|[Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Personalizar cómo se guardan los modelos al archivo.|Consulte [personalizar la serialización XML y el almacenamiento de archivos](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Guardar modelos en las bases de datos u otros medios.|Invalidar *Sulenguaje*DocData<br /><br /> Consulte [personalizar la serialización XML y el almacenamiento de archivos](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Integrar varios DSL para que funcionen como parte de una aplicación.|Consulte [integrar modelos utilizando Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|  
|Permitir su DSL extenderse por terceros y controlar la extensión.|[Ampliar DSL mediante MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Compartir clases entre DSL mediante una biblioteca DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definir una directiva de bloqueo para crear segmentos de solo lectura](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|  
|||  
  
## <a name="see-also"></a>Vea también  
 [Cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md)   
 [Escribir código para personalizar un lenguaje específico de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Modelar el SDK de Visual Studio: lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


