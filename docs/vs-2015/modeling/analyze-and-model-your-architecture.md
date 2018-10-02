---
title: Analizar y modelar la arquitectura | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: get-started-article
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 129
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1d2accb12f172cc5a6e4b69026a58a1cc04937ce
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566771"
---
# <a name="analyze-and-model-your-architecture"></a>Analizar y modelar la arquitectura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [analizar y modelar la arquitectura](https://docs.microsoft.com/visualstudio/modeling/analyze-and-model-your-architecture).  
  
Asegúrese de que la aplicación cumple los requisitos de usuario: use la arquitectura de Visual Studio y las herramientas de modelado para diseñar y modelar la aplicación. Use Visual Studio para visualizar la estructura, el comportamiento y las relaciones del código, y así comprender más fácilmente el código actual del programa.  
  
 Cree modelos con distintos niveles de detalle a lo largo del ciclo de vida de la aplicación como parte del proceso de desarrollo. Vincule elementos del modelo a elementos de trabajo de Team Foundation Server y su plan de desarrollo. De este modo, podrá realizar un seguimiento de los requisitos, las tareas, los casos de prueba, los errores y otros trabajos asociados con los modelos. Consulte [escenario: cambiar el diseño usando modelado y visualización](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).  
  
 Para ver qué versiones de Visual Studio admite cada característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="to"></a>En  
  
