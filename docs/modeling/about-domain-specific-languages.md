---
title: Acerca de los lenguajes específicos de dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0743fa0dd1f8b876c4396d4e52d9c8636c504d67
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749150"
---
# <a name="about-domain-specific-languages"></a>Acerca de los lenguajes específicos de dominio

A diferencia de un lenguaje de propósito general, como C# o UML, un lenguaje específico de dominio (DSL) está diseñado para expresar las instrucciones en un determinado problema de espacio o dominio.

DSL Well-Known incluye expresiones regulares y SQL. Cada DSL es mucho mejor que un lenguaje de propósito general para describir las operaciones en cadenas de texto o en una base de datos, pero peor para describir ideas que se encuentran fuera de su propio ámbito. Sectores individuales también tienen sus propios DSL. Por ejemplo, en el sector de telecomunicaciones, llame a descripción idiomas se utilizan ampliamente para especificar la secuencia de Estados en una llamada de teléfono y en el aire viajes sector un estándar que DSL se utiliza para describir las reservas de vuelo.

Su empresa y el proyecto también se aplican a conjuntos especial de conceptos que se describen con un DSL. Por ejemplo, podría definir un DSL para una de estas aplicaciones:

-   Plan de rutas de navegación en un sitio Web.

-   Diagramas de cableado para componentes electrónicos.

-   Redes de bandas transportadoras y equipos de un aeropuerto de control de equipaje.

Cuando se diseña un DSL, defina un *clase dominio* para cada uno de los conceptos más importantes en el dominio, como una página Web, luz o aeropuerto comprobación mostrador de facturación. Defina *relaciones de dominio* como hipervínculo, conexión o una banda transportadora para vincular entre sí los conceptos.

Crean usuarios de ADSL *modelos.* Los modelos son *instancias* de DSL. Por ejemplo, describe un sitio Web determinado, o el cableado de un determinado dispositivo o el sistema en un aeropuerto determinado de control de equipaje.

Los usuarios pueden ver un modelo como un diagrama o un formulario Windows Forms. Los modelos también pueden ver como XML, que es cómo se almacenan. Al definir un DSL, puede definir cómo las instancias de cada clase de dominio y cada relación aparecen en la pantalla del usuario. Un DSL típico se muestra como una colección de iconos o rectángulos conectados mediante flechas.

La siguiente ilustración muestra un pequeño modelo en un DSL esquemática:

![Modelo de árbol de familia Tudor](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>¿Qué puede hacer con DSL

Una aplicación típica de un DSL es generar código de programa u otros artefactos. Cuando se define el ADSL, puede definir *plantillas de texto* que leer un modelo de DSL y para generar archivos de texto.

Por ejemplo, podría escribir plantillas que toman un plan de aeropuerto y generan parte del software de control, así como algunos de los documentos de usuario que describen el plan de equipaje.

Una vez haya definido un DSL, puede distribuirla a otros usuarios que pueden instalarlo en sus equipos. Los usuarios de ADSL pueden crear y editar modelos en Visual Studio.

También puede definir comandos de menú y otras herramientas que ayudan a los usuarios edición DSL, restricciones de validación para ayudar a garantizar que la DSL se utiliza correctamente, y plantillas de elementos que le ayudan a los usuarios crean nuevas instancias. Puede ajustar uno o más DSL con sus herramientas y otras extensiones de Visual Studio como un paquete integrado.

Normalmente, un lenguaje específico de dominio se crea cuando un equipo de desarrollo tiene que escribir un código similar para varios productos. Por ejemplo, una compañía que se especializa en sistemas de control de equipaje podría definir un DSL de pista de equipaje desde la que pueden generar parte del código para cada instalación. Las ventajas de DSL son que se pueda entender sus clientes, que el código generado desde el es de confianza y que se puede actualizar rápidamente el sistema si cambian los requisitos de los clientes.

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] permite crear un lenguaje específico de dominio que tiene su propio diseñador gráfico y su propia notación de diagrama y, a continuación, usar el lenguaje para generar código fuente adecuado para cada proyecto.

## <a name="domain-specific-development"></a>Desarrollo específico de dominio

Desarrollo específico de dominio es el proceso de identificar las partes de las aplicaciones que se pueden crear mediante un lenguaje específico de dominio y, a continuación, construir el idioma y su implementación en los desarrolladores de aplicaciones. Los desarrolladores usar el lenguaje específico de dominio para generar modelos que son específicos para sus aplicaciones, usar los modelos para generar código fuente y, a continuación, use el código fuente para desarrollar las aplicaciones.

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspectos del desarrollo gráfico específico de dominio

