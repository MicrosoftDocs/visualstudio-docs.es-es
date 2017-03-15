---
title: Analizar y modelar la arquitectura | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
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
caps.latest.revision: 127
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 98d1214d1cda81102f9e03a8ce8b83886aa2c0ec
ms.openlocfilehash: 78217396085aa5531ec2cbdd5dff522201287777
ms.lasthandoff: 02/22/2017

---
# <a name="analyze-and-model-your-architecture"></a>Analizar y modelar la arquitectura
Asegúrese de que la aplicación cumple los requisitos de arquitectura mediante la arquitectura de Visual Studio y herramientas de modelado para diseñar y modelar la aplicación. 

* Use Visual Studio para visualizar la estructura, el comportamiento y las relaciones del código, y así comprender más fácilmente el código actual del programa. 

* Formar a su equipo en la necesidad de respetar las dependencias arquitectónicas.  
  
* Cree modelos con distintos niveles de detalle a lo largo del ciclo de vida de la aplicación como parte del proceso de desarrollo.

Consulte [escenario: cambiar el diseño mediante visualización y modelado](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).  
  
## <a name="to"></a>En  
  
|||  
|-|-|  
|**Visualizar el código**:<br /><br /> -Consulte el código de la organización y las relaciones mediante la creación de mapas de código. Visualice las dependencias entre ensamblados, espacios de nombres, clases, métodos, etcétera.<br />-Consulte la estructura de clases y miembros de un proyecto específico creando diagramas de clases desde el código.<br />-Busque los conflictos entre el código y su diseño creando diagramas de dependencia para validar el código.|-   [Visualizar el código](../modeling/visualize-code.md)<br />-   [Trabajar con clases y otros tipos (Diseñador de clases)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Vídeo: Comprender el diseño desde el código con mapas de código de Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [Vídeo: Validar las dependencias de la arquitectura en tiempo real](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|  
|**Definir la arquitectura**:<br /><br /> -Defina y aplique restricciones a las dependencias entre los componentes de código creando diagramas de dependencia.|-   [Vídeo: Valide las dependencias de la arquitectura con Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**Validar el sistema con los requisitos y el diseño previsto:**<br /><br /> -Validar las dependencias del código con diagramas de dependencia que describen la arquitectura planeada y evite los cambios que entran en conflicto con el diseño.|-   [Vídeo: Valide las dependencias de la arquitectura con Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**Compartir modelos, diagramas y mapas de código mediante el control de versiones de Team Foundation**:<br /><br /> -Poner los mapas de código, proyectos y diagramas de deoendency bajo control de versiones de Team Foundation para poder compartirlos.|Cuando haya varios usuarios que trabajen con estos elementos en el control de versiones de Team Foundation, use estas instrucciones para evitar problemas con el control de versiones:<br /><br /> -   [Administrar modelos y diagramas con control de versiones](../modeling/manage-models-and-diagrams-under-version-control.md)|  
|**Personalizar modelos y diagramas**:<br /><br /> : Cree sus propios lenguajes específicos de dominio.|-   [Modelar el SDK de Visual Studio - lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**Generación de texto usando plantillas T4**:<br /><br /> -Utilice bloques de texto y lógica de control dentro de las plantillas para generar archivos de texto.<br /> -Compilación de la plantilla de T4 con MSBuild incluida en Visual Studio|-   [Generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md)|

Para ver las versiones de Visual Studio compatibles con cada característica, consulte [compatibilidad con la versión de arquitectura y herramientas de modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="types-of-models-and-their-uses"></a>Tipos de modelos y usos  
  
|**Tipo de modelo y usos habituales**|  
|-------------------------------------|  
|**Mapas de código**<br /><br /> Los mapas de código ayudan a ver la organización y las relaciones existentes en el código.<br /><br /> Usos típicos:<br /><br /> -Examinar el código de programa para entender mejor su estructura y sus dependencias, cómo actualizarlo y calcular el costo de los cambios propuestos.<br /><br /> Vea:<br /><br /> -   [Asignar dependencias en sus soluciones](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Buscar problemas potenciales mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**Diagrama de dependencia**<br /><br /> Diagramas de dependencia permiten definir la estructura de una aplicación como un conjunto de capas o bloques con dependencias explícitas. Puede ejecutar la validación para detectar conflictos entre las dependencias del código y las dependencias descritas en un diagrama de dependencia.<br /><br /> Usos típicos:<br /><br /> -Estabilizar la estructura de la aplicación a través de numerosos cambios a lo largo de su vida.<br />-Detectar conflictos de dependencia involuntarios antes de proteger los cambios en el código.<br /><br /> Vea:<br /><br /> -   [Crear diagramas de dependencia desde el código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)<br />-   [Validar código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)|  
|**Lenguaje específico de dominio (DSL)**<br /><br /> Un DSL es una notación que se diseña con un objetivo concreto. En Visual Studio, suele ser un objetivo gráfico.<br /><br /> Usos típicos:<br /><br /> -Generar o configurar partes de la aplicación. Hay que realizar algún trabajo para desarrollar la notación y las herramientas. El resultado puede ser un mejor ajuste al dominio que una personalización UML.<br />-Para proyectos grandes o en líneas de productos donde la inversión en desarrollo de DSL y sus herramientas se devuelve cuando se usa en más de un proyecto.<br /><br /> Vea:<br /><br /> -   [Modelar el SDK de Visual Studio - lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>¿Dónde puedo obtener más información?  
  
[Visual Studio de visualización aspecto foro sobre herramientas de modelado](http://go.microsoft.com/fwlink/?LinkId=184720)  
  
## <a name="see-also"></a>Vea también  
 [Novedades](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [Operaciones de desarrollo y administración del ciclo de vida de aplicaciones](http://msdn.microsoft.com/Library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)

