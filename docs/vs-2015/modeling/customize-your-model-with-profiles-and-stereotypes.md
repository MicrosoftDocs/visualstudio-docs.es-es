---
title: Personalizar el modelo con perfiles y estereotipos | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, profiles
- UML model, stereotypes
- UML model, customizing
ms.assetid: fd607157-0d3a-4583-a84e-427a4b2a5acb
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f7e9aee38208a96ab75318a86810359392b5b8e1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433355"
---
# <a name="customize-your-model-with-profiles-and-stereotypes"></a>Personalizar el modelo con perfiles y estereotipos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, puede adaptar los elementos del modelo UML estándar, como las clases y los componentes, para personalizarlos con fines específicos. Puede aplicar un *estereotipo* a un elemento de modelo que se puede cambiar la lista del elemento de propiedades. Los estereotipos se definen dentro de las colecciones denominadas *perfiles*.  
  
 Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Para usar un estereotipo, se vincula un paquete a un perfil. De este modo se pueden aplicar los estereotipos definidos en el perfil a los elementos del paquete. Algunos perfiles se instalan con Visual Studio. Además, puede definir sus propios perfiles.  
  
 Los estereotipos se pueden establecer en la lista de propiedades de un elemento. En el caso de los tipos de forma principales de un diagrama, los estereotipos aplicados aparecen también en la forma, como se muestra en el ejemplo.  
  
 ![Una clase UML con un estereotipo. ](../modeling/media/uml-class-stereotype.png "UML_class_stereotype")  
  
> [!NOTE]
> Si usa un perfil para crear un modelo y, a continuación, comparte el modelo con otra persona, esta no podrá ver los estereotipos a menos que tenga instalado el mismo perfil en el equipo.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Agregar estereotipos a elementos del modelo UML](../modeling/add-stereotypes-to-uml-model-elements.md)|Colocar un elemento del modelo en un paquete, vincular el paquete a un perfil y aplicar un estereotipo al elemento.|  
|[Estereotipos estándar para modelos UML](../modeling/standard-stereotypes-for-uml-models.md)|Los perfiles estándar UML L2 y L3 se instalan con Visual Studio, y cada modelo está vinculado a ellos de forma predeterminada. Proporcionan estereotipos que puede usar para anotar los modelos.<br /><br /> Por ejemplo, puede aplicar el estereotipo “Especificación” a una clase para indicar que está pensada únicamente para definir el comportamiento visible externamente de sus instancias|  
|[Definir un perfil para ampliar UML](../modeling/define-a-profile-to-extend-uml.md)|Puede definir sus propios estereotipos y herramientas de modo que estén adaptados a su propia área de aplicación.<br /><br /> Por ejemplo, si desarrolla un software de banca, puede definir un estereotipo "Cuenta" que pueda aplicarse a las clases. Posteriormente, podría usar los diagramas de clases para describir distintos tipos de cuentas y sus relaciones.|  
|[Instalar un perfil UML](../modeling/install-a-uml-profile.md)|Si alguien le ha proporcionado un perfil UML, puede instalarlo en el equipo.|  
|[Definir un elemento personalizado en un cuadro de herramientas de modelado](../modeling/define-a-custom-modeling-toolbox-item.md)|Un elemento personalizado en el cuadro de herramientas le evita tener que establecer varias veces un estereotipo en los elementos nuevos.|  
|[Clases UML de color por estereotipo](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|Este código de ejemplo amplía los diagramas UML. Establece automáticamente el color de una forma UML según el estereotipo del elemento.|
