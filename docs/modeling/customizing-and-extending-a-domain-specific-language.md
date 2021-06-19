---
title: Personalizar y ampliar lenguajes específicos de dominio
description: Obtenga información sobre Visual Studio SDK de modelado y visualización (VMSDK) proporciona varios niveles en los que puede definir herramientas de modelado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04180b1fc8930b58c2d78635c794c8a614db5ed5
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389389"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>Personalización y extensión de un lenguaje específico del dominio

Visual Studio SDK de modelado y visualización (VMSDK) proporciona varios niveles en los que puede definir herramientas de modelado:

1. Defina un lenguaje específico de dominio (DSL) mediante el diagrama de definición de DSL. Puede crear rápidamente un DSL con una notación diagramamática, un formulario XML legible y las herramientas básicas necesarias para generar código y otros artefactos. Para obtener más información, [vea How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md).

2. Ajuste el DSL mediante características más avanzadas de la definición de DSL. Por ejemplo, puede hacer que aparezcan vínculos adicionales cuando el usuario crea un elemento. Estas técnicas se logran principalmente en la definición de DSL y algunas requieren algunas líneas de código del programa.

3. Amplíe las herramientas de modelado mediante el código del programa. VMSDK está diseñado específicamente para facilitar la integración de las extensiones con el código que se genera a partir de la definición de DSL. Para obtener más información, vea [Escribir código para personalizar un Domain-Specific lenguaje .](../modeling/writing-code-to-customise-a-domain-specific-language.md)

> [!NOTE]
> Cuando haya actualizado el archivo de definiciones de  DSL, no olvide hacer clic en Transformar todas las plantillas en la barra de herramientas de **Explorador de soluciones** antes de volver a generar la solución.

## <a name="article-reference"></a>Referencia de artículos

