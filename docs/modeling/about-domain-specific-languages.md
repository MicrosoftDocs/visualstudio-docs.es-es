---
title: Acerca de los lenguajes específicos de dominio
description: Obtenga información sobre cómo un lenguaje específico de dominio (DSL) está diseñado para expresar instrucciones en un espacio de problemas o dominio determinado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab56292aafda25efc0b3dfeeb14e93d4502a5567
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384985"
---
# <a name="about-domain-specific-languages"></a>Acerca de los lenguajes específicos de dominio

A diferencia de un lenguaje de uso general, como C# o UML, un lenguaje específico de dominio (DSL) está diseñado para expresar instrucciones en un espacio de problemas determinado o dominio.

Las DSL conocidas incluyen expresiones regulares y SQL. Cada DSL es mucho mejor que un lenguaje de uso general para describir operaciones en cadenas de texto o una base de datos, pero mucho peor para describir ideas que están fuera de su propio ámbito. Los sectores individuales también tienen sus propias DSL. Por ejemplo, en el sector de las telecomunicaciones, los idiomas de descripción de llamadas se usan ampliamente para especificar la secuencia de estados en una llamada telefónica y, en el sector de los viajes en el aire, se usa un DSL estándar para describir las reservas de vuelos.

Su empresa y su proyecto también tratan con conjuntos especiales de conceptos que se podrían describir con un DSL. Por ejemplo, podría definir un DSL para una de estas aplicaciones:

- Plan de rutas de navegación en un sitio web.

- Diagramas de cableado para componentes electrónicos.

- Redes de cintas transportadoras y equipos de control de equipaje para un aeropuerto.

Al diseñar un DSL,  se define una clase de dominio para cada uno de los conceptos importantes del dominio, como una página web, una bombilla o un escritorio de facturación de aeropuerto. Puede definir *relaciones de dominio como* hipervínculos, cables o una cinta transportadora para vincular los conceptos.

Los usuarios del DSL crean *modelos.* Los modelos *son instancias* del DSL. Por ejemplo, describen un sitio web determinado, el cableado de un dispositivo determinado o el sistema de control de equipaje de un aeropuerto determinado.

Los usuarios pueden ver un modelo como un diagrama o como un formulario Windows. Los modelos también se pueden ver como XML, que es cómo se almacenan. Al definir un DSL, se define cómo aparecen las instancias de cada clase de dominio y relación en la pantalla del usuario. Un DSL típico se muestra como una colección de iconos o rectángulos conectados mediante flechas.

En la ilustración siguiente se muestra un modelo pequeño en un DSL diagramamático:

![Modelo de árbol de familia Tudor](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>Qué puede hacer con las DSL

Una aplicación típica de un DSL es generar código de programa u otros artefactos. Al definir el DSL, puede definir plantillas de *texto* que leen un modelo del DSL y generan archivos de texto.

Por ejemplo, podría escribir plantillas que toman un plan de aeropuerto y generan parte del software para el control de equipaje, así como algunos de los documentos de usuario que describen el plan.

Cuando haya definido un DSL, puede distribuirlo a otros usuarios que puedan instalarlo en sus propios equipos. Los usuarios del DSL pueden crear y editar modelos en Visual Studio.

También puede definir comandos de menú y otras herramientas que ayudan a los usuarios a editar el DSL, las restricciones de validación para ayudar a garantizar que el DSL se usa correctamente y las plantillas de elemento que ayudan a los usuarios a crear nuevas instancias. Puede encapsular una o varias DSL con sus herramientas y otras extensiones Visual Studio como un paquete integrado.

Normalmente, se crea un lenguaje específico del dominio cuando un equipo de desarrollo tiene que escribir código similar para varios productos. Por ejemplo, una empresa especializada en sistemas de control de equipaje podría definir un DSL de pista de equipaje a partir del cual pueden generar parte del código para cada instalación. Las ventajas del DSL son que sus clientes pueden entender que el código generado a partir de él es confiable y que el sistema se puede actualizar rápidamente si cambian los requisitos de los clientes.

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] permite crear un lenguaje específico del dominio que tiene su propio diseñador gráfico y su propia notación de diagrama y, a continuación, usar el lenguaje para generar el código fuente adecuado para cada proyecto.

## <a name="domain-specific-development"></a>Domain-Specific Development

El desarrollo específico del dominio es el proceso de identificar las partes de las aplicaciones que se pueden modelar mediante un lenguaje específico del dominio y, a continuación, crear el lenguaje e implementarlo para los desarrolladores de aplicaciones. Los desarrolladores usan el lenguaje específico del dominio para construir modelos específicos de sus aplicaciones, usar los modelos para generar código fuente y, a continuación, usar el código fuente para desarrollar las aplicaciones.

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspectos del desarrollo Domain-Specific gráfico

