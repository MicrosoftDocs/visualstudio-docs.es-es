---
title: Información general de las herramientas de lenguajes específicos de dominio | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 694ebbc73b531f4fab1c8b2f9621e14f4145bd70
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566250"
---
# <a name="overview-of-domain-specific-language-tools"></a>Información general sobre las herramientas de los lenguajes específicos de dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [información general de herramientas de lenguajes específicos de dominio](https://docs.microsoft.com/visualstudio/modeling/overview-of-domain-specific-language-tools).  
  
Herramientas de lenguajes específicos de dominio (herramientas DSL), que se hospedan en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], permiten diseñar un lenguaje específico de dominio y, a continuación, generar todo lo que los usuarios deben tener para crear modelos que se basan en el lenguaje.  
  
 Las siguientes herramientas se incluyen en las herramientas de DSL:  
  
-   Asistente de proyectos que usa las plantillas de solución diferente que le ayudarán a empezar a desarrollar su lenguaje específico de dominio.  
  
-   Un diseñador gráfico para crear y editar la definición de lenguaje específico de dominio.  
  
-   Un motor de validación que garantiza que la definición de lenguaje específico de dominio es correcto y muestra los errores y advertencias si hay problemas.  
  
-   Un generador de código que toma una definición de lenguaje específico de dominio como entrada y genera código fuente como salida.  
  
## <a name="the-dsl-tools-solution"></a>La solución de las herramientas DSL  
 El Asistente del diseñador específico de dominio proporciona las siguientes plantillas de solución:  
  
-   Flujo de tareas  
  
-   Diagramas de clases  
  
-   Lenguaje mínimo  
  
-   Modelos de componentes  
  
-   WPF mínimo  
  
-   Windows.Forms mínima  
  
-   Biblioteca DSL  
  
 Para obtener más información, consulte [elegir una plantilla de solución de lenguajes específicos de dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 El asistente crea un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] solución que tiene los siguientes proyectos:  
  
-   DSL  
  
     El proyecto Dsl define el lenguaje específico de dominio y sus herramientas de edición y de procesamiento.  
  
-   **DslPackage**  
  
     El proyecto DslPackage determina cómo se integran con las herramientas de lenguajes [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="the-dsl-tools-graphical-interface"></a>La interfaz gráfica de las herramientas DSL  
 Puede usar la interfaz gráfica de las herramientas de DSL para agregar elementos y relaciones a su lenguaje específico de dominio. Después de haber agregado los elementos, puede definir su apariencia mediante su asignación a las formas, personalizar los colores y agregar elementos Decorator. También puede agregar los elementos al cuadro de herramientas.  
  
## <a name="validation-in-dsl-tools"></a>Validación de las herramientas de DSL  
 DSL proporciona un nivel de validación para asegurarse de que el modelo de dominio cumple los requisitos básicos para la generación de código. Normalmente, cuando se crea su propio lenguaje específico de dominio, agregaría su propia validación para expresar las reglas de lógica de negocios. Para obtener más información acerca de la validación personalizada, vea [validación en los lenguajes específicos de dominio](../modeling/validation-in-a-domain-specific-language.md).  
  
 Se recomienda que valide su lenguaje específico de dominio a menudo cuando se está diseñando. Si su lenguaje específico de dominio tiene errores de validación, no se puede generar código fuente. El proceso de generar código fuente a partir de las plantillas se realiza haciendo **Transformar todas las plantillas** en la barra de herramientas del explorador de soluciones. Cada vez que modifique la definición del lenguaje, asegúrese también de **Transformar todas las plantillas**. Para obtener más información, consulte [Cómo: crear soluciones de lenguajes específicos de dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="customization-of-dsl-tools"></a>Personalización de las herramientas DSL  
 Puede proporcionar código adicional para refinar el comportamiento del modelo y para definir restricciones sobre su idioma. Si es necesario, puede realizar cambios significativos mediante la modificación de las plantillas de texto.  
  
## <a name="distributing-your-dsl-solution"></a>Distribuir su solución de DSL  
 Herramientas DSL genera un paquete que se hospeda en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. El paquete muestra un cuadro de herramientas, un explorador de DSL y otros elementos de interfaz de usuario que permiten a los usuarios crear modelos mediante el lenguaje específico de dominio.  
  
 Al compilar y ejecutar la solución de las herramientas de DSL [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], una segunda instancia de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] muestra el aspecto de su lenguaje específico de dominio para el usuario del lenguaje. Después de comprobar que todo funciona correctamente, puede distribuir el `.vsix` archivo que encontrará en la carpeta de compilación del proyecto DslPackage. Este archivo se puede usar para instalar el DSL como un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extensión en otros equipos.  Para obtener más información, consulte [implementar soluciones de lenguajes específicos de dominio](../modeling/deploying-domain-specific-language-solutions.md).  
  
## <a name="see-also"></a>Vea también  
 [La instancia Experimental](../extensibility/the-experimental-instance.md)   
 [Glosario de las herramientas de lenguajes específicos de dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



