---
title: Integrar modelos UML con otros modelos y herramientas | Microsoft Docs
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

- **Propiedades de estereotipo.** Se puede definir un perfil UML en el que se establezca un estereotipo que agregue propiedades a determinadas clases de elementos UML. Por ejemplo, podría definir un perfil que agregue una propiedad denominada **másdetalle** a una acción de UML. Si se desea escribir código de extensión que almacene datos de vínculo en una acción, hay que aplicar el estereotipo a la acción y, después, almacenar los datos en la propiedad.

   El usuario puede ver el estereotipo y sus propiedades en la ventana Propiedades.

   Para implementar esta extensión, empaquete la definición de perfil y el código de extensión en una única extensión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

   Para obtener más información, vea [definir un perfil para ampliar UML](../modeling/define-a-profile-to-extend-uml.md).

   Para ver un proyecto de ejemplo en el que se implementa un perfil junto con los comandos de menú y los controladores de gestos, vea [ejemplo: perfiles de UML](https://go.microsoft.com/fwlink/?LinkID=213811).

- **A.** Un conjunto de cadenas se puede adjuntar a cualquier elemento UML. Se puede escribir código que almacene la información como un nombre de archivo o el GUID de otro elemento. Para ello no es necesario proporcionar definiciones adicionales. El usuario no puede ver directamente las referencias.

   Para obtener más información, vea [adjuntar cadenas de referencia a elementos del modelo UML](../modeling/attach-reference-strings-to-uml-model-elements.md). Para obtener un ejemplo, vea [vincular elementos UML a diagramas u otros archivos](https://go.microsoft.com/fwlink/?LinkId=213813).

  Hay dos formas de codificar las referencias a elementos de modelo:

- **GUID y nombre** del elemento del modelo de destino y el modelo que lo contiene, o un diagrama determinado que lo muestra.

   Para obtener un ejemplo, vea [vincular elementos UML a diagramas u otros archivos](https://go.microsoft.com/fwlink/?LinkId=213813).

- **Referencias de ModelBus.** ModelBus es un marco para la creación y resolución de referencias entre modelos. Incluye el selector ModelBus Picker, que permite al usuario seleccionar un elemento en un modelo. También ayuda al usuario a resolver las referencias que se pierden debido a cambios en el modelo de destino.

   Para obtener más información, vea [integrar modelos mediante Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

  Propague los cambios de un modelo a otro.
  Por ejemplo, puede sincronizar el nombre de un elemento con el nombre del diagrama vinculado, por lo que si el usuario cambia uno, el otro también cambia. Existen dos mecanismos para hacerlo:

1. **Las reglas de VMSDK** se pueden usar para propagar los cambios dentro del mismo modelo.

    Para obtener un ejemplo, vea [vincular elementos UML a diagramas u otros archivos](https://go.microsoft.com/fwlink/?LinkId=213813).

2. **Los eventos VMSDK** se pueden usar para propagar los cambios fuera del modelo; por ejemplo, para cambiar el nombre de archivo de un documento vinculado o para cambiar un elemento de otro modelo.

   Para obtener información acerca de estos dos mecanismos, vea [Cómo: responder a cambios en un modelo UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).

   Arrastre los elementos para copiarlos de un modelo a otro. puede permitir que el usuario cree elementos arrastrando los elementos a un diagrama UML. El elemento creado no tiene por qué ser una copia del original. Por ejemplo, puede permitir que el usuario arrastre un diagrama de actividades desde el Explorador de soluciones hasta otro diagrama de actividades con el fin de crear una nueva acción.

   Para obtener más información, vea [definir un controlador de gestos en un diagrama de modelado](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) y [Cómo: agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="samples"></a>Muestras
 Vea el ejemplo de código [vincular elementos UML a diagramas u otros archivos](https://go.microsoft.com/fwlink/?LinkId=213813). El ejemplo permite a los usuarios arrastrar un archivo a cualquier elemento UML y después abrir el archivo haciendo doble clic en el elemento. Por ejemplo, se puede vincular un diagrama de actividades a un elemento de casos de uso. Un icono muestra los elementos que tienen vínculos.

 En este ejemplo de código se muestran las técnicas siguientes:

- [Adjuntar cadenas de referencia a elementos de modelo UML](../modeling/attach-reference-strings-to-uml-model-elements.md)

   En el código de ejemplo se almacenan las rutas de archivo y los GUID de elemento en las cadenas de referencia que están asociadas con el elemento.

- Cómo agregar decoradores a elementos UML. Para obtener información general sobre los elementos Decorator, vea [personalizar los campos de texto e imagen](../modeling/customizing-text-and-image-fields.md).

   En el ejemplo se agrega un decorador de imagen a las formas UML.

- [Cómo: Responder a cambios en un modelo UML](../misc/how-to-respond-to-changes-in-a-uml-model.md)

   En el ejemplo se muestra cómo definir una regla que responde a las nuevas formas que aparecen en un diagrama.

- [Definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md)

- [Definir un controlador de gestos en un diagrama de modelado](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)

   En el ejemplo se muestra cómo controlar los elementos arrastrados desde el Explorador de Windows (o el Explorador de archivos), el Explorador de soluciones y otros elementos UML.

  Para obtener un ejemplo en el que un DSL Lee un modelo UML, vea [Cómo: agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="see-also"></a>Vea también
 [Definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [definir un controlador de gestos en un diagrama de modelado](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) [Cómo: agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md) [Cómo: responder a los cambios en un modelo UML](../misc/how-to-respond-to-changes-in-a-uml-model.md) [ejemplo: los perfiles de UML](https://go.microsoft.com/fwlink/?LinkID=213811) [vinculan elementos UML a diagramas u otros archivos](https://go.microsoft.com/fwlink/?LinkId=213813)
