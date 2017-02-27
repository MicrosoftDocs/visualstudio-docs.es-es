---
title: "Implementar un Service1 de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Servicios de lenguaje, administrados"
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Implementaci&#243;n de un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Puede utilizar clases en el marco de trabajo de paquete administrado \(MPF\) para implementar un servicio de lenguaje heredado que admite una gran variedad de características, como la finalización de IntelliSense, coincidencia de llaves y resaltado de sintaxis.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la nueva forma de implementar las características del servicio de lenguaje es usar extensiones MEF. Para obtener más información acerca de la nueva forma de implementar un servicio de lenguaje, consulte [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Se recomienda que comience a utilizar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## En esta sección  
 [Información general del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-overview.md)  
 Información general de las características del servicio de lenguaje que se admiten en MPF.  
  
 [Implementación de un servicio de lenguaje](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Describe qué se necesita para implementar un servicio de lenguaje mediante MPF.  
  
 [Registrar un servicio de lenguaje](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Describe los pasos necesarios para registrar un servicio de lenguaje basado en MPF con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Escáneres y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Describe los dos analizadores necesarios para implementar todas las características de un servicio de lenguaje mediante la MPF.  
  
 [Tutorial: Crear un servicio de lenguaje heredado](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Proporciona los pasos básicos necesarios para implementar un servicio de lenguaje MPF en un VSPackage.  
  
 [Tutorial: Obtener una lista de fragmentos de código instalados \(implementación heredado\)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Muestra las técnicas de recuperación de una lista de fragmentos de código instalados.  
  
 [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)  
 Proporciona vínculos a temas que detallan lo que debe hacerse para implementar todas las características de un servicio de lenguaje mediante MPF.