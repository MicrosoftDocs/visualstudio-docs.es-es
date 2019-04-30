---
title: 'Escenario: Cambiar el diseño usando modelado y visualización | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
ms.assetid: ccc80825-a4a0-44fa-a0bb-f95254785a3b
caps.latest.revision: 63
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 914d5806ed0b40a227d61c673e5f463624b0cc11
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63403571"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Escenario: Cambiar el diseño mediante herramientas de visualización y modelado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Asegúrese de que su sistema de software cumple las necesidades de los usuarios mediante las herramientas de visualización y modelado de Visual Studio. Use herramientas como diagramas de Lenguaje de modelos unificado (UML), mapas de código, diagramas de capas y diagramas de clases para:  
  
 Para ver qué versiones de Visual Studio admite cada herramienta, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
- Aclarar los requisitos y procesos de negocio de los usuarios.  
  
- Visualizar y explorar el código existente.  
  
- Describir los cambios de un sistema existente.  
  
- Verificar que el sistema cumple sus requisitos.  
  
- Mantener la coherencia del código con el diseño.  
  
  Este tutorial:  
  
- Describe la manera en que estas herramientas pueden beneficiar a su proyecto de software.  
  
- Muestra cómo puede usar estas herramientas, independientemente de su enfoque de desarrollo, con un escenario de ejemplo.  
  
  Para obtener más información acerca de estas herramientas y los escenarios compatibles, vea:  
  
- [Analizar y modelar la arquitectura](../modeling/analyze-and-model-your-architecture.md)  
  
- [Visualizar el código](../modeling/visualize-code.md)  
  
- [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)  
  
## <a name="ScenarioOverview"></a> Información general del escenario  
 Este escenario describe capítulos de los ciclos de vida de desarrollo de software de dos empresas ficticias: Dinner Now y Lucerne Publishing. Dinner Now, con sede en Seattle, proporciona un servicio de comida a domicilio basado en web. A través de él, los clientes pueden pedir comida y pagarla en el sitio web de Dinner Now. Los pedidos se envían entonces al restaurante local que corresponda para que realice la entrega. Lucerne Publishing es una empresa de Nueva York con varios negocios tanto en Internet como fuera de ella. Entre esos negocios, Lucerne cuenta con un sitio web donde los clientes pueden publicar opiniones sobre restaurantes.  
  
 Lucerne adquirió recientemente Dinner Now y quiere realizar los siguientes cambios:  
  
- Integrar sus sitios web y agregar la opción de opinar en Dinner Now.  
  
- Reemplazar el sistema de pago de Dinner Now por el sistema de Lucerne.  
  
- Ampliar el servicio de Dinner Now a toda la región.  
  
  En Dinner Now usan programación eXtreme y SCRUM y tienen una cobertura de pruebas muy elevada y mucho código compatible. Minimizan los riesgos mediante la creación de versiones de un sistema, pequeñas pero funcionales, a las que se les agrega funcionalidad de forma incremental. Desarrollan el código en iteraciones cortas y frecuentes, lo que les permite adoptar cambios con confianza, refactorizar el código frecuentemente y evitar tener que realizar un "gran diseño por adelantado".  
  
  Lucerne mantiene una colección mucho más grande y compleja de sistemas, algunos de los cuales tienen más de 40 años de antigüedad. Son muy prudentes a la hora de realizar cambios debido a la complejidad y al ámbito del código heredado. Siguen un proceso de desarrollo más riguroso; prefieren diseñar soluciones detalladas y documentar el diseño y los cambios que se producen durante el desarrollo.  
  
  Ambos equipos usan diagramas de modelado de Visual Studio para desarrollar sistemas que satisfagan las necesidades del usuario. Asimismo, usan Team Foundation Server junto con otras herramientas para la planeación, organización y administración de su trabajo.  
  
  Para obtener más información acerca de Team Foundation Server, vea:  
  
