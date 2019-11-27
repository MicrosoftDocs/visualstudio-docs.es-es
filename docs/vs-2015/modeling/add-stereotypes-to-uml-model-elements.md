---
title: Agregar estereotipos a elementos del modelo UML | Microsoft Docs
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

1. Abra el **Explorador de modelos UML**. En el menú **arquitectura** , elija **ventanas**y, a continuación, haga clic en **Explorador de modelos UML**.

2. Busque un paquete o un modelo que contenga todos los elementos a los que desea aplicar los estereotipos del perfil.

3. Haga clic con el botón secundario en el paquete o el modelo y, a continuación, haga clic en **propiedades**.

4. En la ventana **propiedades** , establezca la propiedad **perfiles** en los perfiles que contienen los estereotipos que desea usar.

     Los estereotipos del perfil ahora estarán disponibles en todos los elementos del modelo o paquete. Si el paquete contiene otros paquetes, los estereotipos también estarán disponibles en los elementos dentro de ellos.

### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>Para agregar estereotipos a relaciones o elementos del modelo

1. Haga clic con el botón secundario en el elemento o la relación del modelo, ya sea en un diagrama o en el **Explorador de modelos UML**y, a continuación, haga clic en **propiedades**.

    > [!NOTE]
    > Para agregar los mismos estereotipos a varios elementos, puede seleccionar varios elementos y hacer clic con el botón secundario en uno de ellos.

2. Haga clic en la propiedad **estereotipos** y seleccione los estereotipos que desea aplicar.

     Los estereotipos seleccionados aparecen entre «comillas angulares» en el elemento del modelo, para casi todos los tipos de elemento y relación.

    > [!NOTE]
    > Si no puede ver la propiedad **estereotipos** , o si el estereotipo que desea no aparece, compruebe que el elemento de modelo está dentro de un paquete o un modelo al que se ha vinculado el perfil adecuado.

3. Algunos estereotipos permiten establecer los valores de las propiedades adicionales para el elemento del modelo. Para ver estas propiedades, expanda la propiedad **estereotipos** .

### <a name="to-create-model-elements-within-a-package"></a>Para crear elementos del modelo dentro de un paquete

1. Cree un paquete en un diagrama de clases UML o en el **Explorador de modelos UML**.

2. Agregue elementos de modelo al paquete de una de las maneras siguientes:

    - En un diagrama de clases UML, haga clic en la herramienta de un elemento y, a continuación, haga clic dentro del paquete en el diagrama.

         \- o -

    - En el explorador de modelos UML, haga clic con el botón secundario en el paquete, elija **Agregar**y, a continuación, haga clic en un tipo de elemento.

         \- o -

    - En el Explorador de modelos UML, arrastre un elemento existente al paquete.

         \- o -

    - Vincule un diagrama al paquete y, a continuación, cree elementos dentro del diagrama.

         Para ello, haga clic con el botón secundario en una parte en blanco del diagrama y, a continuación, haga clic en **propiedades**. En la ventana **propiedades** , establezca **paquete vinculado** en el paquete que desee.

         Todos los elementos nuevos que cree en el diagrama se definirán dentro de ese paquete.

         Solo puede hacerlo con algunos tipos de diagramas.

## <a name="see-also"></a>Vea también
 [Definir un perfil para ampliar UML](../modeling/define-a-profile-to-extend-uml.md) [personalizar el modelo con perfiles y estereotipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [definir paquetes y espacios de nombres](../modeling/define-packages-and-namespaces.md)

