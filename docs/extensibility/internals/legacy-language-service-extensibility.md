---
title: "Extensibilidad de servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Servicios de lenguaje"
  - "Servicios de lenguaje de Visual Studio"
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 42
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 42
---
# Extensibilidad de servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un servicio de lenguaje proporciona compatibilidad específica del idioma para la edición de código fuente en el IDE.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la nueva forma de implementar las características del servicio de lenguaje es usar extensiones MEF. Para obtener más información acerca de la nueva forma de implementar un servicio de lenguaje, consulte [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).  
  
 Esta sección describe la estructura y la implementación de un servicio de lenguaje heredado.  
  
## En esta sección  
 [Migrar un servicio de lenguaje heredado](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Explica cómo actualizar un servicio de lenguaje de Visual Studio 2008 para la versión más reciente.  
  
 [Fundamentos de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-essentials.md)  
 Proporciona información importante acerca de cómo desarrollar servicios de lenguaje para integrar un lenguaje de programación en Visual Studio.  
  
 [Desarrollar un servicio de lenguaje](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Proporciona vínculos a temas que pueden ayudarle a crear un servicio de lenguaje.  
  
 [Colores en un servicio de lenguaje heredado de sintaxis](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Proporciona información sobre la compatibilidad de resaltado de sintaxis en un servicio de lenguaje.  
  
 [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Proporciona información acerca de cómo usar el marco de trabajo de paquete administrado \(MPF\) para implementar un servicio de lenguaje completo en código administrado.  
  
 [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Describe las bibliotecas y herramientas que permiten examinar vistas de árbol de símbolos en el IDE.  
  
## Secciones relacionadas  
 [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md)  
 Proporciona información general sobre editores de Visual Studio.  
  
 [Soporte técnico de servicio de lenguaje para la depuración](../../extensibility/internals/language-service-support-for-debugging.md)  
 Proporciona información y un vínculo a la depuración de SDK de Visual Studio, que contiene la información necesaria para crear y personalizar los componentes del depurador para depurar programas.