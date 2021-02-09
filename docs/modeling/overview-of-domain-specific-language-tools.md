---
title: Información general sobre las herramientas de los lenguajes específicos de dominio
description: Aprenda cómo las herramientas DSL le permiten diseñar un lenguaje específico de dominio y, después, generar todo lo que los usuarios deben tener para crear modelos basados en el lenguaje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dbae3a1b36e6a948766c7dc31d4a8ea8af6d70c9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897770"
---
# <a name="overview-of-domain-specific-language-tools"></a>Información general sobre las herramientas de los lenguajes específicos de dominio
Las Herramientas del lenguaje específico de dominio (Herramientas DSL), que se hospedan en Visual Studio, permiten diseñar un lenguaje específico de dominio y, después, generar todo lo que los usuarios necesitan para crear modelos basados en el lenguaje.

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

  El asistente crea una solución de Visual Studio que tiene los proyectos siguientes:

- Dsl

   El proyecto Dsl define el lenguaje específico de dominio y sus herramientas de edición y de procesamiento.

- **DslPackage**

   El proyecto DslPackage determina cómo se integran las herramientas de lenguaje con Visual Studio.

## <a name="the-dsl-tools-graphical-interface"></a>Interfaz gráfica de Herramientas DSL
 Puede usar la interfaz gráfica de Herramientas DSL para agregar elementos y relaciones al lenguaje específico de dominio. Después de agregar los elementos, puede definir su apariencia si los asigna a las formas, personaliza los colores y agrega elementos Decorator. También puede agregar los elementos al cuadro de herramientas.

## <a name="validation-in-dsl-tools"></a>Validación en Herramientas DSL
 Dsl proporciona un nivel de validación para asegurarse de que el modelo de dominio cumple los requisitos básicos para la generación de código. Normalmente, cuando crea su propio lenguaje específico de dominio, agrega su propia validación para expresar las reglas de lógica de negocios. Para más información sobre la validación personalizada, vea [Validación en un lenguaje específico de dominio](../modeling/validation-in-a-domain-specific-language.md).

 Se recomienda que valide su lenguaje específico de dominio a menudo cuando lo esté diseñando. Si el lenguaje específico de dominio tiene errores de validación, no podrá generar código fuente. Para generar código fuente a partir de plantillas, es necesario hacer clic en **Transformar todas las plantillas** en la barra de herramientas del Explorador de soluciones. Cada vez que modifique la definición de lenguaje, asegúrese también de **Transformar todas las plantillas**. Para obtener más información, vea [Cómo: Crear una solución de lenguaje específico de dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Personalización de Herramientas DSL
 Puede proporcionar código adicional para refinar el comportamiento del modelo y definir restricciones sobre el lenguaje. Si es necesario, puede realizar cambios importantes mediante la modificación de plantillas de texto.

## <a name="distributing-your-dsl-solution"></a>Distribución de la solución de DSL
 Herramientas DSL genera un paquete que se hospeda en Visual Studio. El paquete muestra un cuadro de herramientas, un explorador de DSL y otros elementos de interfaz de usuario que permiten a los usuarios crear modelos mediante el lenguaje específico de dominio.

 Al compilar y ejecutar la solución Herramientas de DSL en Visual Studio, en una segunda instancia de Visual Studio se muestra el aspecto del lenguaje específico de dominio para el usuario del lenguaje. Después de comprobar que todo funciona correctamente, puede distribuir el archivo `.vsix` que encontrará en la carpeta de compilación del proyecto DslPackage. Este archivo se puede usar para instalar DSL como una extensión de Visual Studio en otros equipos.  Para obtener más información, vea [Implementación de soluciones de lenguaje específico de dominio](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Vea también

- [Instancia experimental](../extensibility/the-experimental-instance.md)
- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))