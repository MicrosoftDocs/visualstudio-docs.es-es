---
title: Información general sobre las herramientas de los lenguajes específicos de dominio
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
ms.openlocfilehash: 6942511e325b77aaa3d646b6e84cd833b8b55ab2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871750"
---
# <a name="overview-of-domain-specific-language-tools"></a>Información general sobre las herramientas de los lenguajes específicos de dominio
Herramientas de lenguajes específicos de dominio (herramientas DSL), que se hospeda en Visual Studio, le permiten diseñar un lenguaje específico de dominio y, a continuación, generar todo lo que los usuarios deben tener para crear modelos que se basan en el lenguaje.

 Las siguientes herramientas se incluyen en las herramientas de DSL:

-   Asistente de proyectos que usa las plantillas de solución diferente que le ayudarán a empezar a desarrollar su lenguaje específico de dominio.

-   Un diseñador gráfico para crear y editar la definición de lenguaje específico de dominio.

-   Un motor de validación que garantiza que la definición de lenguaje específico de dominio es correcto y muestra los errores y advertencias si hay problemas.

-   Un generador de código que toma una definición de lenguaje específico de dominio como entrada y genera código fuente como salida.

## <a name="the-dsl-tools-solution"></a>La solución de las herramientas DSL
 El Asistente del diseñador específico de dominio proporciona las siguientes plantillas de solución:

- Flujo de tareas

- Diagramas de clases

- Lenguaje mínimo

- Modelos de componentes

- WPF mínimo

- Windows.Forms mínima

- Biblioteca DSL

  Para obtener más información, consulte [elegir una plantilla de solución de lenguajes específicos de dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).

  El asistente crea una solución de Visual Studio que tiene los siguientes proyectos:

- DSL

   El proyecto Dsl define el lenguaje específico de dominio y sus herramientas de edición y de procesamiento.

- **DslPackage**

   El proyecto DslPackage determina cómo integran las herramientas de lenguaje con Visual Studio.

## <a name="the-dsl-tools-graphical-interface"></a>La interfaz gráfica de las herramientas DSL
 Puede usar la interfaz gráfica de las herramientas de DSL para agregar elementos y relaciones a su lenguaje específico de dominio. Después de haber agregado los elementos, puede definir su apariencia mediante su asignación a las formas, personalizar los colores y agregar elementos Decorator. También puede agregar los elementos al cuadro de herramientas.

## <a name="validation-in-dsl-tools"></a>Validación de las herramientas de DSL
 DSL proporciona un nivel de validación para asegurarse de que el modelo de dominio cumple los requisitos básicos para la generación de código. Normalmente, cuando se crea su propio lenguaje específico de dominio, agregaría su propia validación para expresar las reglas de lógica de negocios. Para obtener más información acerca de la validación personalizada, vea [validación en los lenguajes específicos de dominio](../modeling/validation-in-a-domain-specific-language.md).

 Se recomienda que valide su lenguaje específico de dominio a menudo cuando se está diseñando. Si su lenguaje específico de dominio tiene errores de validación, no se puede generar código fuente. El proceso de generar código fuente a partir de las plantillas se realiza haciendo **Transformar todas las plantillas** en la barra de herramientas del explorador de soluciones. Cada vez que modifique la definición del lenguaje, asegúrese también de **Transformar todas las plantillas**. Para obtener más información, consulte [Cómo: crear soluciones de lenguajes específicos de dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Personalización de las herramientas DSL
 Puede proporcionar código adicional para refinar el comportamiento del modelo y para definir restricciones sobre su idioma. Si es necesario, puede realizar cambios significativos mediante la modificación de las plantillas de texto.

## <a name="distributing-your-dsl-solution"></a>Distribuir su solución de DSL
 Herramientas DSL genera un paquete que se hospeda en Visual Studio. El paquete muestra un cuadro de herramientas, un explorador de DSL y otros elementos de interfaz de usuario que permiten a los usuarios crear modelos mediante el lenguaje específico de dominio.

 Al compilar y ejecutar la solución de las herramientas de DSL en Visual Studio, una segunda instancia de Visual Studio muestra el aspecto de su lenguaje específico de dominio para el usuario del lenguaje. Después de comprobar que todo funciona correctamente, puede distribuir el `.vsix` archivo que encontrará en la carpeta de compilación del proyecto DslPackage. Este archivo se puede usar para instalar el DSL como una extensión de Visual Studio en otros equipos.  Para obtener más información, consulte [implementar soluciones de lenguajes específicos de dominio](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Vea también

- [Instancia experimental](../extensibility/the-experimental-instance.md)
- [Glosario de las herramientas de lenguajes específicos de dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)