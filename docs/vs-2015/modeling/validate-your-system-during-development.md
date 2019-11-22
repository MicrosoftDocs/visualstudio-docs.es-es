---
title: Validate your system during development | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4fec3595ba7886f5ba979c35e9441ab108174726
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301341"
---
# <a name="validate-your-system-during-development"></a>Validar el sistema durante el desarrollo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio puede ayudarle a mantener la coherencia del software con los requisitos de los usuarios y con la arquitectura del sistema.

 Para ver las versiones de Visual Studio compatibles con cada característica, consulte [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Tareas clave
 Use las tareas siguientes para validar el software.

|**Tareas**|**Temas relacionados**|
|---------------|---------------------------|
|**Make sure your model is consistent:**<br /><br /> En función de la forma en que el proyecto usa e interpreta los modelos, podría ser útil impedir algunas combinaciones de elementos. Por ejemplo, puede restringir las clases UML para que siempre tengan nombres conformes a [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]. Puede definir restricciones como estas en las extensiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|-   [Validate your UML model](../modeling/validate-your-uml-model.md)<br />-   [Define validation constraints for UML models](../modeling/define-validation-constraints-for-uml-models.md)|
|**Asegúrese de que el software cumple los requisitos de los usuarios**:<br /><br /> Puede usar modelos arquitectónicos y modelos de requisitos que le ayuden a organizar las pruebas del sistema y sus componentes. Con esta práctica, tendrá la certeza de que incluye en la prueba los requisitos que son importantes para los usuarios y otras partes interesadas, y podrá actualizar las pruebas rápidamente cuando cambien los requisitos.|-   [Develop tests from a model](../modeling/develop-tests-from-a-model.md)|
|**Asegúrese de que el software mantiene la coherencia con el diseño previsto del sistema:**<br /><br /> En los diagramas de capas se describen las dependencias previstas entre los componentes de la aplicación. Durante el desarrollo, puede comprobar si las dependencias reales del código se ajustan al diseño previsto.|-   [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Recursos externos

|**Categoría**|**Links**|
|------------------|---------------|
|**Vídeos**|![link to video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Doug Seven: Code Understanding and System Design with Visual Studio 2010](https://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![link to video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Architecting an Application using a Layer Diagram](https://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![link to video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN How Do I Series: How to Validate Code using Layer Diagrams](https://go.microsoft.com/fwlink/?LinkID=214405)|
|**Foros**|-   [Herramientas de visualización y modelado de Visual Studio](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [SDK de visualización y modelado de Visual Studio (Herramientas ADSL)](https://go.microsoft.com/fwlink/?LinkId=184721)|
|**Blogs**|-   [Blog de Visual Studio ALM + Team Foundation Server](https://go.microsoft.com/fwlink/?LinkID=201340)|
|**Artículos y diarios técnicos**|[Centro de arquitectura - MSDN](https://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>Vea también
 [Testing the application](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md) [Model user requirements](../modeling/model-user-requirements.md) [Analyzing and Modeling Architecture](../modeling/analyze-and-model-your-architecture.md)
