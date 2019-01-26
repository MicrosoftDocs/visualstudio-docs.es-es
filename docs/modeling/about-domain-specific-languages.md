---
title: Acerca de los lenguajes específicos de dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: f50c805aa0086a575b9a1dafcc590a42ddd319c1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54978209"
---
# <a name="about-domain-specific-languages"></a>Acerca de los lenguajes específicos de dominio

A diferencia de un lenguaje como C# o UML de uso general, un lenguaje específico de dominio (DSL) está diseñado para expresar las instrucciones en un determinado problema de espacio o dominio.

DSL Well-Known incluye expresiones regulares y SQL. Cada DSL es mucho mejor que un lenguaje de uso general para describir las operaciones de cadenas de texto o una base de datos, pero mucho peor para describir las ideas que están fuera de su propio ámbito. Sectores individuales también tienen su propio DSL. Por ejemplo, en el sector de telecomunicaciones, llame a descripción lenguajes se utilizan ampliamente para especificar la secuencia de Estados en una llamada de teléfono y, en el aire de desplazamiento del sector un estándar de que DSL se utiliza para describir las reservas del vuelo.

Su negocio y el proyecto también se encargan conjuntos especiales de los conceptos que se podrían describir con un DSL. Por ejemplo, podría definir un DSL de una de estas aplicaciones:

-   Plan de rutas de navegación en un sitio Web.

-   Diagramas de cableado de componentes electrónicos.

-   Redes de cintas transportadoras y equipos de un aeropuerto de control de equipaje.

Cuando diseñe un DSL, definirá un *la clase de dominio* para cada uno de los conceptos importantes en el dominio, por ejemplo, un mostrador de aeropuerto, lamp o página web. Define *relaciones de dominio* como hipervínculo, conexión o una cinta transportadora para vincular entre sí los conceptos.

Crean usuarios de su DSL *modelos.* Los modelos son *instancias* del DSL. Por ejemplo, describe un determinado sitio Web o el cableado de un determinado dispositivo o el sistema en un aeropuerto determinado de control de equipaje.

Los usuarios pueden ver un modelo como un diagrama o como un formulario de Windows. Los modelos también pueden ver como XML, que es cómo se almacenan. Al definir un DSL, se definen cómo aparecen las instancias de cada clase de dominio y la relación en la pantalla del usuario. Un DSL típico se muestra como una colección de iconos o rectángulos conectados por flechas.

En la siguiente ilustración se muestra un modelo pequeño en un forma de diagrama DSL:

![Modelo de árbol de familia Tudor](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>Lo que puede hacer con DSL

Una aplicación típica de un DSL consiste en generar código de programa u otros artefactos. Al definir su DSL, puede definir *plantillas de texto* que leer un modelo de DSL y generar archivos de texto.

Por ejemplo, podría escribir plantillas que adoptar un plan de aeropuerto y generan parte del software de control, así como algunos de los documentos de usuario que describen el plan de equipaje.

Cuando haya definido un DSL, puede distribuirla a otros usuarios que pueden instalarlo en sus propios equipos. Los usuarios de su DSL pueden crear y editar los modelos en Visual Studio.

También puede definir comandos de menú y otras herramientas que ayudan a los usuarios edición el DSL, las restricciones de validación para ayudar a garantizar que el DSL se utiliza correctamente, y plantillas de elementos que ayudan a los usuarios crean nuevas instancias. Puede ajustar uno o más DSL con sus herramientas y otras extensiones de Visual Studio como un paquete integrado.

Normalmente, un lenguaje específico de dominio se crea cuando un equipo de desarrollo tiene que escribir código similar para diversos productos. Por ejemplo, una empresa que se especializa en sistemas de control de equipaje puede definir un DSL de pista de equipaje desde el que puede generar parte del código para cada instalación. Las ventajas del DSL son que se puede entender sus clientes, que es confiable el código generado a partir de él, y que el sistema se puede actualizar rápidamente si cambian los requisitos de los clientes.

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] le permite crear un lenguaje específico de dominio que tiene su propio diseñador gráfico y su notación del diagrama y, a continuación, usar el lenguaje para generar código fuente adecuado para cada proyecto.

## <a name="domain-specific-development"></a>Desarrollo específico de dominio

Desarrollo específico de dominio es el proceso de identificar las partes de las aplicaciones que se pueden modelar mediante un lenguaje específico de dominio y, a continuación, construir el lenguaje y implementarla para los desarrolladores de aplicaciones. Los desarrolladores usar el lenguaje específico de dominio para construir modelos que son específicos de sus aplicaciones, usar los modelos para generar código fuente y, a continuación, utilice el código fuente para desarrollar las aplicaciones.

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspectos del desarrollo gráfico específicos de dominio

