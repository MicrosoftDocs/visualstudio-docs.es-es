---
title: "Modelo de automatizaci&#243;n | Microsoft Docs"
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
  - "automatización [SDK de Visual Studio], modelo de automatización"
ms.assetid: 48ddc192-96ff-46dc-a1fe-df4eb5c62c84
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Modelo de automatizaci&#243;n
El modelo de automatización proporciona una alternativa a los VSPackages para extender [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Conocido en versiones anteriores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como modelo de extensibilidad, el modelo de automatización es una interfaz de programación que proporciona acceso a las rutinas subyacentes que controlan el entorno de desarrollo integrado \(IDE\) y permite personalizarlo, ajustarlo y automatizarlo.  
  
## VSPackages y automatización  
 La documentación del SDK de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se centra en los VSPackages, que ofrecen más potencial de desarrollo que el modelo de automatización. Por ejemplo, puede escribir código en los objetos en el modelo de automatización para personalizar un lenguaje, como [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Sin embargo, no se puede agregar un nuevo idioma al IDE mediante el modelo de automatización. Para agregar un nuevo idioma para el entorno, debe desarrollar un VSPackage.  
  
 Juntos, el modelo de automatización y el modelo de VSPackage componen un enfoque doble para la extensibilidad de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. La extensibilidad es la capacidad de mejorar y ampliar la función del IDE. La automatización hace referencia a código creado por el usuario y herramientas que automatizan las tareas en el entorno existente y controlan el IDE mediante programación. Los VSPackages, por otro lado, le permiten agregar nuevas funciones al IDE. Un VSPackage es un objeto que se puede co\-crear; es decir, tiene un generador de clases y está disponible para el IDE implementando la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  
  
 Los complementos y asistentes usan el modelo de automatización para controlar o extender la funcionalidad del IDE mediante el uso de sus interfaces de automatización. Normalmente, Microsoft incluye muchos complementos con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Puede usar complementos para integrar nuevos comandos en las barras de herramientas y menús, para agregar ventanas de herramientas o automatizar algunas tareas que se realizan con regularidad en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Como desarrollador del VSPackage, debe contribuir al modelo de automatización. Por ejemplo, si agrega un nuevo lenguaje a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usando el SDK de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], el lenguaje debe proporcionar un modelo de código sólido que extienda el ya existente. Para obtener más información, consulta [Que contribuyen al modelo de automatización](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## Vea también  
 [VSPackages](../extensibility/internals/vspackages.md)   
 [Que contribuyen al modelo de automatización](../extensibility/internals/contributing-to-the-automation-model.md)