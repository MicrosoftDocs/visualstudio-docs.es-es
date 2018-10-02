---
title: Validar el sistema durante el desarrollo | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 39
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8b0d65d99cf99c7f1468a0bf596eb687f931b5d3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580578"
---
# <a name="validate-your-system-during-development"></a>Validar el sistema durante el desarrollo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [validar el sistema durante el desarrollo](https://docs.microsoft.com/visualstudio/modeling/validate-your-system-during-development).  
  
Visual Studio puede ayudarle a mantener la coherencia del software con los requisitos de los usuarios y con la arquitectura del sistema.  
  
 Para ver las versiones de Visual Studio compatibles con cada característica, consulte [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="key-tasks"></a>Tareas clave  
 Use las tareas siguientes para validar el software.  
  
|**Tareas**|**Temas relacionados**|  
|---------------|---------------------------|  
|**Asegúrese de que el modelo es coherente:**<br /><br /> En función de la forma en que el proyecto usa e interpreta los modelos, podría ser útil impedir algunas combinaciones de elementos. Por ejemplo, puede restringir las clases UML para que siempre tengan nombres conformes a [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]. Puede definir restricciones como estas en las extensiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|-   [Validar el modelo UML](../modeling/validate-your-uml-model.md)<br />-   [Definir restricciones de validación para modelos UML](../modeling/define-validation-constraints-for-uml-models.md)|  
|**Asegúrese de que el software cumple los requisitos de los usuarios**:<br /><br /> Puede usar modelos arquitectónicos y modelos de requisitos que le ayuden a organizar las pruebas del sistema y sus componentes. Con esta práctica, tendrá la certeza de que incluye en la prueba los requisitos que son importantes para los usuarios y otras partes interesadas, y podrá actualizar las pruebas rápidamente cuando cambien los requisitos.|-   [Desarrollar pruebas en un modelo](../modeling/develop-tests-from-a-model.md)|  
|**Asegúrese de que el software mantiene la coherencia con el diseño previsto del sistema:**<br /><br /> En los diagramas de capas se describen las dependencias previstas entre los componentes de la aplicación. Durante el desarrollo, puede comprobar si las dependencias reales del código se ajustan al diseño previsto.|-   [Crear diagramas de capas desde el código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Validar código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md)|  
  
## <a name="external-resources"></a>Recursos externos  
  
|**Categoría**|**Vínculos**|  
|------------------|---------------|  
|**Vídeos**|![vínculo a vídeo](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Doug siete: comprensión del código y diseño del sistema con Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![vínculo a vídeo](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: diseñar una aplicación con un diagrama de capas](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![vínculo a vídeo](../data-tools/media/playvideo.gif "PlayVideo") [MSDN How Do I Series: cómo validar código con diagramas de capas](http://go.microsoft.com/fwlink/?LinkID=214405)|  
|**Foros**|-   [Herramientas de visualización y modelado de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [SDK de visualización y modelado de Visual Studio (Herramientas DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blogs**|-   [Blog de Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Artículos y diarios técnicos**|[Centro de arquitectura - MSDN](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Vea también  
 [Probar la aplicación](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)   
 [Ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Requisitos de usuario del modelo](../modeling/model-user-requirements.md)   
 [Analizar y modelar la arquitectura](../modeling/analyze-and-model-your-architecture.md)