Un lenguaje específico de dominio gráfico debe incluir las siguientes características:

- Notation

- Modelo de dominio

- Generación de artefacto

- Serialización

- Integración con Visual Studio

### <a name="notation"></a>Notation

Un lenguaje específico de dominio debe tener un conjunto relativamente pequeño de elementos que puede definirse fácilmente y extendido para representar construcciones específicas del dominio. Una notación consta de formas, que representan los elementos, y los conectores, que representan las relaciones entre elementos en una superficie de diagrama de gráficos. En [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], pueden ampliar las formas y refinadas para representar los elementos de su lenguaje específico de dominio.

### <a name="domain-model"></a>Modelo de dominio

Un lenguaje específico de dominio debe combinar el conjunto de elementos y las relaciones entre ellos en una gramática coherente. También debe definir si las combinaciones de elementos y relaciones son válidas. Por ejemplo, lenguajes de programación normalmente impedir la herencia circular, en el que una clase se deriva de una segunda clase y la segunda clase se deriva de la primera clase. También pueden utilizarse restricciones para expresar la lógica empresarial, por ejemplo, una persona no puede ser una dependencia de sí mismo. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] utiliza las restricciones para expresar los tipos de restricciones que requieren más los lenguajes específicos de dominio.

### <a name="artifact-generation"></a>Generación de artefacto

Uno de los principales propósitos de un lenguaje específico de dominio consiste en generar un artefacto, por ejemplo, código fuente, un archivo XML o algunos otros datos utilizables. Normalmente, un cambio en el modelo significa un cambio en el artefacto. Puede usar [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] para generar artefactos y volver a generarlas cuando se cambia el modelo.

### <a name="serialization"></a>Serialización

Un lenguaje específico de dominio debe conservarse en alguna forma que puede editar, guardar, cierra y vuelve a cargar. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] usa un formato XML que le permite definir y personalizar cómo se serializa o se conserva su lenguaje específico de dominio.

### <a name="integration-with-visual-studio"></a>Integración con Visual Studio

Dado que [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] se hospeda en Visual Studio, lo extiende muchas ventanas de Visual Studio y controles. También permite personalizar el comportamiento de los comandos de menú, elementos de cuadro de herramientas y otros elementos de la interfaz de usuario.

También puede crear un adaptador de Bus de modelo para su lenguaje específico de dominio. Este adaptador le permite un modelo de referencia y elementos dentro de un modelo y permite escribir código que puede obtener acceso y actualizar una instancia del DSL. Mediante el mecanismo de Model Bus eficaz, puede escribir las extensiones de Visual Studio que funcionan con varios modelos. También puede escribir aplicaciones independientes que funcionan con modelos. Para obtener más información, consulte [integrar modelos utilizando Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

## <a name="benefits-of-domain-specific-development"></a>Ventajas de desarrollo específico de dominio

Un lenguaje específico de dominio puede proporcionar las siguientes ventajas:

- Contiene construcciones que se ajuste exactamente al espacio del problema.

     A diferencia de los lenguajes de uso general, un lenguaje específico de dominio consta de los elementos y relaciones que representan directamente la lógica del espacio del problema. Por ejemplo, una aplicación de la póliza de seguro debe incluir elementos de las directivas y las notificaciones. Un lenguaje específico de dominio resulta más fácil diseñar la aplicación y buscar y corregir los errores de lógica.

- Permite que no son desarrolladores y las personas que no conocen comprender el diseño general del dominio.

     Mediante el uso de un lenguaje específico de dominio gráfico, puede crear una representación visual del dominio para que no sean desarrolladores puedan comprender fácilmente el diseño de la aplicación.

- Facilita la creación de un prototipo de la aplicación final.

     Los desarrolladores pueden usar el código que genera su modelo para crear una aplicación de prototipo que pueden mostrar a los clientes.

## <a name="the-process-of-domain-specific-development"></a>El proceso de desarrollo específico de dominio

La mayoría de los equipos de desarrollo de software que utilizan lenguajes específicos de dominio siguen estos pasos para crear y usar sus modelos:

-   El equipo distingue las partes variables del dominio de las partes que no cambia nunca.

-   Los desarrolladores escribir código para los elementos fijos y dejar los puntos de extensión para las partes variables.

-   El jefe de desarrollo de software o el arquitecto crea un lenguaje específico de dominio que incorpora los patrones de diseño de las partes del dominio y los puntos de extensión para las partes variables fijos.

-   El jefe de desarrollo de software o el arquitecto se implementa el lenguaje específico de dominio a los desarrolladores de las distintas aplicaciones producidos por el equipo.

-   Todos los desarrolladores, crea un modelo que se aplica a la aplicación específica.