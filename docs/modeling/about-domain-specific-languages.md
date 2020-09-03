---
title: Acerca de los lenguajes específicos de dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfd073b07902e3c0a9e33dfe9ae50d4947a50ef2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75597274"
---
# <a name="about-domain-specific-languages"></a>Acerca de los lenguajes específicos de dominio

A diferencia de un lenguaje de uso general como C# o UML, un lenguaje específico del dominio (DSL) está diseñado para expresar instrucciones en un espacio de problemas determinado o dominio.

Los DSL conocidos incluyen expresiones regulares y SQL. Cada DSL es mucho mejor que un lenguaje de uso general para describir operaciones en cadenas de texto o en una base de datos, pero mucho peor para describir ideas que están fuera de su propio ámbito. Los distintos sectores también tienen sus propios DSL. Por ejemplo, en el sector de las telecomunicaciones, los lenguajes de descripción de llamadas se usan ampliamente para especificar la secuencia de Estados en una llamada telefónica y, en el sector de viajes de aire, se usa un DSL estándar para describir las reservas de vuelos.

Su negocio y su proyecto también abordan conjuntos especiales de conceptos que podrían describirse con un DSL. Por ejemplo, podría definir un DSL para una de estas aplicaciones:

- Plan de rutas de navegación en un sitio Web.

- Diagramas de cableado para componentes electrónicos.

- Redes de correas transportadoras y equipos de control de equipaje para un aeropuerto.

Al diseñar un DSL, se define una *clase de dominio* para cada uno de los conceptos importantes del dominio, como una página web, una lámpara o un escritorio de inserción en el aeropuerto. Se definen *relaciones de dominio* como el hipervínculo, la conexión o una cinta transportadora para vincular los conceptos entre sí.

Los usuarios de los modelos de creación de DSL *.* Los modelos son *instancias* de DSL. Por ejemplo, describen un sitio Web determinado o el cableado de un dispositivo determinado, o el sistema de control de equipaje en un aeropuerto determinado.

Los usuarios pueden ver un modelo como un diagrama o como Windows Forms. Los modelos también se pueden ver como XML, que es cómo se almacenan. Al definir un DSL, se define el modo en que las instancias de cada clase de dominio y relación aparecen en la pantalla del usuario. Un DSL típico se muestra como una colección de iconos o rectángulos conectados por flechas.

En la ilustración siguiente se muestra un modelo pequeño en un DSL en un diagrama:

![Modelo de árbol de familia Tudor](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>Qué puede hacer con los DSL

Una aplicación típica de DSL es generar código de programa u otros artefactos. Al definir el DSL, puede definir plantillas de *texto* que lean un modelo del DSL y generen archivos de texto.

Por ejemplo, puede escribir plantillas que toman un plan de aeropuerto y que generan parte del software para el tratamiento de equipaje, así como algunos de los documentos de usuario que describen el plan.

Una vez que haya definido un DSL, puede distribuirlo a otros usuarios que puedan instalarlo en sus propios equipos. Los usuarios de su DSL pueden crear y editar modelos en Visual Studio.

También puede definir comandos de menú y otras herramientas que ayuden a los usuarios a editar el DSL, las restricciones de validación para ayudar a garantizar que el DSL se use correctamente y plantillas de elementos que ayuden a los usuarios a crear nuevas instancias. Puede ajustar uno o más DSL con sus herramientas y otras extensiones de Visual Studio como un paquete integrado.

Normalmente, se crea un lenguaje específico del dominio cuando un equipo de desarrollo tiene que escribir código similar para varios productos. Por ejemplo, una compañía que se especializa en sistemas de control de equipaje podría definir un ADSL de seguimiento de equipaje desde el que puede generar parte del código para cada instalación. Las ventajas de la DSL son que los clientes pueden entenderla, que el código generado a partir de ella es confiable y que el sistema se puede actualizar rápidamente si cambian los requisitos de los clientes.

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] permite crear un lenguaje específico de dominio que tenga su propio diseñador gráfico y su propia notación de diagrama y, a continuación, utilizar el lenguaje para generar el código fuente adecuado para cada proyecto.

## <a name="domain-specific-development"></a>Desarrollo específico del dominio

El desarrollo específico del dominio es el proceso de identificar las partes de las aplicaciones que se pueden modelar con un lenguaje específico del dominio y, a continuación, construir el lenguaje e implementarlo en los desarrolladores de aplicaciones. Los desarrolladores usan el lenguaje específico de dominio para construir modelos que son específicos de sus aplicaciones, usar los modelos para generar código fuente y, a continuación, usar el código fuente para desarrollar las aplicaciones.

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspectos del desarrollo gráfico específico del dominio

