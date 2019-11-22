---
title: Integrate UML models with other models and tools | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, references to models
ms.assetid: 9e75e7d1-93cf-4196-baa3-bd10b9af16d3
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: caecb85392170559a860a7dc334570880d6e76f1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301467"
---
# <a name="integrate-uml-models-with-other-models-and-tools"></a>Integrar modelos UML con otros modelos y herramientas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los modelos UML pueden integrarse con otros modelos y con lenguajes específicos de dominio.

 La integración de modelos se puede realizar de las siguientes maneras con código de extensión que realice una serie de funciones:

 Adjunte referencias desde cualquier elemento a elementos de otros modelos o a archivos.
En un elemento UML se pueden almacenar vínculos a otros elementos UML, archivos u otros objetos; para ello, hay que codificar sus identidades como cadenas.

 Por ejemplo, puede escribir una extensión que permita vincular cualquier acción UML (es decir, un elemento de un diagrama de actividades) a otro diagrama de actividades. Cuando el usuario hace doble clic en la acción, se abre el otro diagrama. Esto permite al usuario proporcionar una vista más detallada de la acción.

 Hay dos formas de almacenar cadenas y otros datos de cualquier elemento:

- **Stereotype properties.** Se puede definir un perfil UML en el que se establezca un estereotipo que agregue propiedades a determinadas clases de elementos UML. For example, you could define a profile that adds a property named **MoreDetail** to a UML action. Si se desea escribir código de extensión que almacene datos de vínculo en una acción, hay que aplicar el estereotipo a la acción y, después, almacenar los datos en la propiedad.

   El usuario puede ver el estereotipo y sus propiedades en la ventana Propiedades.

   Para implementar esta extensión, empaquete la definición de perfil y el código de extensión en una única extensión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

   For more information, see [Define a profile to extend UML](../modeling/define-a-profile-to-extend-uml.md).

   For a sample project in which a profile is deployed together with menu commands and gesture handlers, see [Sample: UML Profiles](https://go.microsoft.com/fwlink/?LinkID=213811).

- **References.** Un conjunto de cadenas se puede adjuntar a cualquier elemento UML. Se puede escribir código que almacene la información como un nombre de archivo o el GUID de otro elemento. Para ello no es necesario proporcionar definiciones adicionales. El usuario no puede ver directamente las referencias.

   For more information, see [Attach reference strings to UML model elements](../modeling/attach-reference-strings-to-uml-model-elements.md). For a sample, see [Link UML Elements to Diagrams or other Files](https://go.microsoft.com/fwlink/?LinkId=213813).

  Hay dos formas de codificar las referencias a elementos de modelo:

- **GUID and Filename** of the target model element and the model that contains it, or a particular diagram that displays it.

   For an example, see [Link UML Elements to Diagrams or other Files](https://go.microsoft.com/fwlink/?LinkId=213813).

- **ModelBus References.** ModelBus es un marco para la creación y resolución de referencias entre modelos. Incluye el selector ModelBus Picker, que permite al usuario seleccionar un elemento en un modelo. También ayuda al usuario a resolver las referencias que se pierden debido a cambios en el modelo de destino.

   For more information, see [Integrating Models by using Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

  Propague los cambios de un modelo a otro.
  Por ejemplo, puede sincronizar el nombre de un elemento con el nombre del diagrama vinculado, por lo que si el usuario cambia uno, el otro también cambia. Existen dos mecanismos para hacerlo:

1. **VMSDK Rules** can be used to propagate changes inside the same model.

    For an example, see [Link UML Elements to Diagrams or other Files](https://go.microsoft.com/fwlink/?LinkId=213813).

2. **VMSDK Events** can be used to propagate changes outside the model – for example, to change the filename of a linked document, or to change an element in another model.

   For information about both these mechanisms, see [How to: Respond to Changes in a UML Model](../misc/how-to-respond-to-changes-in-a-uml-model.md).

   Drag elements to copy them from one model to another You can let the user create elements by dragging items onto a UML diagram. El elemento creado no tiene por qué ser una copia del original. Por ejemplo, puede permitir que el usuario arrastre un diagrama de actividades desde el Explorador de soluciones hasta otro diagrama de actividades con el fin de crear una nueva acción.

   For more information see [Define a gesture handler on a modeling diagram](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) and [How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="samples"></a>Ejemplos
 Please see the code sample [Link UML Elements to Diagrams or other Files](https://go.microsoft.com/fwlink/?LinkId=213813). El ejemplo permite a los usuarios arrastrar un archivo a cualquier elemento UML y después abrir el archivo haciendo doble clic en el elemento. Por ejemplo, se puede vincular un diagrama de actividades a un elemento de casos de uso. Un icono muestra los elementos que tienen vínculos.

 En este ejemplo de código se muestran las técnicas siguientes:

- [Adjuntar cadenas de referencia a elementos de modelo UML](../modeling/attach-reference-strings-to-uml-model-elements.md)

   En el código de ejemplo se almacenan las rutas de archivo y los GUID de elemento en las cadenas de referencia que están asociadas con el elemento.

- Cómo agregar decoradores a elementos UML. For general information about decorators, see [Customizing Text and Image Fields](../modeling/customizing-text-and-image-fields.md).

   En el ejemplo se agrega un decorador de imagen a las formas UML.

- [Cómo: Responder a cambios en un modelo UML](../misc/how-to-respond-to-changes-in-a-uml-model.md)

   En el ejemplo se muestra cómo definir una regla que responde a las nuevas formas que aparecen en un diagrama.

- [Definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md)

- [Definir un controlador de gestos en un diagrama de modelado](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)

   En el ejemplo se muestra cómo controlar los elementos arrastrados desde el Explorador de Windows (o el Explorador de archivos), el Explorador de soluciones y otros elementos UML.

  For an example in which a UML model is be read by a DSL, see [How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="see-also"></a>Vea también
 [Define a menu command on a modeling diagram](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Define a gesture handler on a modeling diagram](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) [How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md) [How to: Respond to Changes in a UML Model](../misc/how-to-respond-to-changes-in-a-uml-model.md) [Sample: UML Profiles](https://go.microsoft.com/fwlink/?LinkID=213811) [Link UML Elements to Diagrams or other Files](https://go.microsoft.com/fwlink/?LinkId=213813)