- [Planeación y seguimiento del trabajo](#PlanningTracking)  
  
- [Pruebas, validación y protección de código actualizado](#TestValidateCheckInCode)  
  
## <a name="ModelingDiagramsTools"></a> Roles de arquitectura y diagramas de modelado en el desarrollo de software  
 En la tabla siguiente se describen las funciones que estas herramientas pueden desempeñar durante múltiples y diversas fases del ciclo de vida de desarrollo de software:  
  
||**Modelado de requisitos de usuarios**|**Modelado de procesos de negocio**|**Diseño y arquitectura de sistemas**|**Visualización y exploración de código**|**Comprobación**|  
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|  
|Diagrama de casos de uso (UML)|√|√|||√|  
|Diagrama de actividades (UML)|√|√|√||√|  
|Diagrama de clases (UML)|√|√|√||√|  
|Diagrama de componentes (UML)|√|√|√||√|  
|Diagrama de secuencia (UML)|√|√|√||√|  
|Diagrama de Lenguaje específico del dominio (DSL)|√|√|√|||  
|Diagrama de capas, validación de capas|||√|√|√|  
|Mapa de código|||√|√|√|  
|Diseñador de clases (basado en código)||||√||  
  
 Para dibujar diagramas de UML y diagramas de capas, cree un proyecto de modelado como parte de una solución nueva o existente. Estos diagramas se deben crear en el proyecto de modelado. Los elementos de los diagramas de UML forman parte de un modelo común y los diagramas de UML son vistas de ese modelo. Los elementos de los diagramas de capas se encuentran en el proyecto de modelado, pero no se almacenan en el modelo común. Los mapas de código y los diagramas de clases de .NET creados a partir de código existen fuera del proyecto de modelado.  
  
 Vea:  
  
- [Crear proyectos y diagramas de modelado UML](../modeling/create-uml-modeling-projects-and-diagrams.md)  
  
- [Crear diagramas de capas a partir del código](../modeling/create-layer-diagrams-from-your-code.md)  
  
- [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)  
  
- [Cómo: Agregar diagramas de clases a proyectos (Diseñador de clases)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
- [Modelar el SDK de Visual Studio: lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  
  
  Para mostrar vistas alternativas de la arquitectura, puede volver a usar ciertos elementos del mismo modelo en varios o en distintos diagramas. Por ejemplo, puede arrastrar un componente a otro diagrama de componentes o a un diagrama de secuencia para que pueda funcionar como un actor. Consulte [modelos y diagramas UML editar](../modeling/edit-uml-models-and-diagrams.md).  
  
  Ambos equipos también usan la validación de capas para asegurarse de que el código en desarrollo siga siendo coherente con el diseño.  
  
  Vea:  
  
- [Coherencia entre código y diseño](#ValidatingCode)  
  
- [Describe la arquitectura lógica: Diagramas de capas](#DescribeLayers)  
  
- [Validar código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md)  
  
  > [!NOTE]
  > Algunas versiones de Visual Studio admiten validación de capas, versiones de solo lectura de mapas de código y diagramas de UML para visualización y modelado. Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="UnderstandingCommunicating"></a> Comprensión y comunicación de información sobre el sistema  
 No hay ningún orden establecido para usar los diagramas de modelado de Visual Studio, por lo que puede usarlos como mejor se adapten a sus necesidades o enfoque. Normalmente, los equipos revisan sus modelos de forma iterativa y con frecuencia a lo largo de un proyecto. Cada diagrama ofrece determinados puntos fuertes para ayudarle a entender, describir y comunicar diferentes aspectos del sistema en desarrollo.  
  
 Dinner Now y Lucerne se comunican entre sí y con los participantes del proyecto mediante el uso de diagramas como su lenguaje común. Por ejemplo, Dinner Now usa diagramas para realizar estas tareas:  
  
- Visualizar el código existente.  
  
- Comunicarse con Lucerne acerca de casos de usuario nuevos o actualizados.  
  
- Identificar los cambios que son necesarios para admitir casos de usuario nuevos o actualizados.  
  
  Lucerne usa diagramas para realizar estas tareas:  
  
- Obtener información acerca del proceso de negocio de Dinner Now.  
  
- Entender el diseño del sistema.  
  
- Comunicarse con Dinner Now acerca de los requisitos de usuario nuevos o actualizados.  
  
- Documentar las actualizaciones del sistema.  
  
  Los diagramas se integran con Team Foundation Server para que los equipos puedan planear, administrar y realizar un seguimiento de su trabajo más fácilmente. Por ejemplo, usan modelos para identificar los casos de prueba y las tareas de desarrollo, y para calcular su trabajo. Lucerne vincula los elementos de trabajo de Team Foundation Server con elementos del modelo para poder supervisar el progreso y asegurarse de que el sistema cumple los requisitos de los usuarios. Por ejemplo, los casos de uso se vinculan a elementos de trabajo de caso de prueba para poder ver si los casos de uso se cumplen cuando se pasan todas las pruebas.  
  
  Antes de que los equipos protejan sus cambios, el código se valida con las pruebas y el diseño mediante la ejecución de compilaciones que incluyen validación de capas y pruebas automatizadas. Con esto se garantiza que el código actualizado no está en conflicto con el diseño ni interrumpe funcionalidades que anteriormente no presentaban problemas.  
  
  Vea:  
  
- [Descripción del rol del sistema en el proceso empresarial](#UnderstandingBPMandSystemDesign)  
  
- [Descripción de los requisitos de usuario nuevos o actualizados](#DescribingURM)  
  
- [Crear pruebas de modelos](#CreatingTests)  
  
- [Identificación de cambios en el sistema existente](#DeterminingChanges)  
  
- [Keeping code consistent with the design](#ValidatingCode)  
  
- [Sugerencias generales para crear y usar modelos](#GeneralTips)  
  
- [Planeación y seguimiento del trabajo](#PlanningTracking)  
  
- [Pruebas, validación y protección de código actualizado](#TestValidateCheckInCode)  
  
### <a name="UnderstandingBPMandSystemDesign"></a> Descripción del rol del sistema en el proceso empresarial  
 Lucerne desea obtener más información acerca del proceso de negocio de Dinner Now. Para ello crean los diagramas siguientes con el fin de mejorar su entendimiento con Dinner Now:  
  
|**Diagram**|**Qué describe**|  
|-----------------|-------------------|  
|*Diagrama de casos de uso (UML)*<br /><br /> Vea:<br /><br /> -   [Diagramas de casos de uso UML: Referencia](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramas de casos de uso UML: directrices](../modeling/uml-use-case-diagrams-guidelines.md)|-Las actividades que admite el sistema de Dinner Now<br />-Las personas y los sistemas externos que realizan las actividades<br />-Los principales componentes del sistema que admiten cada actividad<br />-Las partes del proceso empresarial que están fuera del ámbito del sistema actual, por ejemplo, entrega de alimentos|  
|*Diagrama de actividades (UML)*<br /><br /> Vea:<br /><br /> -   [Diagramas de actividades UML: Referencia](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramas de actividades UML: directrices](../modeling/uml-activity-diagrams-guidelines.md)|El flujo de pasos que se producen cuando un cliente crea un pedido|  
|*Diagrama de clases (UML)*<br /><br /> Vea:<br /><br /> -   [Diagramas de clases UML: Referencia](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramas de clases UML: directrices](../modeling/uml-class-diagrams-guidelines.md)|Las entidades de negocio, los términos usados y las relaciones entre las entidades. Por ejemplo, “pedido” (Order) y “menú” (Menu) forman parte del vocabulario de este escenario.|  
  
 Por ejemplo, Lucerne crea el siguiente diagrama de casos de uso para entender las tareas que se realizan en el sitio web de Dinner Now y quién las realiza:  
  
 ![Diagrama de casos de uso UML](../modeling/media/uml-usecase.png "UML_UseCase")  
  
 **Diagrama de casos de uso UML**  
  
 El siguiente diagrama de actividades describe el flujo de pasos cuando un cliente crea un pedido en el sitio web de Dinner Now. En esta versión, los elementos de comentario identifican los roles y las líneas forman *calles*, que organizan los pasos por rol:  
  
 ![Diagrama de actividades UML](../modeling/media/uml-dinnernowprocess.png "UML_DinnerNowProcess")  
  
 **Diagrama de actividades UML**  
  
 En el siguiente diagrama de clase se describen las entidades que participan en el proceso de pedido:  
  
 ![Diagrama de clases UML](../modeling/media/uml-dinnerorders.png "UML_DinnerOrders")  
  
 **Diagrama de clases UML**  
  
### <a name="DescribingURM"></a> Descripción de los requisitos de usuario nuevos o actualizados  
 Lucerne desea agregar funcionalidad al sistema de Dinner Now para que los clientes puedan leer opiniones sobre restaurantes y aportar las suyas propias. Para ello, actualizan los diagramas siguientes, para que sean capaces de describir y analizar este nuevo requisito con Dinner Now:  
  
|**Diagram**|**Qué describe**|  
|-----------------|-------------------|  
|*Diagrama de casos de uso (UML)*<br /><br /> Vea:<br /><br /> -   [Diagramas de casos de uso UML: Referencia](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramas de casos de uso UML: directrices](../modeling/uml-use-case-diagrams-guidelines.md)|Un nuevo caso de uso de “Escribir una opinión de un restaurante” (Write a restaurant review)|  
|*Diagrama de actividades (UML)*<br /><br /> Vea:<br /><br /> -   [Diagramas de actividades UML: Referencia](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramas de actividades UML: directrices](../modeling/uml-activity-diagrams-guidelines.md)|Los pasos que se producen cuando un cliente quieren escribir una opinión sobre un restaurante|  
|*Diagrama de clases (UML)*<br /><br /> Vea:<br /><br /> -   [Diagramas de clases UML: Referencia](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramas de clases UML: directrices](../modeling/uml-class-diagrams-guidelines.md)|Los datos que son necesarios para almacenar una opinión|  
  
 Por ejemplo, el siguiente diagrama de casos de uso incluye un nuevo caso de uso de “Escribir opinión” (Write Review) para representar el nuevo requisito. Para facilitar la identificación, se resalta en color naranja en el diagrama:  
  
 ![Diagrama de casos de uso UML](../modeling/media/uml-writerev.png "UML_WriteRev")  
  
 **Diagrama de casos de uso UML**  
  
 En el siguiente diagrama de actividades se incluyen nuevos elementos en color naranja para describir el flujo de pasos en el nuevo caso de uso:  
  
 ![Diagrama de actividades UML](../modeling/media/uml-writereview.png "UML_WriteReview")  
  
 **Diagrama de actividades UML**  
  
 El siguiente diagrama de clases incluye una nueva clase para las opiniones (Review) y sus relaciones con otras clases para que los equipos puedan analizar los detalles. Observe que un cliente (Customer) y un restaurante (Restaurant) pueden tener varias opiniones:  
  
 ![Diagrama de clases UML](../modeling/media/uml-dinnerreviews.png "UML_DinnerReviews")  
  
 **Diagrama de clases UML**  
  
### <a name="CreatingTests"></a> Crear pruebas de modelos  
 Ambos equipos acuerdan que necesitan llevar a cabo un completo conjunto de pruebas en el sistema y sus componentes antes de realizar cualquier cambio. Lucerne tiene un equipo especializado que realiza las pruebas en los componentes y el sistema. Reutilizan las pruebas creadas por Dinner Now y las estructuran mediante los diagramas de UML:  
  
- Cada caso de uso está representado por una o varias pruebas. Los elementos del diagrama de caso de uso se vinculan a los elementos de trabajo del caso de prueba en Team Foundation Server.  
  
- Cada flujo de un diagrama de actividades o diagrama de secuencia de nivel de sistema está vinculado a una prueba como mínimo. El equipo de pruebas se asegura sistemáticamente de que se prueban todas las rutas posibles a través del diagrama de actividades.  
  
- Los términos usados para describir las pruebas se basan en los términos definidos por caso de uso, clase y diagramas de actividad.  
  
  A medida que cambian los requisitos y los diagramas se actualizan para reflejar dichos cambios, también se actualizan las pruebas. Un requisito solo se considera completado si se superan las pruebas. Si es posible o práctico, las pruebas se definen y se basan en diagramas de UML antes de iniciar la implementación.  
  
  Vea:  
  
- [Desarrollar pruebas a partir de un modelo](../modeling/develop-tests-from-a-model.md)  
  
- [Validar el modelo UML](../modeling/validate-your-uml-model.md)  
  
### <a name="DeterminingChanges"></a> Identifying Changes to the Existing System  
 Dinner Now debe estimar el costo de satisfacer el requisito nuevo. Esto depende en parte de en qué medida afectará este cambio a las otras partes del sistema. Para ayudarles a comprender esto, uno de los desarrolladores de Dinner Now crea estos mapas y diagramas a partir del código existente:  
  
|**Mapa o diagrama**|**Qué muestra**|  
|------------------------|---------------|  
|*Mapa de código*<br /><br /> Vea:<br /><br /> -   [Asignar dependencias en sus soluciones](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)<br />-   [Personalizar mapas de código mediante la edición de los archivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Dependencias y otras relaciones en el código.<br /><br /> Por ejemplo, Dinner Now puede empezar revisando los mapas de código de ensamblado para obtener información general de los ensamblados y de sus dependencias. Dinner Now puede profundizar en los mapas para explorar los espacios de nombres y las clases de esos ensamblados.<br /><br /> Dinner Now también puede crear mapas para explorar áreas particulares y otros tipos de relaciones en el código. Mediante el Explorador de soluciones, buscan y seleccionan las áreas y las relaciones de interés.|  
|*Diagrama de clases basado en código*<br /><br /> Vea [Cómo: Agregar diagramas de clases a proyectos (Diseñador de clases)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Clases existentes en el código|  
  
 Por ejemplo, el desarrollador crea un mapa de código y ajusta su ámbito para centrarse en las áreas que se verán afectadas por el nuevo escenario. Estas áreas se seleccionan y se resaltan en el mapa:  
  
 ![Gráfico de dependencias de Namespace](../modeling/media/namespace-reviewsystem.png "Namespace_ReviewSystem")  
  
 **Mapa de código de espacio de nombres**  
  
 El desarrollador expande los espacios de nombres seleccionados para ver sus clases, métodos y relaciones:  
  
 ![Gráfico de dependencias de espacios de nombres expandidos](../modeling/media/dep-reviewsystem.png "Dep_ReviewSystem")  
  
 **Mapa de código de espacios de nombres expandidos con vínculos entre grupos visibles**  
  
 El desarrollador examina el código para encontrar los métodos y las clases afectados. Para ver los efectos de cada cambio a medida que se producen, regenere los mapas de código después de cada cambio. Consulte [visualizar el código](../modeling/visualize-code.md).  
  
 Para describir los cambios realizados en otras partes del sistema, como componentes o interacciones, el equipo podría dibujar estos elementos en pizarras. También pueden dibujar los siguientes diagramas en Visual Studio, de manera que ambos equipos puedan capturar, administrar y entender los detalles:  
  
|**Diagramas**|**Qué describe**|  
|------------------|-------------------|  
|*Diagrama de actividades (UML)*<br /><br /> Vea:<br /><br /> -   [Diagramas de actividades UML: Referencia](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramas de actividades UML: directrices](../modeling/uml-activity-diagrams-guidelines.md)|El flujo de pasos que se producen cuando el sistema detecta que un cliente vuelve a realizar un pedido en un restaurante y le pide que escriba una opinión.|  
|*Diagrama de clases (UML)*<br /><br /> Vea:<br /><br /> -   [Diagramas de clases UML: Referencia](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramas de clases UML: directrices](../modeling/uml-class-diagrams-guidelines.md)|Las clases lógicas y sus relaciones. Por ejemplo, se agrega una nueva clase para describir una **Opinión** (Review) y sus relaciones con otras entidades, como **Restaurante**(Restaurant), **Menú**(Menu) y **Cliente**(Customer).<br /><br /> Para poder asociar opiniones a un cliente, el sistema debe almacenar detalles del cliente. Un diagrama de clases UML puede ayudar a aclarar esos detalles.|  
|*Diagrama de clases basado en código*<br /><br /> Vea [Cómo: Agregar diagramas de clases a proyectos (Diseñador de clases)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Las clases existentes en el código.|  
|*Diagrama de componentes (UML)*<br /><br /> Vea:<br /><br /> -   [Diagramas de componentes UML: Referencia](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramas de componentes UML: directrices](../modeling/uml-component-diagrams-guidelines.md)|Las partes de alto nivel del sistema, como el sitio web de Dinner Now, y sus interfaces. En estas interfaces se define cómo interactúan entre sí los componentes a través de los métodos o servicios que proporcionan y consumen.|  
|*Diagrama de secuencia (UML)*<br /><br /> Vea:<br /><br /> -   [Diagramas de secuencia UML: Referencia](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagramas de secuencia UML: directrices](../modeling/uml-sequence-diagrams-guidelines.md)|La secuencia de interacciones entre instancias.|  
  
 Por ejemplo, en el siguiente diagrama de componentes se muestra el nuevo componente, que forma parte del componente de sitio web de Dinner Now. El componente ReviewProcessing controla la funcionalidad de creación de opiniones y aparece resaltado en color naranja:  
  
 ![Diagrama de componentes UML](../modeling/media/uml-internal.png "UML_Internal")  
  
 **Diagrama de componentes UML**  
  
 En el diagrama de secuencia siguiente se muestra la secuencia de interacciones que se producen cuando el sitio web de Dinner Now comprueba si el cliente realizó anteriormente algún pedido en un restaurante. En caso afirmativo, le pregunta al cliente si quiere dejar su opinión, que se envía al restaurante y se publica en el sitio web:  
  
 ![Diagrama de secuencia UML](../modeling/media/uml-revsystem.png "UML_RevSystem")  
  
 **Diagrama de secuencia UML**  
  
### <a name="ValidatingCode"></a> Coherencia entre código y diseño  
 Dinner Now debe asegurarse de que el código actualizado mantiene la coherencia con el diseño. Crea diagramas de capas en los que se describen las capas de funcionalidad del sistema, se especifican las dependencias permitidas entre ellas y se asocian artefactos de la solución a esas capas.  
  
|**Diagram**|**Qué describe**|  
|-----------------|-------------------|  
|*Diagrama de capas*<br /><br /> Vea:<br /><br /> -   [Crear diagramas de capas desde el código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de capas: Referencia](../modeling/layer-diagrams-reference.md)<br />-   [Diagramas de capas: directrices](../modeling/layer-diagrams-guidelines.md)<br />-   [Validar código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md)|La arquitectura lógica del código.<br /><br /> Un diagrama de capas organiza y asigna los artefactos de una solución de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para abstraer grupos denominados *capas*. Estas capas identifican los roles, las tareas o las funciones que realizan estos artefactos en el sistema.<br /><br /> Los diagramas de capas son útiles para describir el diseño previsto del sistema y validar el código cambiante comparándolo con ese diseño.<br /><br /> Para crear las capas, arrastre elementos desde el Explorador de soluciones, los mapas de código, la vista de clases y el examinador de objetos. Para dibujar capas nuevas, use el cuadro de herramientas o haga clic con el botón derecho en la superficie del diagrama.<br /><br /> Para ver las dependencias actuales, haga clic con el botón derecho en la superficie del diagrama de capas y, después, haga clic en **Generar dependencias**. Para especificar dependencias previstas, trace nuevas dependencias.|  
  
 Por ejemplo, en el siguiente diagrama de capas se describen las dependencias existentes entre capas y el número de artefactos que están asociados con cada capa:  
  
 ![Diagrama de capas de sistema de pago integrado](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **Diagrama de capas**  
  
 Para asegurarse de que no haya conflictos con el diseño durante el desarrollo de código, los equipos usan validación de capas en compilaciones que se ejecutan en Team Foundation Build. También crean una tarea MSBuild personalizada para exigir la validación de capas en las operaciones de protección. Para recopilar los errores de validación, usan informes de compilación.  
  
 Vea:  
  
- [Definir el proceso de compilación](http://msdn.microsoft.com/library/61593e10-d24b-492f-b19a-af4d85abea6b)  
  
- [Utilizar un proceso de compilación de protección controlada para validar cambios](http://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)  
  
- [Personalizar la plantilla de proceso de compilación](http://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
### <a name="GeneralTips"></a> General Tips for Creating and Using Models  
  
- La mayoría de los diagramas constan de nodos que están conectados mediante líneas. Para cada tipo de diagrama, el cuadro de herramientas proporciona distintas clases de nodos y líneas.  
  
   Para abrir el cuadro de herramientas, vaya el menú **Ver** y haga clic en **Cuadro de herramientas**.  
  
- Para crear un nodo, arrástrelo desde el cuadro de herramientas al diagrama. Hay determinados tipos de nodos que deben arrastrarse a los nodos existentes. Por ejemplo, en un diagrama de componentes, un puerto nuevo debe agregarse a un componente existente.  
  
- Para crear una línea o una conexión, haga clic en la herramienta correspondiente del cuadro de herramientas, luego haga clic en el nodo de origen y, por último, haga clic en el nodo de destino. Algunas líneas solo se pueden crear entre determinados tipos de nodos. Cuando mueve el puntero sobre un posible origen o destino, el puntero indica si puede crear una conexión.  
  
- Cuando crea elementos en diagramas de UML, también los agrega a un modelo común. Los diagramas de UML de un proyecto de modelado son vistas de ese modelo. Los elementos de un diagrama de capas forman parte del proyecto de modelado, a pesar de que no se almacenan en el modelo común.  
  
   Para ver el modelo, vaya al menú **Arquitectura** , elija  **Windows**y haga clic en **Explorador de modelos UML**.  
  
- En algunos casos, puede arrastrar determinados elementos desde el **Explorador de modelos UML** hasta un diagrama de UML. Para mostrar vistas alternativas de la arquitectura, pueden usarse algunos elementos del mismo modelo en varios o en distintos diagramas. Por ejemplo, puede arrastrar un componente a otro diagrama de componentes o a un diagrama de secuencia para usarlo como un actor.  
  
- Visual Studio es compatible con UML 2.1.2. Esta información general se ocupa únicamente de las características principales de los diagramas de UML de esta versión, pero hay muchos libros que analizan en detalle el UML y su uso.  
  
  Consulte [crear modelos para la aplicación](../modeling/create-models-for-your-app.md).  
  
### <a name="PlanningTracking"></a> Planning and Tracking Work  
 Los diagramas de modelado de Visual Studio se integran con Team Foundation Server para que pueda planear, administrar y realizar un seguimiento del trabajo más fácilmente. Ambos equipos usan modelos para identificar los casos de prueba y las tareas de desarrollo, y para calcular su trabajo. Lucerne crea elementos de trabajo de Team Foundation Server y los vincula a elementos de modelo, como casos de uso o componentes. Esto les ayuda a supervisar sus progresos y a realizar un seguimiento de su trabajo hasta los requisitos de los usuarios. Así se aseguran de que sus cambios continúan cumpliendo dichos requisitos.  
  
 A medida que avanza su trabajo, los equipos actualizan los elementos de trabajo para que reflejen el tiempo que invierten en sus tareas. También supervisan y registran el estado de su trabajo con las siguientes características de Team Foundation Server:  
  
- *Informes de evolución* diarios que muestran si se completa el trabajo planeado en el tiempo esperado. También generan otros informes similares de Team Foundation Server para realizar un seguimiento del progreso de los errores.  
  
- Una *hoja de cálculo de iteración* que usa Microsoft Excel para ayudar al equipo a supervisar y repartir la carga de trabajo entre sus miembros. Esta hoja de cálculo está vinculada a Team Foundation Server y sirve de foco de discusión durante las reuniones en las que se analizan los progresos.  
  
- Un *panel de desarrollo* que usa Office Project para mantener informado al equipo sobre aspectos importantes del proyecto.  
  
  Vea:  
  
- [Seguimiento del trabajo mediante Visual Studio Online o Team Foundation Server](http://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)  
  
- [Vincular elementos de modelo con elementos de trabajo](../modeling/link-model-elements-and-work-items.md)  
  
- [Gráficos, paneles e informes para Visual Studio ALM](http://msdn.microsoft.com/library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)  
  
- [Crear un registro de trabajo pendiente y tareas mediante Project](http://msdn.microsoft.com/library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)  
  
### <a name="TestValidateCheckInCode"></a> Pruebas, validación y protección de código  
 Cuando los equipos completan una tarea, comprueban su código en el control de versiones de Team Foundation y reciben un aviso de Team Foundation Server si se olvidan de hacerlo. Antes de que Team Foundation Server acepte las protecciones, los equipos ejecutan pruebas unitarias y validación de capas para comprobar el código comparándolo con sus casos de prueba y el diseño. Usan Team Foundation Server para ejecutar con regularidad compilaciones, pruebas unitarias automatizadas y validación de capas. Con esto se aseguran de que el código cumple los criterios siguientes:  
  
- Funciona.  
  
- No interrumpe código que ya funcionaba anteriormente.  
  
- No está en conflicto con el diseño.  
  
  Dinner Now tiene una gran cantidad de pruebas automatizadas que Lucerne puede reutilizar porque casi todo se sigue aplicando. Lucerne también puede compilar en estas pruebas y agregar nuevas pruebas que cubran nuevas funcionalidades. Ambos también usan Visual Studio para ejecutar pruebas manuales.  
  
  Para asegurarse de que el código se ajusta al diseño, los equipos configuran sus compilaciones en Team Foundation Build para incluir la validación de capas. Si se produce algún conflicto, se genera un informe con los detalles.  
  
  Vea:  
  
- [Probar la aplicación](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)  
  
- [Validar el sistema durante el desarrollo](../modeling/validate-your-system-during-development.md)  
  
- [Usar el control de versiones](http://go.microsoft.com/fwlink/?LinkID=525605)  
  
- [Compilar la aplicación](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
## <a name="UpdatingSystem"></a> Updating the System Using Visualization and Modeling  
 Lucerne y Dinner Now deben integrar sus sistemas de pago. En las secciones siguientes se muestra cómo los diagramas de modelado de Visual Studio les ayudan con esta tarea:  
  
- [Comprender los requisitos del usuario: Diagramas de casos de uso](#UnderstandUseCases)  
  
- [Comprender el proceso empresarial: Diagramas de actividades](#UnderstandActivities)  
  
- [Describe la estructura del sistema: Diagramas de componentes](#DescribeComponents)  
  
- [Describe las interacciones: Diagramas de secuencia](#DescribeSequence)  
  
- [Visualización del código existente: Mapas de código](#VisualizeCode)  
  
- [Definir un glosario de tipos: Diagramas de clases](#DefineClasses)  
  
- [Describe la arquitectura lógica: Diagramas de capas](#DescribeLayers)  
  
  Vea:  
  
- [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)  
  
- [Visualizar el código](../modeling/visualize-code.md)  
  
- [Usar modelos en el proceso de desarrollo](../modeling/use-models-in-your-development-process.md)  
  
- [Requisitos del usuario de modelos](../modeling/model-user-requirements.md)  
  
- [Modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)  
  
### <a name="UnderstandUseCases"></a> Comprender los requisitos del usuario: Diagramas de casos de uso  
 Los diagramas de casos de uso resumen las actividades que admite un sistema e indican quién lleva a cabo dichas actividades. Lucerne usa un diagrama de casos de uso para obtener la información siguiente sobre el sistema de Dinner Now:  
  
- Los clientes realizan pedidos.  
  
- Los restaurantes reciben pedidos.  
  
- La puerta de enlace externa del procesador de pago, usada por el sistema de pago de Dinner Now para validar los pagos, está fuera del ámbito del sitio web.  
  
  En el diagrama también se muestra cómo algunos de los principales casos de uso se dividen en casos de uso más pequeños. En Lucerne quieren usar su propio sistema de pago y resaltan con otro color el caso de uso del proceso de pago (Process Payment) para indicar que requiere cambios:  
  
  ![Resaltar el proceso de pago en un diagrama de casos de uso](../modeling/media/uml-processpay.png "UML_ProcessPay")  
  
  **Resaltar el proceso de pago en el diagrama de casos de uso**  
  
  Si el tiempo de desarrollo es breve, el equipo quizá quiera que los clientes paguen directamente a los restaurantes. Para mostrar esta posibilidad, reemplazan el caso de uso del proceso de pago por uno que esté fuera del límite del sistema de Dinner Now. A continuación vinculan el cliente (Customer) directamente al restaurante (Restaurant), con lo que indican que Dinner Now solo se dedica a procesar los pedidos:  
  
  ![Exponga el restaurante de pago en el diagrama de casos de uso](../modeling/media/uml-payrestaurant.png "UML_PayRestaurant")  
  
  **Exponga el restaurante de pago en el diagrama de casos de uso**  
  
  Vea:  
  
- [Diagramas de casos de uso UML: referencia](../modeling/uml-use-case-diagrams-reference.md)  
  
- [Diagramas de casos de uso UML: directrices](../modeling/uml-use-case-diagrams-guidelines.md)  
  
#### <a name="drawing-a-use-case-diagram"></a>Dibujo de un diagrama de casos de uso  
 Un diagrama de casos de uso tiene las siguientes características principales:  
  
- *Actores* , que representan roles desempeñados por personas, organizaciones, máquinas o sistemas de software. Por ejemplo, el cliente, el restaurante y el sistema de pago de Dinner Now son actores.  
  
- *Casos de uso* , que representan interacciones entre actores y el sistema en desarrollo.  Pueden representar cualquier escala de interacción, desde un solo clic del mouse o un mensaje, hasta una transacción que se extiende durante varios días.  
  
- *Asociaciones* , que vinculan actores con casos de uso.  
  
- Un caso de uso grande puede *incluir* otros más pequeños. Por ejemplo, Crear pedido (Create Order) incluye Seleccionar restaurante (Select Restaurant). También puede *extender* un caso de uso, que agrega objetivos y pasos al caso de uso extendido, para indicar que el caso de uso se produce únicamente bajo ciertas condiciones. Los casos de uso también pueden heredar de otros casos de uso.  
  
- Un *subsistema* representa el sistema de software que está desarrollándose o uno de sus componentes, y es un cuadro grande que contiene los casos de uso. Un diagrama de casos de uso aclara lo que queda dentro o fuera del límite del subsistema. Para indicar que el usuario debe alcanzar ciertos objetivos de otras formas, dibuje esos casos de uso fuera del límite del subsistema.  
  
- *Artefactos* , que vinculan elementos del diagrama a otros diagramas o documentos.  
  
  Vea:  
  
- [Diagramas de casos de uso UML: referencia](../modeling/uml-use-case-diagrams-reference.md)  
  
- [Diagramas de casos de uso UML: directrices](../modeling/uml-use-case-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-use-case-diagrams"></a>Resumen: Puntos fuertes de diagramas de casos de uso  
 Los diagramas de casos de uso le ayudan a visualizar:  
  
- Las actividades que un sistema admite o no admite  
  
- Las personas y los sistemas externos que realizan esas actividades  
  
- Los principales componentes del sistema que admiten cada actividad y que puede representar como subsistemas anidados dentro del sistema principal  
  
- Cómo se puede dividir un caso de uso en casos de uso más pequeños o en variaciones del mismo  
  
#### <a name="relationship-to-other-diagrams"></a>Relación con otros diagramas  
  
|**Diagram**|**Qué describe**|  
|-----------------|-------------------|  
|Diagrama de actividades|El flujo de pasos de un caso de uso y quiénes realizan esos pasos en dicho caso de uso.<br /><br /> Con frecuencia, los nombres de casos de uso reflejan los pasos de un diagrama de actividades. Los diagramas de actividades admiten elementos como decisiones, combinaciones, entradas y salidas, flujos simultáneos, etc.<br /><br /> Vea:<br /><br /> -   [Diagramas de actividades UML: Referencia](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramas de actividades UML: directrices](../modeling/uml-activity-diagrams-guidelines.md)|  
|Diagrama de secuencia|La secuencia de interacciones entre los participantes en un caso de uso.<br /><br /> Vea:<br /><br /> -   [Diagramas de secuencia UML: Referencia](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagramas de secuencia UML: directrices](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Diagrama de clases (UML)|Las entidades o tipos que participan en el caso de uso.<br /><br /> Vea:<br /><br /> -   [Diagramas de clases UML: Referencia](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramas de clases UML: directrices](../modeling/uml-class-diagrams-guidelines.md)|  
  
### <a name="UnderstandActivities"></a> Comprender el proceso empresarial: Diagramas de actividades  
 Los diagramas de actividades describen el flujo de pasos de un proceso de negocio y proporcionan una manera sencilla para la comunicación de flujo de trabajo. Un proyecto de desarrollo puede tener varios diagramas de actividades. Normalmente, una actividad abarca todas las acciones resultantes de una acción externa, por ejemplo, pedir una comida, actualizar un menú o agregar un nuevo restaurante al negocio. Una actividad también puede describir los detalles de una acción compleja.  
  
 Lucerne actualiza el siguiente diagrama de actividad para mostrar que procesa el pago y paga al restaurante. Reemplazan el sistema de pago (Payment System) de Dinner Now por el sistema de pago de Lucerne, como se muestra con el resaltado:  
  
 ![Sistema de pago de Lucerne en diagrama de actividades](../modeling/media/uml-lucerne.png "UML_Lucerne")  
  
 **Reemplazar el pago sistema de Dinner Now en el diagrama de actividad**  
  
 El diagrama actualizado sirve para que Lucerne y Dinner Now visualicen en qué parte del proceso de negocio encaja el sistema de pago de Lucerne. En esta versión, los comentarios se usan para identificar los roles que llevan a cabo los pasos. Las líneas se usan para crear *calles*, que organizan los pasos por rol.  
  
 Los equipos también pueden estudiar la opción de que el cliente pague al restaurante después de que se entregue el pedido. Esto crearía distintos requisitos para el sistema de software.  
  
 Anteriormente, Dinner Now dibujaba estos diagramas en una pizarra o en PowerPoint. En cambio, ahora también usan Visual Studio para trazar estos diagramas, lo que permite a ambos equipos capturar, comprender y administrar los detalles.  
  
 Vea:  
  
- [Diagramas de actividades UML: referencia](../modeling/uml-activity-diagrams-reference.md)  
  
- [Diagramas de actividades UML: directrices](../modeling/uml-activity-diagrams-guidelines.md)  
  
#### <a name="drawing-an-activity-diagram"></a>Dibujo de un diagrama de actividades  
 Un diagrama de actividades tiene las siguientes características principales:  
  
- Un *nodo inicial* que indica la primera acción de la actividad.  
  
   El diagrama siempre debe tener uno de estos nodos.  
  
- *Acciones* que describen los pasos en los que el usuario o el software realizan una tarea.  
  
- *Flujos de control* que muestran el flujo entre las acciones.  
  
- *Nodos de decisión* que representan las bifurcaciones condicionales en el flujo.  
  
- *Nodos de bifurcación* que dividen un flujo único en flujos simultáneos.  
  
- *Nodos finales de actividad* que muestran el final de la actividad.  
  
   Aunque estos nodos son opcionales, resulta útil incluirlos en el diagrama para mostrar dónde finaliza la actividad.  
  
  Vea:  
  
- [Diagramas de actividades UML: referencia](../modeling/uml-activity-diagrams-reference.md)  
  
- [Diagramas de actividades UML: directrices](../modeling/uml-activity-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-activity-diagrams"></a>Resumen: Puntos fuertes de los diagramas de actividades  
 Los diagramas de actividades ayudan a visualizar y describir el flujo de control y de información entre las acciones de un negocio, un sistema o un programa. Es una manera sencilla y útil de describir el flujo de trabajo al comunicarse con otras personas.  
  
#### <a name="relationship-to-other-diagrams"></a>Relación con otros diagramas  
  
|**Diagram**|**Descripción**|  
|-----------------|---------------------|  
|Diagrama de casos de uso|Resumen de las actividades que realiza cada actor.<br /><br /> Vea:<br /><br /> -   [Diagramas de casos de uso UML: Referencia](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramas de casos de uso UML: directrices](../modeling/uml-use-case-diagrams-guidelines.md)|  
|Diagrama de componentes|Visualización del sistema como una colección de elementos reutilizables que proporcionan o usan el comportamiento a través de un conjunto de interfaces bien definido.<br /><br /> Vea:<br /><br /> -   [Diagramas de componentes UML: Referencia](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramas de componentes UML: directrices](../modeling/uml-component-diagrams-guidelines.md)|  
  
### <a name="DescribeComponents"></a> Describe la estructura del sistema: Diagrama de componentes  
 Los diagramas de componentes describen un sistema como una colección de elementos separables que proporcionan o usan el comportamiento a través de un conjunto de interfaces bien definido. Los elementos pueden tener cualquier escala y estar conectados de cualquier modo.  
  
 Para ayudar a Lucerne y a Dinner Now a visualizar y analizar los componentes del sistema y sus interfaces, se crean los siguientes diagramas de componentes:  
  
 ![Los componentes externos en el sistema de pago](../modeling/media/uml-extdnpayment.png "UML_ExtDNPayment")  
  
 **Componentes del sistema de pago de Dinner Now**  
  
 Este diagrama muestra distintos tipos de componentes y sus *dependencias*. Por ejemplo, tanto el sitio web de Dinner Now como el sistema de pago de Lucerne requieren que haya una puerta de enlace externa del procesador de pagos (External Payment Processor Gateway) para validar los pagos. Las flechas entre los componentes representan las dependencias que indican qué componentes necesitan la funcionalidad de otros componentes.  
  
 Para poder usar el sistema de pago de Lucerne, el sitio web de Dinner Now debe actualizarse para usar las interfaces PaymentApproval y PayableInsertion del sistema de pago de Lucerne.  
  
 En el diagrama siguiente se muestra una configuración específica de componentes para el sitio web de Dinner Now. Esta configuración indica que cualquier instancia del sitio web se compone de cuatro *elementos*:  
  
- CustomerProcessing  
  
- OrderProcessing  
  
- ReviewProcessing  
  
- PaymentProcessing  
  
  Estos elementos son instancias de los tipos de componente especificados y están conectados del modo siguiente:  
  
  ![Componentes de sitio Web de Dinner Now](../modeling/media/uml-dinnernow.png "UML_DinnerNow")  
  
  **Sitio Web de los componentes dentro de la cena ahora**  
  
  El sitio web de Dinner Now delega su comportamiento en estos elementos, que controlan las funciones del sitio web. Las flechas entre el componente primario y sus componentes miembros muestran *delegaciones* que indican qué elementos controlan los mensajes que el elemento primario recibe o envía a través de sus interfaces.  
  
  En esta configuración, el componente PaymentProcessing procesa los pagos del cliente. Por lo tanto, debe actualizarse para integrarse con el sistema de pago de Lucerne. En otros escenarios pueden existir varias instancias de un tipo de componente en el mismo componente primario.  
  
  Vea:  
  
- [Diagramas de componentes UML: referencia](../modeling/uml-component-diagrams-reference.md)  
  
- [Diagramas de componentes UML: directrices](../modeling/uml-component-diagrams-guidelines.md)  
  
#### <a name="drawing-a-component-diagram"></a>Dibujo de un diagrama de componentes  
 Un diagrama de componentes tiene las siguientes características principales:  
  
- *Componentes* que representan partes separables de funcionalidad del sistema.  
  
- *Puertos de interfaz proporcionados* que representan grupos de mensajes o llamadas que los componentes implementan y que son usados por otros componentes o sistemas externos.  
  
- *Puertos de interfaz necesarios* que representan grupos de mensajes o llamadas que los componentes envían a otros componentes o sistemas externos. Este tipo de puerto describe las operaciones que un componente espera como mínimo de otros componentes o sistemas externos.  
  
- *Elementos* que son miembros de componentes y normalmente son instancias de otros componentes. Un elemento es un fragmento del diseño interno del componente primario.  
  
- *Dependencias* que indican que los componentes requieren la funcionalidad de otros componentes.  
  
- *Delegaciones* que indican que las partes de un componente controlan los mensajes enviados o recibidos por el componente primario.  
  
  Vea:  
  
- [Diagramas de componentes UML: referencia](../modeling/uml-component-diagrams-reference.md)  
  
- [Diagramas de componentes UML: directrices](../modeling/uml-component-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-component-diagrams"></a>Resumen: Puntos fuertes de diagramas de componentes  
 Los diagramas de componentes le ayudan a visualizar:  
  
- El sistema como una colección de elementos separables independientemente de su lenguaje de implementación o estilo.  
  
- Componentes con interfaces bien definidas, que facilitan la comprensión del diseño y su actualización cuando cambian los requisitos.  
  
#### <a name="relationship-to-other-diagrams"></a>Relación con otros diagramas  
  
|**Diagram**|**Descripción**|  
|-----------------|---------------------|  
|Mapa de código|Visualización de la organización y las relaciones en el código existente.<br /><br /> Para identificar los candidatos a componentes, cree un mapa de código y agrupe los elementos según su función en el sistema.<br /><br /> Vea:<br /><br /> -   [Asignar dependencias en sus soluciones](../modeling/map-dependencies-across-your-solutions.md)|  
|Diagrama de secuencia|Visualización de la secuencia de interacciones entre los componentes o los elementos dentro de un componente.<br /><br /> Para crear una línea de vida en un diagrama de secuencia a partir de un componente, haga clic con el botón derecho en el componente y, después, haga clic en **Crear línea de vida**.<br /><br /> Vea:<br /><br /> -   [Diagramas de secuencia UML: Referencia](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagramas de secuencia UML: directrices](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Diagrama de clases (UML)|Definición de las interfaces en los puertos proporcionados o necesarios y las clases que implementan la funcionalidad de los componentes.<br /><br /> Vea:<br /><br /> -   [Diagramas de clases UML: Referencia](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramas de clases UML: directrices](../modeling/uml-class-diagrams-guidelines.md)|  
|Diagrama de capas|Descripción de la arquitectura lógica del sistema en lo referente a los componentes. Mediante la validación de capas, asegúrese de que el código mantiene la coherencia con el diseño.<br /><br /> Vea:<br /><br /> -   [Crear diagramas de capas desde el código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de capas: Referencia](../modeling/layer-diagrams-reference.md)<br />-   [Diagramas de capas: directrices](../modeling/layer-diagrams-guidelines.md)<br />-   [Validar código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md)|  
|Diagrama de actividades|Visualización del procesamiento interno efectuado por los componentes en respuesta a los mensajes entrantes.<br /><br /> Vea:<br /><br /> -   [Diagramas de actividades UML: Referencia](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramas de actividades UML: directrices](../modeling/uml-activity-diagrams-guidelines.md)|  
  
### <a name="VisualizeCode"></a> Visualización del código existente: Mapas de código  
 Los mapas de código muestran la organización y las relaciones actuales del código. Los elementos se representan mediante *nodos* en el mapa y las relaciones mediante *vínculos*. Los mapas de código le ayudan a realizar los siguientes tipos de tareas:  
  
- Examinar código desconocido.  
  
- Comprender dónde y cómo un cambio propuesto podría afectar al código existente.  
  
- Buscar áreas de complejidad, capas naturales o patrones, u otras áreas que podrían beneficiarse de una mejora.  
  
  Por ejemplo, Dinner Now debe calcular el costo de actualización del componente PaymentProcessing. Esto depende en parte de en qué medida afectará este cambio a las otras partes del sistema. Para tener una idea más clara, uno de los desarrolladores de Dinner Now genera mapas de código a partir del código y se centra en las áreas que podrían verse afectadas por el cambio.  
  
  En el mapa siguiente se muestran las dependencias entre la clase PaymentProcessing y otros elementos del sistema Dinner Now, que aparecen seleccionados:  
  
  ![Gráfico de dependencias para el sistema de pago de Dinner Now](../modeling/media/dep-dnpayment.png "Dep_DNPayment")  
  
  **Mapa de código del sistema de pago de Dinner Now**  
  
  Para explorar el mapa, el desarrollador expande la clase PaymentProcessing y selecciona sus miembros para ver las áreas que podrían verse afectadas:  
  
  ![Métodos de PaymentProcessing y dependencias](../modeling/media/depgraph-expandeddn.png "DepGraph_ExpandedDN")  
  
  **Métodos de la clase PaymentProcessing y sus dependencias**  
  
  El mapa siguiente del sistema de pago de Lucerne se genera para inspeccionar sus clases, métodos y dependencias. El equipo ve que también podría ser necesario actuar en el sistema de Lucerne para que interactúe con los demás elementos de Dinner Now:  
  
  ![Gráfico de dependencias para el sistema de pago de Lucerne](../modeling/media/depgraph-lucernepay.png "DepGraph_LucernePay")  
  
  **Mapa de código del sistema de pago de Lucerne**  
  
  Ambos equipos colaboran para determinar los cambios que son necesarios para integrar los dos sistemas. Deciden refactorizar parte del código para que sea más fácil de actualizar. La clase PaymentApprover se moverá al espacio de nombres DinnerNow.Business y requerirá algunos métodos nuevos. Las clases de Dinner Now que controlan las transacciones tendrán su propio espacio de nombres. Los equipos crean y usan elementos de trabajo para planear, organizar y realizar un seguimiento de su trabajo. Vinculan los elementos de trabajo a elementos del modelo donde resulta útil.  
  
  Después de reorganizar el código, los equipos generan un nuevo mapa de código para ver la estructura y las relaciones actualizadas:  
  
  ![Gráfico de dependencias con código reorganizado](../modeling/media/depgraph-integrated.png "DepGraph_Integrated")  
  
  **Mapa de código con código reorganizado**  
  
  Este mapa muestra que la clase PaymentApprover se encuentra ahora en el espacio de nombres DinnerNow.Business y tiene algunos métodos nuevos. Las clases de transacción de Dinner Now ahora tienen su propio espacio de nombres PaymentSystem, lo que facilita el trabajo posterior con ese código.  
  
#### <a name="creating-a-code-map"></a>Creación de un mapa de código  
  
- Para obtener una visión general rápida del código fuente, siga estos pasos para generar un mapa de código:  
  
     En el menú **Arquitectura** , haga clic en **Generar mapa de código para solución**.  
  
     Para obtener una visión general rápida del código compilado, cree un mapa de código en blanco y, después, arrastre los archivos de ensamblado o los archivos binarios a la superficie del mapa.  
  
- Para explorar código específico o elementos de la solución, use el Explorador de soluciones para seleccionar los elementos y las relaciones que quiere visualizar. A continuación puede generar un mapa nuevo o agregar elementos seleccionados a un mapa existente. Vea [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).  
  
- Para que le sea más fácil explorar el mapa, reorganice el diseño para que se adapte a los tipos de tareas que quiere realizar.  
  
     Por ejemplo, para visualizar la distribución en capas del código, seleccione un diseño de árbol. Consulte [examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).  
  
#### <a name="summary-strengths-of-code-maps"></a>Resumen: Puntos fuertes de mapas de código  
 Los mapas de código le ayudan en las siguientes tareas:  
  
- Obtener información acerca de la organización y las relaciones en el código existente.  
  
- Identificar áreas que podrían verse afectadas por un cambio propuesto.  
  
- Buscar áreas de complejidad, patrones, capas u otras áreas que se podrían mejorar para que el código sea más fácil de mantener, modificar y reutilizar.  
  
#### <a name="relationship-to-other-diagrams"></a>Relación con otros diagramas  
  
|**Diagram**|**Qué describe**|  
|-----------------|-------------------|  
|Diagrama de capas|La arquitectura lógica del sistema. Mediante la validación de capas, asegúrese de que el código mantiene la coherencia con el diseño.<br /><br /> Para ayudarle a identificar las capas existentes o las previstas, cree un mapa de código y agrupe los elementos relacionados. Para crear un diagrama de capas, vea:<br /><br /> -   [Crear diagramas de capas desde el código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de capas: directrices](../modeling/layer-diagrams-guidelines.md)|  
|Diagrama de componentes|Los componentes, sus interfaces y sus relaciones.<br /><br /> Para identificar los componentes, cree un mapa de código y agrupe los elementos según su función en el sistema.<br /><br /> Vea:<br /><br /> -   [Diagramas de componentes UML: Referencia](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramas de componentes UML: directrices](../modeling/uml-component-diagrams-guidelines.md)|  
|Diagrama de clases (UML)|Las clases, sus atributos y operaciones, y sus relaciones.<br /><br /> Para ayudarle a identificar estos elementos, cree un diagrama de clases UML que muestre esos elementos.<br /><br /> Vea:<br /><br /> -   [Diagramas de clases UML: Referencia](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramas de clases UML: directrices](../modeling/uml-class-diagrams-guidelines.md)|  
|Diagrama de clases (basado en código)|Las clases existentes en el código de un proyecto específico.<br /><br /> Para visualizar y modificar una clase existente en el código, use el Diseñador de clases.<br /><br /> Vea [Cómo: Agregar diagramas de clases a proyectos (Diseñador de clases)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|  
  
### <a name="DescribeSequence"></a> Describe las interacciones: Diagramas de secuencia  
 Los diagramas de secuencia describen una serie de interacciones entre los elementos de un sistema. Los elementos pueden ser de cualquier escala, desde objetos individuales de un programa a grandes subsistemas o actores externos. Las interacciones pueden ser de cualquier escala y tipo, desde mensajes individuales a transacciones extendidas, y pueden ser llamadas a funciones o mensajes del servicio web.  
  
 Para poder describir y analizar los pasos del caso de uso del proceso de pago, Lucerne y Dinner Now crean el siguiente diagrama de secuencia a partir del diagrama de componentes. Las líneas de vida reflejan el componente de sitio web de Dinner Now y sus elementos. Los mensajes que aparecen entre las líneas de vida siguen las conexiones en los diagramas de componentes:  
  
 ![Caso de uso del diagrama de secuencia para el proceso de pago](../modeling/media/umlsequence-processpayment.png "UMLSequence_ProcessPayment")  
  
 **Caso de uso del diagrama de secuencia para el proceso de pago**  
  
 En el diagrama de secuencia se muestra que, cuando el cliente crea un pedido, el sitio de web de Dinner Now llama a ProcessOrder en una instancia de OrderProcessing. A continuación, OrderProcessing llama a ProcessPayment en PaymentProcessing. Este proceso continúa hasta que la puerta de enlace externa del procesador de pago (External Payment Processor Gateway) valida el pago. Solo entonces el control vuelve al sitio web de Dinner Now.  
  
 Lucerne debe calcular el costo de actualizar su sistema de pago para integrarlo con el sistema de Dinner Now. Para ayudarles en la decisión, también pueden crear mapas de código con los que visualizar el código afectado.  
  
 Vea:  
  
- [Diagramas de secuencia de UML: referencia](../modeling/uml-sequence-diagrams-reference.md)  
  
- [Diagramas de secuencia de UML: directrices](../modeling/uml-sequence-diagrams-guidelines.md)  
  
- [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)  
  
#### <a name="drawing-a-sequence-diagram"></a>Dibujo de un diagrama de secuencia  
 Un diagrama de secuencia tiene las siguientes características principales:  
  
- *Líneas de vida* verticales que representan actores o instancias de objetos de software.  
  
   Para agregar un símbolo de actor, que indica que un participante está fuera del sistema en desarrollo, haga clic en la línea de vida. En la ventana **Propiedades** , establezca **Actor** en **True**. Si la ventana **Propiedades** no está abierta, presione **F4**.  
  
- *Mensajes* horizontales que representan llamadas a métodos, mensajes del servicio web o algún otro tipo de comunicación. *Incidencias de ejecución* que son rectángulos sombreados verticales que aparecen en las líneas de vida y que representan los períodos en que los objetos receptores procesan llamadas.  
  
- Durante una *sincrónica* mensaje, el objeto remitente espera a control <\<devolver >> como en una llamada de función normal. Durante un mensaje *asincrónico* , el remitente puede continuar de inmediato.  
  
- Use <\<crear >> mensajes para indicar la construcción de objetos por otros objetos. Debe ser el primer mensaje enviado al objeto.  
  
  Vea:  
  
- [Diagramas de secuencia de UML: referencia](../modeling/uml-sequence-diagrams-reference.md)  
  
- [Diagramas de secuencia de UML: directrices](../modeling/uml-sequence-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-sequence-diagrams"></a>Resumen: Puntos fuertes de diagramas de secuencia  
 Los diagramas de secuencia le ayudan a visualizar:  
  
- El flujo de control que se transfiere entre actores u objetos durante la ejecución de un caso de uso.  
  
- La implementación de un mensaje o una llamada a método.  
  
#### <a name="relationship-to-other-diagrams"></a>Relación con otros diagramas  
  
|**Diagram**|**Descripción**|  
|-----------------|---------------------|  
|Diagrama de clases (UML)|Definición de las clases que las líneas de vida representan y de los parámetros y valores devueltos que se usan en los mensajes enviados entre las líneas de vida.<br /><br /> Para crear una clase a partir de una línea de vida, haga clic con el botón derecho en la línea de vida y luego haga clic en **Crear clase** o **Crear interfaz**. Para crear una línea de vida a partir de un tipo en un diagrama de clases, haga clic con el botón derecho en el tipo y, después, elija **Crear línea de vida**.<br /><br /> Vea:<br /><br /> -   [Diagramas de clases UML: Referencia](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramas de clases UML: directrices](../modeling/uml-class-diagrams-guidelines.md)|  
|Diagrama de componentes|Descripción de los componentes que las líneas de vida representan y las interfaces que proporcionan y usan el comportamiento representado por los mensajes.<br /><br /> Para crear una línea de vida a partir de un diagrama de componentes, haga clic con el botón derecho en el componente y, después, haga clic en **Crear línea de vida**.<br /><br /> Vea:<br /><br /> -   [Diagramas de componentes UML: Referencia](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramas de componentes UML: directrices](../modeling/uml-component-diagrams-guidelines.md)|  
|Diagrama de casos de uso|Resumen de las interacciones entre los usuarios y los componentes en un diagrama de secuencia como un caso de uso, que representa el objetivo de un usuario.<br /><br /> Vea:<br /><br /> -   [Diagramas de casos de uso UML: Referencia](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramas de casos de uso UML: directrices](../modeling/uml-use-case-diagrams-guidelines.md)|  
  
### <a name="DefineClasses"></a> Definir un glosario de tipos: Diagramas de clases  
 Los diagramas de clases definen las entidades, términos o conceptos que participan en el sistema y sus relaciones entre sí. Por ejemplo, estos diagramas se pueden usar durante el desarrollo para describir los atributos y las operaciones de cada clase, independientemente del lenguaje de implementación o el estilo.  
  
 Para describir y analizar las entidades que participan en el caso de uso del proceso de pago, en Lucerne dibujan el diagrama de clases siguiente:  
  
 ![Entidades de pago en el diagrama de clases del proceso](../modeling/media/uml-payentities.png "UML_PayEntities")  
  
 **Entidades del proceso de pago en un diagrama de clases**  
  
 En este diagrama se muestra que un cliente (Customer) puede tener muchos pedidos (Orders) y diferentes modos de pago para los pedidos. BankAccount y CreditCard heredan de Payment.  
  
 Durante el desarrollo, Lucerne usa el siguiente diagrama de clases para describir y analizar los detalles de cada clase:  
  
 ![Detalles de la entidad de pago en un diagrama de clases del proceso](../modeling/media/uml-payment.png "UML_Payment")  
  
 **Detalles del proceso de pago en el diagrama de clases**  
  
 Vea:  
  
- [Diagrama de clases de UML: referencia](../modeling/uml-class-diagrams-reference.md)  
  
- [Diagrama de clases de UML: directrices](../modeling/uml-class-diagrams-guidelines.md)  
  
#### <a name="drawing-a-class-diagram"></a>Dibujo de un diagrama de clases  
 Un diagrama de clases tiene las siguientes características principales:  
  
- Tipos como clases, interfaces y enumeraciones:  
  
  - Una *clase* es la definición de objetos que comparten determinadas características estructurales y de comportamiento.  
  
  - Una *interfaz* define una parte del comportamiento externamente visible de un objeto.  
  
  - Una *enumeración* es un clasificador que contiene una lista de valores literales.  
  
- Los*atributos* son valores de un tipo determinado que describen cada instancia de un *clasificador*. Un clasificador es un nombre general para tipos, componentes, casos de uso e incluso actores.  
  
- Las*operaciones* son métodos o funciones que las instancias de un clasificador pueden realizar.  
  
- Una *asociación* indica algún tipo de relación entre dos clasificadores.  
  
  - Una *agregación* es una asociación que indica una propiedad compartida entre clasificadores.  
  
  - Una *composición* es una asociación que indica una relación todo-parte entre clasificadores.  
  
    Para mostrar las agregaciones o composiciones, establezca la propiedad **Agregación** en una asociación. **Compartido** muestra las agregaciones y **Compuesto** muestra las composiciones.  
  
- Una *dependencia* indica que al cambiar la definición de un clasificador, también puede cambiar la definición de otro clasificador.  
  
- Una *generalización* indica que un clasificador específico hereda parte de su definición de un clasificador general. Una *realización* indica que una clase implementa las operaciones y los atributos que ofrece una interfaz.  
  
   Para crear estas relaciones, use la herramienta **Herencia** . Una realización también puede representarse como un *círculo*.  
  
- Los*paquetes* son grupos de clasificadores, asociaciones, líneas de vida, componentes y otros paquetes. Las relaciones de*importación* indican que un paquete incluye todas las definiciones de otro paquete.  
  
  Como punto de partida para explorar y analizar las clases existentes, puede usar el Diseñador de clases para crear diagramas de clases desde el código.  
  
  Vea:  
  
- [Diagrama de clases de UML: referencia](../modeling/uml-class-diagrams-reference.md)  
  
- [Diagrama de clases de UML: directrices](../modeling/uml-class-diagrams-guidelines.md)  
  
- [Cómo: Agregar diagramas de clases a proyectos (Diseñador de clases)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
#### <a name="summary-strengths-of-class-diagrams"></a>Resumen: Puntos fuertes de diagramas de clases  
 Los diagramas de clases le ayudan a definir lo siguiente:  
  
- Un glosario común de términos que se usan al analizar las necesidades de los usuarios y las entidades que participan en el sistema. Consulte [modelar los requisitos del usuario](../modeling/model-user-requirements.md).  
  
- Tipos usados por partes del sistema, como los componentes, independientemente de su implementación. Consulte [modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md).  
  
- Relaciones entre tipos, como dependencias. Por ejemplo, puede mostrar un tipo que se puede asociar con varias instancias de otro tipo.  
  
#### <a name="relationship-to-other-diagrams"></a>Relación con otros diagramas  
  
|**Diagram**|**Descripción**|  
|-----------------|---------------------|  
|Diagrama de casos de uso|Definición de los tipos que se usan para describir los objetivos y los pasos de casos de uso.<br /><br /> Vea:<br /><br /> -   [Diagramas de casos de uso UML: Referencia](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramas de casos de uso UML: directrices](../modeling/uml-use-case-diagrams-guidelines.md)|  
|Diagrama de actividades|Definición de los tipos de datos que pasan a través de los nodos de objeto, input pins, output pins y nodos de parámetros de actividad.<br /><br /> Vea:<br /><br /> -   [Diagramas de actividades UML: Referencia](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramas de actividades UML: directrices](../modeling/uml-activity-diagrams-guidelines.md)|  
|Diagrama de componentes|Descripción de los componentes, sus interfaces y sus relaciones. Una clase también puede describir un componente completo.<br /><br /> Vea:<br /><br /> -   [Diagramas de componentes UML: Referencia](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramas de componentes UML: directrices](../modeling/uml-component-diagrams-guidelines.md)|  
|Diagrama de capas|Definición de la arquitectura lógica del sistema en lo referente a las clases.<br /><br /> Mediante la validación de capas, asegúrese de que el código mantiene la coherencia con el diseño.<br /><br /> Vea:<br /><br /> -   [Crear diagramas de capas desde el código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de capas: Referencia](../modeling/layer-diagrams-reference.md)<br />-   [Diagramas de capas: directrices](../modeling/layer-diagrams-guidelines.md)<br />-   [Validar código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md)|  
|Diagrama de secuencia|Definición de los tipos de líneas de vida y las operaciones, parámetros y valores devueltos para todos los mensajes que puede recibir la línea de vida.<br /><br /> Para crear una línea de vida a partir de un tipo en un diagrama de clases, haga clic con el botón derecho en el tipo y, después, elija **Crear línea de vida**.<br /><br /> Vea:<br /><br /> -   [Diagramas de secuencia UML: Referencia](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagramas de secuencia UML: directrices](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Mapa de código|Visualización de la organización y las relaciones en el código existente.<br /><br /> Para identificar las clases, sus relaciones y sus métodos, cree un mapa de código que muestre esos elementos.<br /><br /> Vea:<br /><br /> -   [Asignar dependencias en sus soluciones](../modeling/map-dependencies-across-your-solutions.md)|  
  
### <a name="DescribeLayers"></a> Describe la arquitectura lógica: Diagramas de capas  
 Los diagramas de capas organizan los artefactos de la solución en grupos abstractos, o *capas*, con los que describen la arquitectura lógica de un sistema. Estos artefactos pueden ser muchas cosas: espacios de nombres, proyectos, clases, métodos, etcétera. En las capas se representan y describen los roles o las tareas que realizan los artefactos en el sistema. También puede incluir la validación de capas en la compilación y las operaciones de protección para asegurarse de que el código sigue siendo coherente con el diseño.  
  
 Para mantener la coherencia entre el código y el diseño, Dinner Now y Lucerne usan el siguiente diagrama de capas para validar el código a medida que evoluciona:  
  
 ![Diagrama de capas de sistema de pago integrado](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **Diagrama de capas de Dinner Now y Lucerne**  
  
 Las capas de este diagrama se vinculan a los artefactos correspondientes de la solución de Dinner Now y Lucerne. Por ejemplo, la capa Business se vincula al espacio de nombres DinnerNow.Business y a sus miembros, que ahora incluyen la clase PaymentApprover. La capa Resource Access se vincula al espacio de nombres DinnerNow.Data. Las flechas, o *dependencias*, especifican que solo la capa Business puede usar la funcionalidad de la capa Resource Access. La validación de capas se realiza con regularidad a medida que los equipos actualizan su código; esto les permite detectar los conflictos cuando se producen y resolverlos rápidamente.  
  
 Los equipos trabajan juntos para que la integración se realice de forma incremental y para probar los dos sistemas. Antes de ocuparse de PaymentProcessing, primero se aseguran de que PaymentApprover y el resto de Dinner Now trabajan de forma conjunta y correcta.  
  
 En el mapa de código siguiente se muestran las nuevas llamadas entre Dinner Now y PaymentApprover:  
  
 ![Gráfico de dependencias actualizado con sistema integrado](../modeling/media/depgraph-intsystem.png "DepGraph_IntSystem")  
  
 **Mapa de código con llamadas a método actualizadas**  
  
 Una vez que confirman que el sistema funciona según lo esperado, Dinner Now convierte en comentario el código de PaymentProcessing. Los informes de validación de capas están limpios y el mapa de código resultante muestra que ya no existen más dependencias de PaymentProcessing:  
  
 ![Gráfico de dependencias sin PaymentProcessing](../modeling/media/depgraph-nomore.png "DepGraph_NoMore")  
  
 **Mapa de código sin PaymentProcessing**  
  
#### <a name="drawing-a-layer-diagram"></a>Dibujo de un diagrama de capas  
 Un diagrama de capas tiene las siguientes características principales:  
  
- *Capas* que describen grupos lógicos de artefactos.  
  
- *Vínculos* , es decir, asociaciones entre capas y artefactos.  
  
   Para crear las capas a partir de artefactos, arrastre elementos desde el Explorador de soluciones, los mapas de código, la vista de clases o el examinador de objetos. Para dibujar capas nuevas y luego vincularlas a artefactos, use el cuadro de herramientas o haga clic con el botón derecho en la superficie del diagrama para crear las capas y, después, arrastre elementos a esas capas.  
  
   El número de una capa muestra la cantidad de artefactos vinculados a ella. Estos artefactos pueden ser espacios de nombres, proyectos, clases, métodos, etc. Cuando interprete el número de artefactos de una capa, recuerde lo siguiente:  
  
  - Si una capa se vincula a un artefacto que contiene otros artefactos, pero no se vincula directamente a estos otros artefactos, el número incluye únicamente el artefacto vinculado. Sin embargo, los demás artefactos se incluyen para el análisis durante la validación de capas.  
  
     Por ejemplo, si una capa está vinculada a un solo espacio de nombres, el número de artefactos vinculados es 1, aunque el espacio de nombres contenga clases. Si la capa tiene también vínculos a cada clase del espacio de nombres, el número incluirá las clases vinculadas.  
  
  - Si una capa contiene otras que están vinculadas a artefactos, la capa contenedora también está vinculada a esos artefactos, incluso aunque el número de la capa contenedora no los incluya.  
  
    Para ver los artefactos que están vinculados a una capa, haga clic con el botón derecho en la capa y luego haga clic en **Ver vínculos** para abrir el **Explorador de capas**.  
  
- *Dependencias* que indican que una capa puede usar la funcionalidad de otra capa, pero no viceversa. Una *dependencia bidireccional* indica que una capa puede usar la funcionalidad de otra capa, y viceversa.  
  
   Para ver las dependencias actuales en el diagrama de capas, haga clic con el botón derecho en la superficie del diagrama y, después, haga clic en **Generar dependencias**. Para describir las dependencias previstas, dibuje unas nuevas.  
  
  Vea:  
  
- [Crear diagramas de capas a partir del código](../modeling/create-layer-diagrams-from-your-code.md)  
  
- [Diagramas de capas: referencia](../modeling/layer-diagrams-reference.md)  
  
- [Diagramas de capas: directrices](../modeling/layer-diagrams-guidelines.md)  
  
- [Validar código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md)  
  
#### <a name="summary-strengths-of-layer-diagrams"></a>Resumen: Puntos fuertes de diagramas de capas  
 Los diagramas de capas le permiten hacer lo siguiente:  
  
- Describir la arquitectura lógica de un sistema conforme a la funcionalidad de sus artefactos.  
  
- Asegurarse de que el código en desarrollo se ajusta al diseño especificado.  
  
#### <a name="relationship-to-other-diagrams"></a>Relación con otros diagramas  
  
|**Diagram**|**Descripción**|  
|-----------------|---------------------|  
|Mapa de código|Visualización de la organización y las relaciones en el código existente.<br /><br /> Para crear las capas, genere un mapa de código y, después, agrupe los elementos en el mapa como capas potenciales. Arrastre los grupos desde el mapa al diagrama de capas.<br /><br /> Vea:<br /><br /> -   [Asignar dependencias en sus soluciones](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)|  
|Diagrama de componentes|Descripción de los componentes, sus interfaces y sus relaciones.<br /><br /> Para visualizar las capas, cree un diagrama de componentes en el que se describa la funcionalidad de los distintos componentes del sistema.<br /><br /> Vea:<br /><br /> -   [Diagramas de componentes UML: Referencia](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramas de componentes UML: directrices](../modeling/uml-component-diagrams-guidelines.md)|  
  
## <a name="external-resources"></a>Recursos externos  
  
|**Categoría**|**Links**|  
|------------------|---------------|  
|**Foros**|-   [Herramientas de visualización y modelado de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [SDK de visualización y modelado de Visual Studio (Herramientas ADSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
  
## <a name="see-also"></a>Vea también  
 [Visualizar el código](../modeling/visualize-code.md)   
 [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)   
 [Usar modelos en el proceso de desarrollo](../modeling/use-models-in-your-development-process.md)   
 [Usar modelos en Agile Development](http://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)   
 [Validar el sistema durante el desarrollo](../modeling/validate-your-system-during-development.md)   
 [Ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md)