Un lenguaje gráfico específico del dominio debe incluir las siguientes características:

- Notación

- Modelo de dominio

- Generación de artefactos

- Serialización

- Integración con Visual Studio

### <a name="notation"></a>Notación

Un lenguaje específico del dominio debe tener un conjunto razonablemente pequeño de elementos que se pueden definir y ampliar fácilmente para representar construcciones específicas del dominio. Una notación consta de formas, que representan los elementos, y los conectores, que representan las relaciones entre los elementos, en una superficie de diagrama gráfico. En [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , las formas se pueden extender y refinar para representar los elementos de su lenguaje específico del dominio.

### <a name="domain-model"></a>Modelo de dominio

Un lenguaje específico del dominio debe combinar el conjunto de elementos y las relaciones entre ellos en una gramática coherente. También debe definir si las combinaciones de elementos y relaciones son válidas. Por ejemplo, los lenguajes de programación normalmente impiden la herencia circular, en la que una clase se deriva de una segunda clase y la segunda clase se deriva de la primera. Las restricciones también se pueden usar para expresar la lógica de negocios, por ejemplo, una persona no puede depender de sí misma. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] utiliza restricciones para expresar los tipos de restricciones que requieren la mayoría de los lenguajes específicos de dominio.

### <a name="artifact-generation"></a>Generación de artefactos

Uno de los objetivos principales de un lenguaje específico de dominio es generar un artefacto, por ejemplo, código fuente, un archivo XML u otros datos que se puedan usar. Normalmente, un cambio en el modelo significa un cambio en el artefacto. Puede usar [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] para generar artefactos y volver a generarlos al cambiar el modelo.

### <a name="serialization"></a>Serialización

Un lenguaje específico del dominio debe conservarse de alguna forma que se pueda editar, guardar, cerrar y recargar. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] usa un formato XML que permite definir y personalizar el modo en que se serializa o se conserva el lenguaje específico del dominio.

### <a name="integration-with-visual-studio"></a>Integración con Visual Studio

Dado [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] que se hospeda en Visual Studio, extiende muchas ventanas y controles de Visual Studio. También permite personalizar el comportamiento de los comandos de menú, los elementos del cuadro de herramientas y otros elementos de la interfaz de usuario.

También puede crear un adaptador de bus de modelo para su lenguaje específico de dominio. Este adaptador le permite hacer referencia a un modelo y a los elementos de un modelo, y le permite escribir código que puede tener acceso a una instancia de DSL y actualizarla. Mediante el potente mecanismo de bus de modelo, puede escribir extensiones de Visual Studio que funcionen con varios modelos. También puede escribir aplicaciones independientes que funcionen con modelos. Para obtener más información, vea [integrar modelos mediante Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

## <a name="benefits-of-domain-specific-development"></a>Ventajas del desarrollo específico del dominio

Un lenguaje específico de dominio puede proporcionar las siguientes ventajas:

- Contiene construcciones que se ajustan exactamente al espacio del problema.

     A diferencia de los lenguajes de uso general, un lenguaje específico de dominio consta de elementos y relaciones que representan directamente la lógica del espacio de problemas. Por ejemplo, una aplicación de póliza de seguros debe incluir elementos para las directivas y las notificaciones. Un lenguaje específico del dominio facilita el diseño de la aplicación y la búsqueda y corrección de errores de lógica.

- Permite a los desarrolladores y personas que no conocen el dominio comprender el diseño global.

     Mediante el uso de un lenguaje gráfico específico del dominio, puede crear una representación visual del dominio para que los desarrolladores que no son de puedan comprender fácilmente el diseño de la aplicación.

- Facilita la creación de un prototipo de la aplicación final.

     Los desarrolladores pueden usar el código que su modelo genera para crear una aplicación prototipo que se puede mostrar a los clientes.

## <a name="the-process-of-domain-specific-development"></a>El proceso de desarrollo específico del dominio

La mayoría de los equipos de desarrollo de software que usan lenguajes específicos de dominio siguen estos pasos para crear y usar sus modelos:

- El equipo distingue las partes variables del dominio de las partes que nunca cambian.

- Los desarrolladores escriben código para los elementos fijos y dejan puntos de extensión para las partes variables.

- El desarrollador jefe de software o el arquitecto crea un lenguaje específico del dominio que incorpora los patrones de diseño de las partes fijas del dominio y los puntos de extensión para las partes variables.

- El desarrollador jefe de software o el arquitecto implementa el lenguaje específico del dominio para los desarrolladores de las distintas aplicaciones que produce el equipo.

- Cada desarrollador crea un modelo que se aplica a la aplicación específica.
