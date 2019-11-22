---
title: Add stereotypes to UML model elements | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, stereotypes
ms.assetid: 82545252-83ce-4e11-a419-61373be75d16
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d489b1446e7205d72b53e160a8c7ca87f216d7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292328"
---
# <a name="add-stereotypes-to-uml-model-elements"></a>Agregar estereotipos a elementos del modelo UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede agregar un estereotipo a un elemento del modelo UML para anotarlo y proporcionarle propiedades especializadas. Para agregar un estereotipo a un elemento del modelo, el estereotipo debe definirse en un perfil y debe vincular el perfil a un paquete o al modelo que contiene el elemento del modelo. Cada estereotipo puede agregarse solo a determinados tipos de elemento de modelo, como clases, casos de uso o componentes de UML.

 Por ejemplo, si desea definir una clase UML con el estereotipo «specification», debe crearlo dentro de un paquete o un modelo que esté vinculado al perfil estándar L2.

 De forma predeterminada, todos los modelos están vinculados a los perfiles estándar UML L2 y L3.

### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Para vincular un perfil a un modelo o un paquete

1. Open **UML Model Explorer**. On the **Architecture** menu, point to **Windows**, and then click **UML Model Explorer**.

2. Busque un paquete o un modelo que contenga todos los elementos a los que desea aplicar los estereotipos del perfil.

3. Right-click the package or the model and then click **Properties**.

4. In the **Properties** window, set the **Profiles** property to the profiles that contain the stereotypes you want to use.

     Los estereotipos del perfil ahora estarán disponibles en todos los elementos del modelo o paquete. Si el paquete contiene otros paquetes, los estereotipos también estarán disponibles en los elementos dentro de ellos.

### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>Para agregar estereotipos a relaciones o elementos del modelo

1. Right-click the model element or relationship, either on a diagram or in **UML Model Explorer**, and then click **Properties**.

    > [!NOTE]
    > Para agregar los mismos estereotipos a varios elementos, puede seleccionar varios elementos y hacer clic con el botón secundario en uno de ellos.

2. Click the **Stereotypes** property and select the stereotypes that you want to apply.

     Los estereotipos seleccionados aparecen entre «comillas angulares» en el elemento del modelo, para casi todos los tipos de elemento y relación.

    > [!NOTE]
    > If you cannot see the **Stereotypes** property, or if the stereotype you want does not appear, verify that the model element is inside a package or a model to which the appropriate profile has been linked.

3. Algunos estereotipos permiten establecer los valores de las propiedades adicionales para el elemento del modelo. To see these properties, expand the **Stereotypes** property.

### <a name="to-create-model-elements-within-a-package"></a>Para crear elementos del modelo dentro de un paquete

1. Create a package either in a UML Class Diagram, or in **UML Model Explorer**.

2. Agregue elementos de modelo al paquete de una de las maneras siguientes:

    - En un diagrama de clases UML, haga clic en la herramienta de un elemento y, a continuación, haga clic dentro del paquete en el diagrama.

         \- o -

    - In UML Model Explorer, right-click the package, point to **Add**, and then click an element type.

         \- o -

    - En el Explorador de modelos UML, arrastre un elemento existente al paquete.

         \- o -

    - Vincule un diagrama al paquete y, a continuación, cree elementos dentro del diagrama.

         To do this, right-click a blank part of the diagram and then click **Properties**. In the **Properties** window, set **Linked Package** to the package you want.

         Todos los elementos nuevos que cree en el diagrama se definirán dentro de ese paquete.

         Solo puede hacerlo con algunos tipos de diagramas.

## <a name="see-also"></a>Vea también
 [Define a profile to extend UML](../modeling/define-a-profile-to-extend-uml.md) [Customize your model with profiles and stereotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [Define packages and namespaces](../modeling/define-packages-and-namespaces.md)