|Para lograr este efecto|Consulte este tema.|
|-|-|
|Permite al usuario establecer las propiedades de color y estilo de una forma.|Haga clic con el botón derecho en la forma o la clase de conector, seleccione **Agregar** expuesto y haga clic en un elemento.|
|Las diferentes clases de elemento de modelo tienen un aspecto similar en el diagrama, compartiendo propiedades como el alto y ancho iniciales, el color y la información sobre herramientas.|Use la herencia entre formas o clases de conector. Las asignaciones entre las formas derivadas y las clases de dominio derivadas heredan los detalles de asignación de los elementos maestros.<br /><br /> O bien, asigne clases de dominio diferentes a la misma clase de forma.|
|Diferentes contextos de formas muestran una clase de elemento de modelo.|Asigne más de una clase de forma a la misma clase de dominio. Al compilar la solución, siga el informe de errores y proporcione el código solicitado para decidir qué forma usar.|
|El color de la forma u otras características como la fuente indican el estado actual.|Consulte [Actualización de formas y conectores para reflejar el modelo.](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)<br /><br /> Cree una regla que actualice las propiedades expuestas. Vea [Reglas para propagar cambios dentro del modelo.](../modeling/rules-propagate-changes-within-the-model.md)<br /><br /> O bien, use OnAssociatedPropertyChanged() para actualizar características no expuestas, como flechas de vínculo o fuentes.|
|Icono de los cambios de forma para indicar el estado.|Establezca la visibilidad de la asignación del decorador en la ventana Detalles de DSL. Busque varios decoradores de imágenes en la misma posición. Vea [Actualizar formas y conectores para reflejar el modelo.](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)<br /><br /> O bien, invalide `ImageField.GetDisplayImage()` . Vea el ejemplo en <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField> .|
|Establecer una imagen de fondo en cualquier forma|Invalide InitializeInstanceResources() para agregar un ImageField delimitado.|
|Anidar formas a cualquier profundidad|Configure un árbol de incrustación recursiva. Defina BoundsRules para que contenga las formas.|
|Conecte conectores en puntos fijos en el límite de un elemento.|Defina elementos de terminal incrustados, representados por puertos pequeños en el diagrama. Use BoundsRules para corregir los puertos en su lugar. Consulte el ejemplo de diagrama de circuitos [en El SDK de visualización y modelado.](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|
|El campo de texto muestra un valor derivado de otros valores.|Asigne el decorador de texto a una propiedad de dominio de almacenamiento calculado o personalizado. Para obtener más información, vea [Propiedades de almacenamiento calculadas y personalizadas.](../modeling/calculated-and-custom-storage-properties.md)|
|Propagar cambios entre elementos del modelo o entre formas|Vea [Validación en un Domain-Specific lenguaje](../modeling/validation-in-a-domain-specific-language.md).|
|Propague los cambios a recursos como otras extensiones Visual Studio fuera del almacén.|Vea [Controladores de eventos Propagar cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).|
|Ventana De propiedades muestra las propiedades de un elemento relacionado.|Configure el reenvío de propiedades. Vea [Personalización de la ventana Propiedades](../modeling/customizing-the-properties-window.md).|
|Categorías de propiedades|La ventana de propiedades se divide en secciones denominadas categorías. Establezca la **Categoría de** las propiedades del dominio. Las propiedades con el mismo nombre de categoría aparecerán en la misma sección. También puede establecer la **categoría de** un rol de relación.|
|Control del acceso de los usuarios a las propiedades de dominio|Set **Is Browsable** false para evitar que una propiedad de dominio aparezca en el ventana Propiedades en tiempo de ejecución. Todavía puede asignarlo a decoradores de texto.<br /><br /> **Is UI Read Only impide** que los usuarios cambien una propiedad de dominio.<br /><br /> El acceso del programa a la propiedad de dominio no se ve afectado.|
|Cambie el nombre, el icono y la visibilidad de los nodos en el explorador de modelos de DSL.|Vea [Personalización del Explorador de modelos.](../modeling/customizing-the-model-explorer.md)|
|Habilitación de copiar, cortar y pegar|Establezca la **propiedad Habilitar copiar pegar** del nodo **Editor** en el Explorador DSL.|
|Copie los vínculos de referencia y sus destinos cada vez que se copie un elemento. Por ejemplo, copie los comentarios adjuntos a un elemento.|Establezca la **propiedad Propagates Copy del** rol de origen (representado por la línea en un lado de la relación de dominio en el diagrama de definición de DSL).<br /><br /> Escribir código para invalidar ProcessOnCopy para lograr efectos más complejos.<br /><br /> Vea [Personalización del comportamiento de copia.](../modeling/customizing-copy-behavior.md)|
|Eliminar, volver aparentr o volver a vincular elementos relacionados cuando se elimina un elemento.|Establezca el **valor Propagates Delete** de un rol de relación. Para efectos más complejos, `ShouldVisitRelationship` invalide los métodos y de la clase `ShouldVisitRolePlayer` , `MyDslDeleteClosure` definidos en **DomainModel.cs**.|
|Conservar el diseño y la apariencia de las formas al copiar y arrastrar y colocar.|Agregue las formas y conectores al objeto `ElementGroupPrototype` copiado. El método más conveniente para invalidar es `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Vea [Personalización del comportamiento de copia.](../modeling/customizing-copy-behavior.md)|
|Pegar formas en la ubicación elegida, como la posición actual del cursor.|Invalide `ClipboardCommandSet.ProcessOnCopy()` para usar la versión específica de la ubicación de Vea `ElementOperations.Merge().` [Personalización del comportamiento de copia](../modeling/customizing-copy-behavior.md).|
|Crear vínculos adicionales al pegar|Invalidar ClipboardCommandSet.ProcessOnPasteCommand()|
|Habilitar arrastrar y colocar desde este diagrama, otros archivos DSL y elementos de Windows|Vea [Cómo: Agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|Permitir que una forma o herramienta se arrastre a una forma secundaria, como un puerto, como si se arrastrara al elemento primario.|Defina una directiva de combinación de elementos en la clase de objeto de destino para reenviar el objeto eliminado al elemento primario. Vea [Personalización de la creación y el movimiento de elementos.](../modeling/customizing-element-creation-and-movement.md)|
|Permite arrastrar una forma o herramienta a una forma y crear vínculos u objetos adicionales. Por ejemplo, para permitir que un comentario se pueda pasar a un elemento al que se va a vincular.|Defina una directiva de combinación de elementos en la clase de dominio de destino y defina los vínculos que se generarán. En casos complejos, puede agregar código personalizado. Vea [Personalización de la creación y el movimiento de elementos.](../modeling/customizing-element-creation-and-movement.md)|
|Cree un grupo de elementos con una herramienta. Por ejemplo, un componente con un conjunto fijo de puertos.|Invalide el método de inicialización del cuadro de herramientas en ToolboxHelper.cs. Cree un prototipo de grupo de elementos (EGP) que contenga los elementos y sus vínculos de relación. Vea [Personalizar herramientas y cuadro de herramientas.](../modeling/customizing-tools-and-the-toolbox.md)<br /><br /> Incluya las formas principal y de puerto en el EGP, o defina BoundsRules para colocar las formas de puerto cuando se crea una instancia de EGP.|
|Use una herramienta de conexión para crear instancias de varios tipos de relación.|Agregue Directivas de conexión de vínculo (ECT) al Generador de conexiones invocado por la herramienta. Los LCD determinan el tipo de relación a partir de los tipos de los dos elementos. Para que esto dependa de los estados de los elementos, puede agregar código personalizado. Vea [Personalizar herramientas y cuadro de herramientas.](../modeling/customizing-tools-and-the-toolbox.md)|
|Herramientas permanentes: el usuario puede hacer doble clic en cualquier herramienta para crear muchas formas o conectores en sucesión.|En el Explorador de DSL, seleccione el `Editor` nodo . En la ventana Propiedades, establezca **Utiliza elementos permanentes del cuadro de herramientas**.|
|Definición de comandos de menú|Vea [Cómo: Modificar un comando de menú estándar](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|Restricción del modelo con reglas de validación|Consulte [Validación en un Domain-Specific lenguaje](../modeling/validation-in-a-domain-specific-language.md)|
|Generar código, archivos de configuración o documentos a partir de un DSL.|[Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)|
|Personalice cómo se guardan los modelos en el archivo.|Vea [Personalización de File Storage y serialización XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Guarde modelos en bases de datos u otros medios.|Invalidación *de YourLanguage* DocData<br /><br /> Vea [Personalización de File Storage y serialización XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Integre varias DSL para que funcionen como parte de una aplicación.|Consulte [Integración de modelos mediante Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|
|Permita que terceros puedan ampliar su DSL y controlar la extensión.|[Ampliar DSL mediante MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Compartir clases entre DSL mediante una biblioteca DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definir una directiva de bloqueo para crear segmentos de solo lectura](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>Vea también

- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Escribir código para personalizar un Domain-Specific personalizado](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modelar el SDK de Visual Studio: lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