Un lenguaje específico de dominio gráfico debe incluir las siguientes características:

- Notation

- Modelo de dominio

- Generación de artefacto

- Serialización

- Integración con Visual Studio

### <a name="notation"></a>Notation

Un lenguaje específico de dominio debe tener un conjunto de elementos que puede definirse y amplía para representar construcciones específicas del dominio fácilmente suficientemente pequeño. Una notación consta de formas, que representan los elementos, y conectores, que representan las relaciones entre elementos en una superficie de diagrama de gráficos. En [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], pueden ampliar las formas y se ha refinado para representar los elementos de su lenguaje específico de dominio.

### <a name="domain-model"></a>Modelo de dominio

Un lenguaje específico de dominio debe combinar el conjunto de elementos y las relaciones entre ellos en una gramática coherente. También debe definir si combinaciones de elementos y relaciones son válidas. Por ejemplo, los lenguajes de programación normalmente evitar herencia circular, en el que una clase se deriva de una clase de segundo y la segunda clase se deriva de la primera clase. También pueden utilizarse restricciones para expresar la lógica de negocios, por ejemplo, una persona no puede ser una dependencia de sí mismo. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] usa las restricciones para expresar los tipos de restricciones que requieren más lenguajes específicos de dominio.

### <a name="artifact-generation"></a>Generación de artefacto

Uno de los principales propósitos de un lenguaje específico de dominio consiste en generar un artefacto, por ejemplo, código fuente, un archivo XML o algún otro dato utilizable. Normalmente, un cambio en el modelo indica un cambio en el artefacto. Puede usar [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] para generar artefactos y a generar cuando se cambia el modelo.

### <a name="serialization"></a>Serialización

Un lenguaje específico de dominio se debe conservar en alguna forma que puede editar, guardar, cierra y vuelve a cargar. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] utiliza un formato XML que le permite definir y personalizar cómo se serializa o se conservan su lenguaje específico de dominio.

### <a name="integration-with-visual-studio"></a>Integración con Visual Studio

Dado que [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] se hospeda en Visual Studio, abarca muchas ventanas de Visual Studio y controles. También permite personalizar el comportamiento de los comandos de menú, elementos de cuadro de herramientas y otros elementos de la interfaz de usuario.

También puede crear un adaptador de Bus de modelo para su lenguaje específico de dominio. Este adaptador le permite un modelo de referencia y los elementos dentro de un modelo y permite escribir código que puede obtener acceso y actualizar una instancia de DSL. Mediante el uso de un mecanismo eficaz Model Bus, puede escribir las extensiones de Visual Studio que funcionan con varios modelos. También puede escribir aplicaciones independientes que funcionan con modelos. Para obtener más información, consulte [integrar modelos mediante Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

## <a name="benefits-of-domain-specific-development"></a>Ventajas de desarrollo específico de dominio

Un lenguaje específico de dominio puede proporcionar las siguientes ventajas:

- Contiene construcciones que se ajuste exactamente al problema de espacio.

     A diferencia de los lenguajes de uso generales, un lenguaje específico de dominio consta de elementos y las relaciones que representan directamente la lógica del espacio de problema. Por ejemplo, una aplicación de póliza debe incluir elementos de directivas y notificaciones. Un lenguaje específico de dominio resulta más fácil diseñar la aplicación y buscar y corregir los errores de lógica.

- Permite no a los desarrolladores y las personas que no conoce el dominio entender el diseño general.

     Mediante el uso de un lenguaje específico de dominio gráfico, puede crear una representación visual del dominio para que los desarrolladores no pueden comprender fácilmente el diseño de la aplicación.

- Resulta más fácil crear un prototipo de la aplicación final.

     Los desarrolladores pueden usar el código que genera su modelo para crear una aplicación de prototipo que puede mostrar a los clientes.

## <a name="the-process-of-domain-specific-development"></a>El proceso de desarrollo específico de dominio

La mayoría de los equipos de desarrollo de software que utilizan lenguajes específicos de dominio siguen estos pasos para crear y usar sus modelos:

-   El equipo distingue las partes variables del dominio de los elementos que no cambia nunca.

-   Los desarrolladores escribir código para las partes fijas y deje de puntos de extensión para los elementos de la variable.

-   El jefe de desarrollo de software o el arquitecto crea un lenguaje específico de dominio que incorpora los patrones de diseño de las partes del dominio y los puntos de extensión para las partes variables fijos.

-   El jefe de desarrollo de software o el arquitecto implementa el lenguaje específico de dominio a los desarrolladores de las distintas aplicaciones generadas por el equipo.

-   Cada desarrollador crea un modelo que se aplica a la aplicación específica.