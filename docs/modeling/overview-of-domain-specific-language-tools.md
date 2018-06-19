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
ms.openlocfilehash: d64c819e1d07fed44372edca2c7107d956937d58
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949529"
---
# <a name="overview-of-domain-specific-language-tools"></a>Información general sobre las herramientas de los lenguajes específicos de dominio
Herramientas de lenguajes específicos de dominio (herramientas ADSL), que están hospedadas en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], permiten diseñar un lenguaje específico de dominio y, a continuación, generar todo lo que los usuarios deben tener para crear modelos que se basan en el lenguaje.

 En herramientas DSL se incluyen las siguientes herramientas:

-   Asistente de proyectos que usa las plantillas de solución diferente que le ayudarán a empezar a desarrollar su lenguaje específico de dominio.

-   Un diseñador gráfico para crear y editar la definición de lenguaje específico de dominio.

-   Un motor de validación que se asegura de que la definición de lenguaje específico de dominio está bien formada y muestra los errores y advertencias si hay problemas.

-   Un generador de código que toma una definición de lenguaje específico de dominio como entrada y genera código fuente como salida.

## <a name="the-dsl-tools-solution"></a>La solución de herramientas DSL
 El Asistente para el diseñador específico de dominio proporciona las siguientes plantillas de solución:

-   Flujo de tareas

-   Diagramas de clases

-   Lenguaje mínima

-   Modelos de componentes

-   WPF mínima

-   Windows.Forms mínima

-   Biblioteca DSL

 Para obtener más información, consulte [elegir una plantilla de solución de lenguaje específico de dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).

 El asistente crea un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solución que tenga los siguientes proyectos:

-   DSL

     El proyecto de Dsl define el lenguaje específico de dominio y sus herramientas de edición y procesamiento.

-   **DslPackage**

     El proyecto DslPackage determina cómo se integran con las herramientas de lenguaje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="the-dsl-tools-graphical-interface"></a>La interfaz gráfica de herramientas DSL
 Puede usar la interfaz gráfica de herramientas DSL para agregar elementos y relaciones a su lenguaje específico de dominio. Después de haber agregado los elementos, puede definir su apariencia asignándolas a formas, personalizar colores y agregar decoradores. También puede agregar los elementos al cuadro de herramientas.

## <a name="validation-in-dsl-tools"></a>Validación en herramientas DSL
 DSL proporciona un nivel de validación para asegurarse de que el modelo de dominio cumple los requisitos básicos para la generación de código. Normalmente, cuando se crea su propio lenguaje específico de dominio, debería agregar su propia validación para expresar las reglas de lógica de negocios. Para obtener más información acerca de la validación personalizada, vea [validación en un lenguaje específico de dominio](../modeling/validation-in-a-domain-specific-language.md).

 Se recomienda validar su lenguaje específico de dominio a menudo cuando se está diseñando. Si su lenguaje específico de dominio tiene errores de validación, no se puede generar código fuente. El proceso de generar código fuente a partir de las plantillas se realiza haciendo clic en **Transformar todas las plantillas** en la barra de herramientas del explorador de soluciones. Cada vez que se modifica la definición del lenguaje, asegúrese también de **Transformar todas las plantillas**. Para obtener más información, consulte [Cómo: crear una solución de lenguaje específico de dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Personalización de las herramientas DSL
 Puede proporcionar código adicional para afinar el comportamiento del modelo y para definir restricciones en su idioma. Si es necesario, puede realizar cambios significativos mediante la modificación de las plantillas de texto.

## <a name="distributing-your-dsl-solution"></a>Distribuir la solución DSL
 Herramientas DSL genera un paquete que se hospeda en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. El paquete muestra un cuadro de herramientas, un explorador de DSL y otros elementos de interfaz de usuario que permiten a los usuarios crear modelos mediante el lenguaje específico de dominio.

 Al compilar y ejecutar la solución de herramientas ADSL [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], una segunda instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que se muestra el aspecto de su lenguaje específico de dominio para el usuario del idioma. Después de comprobar que todo funciona correctamente, puede distribuir el `.vsix` archivo que encontrará en la carpeta de compilación del proyecto DslPackage. Este archivo se puede usar para instalar DSL como un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensión en otros equipos.  Para obtener más información, consulte [implementar soluciones de lenguaje específico de dominio](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Vea también

- [Instancia experimental](../extensibility/the-experimental-instance.md)
- [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)