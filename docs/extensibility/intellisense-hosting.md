---
title: Hospedaje de IntelliSense | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9727b6fcbe3c552273ca521e8fd14ab5e5181eb7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="intellisense-hosting"></a>Hospedaje de IntelliSense
Visual Studio permite hospedar de IntelliSense. IntellSense hospedaje permite proporcionar IntelliSense para el código que no esté hospedado por el editor de texto de Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Uso de hospedaje de IntelliSense  
 En Visual Studio, cualquier código que tenga acceso a un conjunto de finalización y un búfer de texto puede obtener windows IntelliSense desde cualquier lugar en la interfaz de usuario (UI). Algunos escenarios de ejemplo de esto son la finalización en el **inspección** ventana o en el campo de condición de una ventana de propiedades de punto de interrupción.  
  
### <a name="implementation-interfaces"></a>Interfaces de implementación  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Cualquier componente de interfaz de usuario que hospeda las ventanas emergentes de IntelliSense debe admitir la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaz. La vista de texto predeterminada core editor incluye un material <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> implementación para conservar la funcionalidad de IntelliSense actual de la interfaz. En su mayor parte, los métodos de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaz representan un subconjunto de lo que se implementa en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz. El subconjunto incluye control de IntelliSense UI, símbolo de intercalación y manipulación de selección y funcionalidad de reemplazo de texto simple. Además, la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaz permite independiente IntelliSense "subject" y "context" de manera que puede proporcionar IntelliSense para asuntos que no existen directamente en el búfer de texto que se utiliza para el contexto.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 Un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaz proveedor debe implementar la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> admite el método para permitir a un cliente determinar qué tipo de IntelliSense características del host.  
  
 Las marcas de host, definidas en [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), a continuación se resumen.  
  
|Marca de Host de IntelliSense|Descripción|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Si establece esta, marca que el búfer de contexto es de solo lectura y edición se produce solo en el texto de asunto.|  
|IHF_NOSEPERATESUBJECT|Si establece esta marca, no existe no es asunto de IntelliSense independiente. El asunto está en el búfer de contexto, como en tradicional <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> sistema IntelliSense.|  
|IHF_SINGLELINESUBJECT|Si establece esta, marca que el sujeto no es de varias líneas capaz, como en una sola línea de edición en el **inspección** ventana.|  
|IHF_FORCECOMMITTOCONTEXT|Si se establece esta marca y debe actualizarse al búfer de contexto, el host habilita la marca de solo lectura en el búfer de contexto que se omitan y modificaciones para continuar.|  
|IHF_OVERTYPE|Editar (en el asunto o el contexto) debe realizarse en el modo de sobrescribir.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit y IVsIntellisenseHost.AfterCompletorCommit  
 Se llama a estos métodos de devolución de llamada mediante la ventana de finalización antes y después de texto se confirma, para habilitar el procesamiento previo y posterior a la.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> interfaz es una versión puede co-crear de la ventana de finalización estándar utilizado por el entorno de desarrollo integrado (IDE). Cualquier <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaz puede implementar rápidamente IntelliSense mediante esta interfaz completor.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop>