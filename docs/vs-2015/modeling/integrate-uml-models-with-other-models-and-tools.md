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
ms.openlocfilehash: 72ea0c562bb9c2a8050fc1365fac19df20232f80
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918352"
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

- **A.** Un conjunto de cadenas se puede adjuntar a cualquier elemento UML. Se puede escribir código que almacene la información como un nombre de archivo o el GUID de otro elemento. Para ello no es necesario proporcionar definiciones adicionales. El usuario no puede ver directamente las referencias.

Hay dos formas de codificar las referencias a elementos de modelo:

- **GUID y nombre** del elemento del modelo de destino y el modelo que lo contiene, o un diagrama determinado que lo muestra.

- **Referencias de ModelBus.** ModelBus es un marco para la creación y resolución de referencias entre modelos. Incluye el selector ModelBus Picker, que permite al usuario seleccionar un elemento en un modelo. También ayuda al usuario a resolver las referencias que se pierden debido a cambios en el modelo de destino.

   Para obtener más información, vea [integrar modelos mediante Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

  Propague los cambios de un modelo a otro.
  Por ejemplo, puede sincronizar el nombre de un elemento con el nombre del diagrama vinculado, por lo que si el usuario cambia uno, el otro también cambia. Existen dos mecanismos para hacerlo:

1. **Las reglas de VMSDK** se pueden usar para propagar los cambios dentro del mismo modelo.

2. **Los eventos VMSDK** se pueden usar para propagar los cambios fuera del modelo; por ejemplo, para cambiar el nombre de archivo de un documento vinculado o para cambiar un elemento de otro modelo.

   Para obtener información acerca de estos dos mecanismos, vea [Cómo: responder a cambios en un modelo UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).

   Arrastre los elementos para copiarlos de un modelo a otro. puede permitir que el usuario cree elementos arrastrando los elementos a un diagrama UML. El elemento creado no tiene por qué ser una copia del original. Por ejemplo, puede permitir que el usuario arrastre un diagrama de actividades desde el Explorador de soluciones hasta otro diagrama de actividades con el fin de crear una nueva acción.

   Para obtener más información, vea [definir un controlador de gestos en un diagrama de modelado](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) y [Cómo: agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="see-also"></a>Vea también
 [Definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [definir un controlador de gestos en un diagrama de modelado](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) [Cómo: agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md) [Cómo: responder a cambios en un modelo UML](../misc/how-to-respond-to-changes-in-a-uml-model.md)
