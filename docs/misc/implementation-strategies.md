---
title: "Estrategias de implementaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "paquetes VSPackage, estrategias de implementación"
ms.assetid: f5512d4e-666d-4934-bd42-9718fd7e4c06
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# Estrategias de implementaci&#243;n
Puede extender Visual Studio con complementos de automatización, paquetes VSPackage, elementos de componentes de Managed Extensibility Framework \(MEF\), o bien una combinación de los tres. Por lo general, los complementos son más fáciles de desarrollar, pero menos eficaces que los componentes paquetes VSPackage o los elementos de componentes de MEF. Los complementos pueden llamar a interfaces de extensibilidad, y los paquetes VSPackage y los componentes de MEF pueden acceder al modelo de automatización de Visual Studio. Puede combinar varios enfoques diferentes para crear una solución eficaz.  
  
 Los paquetes VSPackage pueden escribirse en código administrado o no administrado. Se recomienda escribir nuevos paquetes VSPackage en código administrado mediante Managed Package Framework \(MPF\). Casi todo lo que puede escribirse en código no administrado se puede implementar de forma más fácil y segura en código administrado. Sin embargo, las aplicaciones heredadas escritas en código no administrado se seguirán ejecutando en Visual Studio.  
  
 Las extensiones simples pueden agregar ventanas de herramientas o enviar información a los elementos de interfaz de usuario de Visual Studio, como la barra de estado o la ventana de salida. Las aplicaciones más complejas se pueden escribir como jerarquías de Visual Studio, como el Explorador de servidores. Para mejorar la eficacia se puede implementar un proyecto, editor o diseñador. Por ejemplo, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] están implementados como servicios de lenguaje.  
  
## Secciones relacionadas  
 [SDK de Visual Studio y automatización](../Topic/Visual%20Studio%20SDK%20and%20Automation.md)  
 Aborda el uso de la automatización, los paquetes VSPackage o una combinación de ambos para crear aplicaciones de extensibilidad de Visual Studio.  
  
 [SDK de Visual Studio y código administrado](../misc/visual-studio-sdk-and-managed-code.md)  
 Compara las diferentes maneras de escribir un VSPackage en código administrado.  
  
 [Conceptos del IDE de Visual Studio](../misc/visual-studio-ide-concepts.md)  
 Explica los fundamentos de los paquetes VSPackage y cómo usar un servicio.  
  
 [Extensión de otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Describe los elementos de aplicaciones de interfaz de usuario comunes de Visual Studio, como las ventanas de estado y salida.  
  
 [Jerarquías en Visual Studio](../extensibility/internals/hierarchies-in-visual-studio.md)  
 Proporciona información general de las jerarquías de Visual Studio, que aparecen en el entorno de desarrollo integrado \(IDE\) como árboles de nodos.  
  
 [Proyectos](../extensibility/internals/projects.md)  
 Proporciona información general de las clases de proyectos y soluciones.  
  
 [Editor y extensiones de servicio de lenguaje](../extensibility/editor-and-language-service-extensions.md)  
 Muestra cómo extender el editor de código y de texto, y cómo crear editores y diseñadores personalizados.  
  
 [Extensibilidad de servicio de lenguaje heredado](../extensibility/internals/legacy-language-service-extensibility.md)  
 Muestra cómo crear servicios de lenguaje.  
  
 [Referencia del SDK de Visual Studio](../extensibility/visual-studio-sdk-reference.md)  
 Documentación de referencia del VSSDK.  
  
## Vea también  
 [Empezando a desarrollar extensiones de Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md)