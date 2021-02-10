---
title: Personalizar y ampliar lenguajes específicos de dominio
description: Obtenga información sobre cómo el SDK de modelado y visualización de Visual Studio (VMSDK) proporciona varios niveles en los que puede definir herramientas de modelado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9cfa8a3cda3f6bb2f564efe745a11863cf4d0e8a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945310"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>Personalización y extensión de lenguajes específicos de dominio

El SDK de modelado y visualización de Visual Studio (VMSDK) proporciona varios niveles en los que puede definir herramientas de modelado:

1. Defina un lenguaje específico de dominio (DSL) mediante el diagrama de definición de DSL. Puede crear rápidamente un DSL con una notación en forma de diagrama, un formato XML legible y las herramientas básicas que se necesitan para generar código y otros artefactos. Para obtener más información, consulte [definición de un lenguaje Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md).

2. Ajuste el DSL con características más avanzadas de la definición de DSL. Por ejemplo, puede hacer que aparezcan vínculos adicionales cuando el usuario crea un elemento. Estas técnicas se logran principalmente en la definición de DSL y algunas requieren algunas líneas de código de programa.

3. Amplíe sus herramientas de modelado mediante el código del programa. VMSDK está diseñado específicamente para facilitar la integración de las extensiones con el código que se genera a partir de la definición de DSL. Para obtener más información, vea [escribir código para personalizar un lenguaje Domain-Specific](../modeling/writing-code-to-customise-a-domain-specific-language.md).

> [!NOTE]
> Cuando haya actualizado el archivo de definiciones de DSL, no olvide hacer clic en **transformar todas las plantillas** en la barra de herramientas de **Explorador de soluciones** antes de recompilar la solución.

## <a name="article-reference"></a>Referencia de artículos

