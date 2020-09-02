---
title: Organización jerárquica de recursos para la localización | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- resource files, localized
- localization [Visual Studio], resources
- fallback resources
- international applications [Visual Studio], storing resources
- satellite assemblies, resource hierarchies
- globalization [Visual Studio], resources
- satellite assemblies
- resources [Visual Studio], fallback system
- resource files, fallback processes
ms.assetid: dadf8f2c-f74c-44d7-bec0-a1e956d8d38d
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0a79caca18c7813605ff851eea6bda642e6300a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645614"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Organización jerárquica de recursos para la localización
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, los recursos adaptados (datos como cadenas e imágenes adecuados para cada referencia cultural) se almacenan en archivos independientes y cargan según la configuración de la referencia cultural de la interfaz de usuario. Para comprender cómo se cargan los recursos adaptados, es útil pensar en ellos como si se organizaran de forma jerárquica.

## <a name="kinds-of-resources-in-the-hierarchy"></a>Tipos de recursos de la jerarquía

- En la parte superior de la jerarquía se colocan los recursos de reserva para su referencia cultural predeterminada, por ejemplo, inglés ("en"). Estos son los únicos recursos que no tienen su propio archivo; se almacenan en el ensamblado principal.

- Bajo los recursos de reserva se encuentran los recursos para las referencias culturales neutras. Una referencia cultural neutra se asocia a un idioma, pero no a un país o región. Por ejemplo, francés ("fr") es una referencia cultural neutra. (Tenga en cuenta que los recursos de reserva también son para una referencia cultural neutra, pero una especial).

- Bajo estos se encuentran los recursos para las referencia culturales específicas. Una referencia cultural específica se asocia a un idioma y a un país o región. Por ejemplo, francés canadiense ("fr-CA") es una referencia cultural específica.

  Si una aplicación intenta cargar recursos adaptados, como una cadena, y no los encuentra, recorrerá la jerarquía hasta que encuentre un archivo de recursos que incluya el recurso solicitado.

  La mejor forma de almacenar sus recursos es generalizarlos tanto como sea posible. Eso significa almacenar cadenas localizadas, imágenes y demás en archivos de recursos para referencias culturales neutras en lugar de referencias culturales específicas siempre que sea posible. Por ejemplo, si dispone de recursos para la referencia cultural francés belga ("fr-BE") y los recursos que hay inmediatamente antes son los recursos de reserva en inglés, puede producirse un problema cuando alguien use su aplicación en un sistema configurado para la referencia cultural francés canadiense. El sistema buscará un ensamblado satélite para "fr-CA", sin encontrarlo, y cargará el ensamblado principal que contiene el recurso de reserva, que es el inglés, en lugar de cargar los recursos en francés. En la imagen siguiente se muestra este escenario no deseable.

  ![Sólo recursos específicos](../ide/media/vbspecificresourcesonly.gif "vbSpecificResourcesOnly")

  Si sigue la práctica recomendada de situar tantos recursos como sea posible en un archivo de recursos neutro para la referencia cultural "fr", el usuario francocanadiense no vería los recursos marcados para la referencia cultural "fr-BE", sino cadenas en francés. La situación siguiente muestra este escenario preferible.

  ![Gráfico NeutralSpecificResources](../ide/media/vbneutralspecificresources.gif "vbNeutralSpecificResources")

## <a name="see-also"></a>Consulte también
 [Idiomas de los recursos neutros para la seguridad de la localización](../ide/neutral-resources-languages-for-localization.md) [y ensamblados satélite localizados](../ide/security-and-localized-satellite-assemblies.md) [localizar aplicaciones](../ide/localizing-applications.md) [globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md) [Cómo: establecer la referencia cultural y la referencia cultural de la interfaz de usuario para la globalización de Windows Forms](https://msdn.microsoft.com/694e049f-0b91-474a-9789-d35124f248f0) [Cómo: establecer la referencia cultural y la referencia cultural de la interfaz de usuario para la globalización de páginas Web ASP.net](https://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0)
