---
title: Información general sobre las herramientas de los lenguajes específicos de dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e31d9c01ded7754fd10419f3fd0e18d9616a51eb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078244"
---
# <a name="overview-of-domain-specific-language-tools"></a>Información general sobre las herramientas de los lenguajes específicos de dominio
Herramientas de lenguajes específicos de dominio (herramientas DSL), que se hospeda en Visual Studio, le permiten diseñar un lenguaje específico de dominio y, a continuación, generar todo lo que los usuarios deben tener para crear modelos que se basan en el lenguaje.

 En Herramientas DSL se incluyen estas herramientas:

- Asistente de proyectos que usa plantillas de solución diferentes con las que podrá empezar a desarrollar su lenguaje específico de dominio de manera sencilla.

- Diseñador gráfico para crear y editar la definición de lenguaje específico de dominio.

- Motor de validación que garantiza que la definición de lenguaje específico de dominio es correcta y muestra errores y advertencias si hay problemas.

- Generador de código que toma una definición de lenguaje específico de dominio como entrada y genera código fuente como salida.

## <a name="the-dsl-tools-solution"></a>Solución de Herramientas DSL
 El Asistente de diseñador específico de dominio proporciona estas plantillas de solución:

- Flujo de tareas

- Diagramas de clases

- Lenguaje mínimo

- Modelos de componente

- WPF mínimo

- Windows Forms mínimo

- Biblioteca DSL

  Para obtener más información, vea [Elección de una plantilla de solución de lenguaje específico de dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).

  El asistente crea una solución de Visual Studio que tiene los siguientes proyectos:

- Dsl

   El proyecto Dsl define el lenguaje específico de dominio y sus herramientas de edición y de procesamiento.

- **DslPackage**

   El proyecto DslPackage determina cómo integran las herramientas de lenguaje con Visual Studio.

## <a name="the-dsl-tools-graphical-interface"></a>Interfaz gráfica de Herramientas DSL
 Puede usar la interfaz gráfica de Herramientas DSL para agregar elementos y relaciones al lenguaje específico de dominio. Después de agregar los elementos, puede definir su apariencia si los asigna a las formas, personaliza los colores y agrega elementos Decorator. También puede agregar los elementos al cuadro de herramientas.

## <a name="validation-in-dsl-tools"></a>Validación en Herramientas DSL
 Dsl proporciona un nivel de validación para asegurarse de que el modelo de dominio cumple los requisitos básicos para la generación de código. Normalmente, cuando crea su propio lenguaje específico de dominio, agrega su propia validación para expresar las reglas de lógica de negocios. Para más información sobre la validación personalizada, vea [Validación en un lenguaje específico de dominio](../modeling/validation-in-a-domain-specific-language.md).

 Se recomienda que valide su lenguaje específico de dominio a menudo cuando lo esté diseñando. Si el lenguaje específico de dominio tiene errores de validación, no podrá generar código fuente. Para generar código fuente a partir de plantillas, es necesario hacer clic en **Transformar todas las plantillas** en la barra de herramientas del Explorador de soluciones. Cada vez que modifique la definición de lenguaje, asegúrese también de **Transformar todas las plantillas**. Para obtener más información, vea [Cómo: Crear una solución de lenguaje específico de dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Personalización de Herramientas DSL
 Puede proporcionar código adicional para refinar el comportamiento del modelo y definir restricciones sobre el lenguaje. Si es necesario, puede realizar cambios importantes mediante la modificación de plantillas de texto.

## <a name="distributing-your-dsl-solution"></a>Distribución de la solución de DSL
 Herramientas DSL genera un paquete que se hospeda en Visual Studio. El paquete muestra un cuadro de herramientas, un explorador de DSL y otros elementos de interfaz de usuario que permiten a los usuarios crear modelos mediante el lenguaje específico de dominio.

 Al compilar y ejecutar la solución de las herramientas de DSL en Visual Studio, una segunda instancia de Visual Studio muestra el aspecto de su lenguaje específico de dominio para el usuario del lenguaje. Después de comprobar que todo funciona correctamente, puede distribuir el archivo `.vsix` que encontrará en la carpeta de compilación del proyecto DslPackage. Este archivo se puede usar para instalar el DSL como una extensión de Visual Studio en otros equipos.  Para obtener más información, vea [Implementación de soluciones de lenguaje específico de dominio](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Vea también

- [Instancia experimental](../extensibility/the-experimental-instance.md)
- [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)