|Para lograr este efecto|Consulte este tema|
|-|-|
|Permite al usuario establecer las propiedades de color y estilo de una forma.|Haga clic con el botón secundario en la clase de la forma o conector, seleccione **Agregar exposición** y haga clic en un elemento.|
|Las distintas clases del elemento de modelo tienen un aspecto similar en el diagrama, compartiendo propiedades como el alto y el ancho iniciales, el color, la información sobre herramientas.|Utilice la herencia entre formas o clases de conector. Las asignaciones entre las formas derivadas y las clases de dominio derivadas heredan los detalles de asignación de los elementos primarios.<br /><br /> O bien, asigne distintas clases de dominio a la misma clase de forma.|
|Una clase de elemento de modelo se muestra mediante distintos contextos de formas.|Asigne más de una clase de forma a la misma clase de dominio. Al compilar la solución, siga el informe de errores y proporcione el código solicitado para decidir qué forma usar.|
|El color de la forma u otras características, como la fuente, indican el estado actual.|Consulte [Actualizar formas y conectores para reflejar el modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Cree una regla que actualice las propiedades expuestas. Vea [las reglas propagar los cambios dentro del modelo](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> O bien, use OnAssociatedPropertyChanged () para actualizar características no expuestas, como las flechas de vínculo o la fuente.|
|El icono de la forma cambia para indicar el estado.|Establezca la visibilidad de la asignación de Decorator en la ventana detalles de DSL. Busque varios decoradores de imagen en la misma posición. Consulte  [Actualizar formas y conectores para reflejar el modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> O bien, invalide `ImageField.GetDisplayImage()` . Vea el ejemplo en <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField> .|
|Establecer una imagen de fondo en cualquier forma|Reemplace InitializeInstanceResources () para agregar un ImageField delimitado.|
|Anidar formas en cualquier profundidad|Configure un árbol de incrustación recursiva. Defina formas boundsrules para que contenga las formas.|
|Adjunte conectores en puntos fijos en el límite de un elemento.|Definir elementos terminales incrustados, representados por puertos pequeños en el diagrama. Use formas boundsrules para corregir los puertos en su lugar. Vea el ejemplo de diagrama de circuitos en [SDK de visualización y modelado](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).|
|Campo de texto muestra un valor derivado de otros valores.|Asigne el elemento Decorator de texto a una propiedad de dominio de almacenamiento calculada o personalizada. Para obtener más información, consulte [propiedades de almacenamiento calculado y personalizado](../modeling/calculated-and-custom-storage-properties.md).|
|Propagar los cambios entre los elementos del modelo o entre las formas|Consulte [validación en un lenguaje Domain-Specific](../modeling/validation-in-a-domain-specific-language.md).|
|Propagar los cambios a recursos como otras extensiones de Visual Studio fuera del almacén.|Vea [los controladores de eventos propagan los cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).|
|La ventana de propiedades muestra las propiedades de un elemento relacionado.|Configurar el reenvío de propiedades. Vea [personalizar la ventana Propiedades](../modeling/customizing-the-properties-window.md).|
|Categorías de propiedades|La ventana Propiedades se divide en secciones denominadas categorías. Establezca la **categoría** de las propiedades de dominio. Las propiedades con el mismo nombre de categoría aparecerán en la misma sección. También puede establecer la **categoría** de un rol de relación.|
|Controlar el acceso de usuario a las propiedades del dominio|El valor de set **es** false para impedir que una propiedad de dominio aparezca en el ventana Propiedades en tiempo de ejecución. Todavía puede asignarlo a elementos Decorator de texto.<br /><br /> La **interfaz de usuario de solo lectura** impide que los usuarios cambien una propiedad de dominio.<br /><br /> El acceso de los programas a la propiedad de dominio no se ve afectado.|
|Cambie el nombre, el icono y la visibilidad de los nodos en el explorador de modelos de DSL.|Vea [personalizar el explorador de modelos](../modeling/customizing-the-model-explorer.md).|
|Habilitar copiar, cortar y pegar|Establezca la propiedad **Habilitar copiar pegar** del nodo **Editor** en DSL Explorer.|
|Copiar los vínculos de referencia y sus destinos cada vez que se copia un elemento. Por ejemplo, copie los comentarios adjuntos a un elemento.|Establezca la propiedad **Propagate Copy** del rol de origen (representada por la línea en un lado de la relación de dominio en el diagrama de definición de DSL).<br /><br /> Escriba código para invalidar ProcessOnCopy para lograr efectos más complejos.<br /><br /> Vea [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).|
|Eliminar, Reenlazar o volver a vincular elementos relacionados cuando se elimina un elemento.|Establezca **propaga** el valor de eliminación de un rol de relación. Para efectos más complejos, invalide `ShouldVisitRelationship` `ShouldVisitRolePlayer` los métodos y en la `MyDslDeleteClosure` clase, definidos en **DomainModel.CS**.|
|Conservar el diseño y el aspecto de la forma en copiar y arrastrar y colocar.|Agregue las formas y conectores al copiado `ElementGroupPrototype` . El método más cómodo para invalidar es `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Vea [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).|
|Pegar formas en la ubicación elegida, como la posición actual del cursor.|Invalide `ClipboardCommandSet.ProcessOnCopy()` para usar la versión específica de la ubicación de, `ElementOperations.Merge().` vea [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).|
|Crear vínculos adicionales al pegar|Invalidar ClipboardCommandSet. ProcessOnPasteCommand ()|
|Habilitar arrastrar y colocar desde este diagrama, otros elementos DSL y Windows|Vea [Cómo: agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|Permite arrastrar una forma o herramienta a una forma secundaria, como un puerto, como si se arrastrara al elemento primario.|Defina una directiva de combinación de elementos en la clase de objeto de destino para reenviar el objeto colocado al elemento primario. Vea [personalizar la creación y el movimiento de un elemento](../modeling/customizing-element-creation-and-movement.md).|
|Permite arrastrar una forma o herramienta a una forma y hacer que se creen objetos o vínculos adicionales. Por ejemplo, para permitir que un comentario se coloque en un elemento al que se va a vincular.|Defina una directiva de combinación de elementos en la clase de dominio de destino y defina los vínculos que se van a generar. En casos complejos, puede agregar código personalizado. Vea [personalizar la creación y el movimiento de un elemento](../modeling/customizing-element-creation-and-movement.md).|
|Cree un grupo de elementos con una herramienta. Por ejemplo, un componente con un conjunto fijo de puertos.|Invalide el método de inicialización del cuadro de herramientas en ToolboxHelper.cs. Cree un prototipo de grupo de elementos (EGP) que contenga los elementos y sus vínculos de relación. Vea [personalizar herramientas y el cuadro de herramientas](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Incluya las formas principal y puerto en el EGP, o bien defina formas boundsrules para colocar las formas de puerto cuando se crea una instancia del EGP.|
|Use una herramienta de conexión para crear instancias de varios tipos de relaciones.|Agregue las directivas de conexión de vínculos (LCD) al generador de conexiones que invoca la herramienta. Los monitores de LCD determinan el tipo de la relación a partir de los tipos de los dos elementos. Para que esto dependa de los Estados de los elementos, puede agregar código personalizado. Vea [personalizar herramientas y el cuadro de herramientas](../modeling/customizing-tools-and-the-toolbox.md).|
|Herramientas adhesivas: el usuario puede hacer doble clic en cualquier herramienta para crear muchas formas o conectores en sucesión.|En el explorador de DSL, seleccione el `Editor` nodo. En el ventana Propiedades, set **utiliza elementos del cuadro de herramientas**.|
|Definir comandos de menú|Consulte [Cómo: modificar un comando de menú estándar.](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|Restricción del modelo con reglas de validación|Ver [la validación en un lenguaje Domain-Specific](../modeling/validation-in-a-domain-specific-language.md)|
|Generar código, archivos de configuración o documentos a partir de un DSL.|[Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)|
|Personalizar el modo en que los modelos se guardan en el archivo.|Vea [personalizar File Storage y serialización XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Guardar modelos en bases de datos u otros medios.|Invalidar *sulenguaje*<br /><br /> Vea [personalizar File Storage y serialización XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Integre varios DSL para que funcionen como parte de una aplicación.|Consulte [integración de modelos mediante Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|
|Permita que el DSL sea ampliado por terceros y control de la extensión.|[Ampliar DSL mediante MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Compartir clases entre DSL mediante una biblioteca DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definir una directiva de bloqueo para crear segmentos de solo lectura](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>Vea también

- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Escribir código para personalizar un lenguaje Domain-Specific](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modelar el SDK de Visual Studio: lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
