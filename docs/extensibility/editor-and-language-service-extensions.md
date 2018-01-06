---
title: Las extensiones de servicio de editor y el idioma | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 59de764dfcb976dfac303f44a67340e117ae5e06
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="editor-and-language-service-extensions"></a>Editor y extensiones de servicio de lenguaje
Puede ampliar la mayoría de las características del editor de código de Visual Studio. El editor se basa en Windows Presentation Foundation (WPF) y se escribe en código administrado. Aunque este diseño es diferente de los diseños en versiones anteriores de Visual Studio, proporciona la mayoría de las mismas características. Para extender el editor, utilice Managed Extensibility Framework (MEF).  
  
 El SDK de Visual Studio proporciona adaptadores que se conoce como *correcciones de compatibilidad* para admitir VSPackages escritos para versiones anteriores. No obstante, si tiene un VSPackage existente, se recomienda actualizarla a la nueva tecnología para obtener el mejor rendimiento y confiabilidad.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Creación de una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introducción al uso de las plantillas de elementos del Editor.|  
|[Ampliación del editor y los servicios de lenguaje](../extensibility/extending-the-editor-and-language-services.md)|Vínculos a documentos que se presentan el diseño y características del editor principal y se muestran cómo hacerlo.|  
|[Interfaces heredadas en el Editor](../extensibility/legacy-interfaces-in-the-editor.md)|Vínculos a documentos que explican cómo obtener acceso al editor de núcleo de código existente.|  
|[Creación de diseñadores y editores personalizados](../extensibility/creating-custom-editors-and-designers.md)|Vínculos a documentos que explican cómo crear editores personalizados.|  
|[Extensibilidad de servicio de lenguaje heredado](../extensibility/internals/legacy-language-service-extensibility.md)|Vínculos a documentos que describen cómo integrar los lenguajes de programación en Visual Studio.|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Presenta Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Presenta Windows Presentation Foundation (WPF).|