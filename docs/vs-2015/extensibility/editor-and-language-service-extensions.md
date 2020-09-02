---
title: Extensiones del editor y del servicio de lenguaje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7fa3e4be6ee44011eb1286e3ebf22ee69f8e3397
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683113"
---
# <a name="editor-and-language-service-extensions"></a>Editor y extensiones de servicio de lenguaje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede extender la mayoría de las características del editor de código de Visual Studio. El editor se basa en el Windows Presentation Foundation (WPF) y se escribe en código administrado. Aunque este diseño difiere de los diseños de versiones anteriores de Visual Studio, proporciona la mayoría de las mismas características. Para extender el editor, use el Managed Extensibility Framework (MEF).  
  
 El SDK de Visual Studio proporciona adaptadores denominados *correcciones de compatibilidad (Shim* ) para admitir VSPackages que se escribieron para versiones anteriores. No obstante, si tiene un VSPackage existente, se recomienda que lo actualice a la nueva tecnología para obtener un mejor rendimiento y confiabilidad.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Title|Descripción|  
|-----------|-----------------|  
|[Creación de una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introducción al uso de las plantillas de elementos del editor.|  
|[Ampliación del editor y los servicios de lenguaje](../extensibility/extending-the-editor-and-language-services.md)|Vínculos a documentos que presentan el diseño y las características del editor básico y muestran cómo extenderlo.|  
|[Interfaces heredadas en el editor](../extensibility/legacy-interfaces-in-the-editor.md)|Vínculos a documentos que explican cómo tener acceso al editor principal desde el código existente.|  
|[Creación de diseñadores y editores personalizados](../extensibility/creating-custom-editors-and-designers.md)|Vínculos a documentos que explican cómo crear editores personalizados.|  
|[Extensibilidad de servicio de lenguaje heredado](../extensibility/internals/legacy-language-service-extensibility.md)|Vínculos a documentos que describen cómo integrar los lenguajes de programación en Visual Studio.|  
|[Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Presenta el Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](https://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Presenta el Windows Presentation Foundation (WPF).|
