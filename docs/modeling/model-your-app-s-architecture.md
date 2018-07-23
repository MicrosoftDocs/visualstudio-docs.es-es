---
title: Modelar la aplicación&#39;arquitectura s
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0d75627eac18fa20edad222d168c858b073cecae
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178909"
---
# <a name="model-your-app39s-architecture"></a>Modelar la aplicación&#39;arquitectura s
Para ayudar a garantizar que el sistema de software o la aplicación cumple sus usuarios necesidades, puede crear modelos en Visual Studio como parte de la descripción de la estructura general y el comportamiento de su aplicación o sistema de software. A través de los modelos, también puede describir los patrones que se usan a lo largo de todo el proceso de diseño. Estos modelos le ayudan a entender la arquitectura existente, a analizar los cambios y a comunicar sus intenciones con claridad.

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 El propósito de un modelo es reducir las ambigüedades que se producen en las descripciones con el lenguaje natural y ayudarle a usted y a sus colegas a visualizar el diseño y a analizar diseños alternativos. El modelo debe usarse conjuntamente con otros documentos o explicaciones. Por sí mismo, un modelo no constituye una especificación completa de la arquitectura.

> [!NOTE]
>  A lo largo de este tema, el término “sistema” hace referencia al software que se está desarrollando. Puede ser una colección grande de muchos componentes de hardware y software, una única aplicación o una parte de una aplicación.

 La arquitectura de un sistema puede dividirse en dos áreas:

-   [Diseño de alto nivel](#Structure). Aquí se describen los componentes principales y el modo en que interactúan entre sí para satisfacer cada uno de los requisitos. Si el sistema es grande, cada componente puede tener su propio diseño de alto nivel donde se muestra su composición a partir de componentes más pequeños.

-   [Patrones de diseño](#Patterns) y convenciones que se usan a lo largo de los diseños de los componentes. Un modelo describe un determinado enfoque para lograr un objetivo de programación. Si se usan los mismos modelos a lo largo de un diseño completo, el equipo puede reducir el costo que suponen los cambios y el desarrollo de nuevo software.

##  <a name="Structure"></a> Diseño de alto nivel
 En un diseño de alto nivel se describen los componentes principales del sistema y el modo en que interactúan entre sí para lograr los objetivos del diseño. En el desarrollo del diseño de alto nivel están implicadas las actividades de la lista siguiente, aunque no necesariamente en un orden determinado.

 Si está actualizando código existente, puede comenzar por describir los componentes principales. Asegúrese de que comprende los cambios que deben realizarse en los requisitos de los usuarios y, a continuación, agregue o modifique las interacciones entre los componentes. Si está desarrollando un sistema nuevo, comience por identificar las características principales de las necesidades de los usuarios. A continuación, puede analizar las secuencias de interacciones de los casos de uso principales y, posteriormente, consolidar las secuencias en un diseño de componentes.

 En cualquier caso, resulta útil desarrollar en paralelo las diferentes actividades y desarrollar el código y las pruebas en una fase inicial. No intente completar uno de estos aspectos antes de comenzar con otro. Normalmente, a medida que escriba y pruebe el código, irán cambiando los requisitos y su concepción sobre la mejor manera de diseñar el sistema. Por tanto, debe empezar por concebir y codificar las características principales de los requisitos y el diseño. Ocúpese de los detalles en posteriores iteraciones del proyecto.

-   [Descripción de los requisitos](#Requirements). El punto inicial de cualquier diseño es describir claramente las necesidades de los usuarios.

-   [Modelos arquitectónicos](#BigDecisions). Son las elecciones que hace respecto a las tecnologías y elementos arquitectónicos básicos del sistema.

-   Modelo de datos de los componentes e Interfaces. Puede dibujar diagramas de clases para describir la información que se pasa entre los componentes y que se almacena en los componentes.

##  <a name="Requirements"></a> Descripción de los requisitos
 La forma más eficaz de desarrollar el diseño de alto nivel de una aplicación completa es hacerlo junto con un modelo de requisitos y otra descripción de las necesidades de los usuarios. Para obtener más información acerca de los modelos de requisitos, consulte [modelar los requisitos del usuario](../modeling/model-user-requirements.md).

 Si el sistema que está desarrollando es un componente de un sistema más grande, es posible que parte de los requisitos, o todos ellos, puedan expresarse en interfaces programáticas. 

 El modelo de requisitos proporciona estos elementos de información esenciales:

-   Interfaces proporcionadas. En una interfaz proporcionada aparecen los servicios u operaciones que el sistema o componente debe proporcionar a los usuarios, ya se trate de individuos o de otros componentes de software.

-   Interfaces necesarias. En una interfaz necesaria se muestran los servicios u operaciones que el sistema o componente puede usar. En algunos casos, podrá diseñar todos estos servicios como parte de su propio sistema. En otros casos, sobre todo si está diseñando un componente que se puede combinar con otros componentes en numerosas configuraciones, la interfaz necesaria se establecerá en función de consideraciones externas.

-   Requisitos de calidad del servicio. Rendimiento, seguridad, solidez y otros objetivos y restricciones que el sistema debe satisfacer.

 El modelo de requisitos se escribe desde la perspectiva de los usuarios del sistema, ya se trate de individuos u otros componentes de software. Ellos no saben nada sobre el funcionamiento interno del sistema. En cambio, el objetivo de un modelo arquitectónico es describir los mecanismos internos y mostrar cómo satisfacen las necesidades de los usuarios.

 Resulta útil mantener por separado los requisitos y los modelos arquitectónicos porque así es más fácil analizar los requisitos con los usuarios. También ayuda a refactorizar el diseño y a considerar arquitecturas alternativas mientras los requisitos se mantienen sin cambios.

 El nivel de detalle que debe usarse en los requisitos o en un modelo arquitectónico dependerá de la escala del proyecto y del tamaño y distribución del equipo. Un equipo reducido que trabaje en un proyecto pequeño podría simplemente trazar un diagrama de clases de los conceptos de negocio y algunos modelos de diseño; un proyecto grande distribuido en varias regiones necesitaría mucho más detalle.

##  <a name="BigDecisions"></a> Patrones de arquitectura
 En una fase inicial de desarrollo, tendrá que elegir las principales tecnologías y elementos en los que se va a basar el diseño. Las áreas en las que deben tomarse estas decisiones son, entre otras:

-   Base de las opciones de tecnología, como la elección entre una base de datos y un sistema de archivos y la elección entre una aplicación de red y un cliente web y así sucesivamente.

-   Los marcos; por ejemplo, la elección entre Windows Workflow Foundation o ADO.NET Entity Framework.

-   El método de integración; por ejemplo, la elección entre un bus de servicio de empresa o un canal punto a punto.

 Estas opciones a menudo están determinadas por los requisitos de calidad del servicio, como la escala y la flexibilidad, y pueden hacerse antes de que se conozcan los detalles de los requisitos. En un sistema grande, la configuración del hardware y la configuración del software están estrechamente relacionadas.

 Las elecciones que haga afectarán al modo en que se usa e interpreta el modelo arquitectónico. Por ejemplo, en un sistema que usa una base de datos, las asociaciones de un diagrama de clases pueden representar las relaciones o claves externas de la base de datos, mientras que en un sistema basado en archivos XML, las asociaciones pueden indicar las referencias cruzadas que usan XPath. En un sistema distribuido, los mensajes de un diagrama de secuencia pueden representar los mensajes de una conexión; en una aplicación independiente, pueden representar las llamadas de función.

##  <a name="Patterns"></a> Patrones de diseño
 Un modelo de diseño es un esquema del modo en que debe diseñarse un determinado aspecto del software, sobre todo uno que se repita en diferentes elementos del sistema. Si adopta un enfoque uniforme en todo el proyecto, puede reducir el costo de diseño, garantizar la coherencia de la interfaz de usuario y reducir la carga que supone la comprensión y modificación del código.

 Algunos modelos de diseño generales, como el modelo Observador, son bien conocidos y están muy extendidos. Asimismo, hay modelos que únicamente pueden aplicarse a su proyecto. Por ejemplo, en un sistema de ventas web, habrá varias operaciones en el código donde se realizan cambios en el pedido de un cliente. Para asegurarse de que el estado del pedido se muestra con precisión en cada etapa, todas estas operaciones deben seguir un protocolo determinado para actualizar la base de datos.

 La parte del trabajo de la arquitectura de software consiste en determinar qué modelos deben adoptarse en todo el diseño. Normalmente se trata de una tarea continua, porque los nuevos modelos y las mejoras de los modelos existentes se detectarán a medida que avance el proyecto. Resulta útil organizar el plan de desarrollo para que pueda ocuparse de cada uno de los principales modelos de diseño en una etapa inicial.

 La mayoría de los modelos de diseño pueden expresarse parcialmente en el código del marco. Parte del modelo puede reducirse hasta requerir al desarrollador que use determinadas clases o componentes, como una capa de acceso a la base de datos que garantice que la base de datos se está administrando correctamente.

 Un modelo de diseño se describe en un documento y normalmente incluye estos elementos:

-   Nombre.

-   Descripción del contexto en el que es aplicable. ¿Qué criterios debe tener en cuenta un programador al aplicar este modelo?

-   Breve explicación del problema que resuelve.

-   Modelo de los elementos primarios y sus relaciones. Pueden tratarse de clases o componentes e interfaces, con asociaciones y dependencias entre ellos. Normalmente, los elementos pertenecen a dos categorías:

-   Convenciones de nomenclatura.

-   Descripción del modo en que el modelo resuelve el problema.

-   Descripción de las variaciones que los desarrolladores podrían adoptar.

## <a name="see-also"></a>Vea también

- [Visualizar el código](../modeling/visualize-code.md)
- [Requisitos del usuario de modelos](../modeling/model-user-requirements.md)
- [Desarrollar pruebas a partir de un modelo](../modeling/develop-tests-from-a-model.md)
- [Usar modelos en el proceso de desarrollo](../modeling/use-models-in-your-development-process.md)