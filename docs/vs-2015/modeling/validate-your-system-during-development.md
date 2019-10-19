---
title: Validar el sistema durante el desarrollo | Microsoft Docs
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
ms.openlocfilehash: 489642936c6b309cd7a30eb6e0a5ad9b0edc8bd0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659413"
---
# <a name="validate-your-system-during-development"></a>Validar el sistema durante el desarrollo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio puede ayudarle a mantener la coherencia del software con los requisitos de los usuarios y con la arquitectura del sistema.

 Para ver las versiones de Visual Studio compatibles con cada característica, consulte [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Tareas clave
 Use las tareas siguientes para validar el software.

|**Tareas**|**Temas relacionados**|
|---------------|---------------------------|
|**Asegúrese de que el modelo es coherente:**<br /><br /> En función de la forma en que el proyecto usa e interpreta los modelos, podría ser útil impedir algunas combinaciones de elementos. Por ejemplo, puede restringir las clases UML para que siempre tengan nombres conformes a [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]. Puede definir restricciones como estas en las extensiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|-   [validar el modelo UML](../modeling/validate-your-uml-model.md)<br />-   [definir restricciones de validación para modelos UML](../modeling/define-validation-constraints-for-uml-models.md)|
|**Asegúrese de que el software cumple los requisitos de los usuarios**:<br /><br /> Puede usar modelos arquitectónicos y modelos de requisitos que le ayuden a organizar las pruebas del sistema y sus componentes. Con esta práctica, tendrá la certeza de que incluye en la prueba los requisitos que son importantes para los usuarios y otras partes interesadas, y podrá actualizar las pruebas rápidamente cuando cambien los requisitos.|-   [desarrollar pruebas a partir de un modelo](../modeling/develop-tests-from-a-model.md)|
|**Asegúrese de que el software mantiene la coherencia con el diseño previsto del sistema:**<br /><br /> En los diagramas de capas se describen las dependencias previstas entre los componentes de la aplicación. Durante el desarrollo, puede comprobar si las dependencias reales del código se ajustan al diseño previsto.|-   [crear diagramas de capas a partir del código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [validar el código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Recursos externos

|**Categoría**|**Links**|
|------------------|---------------|
|**Vídeos**|![vínculo al canal de vídeo](../data-tools/media/playvideo.gif "PlayVideo") [9: Doug siete: comprensión del código y diseño del sistema con Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![vínculo al canal de vídeo](../data-tools/media/playvideo.gif "PlayVideo") [9: diseño de una aplicación con un diagrama de capas](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![vínculo a vídeo](../data-tools/media/playvideo.gif "PlayVideo") [: cómo validar código mediante diagramas de capas](http://go.microsoft.com/fwlink/?LinkID=214405)|
|**Foros**|-   [Herramientas de visualización y modelado de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [SDK de visualización y modelado de Visual Studio (Herramientas ADSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|
|**Blogs**|-   [Blog de Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)|
|**Artículos y diarios técnicos**|[Centro de arquitectura - MSDN](http://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>Vea también
 [Probar la aplicación](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md) [requisitos de usuario modelo](../modeling/model-user-requirements.md) [de análisis y modelado arquitectura](../modeling/analyze-and-model-your-architecture.md)
