---
title: Analizar y modelar la arquitectura | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 49c421af5aa6c91535b05f0beca88099ea7a2eaa
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297948"
---
# <a name="analyze-and-model-your-architecture"></a>Analizar y modelar la arquitectura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Asegúrese de que la aplicación cumple los requisitos de usuario: use la arquitectura de Visual Studio y las herramientas de modelado para diseñar y modelar la aplicación. Use Visual Studio para visualizar la estructura, el comportamiento y las relaciones del código, y así comprender más fácilmente el código actual del programa.

 Cree modelos con distintos niveles de detalle a lo largo del ciclo de vida de la aplicación como parte del proceso de desarrollo. Vincule elementos del modelo a elementos de trabajo de Team Foundation Server y su plan de desarrollo. De este modo, podrá realizar un seguimiento de los requisitos, las tareas, los casos de prueba, los errores y otros trabajos asociados con los modelos. Vea [escenario: cambiar el diseño mediante la visualización y el modelado](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

 Para ver qué versiones de Visual Studio admite cada característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="to"></a>Para

|||
|-|-|
|**Visualizar el código**:<br /><br /> -Vea la organización y las relaciones del código mediante la creación de mapas de código. Visualice las dependencias entre ensamblados, espacios de nombres, clases, métodos, etcétera.<br />-Vea la estructura de clase y los miembros de un proyecto específico mediante la creación de diagramas de clases a partir del código.<br />-Encuentre conflictos entre el código y su diseño mediante la creación de diagramas de capas para validar el código.<br /><br /> **Nota**: en esta versión de Visual Studio, se usa el término *mapa de código* en lugar de *gráfico de dependencias*. El término *gráfico* , cuando se usa solo, suele hacer referencia a un gráfico dirigido o a un diagrama DGML (o documento). Los mapas de código son un tipo especializado de diagrama DGML.|-   [Visualizar el código](../modeling/visualize-code.md)<br />-   [trabajar con clases y otros tipos (diseñador de clases)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [vídeo: comprender las dependencias de código mediante la visualización (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252065)<br />-   [vídeo: visualización del impacto de un cambio (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252068)|
|**Describir y comunicar requisitos de usuario**:<br /><br /> -Aclare los casos de usuario, las reglas de negocios y otros requisitos, y ayude a garantizar su coherencia dibujando diagramas de UML, como diagramas de casos de uso, actividades y clases.|-   [crear modelos para la aplicación](../modeling/create-models-for-your-app.md)<br />[requisitos de usuario del modelo](../modeling/model-user-requirements.md) de -   <br />-   [vídeo: mejora de la arquitectura a través del modelado (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252078)|
|**Definir la arquitectura**:<br /><br /> : Modelar la estructura a gran escala del sistema de software y los patrones de diseño dibujando los diagramas de componentes, clases y secuencias de UML.<br />-Defina y aplique restricciones a las dependencias entre los componentes del código mediante la creación de diagramas de capas.|-   [crear modelos para la aplicación](../modeling/create-models-for-your-app.md)<br />-   [modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)<br />-   [vídeo: mejora de la arquitectura a través del modelado (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252078)<br />-   [vídeo: uso de diagramas de capas para diseñar y validar la arquitectura (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252073)|
|**Validar el sistema con los requisitos y el diseño previsto:**<br /><br /> -Definir pruebas de aceptación o pruebas del sistema basadas en los modelos de requisitos. De este modo, establecerá una fuerte relación entre las pruebas y los requisitos del usuario, y costará menos actualizar el sistema cuando cambien los requisitos.<br />-Validar las dependencias de código con diagramas de capas que describen la arquitectura prevista y evitar cambios que puedan entrar en conflicto con el diseño.|-   [validar el sistema durante el desarrollo](../modeling/validate-your-system-during-development.md)<br />-   [vídeo: uso de diagramas de capas para diseñar y validar la arquitectura (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252073)|
|**Compartir modelos, diagramas y mapas de código mediante el control de versiones de Team Foundation**:<br /><br /> -Coloque los mapas de código, los proyectos de modelado, los diagramas de UML y los diagramas de capas en el control de versiones de Team Foundation para poder compartirlos.|Cuando haya varios usuarios que trabajen con estos elementos en el control de versiones de Team Foundation, use estas instrucciones para evitar problemas con el control de versiones:<br /><br /> -   [administrar modelos y diagramas en el control de versiones](../modeling/manage-models-and-diagrams-under-version-control.md)|
|**Generar o configurar partes de la aplicación a partir de UML o de los lenguajes específicos de dominio**:<br /><br /> : Haga que su diseño tenga mayor capacidad de respuesta a los cambios en los requisitos y sea fácilmente variable en una línea de productos.|-   [generar y configurar la aplicación a partir de modelos](../modeling/generate-and-configure-your-app-from-models.md)|
|**Personalizar modelos y diagramas**:<br /><br /> -Adapte los modelos a cómo los usa su proyecto definiendo propiedades adicionales para los elementos UML, restricciones de validación para asegurarse de que los modelos se ajustan a las reglas de negocios, así como los comandos de menú y los elementos de cuadro de herramientas adicionales.<br />-Cree sus propios lenguajes específicos de dominio.|-   [extender modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md)<br />[SDK de modelado de -   para Visual Studio: lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generación de texto usando plantillas T4**:<br /><br /> -Use bloques de texto y lógica de control dentro de las plantillas para generar archivos basados en texto.|-   [de generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md)|

## <a name="types-of-models-and-their-uses"></a>Tipos de modelos y usos

|**Tipo y modelo y usos habituales**|
|-------------------------------------|
|**Mapas de código**<br /><br /> Los mapas de código ayudan a ver la organización y las relaciones existentes en el código.<br /><br /> Usos típicos:<br /><br /> -Examine el código del programa para que pueda entender mejor su estructura y sus dependencias, cómo actualizarlo y calcular el costo de los cambios propuestos.<br /><br /> Vea:<br /><br /> -   [asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)<br />-   [usar mapas de código para depurar las aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)|
|**Diagrama de capas**<br /><br /> Los diagramas de capas permiten definir la estructura de una aplicación como un conjunto de capas o bloques con dependencias explícitas. Puede ejecutar la validación para detectar conflictos entre dependencias del código y las dependencias descritas en un diagrama de capas.<br /><br /> Usos típicos:<br /><br /> -Estabilizar la estructura de la aplicación a través de varios cambios a lo largo de su vida.<br />-Detectar conflictos de dependencias involuntarias antes de proteger los cambios en el código.<br /><br /> Vea:<br /><br /> -   [crear diagramas de capas a partir del código](../modeling/create-layer-diagrams-from-your-code.md)<br />[diagramas de capas de -   : referencia](../modeling/layer-diagrams-reference.md)<br />-   [validar el código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md)|
|**Modelo UML**<br /><br /> Un modelo UML incluye varias vistas, como son los diagramas de secuencias, clases, componentes, casos de uso y actividades. Puede personalizar el modelo UML para que se ajuste al dominio de la aplicación. Por ejemplo, puede adjuntar etiquetas, información adicional y restricciones a los elementos del modelo. También puede definir herramientas que actúen en los modelos. Consulte [crear modelos para la aplicación](../modeling/create-models-for-your-app.md).<br /><br /> Usos típicos:<br /><br /> : Describir los requisitos y el diseño. Puede aplicar rápidamente UML al desarrollo de cualquier aplicación. Consulte [uso de modelos en el proceso de desarrollo](../modeling/use-models-in-your-development-process.md).<br />-Generar o configurar pruebas o partes de una aplicación. Es necesario realizar algún trabajo para personalizar la notación y desarrollar las plantillas de generación o la aplicación configurable. Consulte [generación y configuración de la aplicación a partir de modelos](../modeling/generate-and-configure-your-app-from-models.md).<br />-Para la descripción general y para la generación de código o la configuración en proyectos más pequeños.|
|**Lenguaje específico del dominio (DSL)**<br /><br /> Un DSL es una notación que se diseña con un objetivo concreto. En Visual Studio, suele ser un objetivo gráfico.<br /><br /> Usos típicos:<br /><br /> -Generar o configurar partes de la aplicación. Hay que realizar algún trabajo para desarrollar la notación y las herramientas. El resultado puede ser un mejor ajuste al dominio que una personalización UML.<br />-En proyectos grandes o en líneas de productos en las que la inversión en el desarrollo de DSL y sus herramientas se devuelve por su uso en más de un proyecto.<br /><br /> Vea:<br /><br /> [SDK de modelado de -   para Visual Studio: lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>¿Dónde puedo obtener más información?

|||
|-|-|
|**Foros**|-   [Herramientas de visualización y modelado de Visual Studio](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [SDK de visualización y modelado de Visual Studio (Herramientas ADSL)](https://go.microsoft.com/fwlink/?LinkId=184721)|

## <a name="see-also"></a>Vea también

- [Novedades del modelado en Visual Studio 2015](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps y administración del ciclo de vida de las aplicaciones](https://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
