---
title: Información general sobre las Herramientas del lenguaje específico de dominio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ed5232ed8f0033e5953f14b8e4a9aa08abcb316c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805657"
---
# <a name="overview-of-domain-specific-language-tools"></a>Información general sobre las Herramientas del lenguaje específico de dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las Herramientas del lenguaje específico de dominio (herramientas DSL), que se hospedan en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], permiten diseñar un lenguaje específico de dominio y, después, generar todo lo que los usuarios deben tener para crear modelos basados en el lenguaje.  
  
 En Herramientas DSL se incluyen estas herramientas:  
  
-   Asistente de proyectos que usa plantillas de solución diferentes con las que podrá empezar a desarrollar su lenguaje específico de dominio de manera sencilla.  
  
-   Diseñador gráfico para crear y editar la definición de lenguaje específico de dominio.  
  
-   Motor de validación que garantiza que la definición de lenguaje específico de dominio es correcta y muestra errores y advertencias si hay problemas.  
  
-   Generador de código que toma una definición de lenguaje específico de dominio como entrada y genera código fuente como salida.  
  
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
  
  El asistente crea una solución de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que tiene estos proyectos:  
  
- Dsl  
  
   El proyecto Dsl define el lenguaje específico de dominio y sus herramientas de edición y de procesamiento.  
  
- **DslPackage**  
  
   El proyecto DslPackage determina cómo se integran las herramientas de lenguaje con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="the-dsl-tools-graphical-interface"></a>Interfaz gráfica de Herramientas DSL  
 Puede usar la interfaz gráfica de Herramientas DSL para agregar elementos y relaciones al lenguaje específico de dominio. Después de agregar los elementos, puede definir su apariencia si los asigna a las formas, personaliza los colores y agrega elementos Decorator. También puede agregar los elementos al cuadro de herramientas.  
  
## <a name="validation-in-dsl-tools"></a>Validación en Herramientas DSL  
 Dsl proporciona un nivel de validación para asegurarse de que el modelo de dominio cumple los requisitos básicos para la generación de código. Normalmente, cuando crea su propio lenguaje específico de dominio, agrega su propia validación para expresar las reglas de lógica de negocios. Para más información sobre la validación personalizada, vea [Validación en un lenguaje específico de dominio](../modeling/validation-in-a-domain-specific-language.md).  
  
 Se recomienda que valide su lenguaje específico de dominio a menudo cuando lo esté diseñando. Si el lenguaje específico de dominio tiene errores de validación, no podrá generar código fuente. Para generar código fuente a partir de plantillas, es necesario hacer clic en **Transformar todas las plantillas** en la barra de herramientas del Explorador de soluciones. Cada vez que modifique la definición de lenguaje, asegúrese también de **Transformar todas las plantillas**. Para obtener más información, vea [Cómo: Crear una solución de lenguaje específico de dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="customization-of-dsl-tools"></a>Personalización de Herramientas DSL  
 Puede proporcionar código adicional para refinar el comportamiento del modelo y definir restricciones sobre el lenguaje. Si es necesario, puede realizar cambios importantes mediante la modificación de plantillas de texto.  
  
## <a name="distributing-your-dsl-solution"></a>Distribución de la solución de DSL  
 Herramientas DSL genera un paquete que se hospeda en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. El paquete muestra un cuadro de herramientas, un explorador de DSL y otros elementos de interfaz de usuario que permiten a los usuarios crear modelos mediante el lenguaje específico de dominio.  
  
 Al compilar y ejecutar la solución Herramientas de DSL [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], una segunda instancia de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] muestra el aspecto de su lenguaje específico de dominio para el usuario del lenguaje. Después de comprobar que todo funciona correctamente, puede distribuir el archivo `.vsix` que encontrará en la carpeta de compilación del proyecto DslPackage. Este archivo se puede usar para instalar DSL como una extensión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en otros equipos.  Para obtener más información, vea [Implementación de soluciones de lenguaje específico de dominio](../modeling/deploying-domain-specific-language-solutions.md).  
  
## <a name="see-also"></a>Otras referencias  
 [Instancia experimental](../extensibility/the-experimental-instance.md)   
 [Glosario de las Herramientas del lenguaje específico de dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