Un lenguaje gráfico específico del dominio debe incluir las siguientes características:

- Notación

- Modelo de dominio

- Generación de artefactos

- Serialización

- Integración con Visual Studio

### <a name="notation"></a>Notación

Un lenguaje específico del dominio debe tener un conjunto razonablemente pequeño de elementos que se puedan definir y ampliar fácilmente para representar construcciones específicas del dominio. Una notación consta de formas, que representan los elementos, y conectores, que representan las relaciones entre los elementos, en una superficie gráfica de diagrama. En [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , las formas se pueden ampliar y refinar para representar los elementos del lenguaje específico del dominio.

### <a name="domain-model"></a>Modelo de dominio

Un lenguaje específico del dominio debe combinar el conjunto de elementos y las relaciones entre ellos en una gramática coherente. También debe definir si las combinaciones de elementos y relaciones son válidas. Por ejemplo, los lenguajes de programación suelen evitar la herencia circular, en la que una clase se deriva de una segunda clase y la segunda clase se deriva de la primera clase. Las restricciones también se pueden usar para expresar la lógica de negocios, por ejemplo, una persona no puede depender de sí misma. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] usa restricciones para expresar los tipos de restricciones que requieren la mayoría de los lenguajes específicos del dominio.

### <a name="artifact-generation"></a>Generación de artefactos

Uno de los propósitos principales de un lenguaje específico del dominio es generar un artefacto, por ejemplo, código fuente, un archivo XML o algunos otros datos utilizables. Normalmente, un cambio en el modelo significa un cambio en el artefacto. Puede usar para [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] generar artefactos y regenerarlos al cambiar el modelo.

### <a name="serialization"></a>Serialización

Un lenguaje específico del dominio debe conservarse de alguna forma que se pueda editar, guardar, cerrar y volver a cargar. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] usa un formato XML que le permite definir y personalizar cómo se serializa o conserva el lenguaje específico del dominio.

### <a name="integration-with-visual-studio"></a>Integración con Visual Studio

Dado [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] que se hospeda en Visual Studio, extiende muchos Visual Studio ventanas y controles. También permite personalizar el comportamiento de los comandos de menú, los elementos del cuadro de herramientas y otros elementos de la interfaz de usuario.

También puede crear un adaptador de Bus de modelos para el lenguaje específico del dominio. Este adaptador le permite hacer referencia a un modelo y a los elementos de un modelo, y le permite escribir código que puede tener acceso a una instancia del DSL y actualizarla. Mediante el eficaz mecanismo de Bus de modelos, puede escribir Visual Studio que funcionan con varios modelos. También puede escribir aplicaciones independientes que funcionen con modelos. Para obtener más información, vea [Integración de modelos mediante Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

## <a name="benefits-of-domain-specific-development"></a>Ventajas del Domain-Specific desarrollo

Un lenguaje específico del dominio puede proporcionar las siguientes ventajas:

- Contiene construcciones que se ajustan exactamente al espacio del problema.

     A diferencia de los lenguajes de uso general, un lenguaje específico del dominio consta de elementos y relaciones que representan directamente la lógica del espacio del problema. Por ejemplo, una aplicación de directiva de seguros debe incluir elementos para las directivas y las notificaciones. Un lenguaje específico del dominio facilita el diseño de la aplicación y la búsqueda y corrección de errores de lógica.

- Permite que los usuarios que no son desarrolladores y personas que no conocen el dominio comprendan el diseño general.

     Mediante el uso de un lenguaje gráfico específico del dominio, puede crear una representación visual del dominio para que los no desarrolladores puedan comprender fácilmente el diseño de la aplicación.

- Facilita la creación de un prototipo de la aplicación final.

     Los desarrolladores pueden usar el código que genera su modelo para crear una aplicación de prototipo que puedan mostrar a los clientes.

## <a name="the-process-of-domain-specific-development"></a>El proceso de Domain-Specific desarrollo

La mayoría de los equipos de desarrollo de software que usan lenguajes específicos de dominio siguen estos pasos para crear y usar sus modelos:

- El equipo distingue las partes variables del dominio de las partes que nunca cambian.

- Los desarrolladores escriben código para las partes fijas y dejan puntos de extensión para las partes variables.

- El desarrollador de software principal o el arquitecto crean un lenguaje específico del dominio que incorpora los patrones de diseño de las partes fijas del dominio y los puntos de extensión para las partes variables.

- El desarrollador de software principal o el arquitecto implementan el lenguaje específico del dominio para los desarrolladores de las distintas aplicaciones que el equipo produce.

- Cada desarrollador crea un modelo que se aplica a la aplicación específica.
