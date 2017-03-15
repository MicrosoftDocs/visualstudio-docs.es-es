---
title: "Extensi&#243;n del modelo de automatizaci&#243;n | Microsoft Docs"
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
  - "modelo de objetos de automatización, extender"
ms.assetid: f09e1365-6291-41a7-b52b-9398270d9da2
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Extensi&#243;n del modelo de automatizaci&#243;n
Esta sección describe cómo el modelo de automatización y el modelo de VSPackage representan un enfoque de dos\-diente a la extensibilidad del entorno de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  La extensibilidad es la capacidad de mejorar y extender la funcionalidad del IDE.  La automatización, por una parte, hace referencia a código creado por el usuario y herramientas que automatizan tareas en el entorno existente y mediante programación controlan el IDE.  VSPackages, por otro lado, permiten agrega nueva funcionalidad al entorno.  
  
 Es posible combinar la automatización y VSPackages en una aplicación de extensibilidad.  Para obtener un ejemplo, vea [Tutorial: Extensión de paquetes VSPackage administrados mediante la automatización](../misc/walkthrough-extending-managed-vspackages-by-using-automation.md).  
  
 Para obtener un ejemplo de un sistema de proyectos de lenguaje que admita el modelo de automatización de, vea [Muestras de VSSDK](../misc/vssdk-samples.md).  
  
## En esta sección  
 [Modelo de automatización](../misc/automation-model.md)  
 Proporciona información general sobre el modelo de automatización y cómo el modelo de automatización permite personalizar, ajustar, y automatizar el entorno.  
  
 [Que contribuyen al modelo de automatización](../extensibility/internals/contributing-to-the-automation-model.md)  
 Proporciona una vista más detallada del modelo de automatización y describe las maneras de proporcionar automatización para el Paquete.  Esta sección también proporciona ejemplos de código que muestran cómo un consumidor de automatización obtiene los objetos iniciales de la automatización de proyectos.  
  
## Secciones relacionadas  
 [SDK de Visual Studio y automatización](../Topic/Visual%20Studio%20SDK%20and%20Automation.md)  
 Explica cómo utilizar la automatización, VSPackages, o una combinación para crear aplicaciones de extensibilidad de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .