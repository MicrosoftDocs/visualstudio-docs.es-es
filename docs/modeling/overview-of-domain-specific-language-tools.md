---
title: "Informaci&#243;n general sobre las herramientas de los lenguajes espec&#237;ficos de dominio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lenguaje específico de dominio"
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 54
caps.handback.revision: 54
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Informaci&#243;n general sobre las herramientas de los lenguajes espec&#237;ficos de dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Herramientas de lenguaje específico de dominio \(herramientas ADSL\), que se hospedan en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], permiten diseñar un lenguaje específico y generar todo que los usuarios deben tener que crear modelos que se basan en el lenguaje.  
  
 Las herramientas siguientes se incluyen en las herramientas ADSL:  
  
-   Un asistente de proyecto que utilice diferentes plantillas de la solución para ayudar inicia desarrollar el lenguaje específico.  
  
-   Un diseñador gráfico para crear y editar el lenguaje específica de dominio.  
  
-   Un motor de validación que garantiza que la definición de lenguaje específica de dominio esté bien formada, y muestra los errores y advertencias si hay problemas.  
  
-   Un generador de código que toma una definición de lenguaje específica de dominio como entrada y genera código fuente como resultado.  
  
## La solución de las herramientas ADSL  
 El asistente del diseñador de lenguaje específico proporciona las siguientes plantillas de la solución:  
  
-   flujo de la tarea  
  
-   diagramas de clases  
  
-   lenguaje mínimo  
  
-   modelos componentes  
  
-   WPF mínimo  
  
-   Windows.Forms mínimo  
  
-   Biblioteca ADSL  
  
 Para obtener más información, vea [Elegir una plantilla de soluciones para lenguajes específicos de dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 El asistente crea una solución de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que tiene los siguientes proyectos:  
  
-   DSL  
  
     El proyecto de ADSL define el lenguaje específico y sus herramientas de edición y de procesamiento.  
  
-   **DslPackage**  
  
     El proyecto de DslPackage determina cómo las herramientas de lenguaje se integran con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## La interfaz gráfica de las herramientas ADSL  
 Puede utilizar la interfaz gráfica de las herramientas ADSL para agregar elementos y relaciones al lenguaje específico.  Después de agregar los elementos, puede definir su aspecto asignándolos a las formas, personalizando colores, así como elementos decorator.  También puede agregar elementos al cuadro de herramientas.  
  
## Validación de las herramientas ADSL  
 El ADSL proporciona un nivel de validación para asegurarse de que el modelo de dominio cumple los requisitos básicos para la generación de código.  Normalmente, cuando se crea posee el lenguaje específico, agregaría dispone de validación para expresar las reglas de lógica de negocios.  Para obtener más información sobre la validación personalizada, vea [Validación en un lenguaje específico de dominio](../modeling/validation-in-a-domain-specific-language.md).  
  
 Se recomienda valida el lenguaje específico a menudo cuando se está diseñando.  Si el lenguaje específico tiene errores de validación, no puede generar código fuente.  El proceso de generar código fuente a partir de las plantillas se realiza haciendo clic **Transformar todas las plantillas** en la barra de herramientas del explorador de soluciones.  Siempre que se modifique la definición del lenguaje, asegúrese también de a **Transformar todas las plantillas**.  Para obtener más información, vea [Cómo: Crear soluciones de lenguajes específicos de dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## Personalización de las herramientas ADSL  
 Puede proporcionar código adicional para refinar el comportamiento del modelo y definir restricciones sobre el lenguaje.  Si es necesario, puede realizar cambios significativos modificando las plantillas de texto.  
  
## Distribuir la solución ADSL  
 Las herramientas ADSL generan un paquete que se hospeda en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  El paquete muestra un cuadro de herramientas, un explorador ADSL, y otros elementos de la interfaz de usuario que permiten a los usuarios crear modelos mediante el lenguaje específico.  
  
 Cuando compile y ejecute la solución de las herramientas ADSL en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], una segunda instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] muestra cómo el lenguaje específico presenta al usuario del lenguaje. Después de comprobar que las todo correctamente, puede distribuir el archivo de `.vsix` que encontrará en la carpeta de compilación del proyecto de DslPackage.  Este archivo se puede utilizar para instalar ADSL como una extensión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en otros equipos.  Para obtener más información, vea [Implementar soluciones de lenguajes específicos de dominio](../modeling/deploying-domain-specific-language-solutions.md).  
  
## Vea también  
 [La instancia Experimental](../extensibility/the-experimental-instance.md)   
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/es-es/ca5e84cb-a315-465c-be24-76aa3df276aa)