|||  
|-|-|  
|**Visualizar el código**:<br /><br /> -Consulte el código de la organización y las relaciones mediante la creación de mapas de código. Visualice las dependencias entre ensamblados, espacios de nombres, clases, métodos, etcétera.<br />-Consulte la estructura de clases y miembros de un proyecto específico creando diagramas de clases desde el código.<br />-Encontrar conflictos entre el código y su diseño creando diagramas de capas para validar el código.<br /><br /> **Nota**: en esta versión de Visual Studio, se usa el término *mapa de código* en lugar de *gráfico de dependencias*. El término *gráfico* , cuando se usa solo, suele hacer referencia a un gráfico dirigido o a un diagrama DGML (o documento). Los mapas de código son un tipo especializado de diagrama DGML.|-   [Visualizar el código](../modeling/visualize-code.md)<br />-   [Trabajar con clases y otros tipos (Diseñador de clases)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Vídeo: Comprenda las dependencias del código visualizándolas (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252065)<br />-   [Vídeo: Visualice el impacto de un cambio (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252068)|  
|**Describir y comunicar requisitos de usuario**:<br /><br /> -Aclarar los casos de usuario, las reglas de negocios y otros requisitos y ayudar a garantizar su coherencia dibujando diagramas de UML, como el caso de uso, actividad y diagramas de clases.|-   [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)<br />-   [Requisitos de usuario del modelo](../modeling/model-user-requirements.md)<br />-   [Vídeo: Mejora de la arquitectura mediante modelado (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252078)|  
|**Definir la arquitectura**:<br /><br /> -Modelar la estructura de su sistema de software y los patrones de diseño a gran escala dibujando diagramas de secuencia, clase y componente de UML.<br />-Definir y aplicar restricciones a las dependencias entre los componentes del código mediante la creación de diagramas de capas.|-   [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)<br />-   [Modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)<br />-   [Vídeo: Mejora de la arquitectura mediante modelado (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252078)<br />-   [Vídeo: Uso de diagramas de capas para diseñar y validar la arquitectura (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252073)|  
|**Validar el sistema con los requisitos y el diseño previsto:**<br /><br /> -Definir pruebas de aceptación o pruebas basadas en los modelos de requisitos del sistema. De este modo, establecerá una fuerte relación entre las pruebas y los requisitos del usuario, y costará menos actualizar el sistema cuando cambien los requisitos.<br />-Validar las dependencias del código con diagramas de capas que describen la arquitectura planeada y evite los cambios que entran en conflicto con el diseño.|-   [Validar el sistema durante el desarrollo](../modeling/validate-your-system-during-development.md)<br />-   [Vídeo: Uso de diagramas de capas para diseñar y validar la arquitectura (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252073)|  
|**Compartir modelos, diagramas y mapas de código mediante el control de versiones de Team Foundation**:<br /><br /> -Coloque los mapas de código, proyectos, diagramas de UML y diagramas de capas en el control de versiones de Team Foundation de modelado para poder compartirlos.|Cuando haya varios usuarios que trabajen con estos elementos en el control de versiones de Team Foundation, use estas instrucciones para evitar problemas con el control de versiones:<br /><br /> -   [Administrar modelos y diagramas con control de versiones](../modeling/manage-models-and-diagrams-under-version-control.md)|  
|**Generar o configurar partes de la aplicación a partir de UML o de los lenguajes específicos de dominio**:<br /><br /> -Haga que su diseño responda mejor a los cambios de requisitos y variable fácilmente a través de una línea de productos.|-   [Generar y configurar su aplicación a partir de modelos](../modeling/generate-and-configure-your-app-from-models.md)|  
|**Personalizar modelos y diagramas**:<br /><br /> -Adaptar modelos de cómo usan en el proyecto definiendo propiedades adicionales para los elementos UML, restricciones de validación para asegurarse de que los modelos se ajustan a sus reglas de negocios y otros comandos de menú y elementos de cuadro de herramientas.<br />-Crear sus propios lenguajes específicos de dominio.|-   [Ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md)<br />-   [SDK de modelado para Visual Studio - lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**Generación de texto usando plantillas T4**:<br /><br /> -Use bloques de texto y lógica de control dentro de las plantillas para generar archivos de texto.|-   [Generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md)|  
  
## <a name="types-of-models-and-their-uses"></a>Tipos de modelos y usos  
  
|**Tipo y modelo y usos habituales**|  
|-------------------------------------|  
|**Mapas de código**<br /><br /> Los mapas de código ayudan a ver la organización y las relaciones existentes en el código.<br /><br /> Usos típicos:<br /><br /> -Examinar el código de programa para que pueda comprender mejor su estructura y sus dependencias, cómo actualizarlo y calcular el costo de los cambios propuestos.<br /><br /> Vea:<br /><br /> -   [Asignar dependencias en sus soluciones](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Usar mapas de código para depurar sus aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Buscar problemas potenciales mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**Diagrama de capas**<br /><br /> Los diagramas de capas permiten definir la estructura de una aplicación como un conjunto de capas o bloques con dependencias explícitas. Puede ejecutar la validación para detectar conflictos entre dependencias del código y las dependencias descritas en un diagrama de capas.<br /><br /> Usos típicos:<br /><br /> -Estabilizar la estructura de la aplicación a través de numerosos cambios durante su vida útil.<br />-Detectar conflictos de dependencia involuntarios antes de comprobar los cambios en el código.<br /><br /> Vea:<br /><br /> -   [Crear diagramas de capas desde el código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de capas: referencia](../modeling/layer-diagrams-reference.md)<br />-   [Validar código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md)|  
|**Modelo UML**<br /><br /> Un modelo UML incluye varias vistas, como son los diagramas de secuencias, clases, componentes, casos de uso y actividades. Puede personalizar el modelo UML para que se ajuste al dominio de la aplicación. Por ejemplo, puede adjuntar etiquetas, información adicional y restricciones a los elementos del modelo. También puede definir herramientas que actúen en los modelos. Consulte [crear modelos para la aplicación](../modeling/create-models-for-your-app.md).<br /><br /> Usos típicos:<br /><br /> -Describir requisitos y diseño. Puede aplicar rápidamente UML al desarrollo de cualquier aplicación. Consulte [usar modelos en el proceso de desarrollo](../modeling/use-models-in-your-development-process.md).<br />-Generar o configurar las pruebas o partes de una aplicación. Es necesario realizar algún trabajo para personalizar la notación y desarrollar las plantillas de generación o la aplicación configurable. Consulte [generar y configurar su aplicación a partir de modelos](../modeling/generate-and-configure-your-app-from-models.md).<br />-Para una descripción general y de generación de código o configuración en los proyectos más pequeños.|  
|**Lenguaje específico del dominio (DSL)**<br /><br /> Un DSL es una notación que se diseña con un objetivo concreto. En Visual Studio, suele ser un objetivo gráfico.<br /><br /> Usos típicos:<br /><br /> -Generar o configurar partes de la aplicación. Hay que realizar algún trabajo para desarrollar la notación y las herramientas. El resultado puede ser un mejor ajuste al dominio que una personalización UML.<br />-Para proyectos grandes o en líneas de productos que se devuelve la inversión en desarrollo de DSL y sus herramientas por su uso en más de un proyecto.<br /><br /> Vea:<br /><br /> -   [SDK de modelado para Visual Studio - lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>¿Dónde puedo obtener más información?  
  
|||  
|-|-|  
|**Foros**|-   [Herramientas de visualización y modelado de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [SDK de visualización y modelado de Visual Studio (Herramientas ADSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
  
## <a name="see-also"></a>Vea también  
 [Novedades](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [DevOps y administración del ciclo de vida de aplicaciones](http://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)



