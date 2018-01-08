---
title: "Personalizar y ampliar un lenguaje específico de dominio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language Tools, creating solutions
ms.assetid: b155eb79-4e0a-4a99-a6f2-ca4f811fb5ca
caps.latest.revision: "48"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 976fbd25965c62e82f9b358f22c8fe3f2b83363e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Personalizar y ampliar lenguajes específicos de dominio
Visual Studio de modelado y visualización SDK (VMSDK) proporciona varios niveles en el que puede definir herramientas de modelado:  
  
1.  Definir un lenguaje específico de dominio (DSL) mediante el diagrama de definición DSL. Puede crear rápidamente un DSL con una notación esquemática, un formato XML legible y las herramientas básicas que se necesitan para generar código y otros artefactos.  
  
     Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md).  
  
2.  Optimizar DSL mediante las características más avanzadas de la definición DSL. Por ejemplo, puede hacer que los vínculos adicionales aparezca cuando el usuario crea un elemento. Estas técnicas se consiguen principalmente en la definición de DSL y algunos requieren unas pocas líneas de código de programa.  
  
3.  Extender las herramientas de modelado mediante código del programa. VMSDK está diseñado específicamente para facilitar la integración de las extensiones con el código que se genera a partir de la definición de DSL.  Para obtener más información, consulte [escribir código para personalizar un lenguaje específico de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
> [!NOTE]
>  Si ha actualizado el archivo de definiciones de DSL, no olvide hacer clic en **Transformar todas las plantillas** en la barra de herramientas del explorador de soluciones antes de volver a generar la solución.  
  
##  <a name="customShapes"></a>En esta sección  
  
|Para lograr este efecto|Consulte este tema|  
|----------------------------|-------------------------|  
|Permite al usuario establecer las propiedades de color y el estilo de una forma.|Haga clic en la clase de forma o conector, seleccione **agregar expone**y haga clic en un elemento.<br /><br /> Vea [personalizar la presentación en el diagrama de](../modeling/customizing-presentation-on-the-diagram.md).|  
|Las distintas clases de elemento de modelo un aspecto similares en el diagrama, comparte las propiedades como inicial alto y ancho, color, información sobre herramientas.|Usar la herencia entre formas o clases de conector. Asignaciones entre las clases de dominio derivada y formas derivadas heredan los detalles de asignación de los elementos primarios.<br /><br /> O bien, asignar clases de dominio diferente a la misma clase de forma.|  
|Contextos de distintas formas, se muestra una clase de elemento de modelo.|Asignar más de una clase de forma a la misma clase de dominio. Cuando se compila la solución, siga el informe de errores y proporciona el código solicitado para decidir qué forma que se va a usar.|  
|Forma y color u otras características como fuente indican el estado actual.|Vea [actualizar formas y conectores para reflejar el modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Crear una regla que actualiza las propiedades expuestas. Vea [reglas propagarán los cambios en el modelo](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> O bien, utilice OnAssociatedPropertyChanged() para actualizar no exponen características como flechas de vínculo o la fuente.|  
|Icono de forma cambia para indicar el estado.|Establecer la visibilidad de la asignación decorador en la ventana Detalles de DSL. Busque varias decoradores de imagen en la misma posición que él. Vea [actualizar formas y conectores para reflejar el modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> O bien, reemplazar `ImageField.GetDisplayImage()`. Vea el ejemplo en <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.|  
|Establecer una imagen de fondo en cualquier forma|Invalidar InitializeInstanceResources() para agregar un ImageField anclado. Vea [personalizar la presentación en el diagrama de](../modeling/customizing-presentation-on-the-diagram.md).|  
|Formas de anidar hasta cualquier profundidad|Configurar una recursiva árbol de incrustación. Definir BoundsRules para contener las formas. Vea [personalizar la presentación en el diagrama de](../modeling/customizing-presentation-on-the-diagram.md).|  
|Adjunta conectores en fijos puntos en los límites de un elemento.|Definir incrustados elementos terminal, en la que se representan mediante los puertos pequeños en el diagrama. Use BoundsRules para corregir los puertos en su lugar. Consulte el ejemplo de diagrama del circuito en [SDK de visualización y modelado](http://go.microsoft.com/fwlink/?LinkID=186128).|  
|Campo de texto muestra un valor derivado de otros valores.|Asignar el elemento decorator de texto a una propiedad de dominio Calculated o almacenamiento personalizado. Para obtener más información, consulte [calculadas y las propiedades de almacenamiento personalizada](../modeling/calculated-and-custom-storage-properties.md).|  
|Propagar los cambios entre los elementos de modelo, o entre formas|Vea [validación en un lenguaje específico de dominio](../modeling/validation-in-a-domain-specific-language.md).|  
|Propagar los cambios a los recursos como Sí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensiones fuera de la tienda.|Vea [controladores de eventos propagan los cambios fuera del modelo de](../modeling/event-handlers-propagate-changes-outside-the-model.md).|  
|Ventana de propiedades muestra las propiedades de un elemento relacionado.|Configurar la propiedad de reenvío. Vea [personalizar la ventana de propiedades](../modeling/customizing-the-properties-window.md).|  
|Categorías de propiedades|La ventana Propiedades se divide en secciones denominadas categorías. Establecer el **categoría** de las propiedades del dominio. Propiedades con el mismo nombre de categoría aparecerán en la misma sección. También puede establecer el **categoría** de un rol de relación.|  
|Controlar el acceso a propiedades del dominio|Establecer **es examinable** false para impedir que una propiedad de dominio que aparecen en la ventana Propiedades en tiempo de ejecución. Todavía puede asignar a decoradores de texto.<br /><br /> **Es de sólo lectura de interfaz de usuario** impide que los usuarios cambiar una propiedad de dominio.<br /><br /> Acceso a la propiedad domain del programa no se ve afectado.|  
|Cambiar el nombre, el icono y la visibilidad de los nodos del explorador de modelos del ADSL.|Vea [personalizar el Explorador de modelos](../modeling/customizing-the-model-explorer.md).|  
|Habilitar copiar, cortar y pegar|Establecer el **habilitar copiar pegar** propiedad de la **Editor** nodo en el Explorador de DSL.|  
|Copiar vínculos de referencia y sus destinos de cada vez que se copia un elemento. Por ejemplo, copie los comentarios adjuntos a un elemento.|Establecer el **copia propaga** propiedad del rol de origen (representado por la línea en un lado de la relación de dominio en el diagrama de definición DSL).<br /><br /> Escribir código para reemplazar ProcessOnCopy para lograr efectos más complejos.<br /><br /> Vea [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).|  
|Eliminar, cambiar el valor primario o volver a vincular elementos relacionados cuando se elimina un elemento.|Establecer el **propaga eliminar** valor de un rol de relación. Para los efectos más complejos, invalida `ShouldVisitRelationship` y `ShouldVisitRolePlayer` métodos en el `MyDslDeleteClosure` (clase), definida en **DomainModel.cs**<br /><br /> Vea [personalizar el comportamiento de eliminación](../modeling/customizing-deletion-behavior.md)|  
|Conservar el diseño de la forma y la apariencia de copia y arrastre y coloque.|Agregar las formas y conectores a copiado `ElementGroupPrototype`. Es el método más conveniente para invalidar`ElementOperations.CreateElementGroupPrototype()`<br /><br /> Vea [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).|  
|Pegar formas en la ubicación elegida, como la posición actual del cursor.|Invalidar `ClipboardCommandSet.ProcessOnCopy()` para usar la versión específica de la ubicación de `ElementOperations.Merge().` vea [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).|  
|Crear vínculos adicionales al pegar|Invalidar ClipboardCommandSet.ProcessOnPasteCommand()|  
|Habilitar arrastre y coloque los elementos de este diagrama, otros lenguajes DSL y Windows|Vea [Cómo: agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|Permiten una forma o una herramienta y se puedan arrastrar una forma secundaria, por ejemplo, un puerto, tal y como si se arrastró el elemento primario.|Definir una directiva de mezcla de elemento en la clase de objeto de destino, para reenviar el objeto quitado al elemento primario. Vea [Personalizar movimiento y la creación del elemento](../modeling/customizing-element-creation-and-movement.md).|  
|Permite que una forma o herramienta que se pueden arrastrar a una forma y tienen vínculos adicionales o los objetos creados. Por ejemplo, para permitir un comentario que se coloca en un elemento al que está vinculado.|Definir una directiva de mezcla de elemento en la clase de dominio de destino y definir los vínculos que se genere. En casos complejos, puede agregar código personalizado. Vea [Personalizar movimiento y la creación del elemento](../modeling/customizing-element-creation-and-movement.md).|  
|Crear un grupo de elementos con una herramienta. Por ejemplo, un componente con un conjunto fijo de puertos.|Invalide el método de inicialización del cuadro de herramientas en ToolboxHelper.cs. Crear un prototipo de grupo de elemento (EGP) que contiene los elementos y sus vínculos de relación. Vea [personalizar herramientas y el cuadro de herramientas](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Incluya las formas de entidad de seguridad y el puertos en el EGP o definir BoundsRules para colocar las formas de puerto cuando se crea una instancia de la EGP. Vea [BoundsRules restringir la ubicación de la forma y el tamaño](../modeling/boundsrules-constrain-shape-location-and-size.md).|  
|Usar una herramienta de conexión para crear instancias de varios tipos de relación.|Agregar vínculo conectar directivas (LCD) para el generador de conexión que se invoca por la herramienta. Los paneles LCD determinan el tipo de la relación entre los tipos de los dos elementos. Para facilitar esta dependen de los Estados de los elementos, puede agregar código personalizado. Vea [personalizar herramientas y el cuadro de herramientas](../modeling/customizing-tools-and-the-toolbox.md).|  
|Herramientas rápidas - el usuario hacer doble clic en cualquier herramienta para crear muchas formas o conectores en sucesión.|En el Explorador de DSL, seleccione la `Editor` nodo. En la ventana Propiedades, establezca **utiliza elementos de cuadro de herramientas rápidas**.|  
|Definir los comandos de menú|Vea [Cómo: modificar un comando de menú estándar](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|Restringir el modelo de reglas de validación|Vea [validación en un lenguaje específico de dominio](../modeling/validation-in-a-domain-specific-language.md)|  
|Generar código, archivos de configuración o documentos desde un DSL.|[Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Personalizar cómo se guardan los modelos al archivo.|Vea [personalizar el almacenamiento de archivos y serialización XML](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Guardar modelos en las bases de datos u otros recursos multimedia.|Invalidar *YourLanguage*DocData<br /><br /> Vea [personalizar el almacenamiento de archivos y serialización XML](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Integrar varios DSL para que funcionen como parte de una aplicación.|Vea [integrar modelos mediante Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|  
|Permitir ADSL ampliar por terceros y controlar la extensión.|[Ampliar DSL mediante MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Compartir clases entre DSL mediante una biblioteca DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definir una directiva de bloqueo para crear segmentos de solo lectura](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|
  
## <a name="see-also"></a>Vea también  
 [Cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md)   
 [Escribir código para personalizar un lenguaje específico de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Modelar el SDK de Visual Studio: lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

