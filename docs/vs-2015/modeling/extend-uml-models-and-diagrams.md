---
title: Ampliar modelos y diagramas UML | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: b5bfa61e-ea59-4c3b-b5af-53475d7d13cd
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 917c88056709cfbeb89ce3f19d9c8da9866feb4e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054617"
---
# <a name="extend-uml-models-and-diagrams"></a>Ampliar modelos y diagramas UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se resumen los distintos mecanismos mediante los que se pueden ampliar las herramientas de modelado de UML de Visual Studio. Para ver qué versiones de Visual Studio admite cada tipo de modelo y herramienta, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 En el escenario del ejemplo siguiente, Fabrikam diseña e instala sistemas de control de equipaje en aeropuertos. Entre los proyectos de aeropuertos existen muchas similitudes en el equipo básico y el software que lo controla. Sin embargo, hay algunos factores que varían considerablemente, como la configuración de las bandas transportadoras, los mostradores de facturación, los contenedores de almacenamiento y otros equipos de control de equipaje.  
  
 Al comienzo de un nuevo proyecto, el equipo de Fabrikam crea un modelo UML que le ayuda a debatir estos requisitos entre ellos y con su cliente. Usan diagramas de actividades para representar el flujo del equipaje, con nodos de objeto que representan cada parte del equipo. El modelo UML no representa directamente el código del sistema.  
  
 El equipo de herramientas de Fabrikam realiza una serie de mejoras para ayudar a los equipos de desarrollo. En las secciones siguientes se describen los diferentes tipos de extensiones que se pueden definir. Puede combinar varias de estas técnicas en una extensión de Visual Studio.  
  
 Para obtener más información, vea este vídeo: ![vínculo al vídeo](../data-tools/media/playvideo.gif "PlayVideo")[MSDN How Do I Series: Extensibilidad y herramientas UML](http://go.microsoft.com/fwlink/?LinkId=214467).  
  
## <a name="Requirements"></a> Requisitos  
  
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
- [Modelado del SDK para Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=48148).  
  
## <a name="profiles"></a>Perfiles  
 Los perfiles permiten definir estereotipos y propiedades adicionales en los elementos de UML.  
  
 Los desarrolladores de herramientas de Fabrikam definen los estereotipos en los nodos de objeto de los diagramas de actividades, como «banda transportadora» y «mostrador de facturación». Si un miembro del equipo crea un esquema de control de equipaje con un diagrama de actividades, el equipo podrá entonces definir los estereotipos para indicar qué tipo de equipo representa cada nodo. Los desarrolladores de herramientas definen propiedades adicionales en algunos de los estereotipos para que los usuarios puedan registrar valores, como la capacidad de una banda transportadora y la situación de un mostrador de facturación.  
  
 Para obtener más información, consulte [definir un perfil para ampliar UML](../modeling/define-a-profile-to-extend-uml.md).  
  
## <a name="custom-toolbox-items"></a>Elementos del cuadro de herramientas personalizados  
 Un elemento personalizado del cuadro de herramientas crea un elemento o grupo de elementos a partir de un prototipo que se define en un diagrama. Por ejemplo, puede diseñar una herramienta que cree casos de uso en un color determinado o un estereotipo, o puede crear un grupo de clases y asociaciones que representen un modelo de diseño. Puede agregar estos elementos del cuadro de herramientas a las extensiones de Visual Studio y distribuirlos a otros usuarios.  
  
 Para obtener más información, consulte [definir personalizado en un elemento de cuadro de herramientas de modelado](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
## <a name="validation"></a>Validación  
 Puede definir reglas para asegurarse de que un modelo UML se ajusta a las restricciones especificadas.  
  
 Los desarrolladores de herramientas de Fabrikam definen reglas que ayudan a los miembros del equipo a evitar que se comentan errores simples en los modelos de control de equipaje. Por ejemplo, un mostrador de facturación no puede estar conectado directamente a un contenedor de almacenamiento. Debe haber por lo menos una banda transportadora entre ellos.  
  
 Para obtener más información, consulte [definir restricciones de validación para modelos UML](../modeling/define-validation-constraints-for-uml-models.md).  
  
## <a name="menu-commands"></a>Comandos de menú  
 Puede definir comandos que los usuarios pueden invocar al hacer clic con el botón derecho del mouse en los elementos de un diagrama de UML. Los comandos pueden actualizar el modelo y los diagramas o realizar otras operaciones en [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
 Fabrikam define los comandos de menú para automatizar las operaciones que realiza habitualmente, como crear un mostrador de facturación y conectarlo a una banda transportadora seleccionada o reorganizar un diagrama con arreglo a las reglas de diseño de la compañía.  
  
 Consulte [definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
## <a name="gestures"></a>Gestos  
 Puede definir comandos que los usuarios inician al hacer doble clic en un elemento del diagrama o al arrastrar el elemento hasta un diagrama o un elemento del diagrama. Puede definir comandos que se ocupen de los elementos arrastrados desde otros diagramas UML, desde otros componentes de Visual Studio, desde otras aplicaciones o desde el Explorador de Windows (o el Explorador de archivos).  
  
 Los miembros del equipo de Fabrikam pueden asociar un archivo, como una especificación, a cualquier elemento del modelo arrastrándolo desde el escritorio de Windows. Los desarrolladores de herramientas definieron un estereotipo que proporciona una propiedad de ruta de acceso del archivo a cualquier elemento y un gesto que establece el estereotipo y la ruta de acceso del archivo cuando un archivo se coloca en un elemento.  
  
 Para obtener más información, consulte [definir un controlador de gestos en un diagrama de modelado](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).  
  
## <a name="responding-to-changes"></a>Responder a cambios  
 Puede escribir código que responda a los cambios del modelo, tanto si se derivan de acciones del usuario como de otro código de programa.  
  
 Los desarrolladores de Fabrikam crean código que establece automáticamente el color de un elemento en función de su estereotipo. De este modo, resulta sencillo para los usuarios distinguir los distintos roles que juegan los elementos en los modelos.  
  
 Para obtener más información, vea [Cómo: Responder a los cambios en un modelo UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).  
  
## <a name="model-bus"></a>Model Bus  
 Model Bus permite obtener acceso a un diagrama o modelo desde otro diagrama o extensión de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . Entre otras cosas, esto le permite compartir información entre varios modelos, de modo que varias personas pueden trabajar al mismo tiempo en el modelo combinado.  
  
 Fabrikam usa los elementos de los diagramas de actividades para representar el equipo de control de equipaje. Cada elemento del equipo puede tener una especificación más detallada en otro diagrama, que puede estar en otro modelo. Las restricciones de validación del diagrama de flujo de equipaje pueden recuperar propiedades del equipo pertinentes desde los demás diagramas. Las referencias a los otros diagramas se almacenan en otras propiedades adicionales que se definen en estereotipos.  
  
 Para obtener más información, consulte [integrar modelos UML con otros modelos y herramientas](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
## <a name="generation"></a>Generación  
 A partir de un modelo, puede generar código de programa, scripts, configuraciones, documentos, nuevos modelos u otros artefactos.  
  
 En los sistemas de equipajes diseñados por Fabrikam, una gran parte del código del programa se comparte entre un proyecto y el siguiente. El aspecto principal que más varía es el plan del flujo del equipaje alrededor del aeropuerto. Tras acumular experiencia con sus primeros proyectos, los desarrolladores de herramientas del equipo de diseño crearon una plantilla que genera, a partir del modelo de flujo de equipaje, gran parte del código del programa que varía y otros archivos, como documentos de usuario. Esto reduce considerablemente el tiempo de desarrollo y la tasa de errores de cada nuevo proyecto.  
  
 Para obtener más información, consulte [generar archivos a partir de un modelo UML](../modeling/generate-files-from-a-uml-model.md).  
  
## <a name="team-foundation-server-integration"></a>Integración de Team Foundation Server  
 Puede vincular los elementos de trabajo a los elementos del modelo y obtener acceso a los elementos vinculados mediante programación.  
  
 Los desarrolladores de herramientas de Fabrikam escriben una herramienta que genera la programación de trabajo de cada proyecto de aeropuerto. Los elementos de trabajo de la programación están vinculados a los elementos del modelo.  
  
 Para obtener más información, consulte [definir un controlador de vínculo de elemento de trabajo](../modeling/define-a-work-item-link-handler.md).  
  
## <a name="tools-that-update-models"></a>Herramientas que actualizan modelos  
 Puede crear aplicaciones independientes y extensiones de Visual Studio que sean capaces de cargar modelos UML.  
  
 Los desarrolladores de Fabrikam crean una herramienta que lee un modelo y genera informes del progreso de trabajo de cada elemento del modelo.  
  
 Para obtener más información, consulte [leer un modelo UML en código de programa](../modeling/read-a-uml-model-in-program-code.md).  
  
## <a name="domain-specific-languages"></a>Lenguajes específicos del dominio  
 Si usa un determinado tipo de modelo frecuentemente, puede ser útil crear un lenguaje específico del dominio. Esto se puede realizar para ajustar sus necesidades comerciales con más detalle que un modelo UML, pero su compilación y mantenimiento requiere más esfuerzo. Para obtener más información, consulte [SDK de modelado de Visual Studio - lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).  
  
## <a name="external-resources"></a>Recursos externos  
  
|**Categoría**|**Vínculos**|  
|------------------|---------------|  
|**Vídeos**|![vínculo a vídeo](../data-tools/media/playvideo.gif "PlayVideo") [MSDN How Do I Series: Extensibilidad y herramientas UML](http://go.microsoft.com/fwlink/?LinkId=214467)<br /><br /> ![vínculo a vídeo](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: UML con Visual Studio](http://go.microsoft.com/fwlink/?LinkId=199957)|  
|**Foros**|-   [Herramientas de visualización y modelado de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [SDK de visualización y modelado de Visual Studio (Herramientas DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blogs**|[Blog de Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Artículos y diarios técnicos**|[Centro de arquitectura - MSDN](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Vea también  
 [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)   
 [Referencia de la API para la extensibilidad del modelado UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
