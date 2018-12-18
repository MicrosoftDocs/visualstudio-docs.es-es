---
title: Las extensiones de servicio de editor y lenguaje | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b5e0b568cee873d29f73eb2b81e38d49b76b5844
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778766"
---
# <a name="editor-and-language-service-extensions"></a>Editor y extensiones de servicio de lenguaje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede ampliar la mayoría de las características del editor de código de Visual Studio. El editor se basa en Windows Presentation Foundation (WPF) y está escrito en código administrado. Aunque este diseño es diferente de los diseños en versiones anteriores de Visual Studio, proporciona la mayoría de las mismas características. Para ampliar el editor, use Managed Extensibility Framework (MEF).  
  
 El SDK de Visual Studio permite a los adaptadores que se conoce como *las correcciones de compatibilidad* para admitir los VSPackages escritos para versiones anteriores. No obstante, si tiene un VSPackage existente, se recomienda actualizarlo a la nueva tecnología para obtener un mejor rendimiento y la confiabilidad.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Creación de una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introducción al uso de las plantillas de elementos de Editor.|  
|[Ampliación del editor y los servicios de lenguaje](../extensibility/extending-the-editor-and-language-services.md)|Vínculos a documentos que presentan el diseño y las características del editor de núcleo y muestran cómo ampliarla.|  
|[Interfaces heredadas en el editor](../extensibility/legacy-interfaces-in-the-editor.md)|Vínculos a documentos que explican cómo tener acceso al editor básico en código existente.|  
|[Creación de diseñadores y editores personalizados](../extensibility/creating-custom-editors-and-designers.md)|Vínculos a documentos que explican cómo crear editores personalizados.|  
|[Extensibilidad de servicio de lenguaje heredado](../extensibility/internals/legacy-language-service-extensibility.md)|Vínculos a documentos que describen cómo integrar los lenguajes de programación en Visual Studio.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Presenta Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Presenta la Windows Presentation Foundation (WPF).|

