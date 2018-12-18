---
title: Hospedaje de IntelliSense | Microsoft Docs
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
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7e6ae688c0af3506f3d77cf2c1bac5291595b80
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737873"
---
# <a name="intellisense-hosting"></a>Hospedaje de IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio permite hospedar de IntelliSense. IntellSense hospedaje permite proporcionar IntelliSense para el código que no se hospeda en el editor de texto de Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Uso de hospedaje de IntelliSense  
 En Visual Studio, cualquier código que tenga acceso a un conjunto de finalizaciones y un búfer de texto puede obtener windows IntelliSense desde cualquier lugar en la interfaz de usuario (UI). Algunos escenarios de ejemplo de esto son la finalización en el **inspección** ventana o en el campo de condición de una ventana de propiedades de punto de interrupción.  
  
### <a name="implementation-interfaces"></a>Interfaces de implementación  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Cualquier componente de interfaz de usuario que hospeda las ventanas emergentes de IntelliSense debe admitir la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaz. La vista de texto predeterminado del editor de core incluye una acción <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> implementación para conservar la funcionalidad de IntelliSense actual de la interfaz. En su mayor parte, los métodos de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> representan un subconjunto de lo que se implementa en la interfaz del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz. El subconjunto incluye IntelliSense UI control, símbolo de intercalación y manipulación de selección y la funcionalidad de reemplazo de texto simple. Además, el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaz posibilita independiente IntelliSense "asunto" y "contexto", lo que se puede proporcionar IntelliSense para los temas que no existen directamente en el búfer de texto que se utiliza para el contexto.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 Un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaz proveedor debe implementar la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> admite el método para permitir que un cliente determinar qué tipo de IntelliSense incluye el host.  
  
 Las marcas de host definidas en [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), se resumen a continuación.  
  
|Marca de Host de IntelliSense|Descripción|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Establecer esta marca decir el búfer de contexto es de solo lectura y edición se producen solo dentro del texto de asunto.|  
|IHF_NOSEPERATESUBJECT|Establecer esto significa que la marca que existe no es ningún asunto independiente de IntelliSense. El asunto existe en el búfer de contexto, como en el tradicional <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> sistema IntelliSense.|  
|IHF_SINGLELINESUBJECT|Establecer esta marca decir el sujeto no es multilínea capaz, como en una sola línea editar en el **inspección** ventana.|  
|IHF_FORCECOMMITTOCONTEXT|Si se establece este marcador y el búfer de contexto debe actualizarse, el host habilita la marca de solo lectura en el búfer de contexto se pasará por alto y modificaciones para continuar.|  
|IHF_OVERTYPE|Edición (en el asunto o el contexto) debe realizarse en modo de reemplazo.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit y IVsIntellisenseHost.AfterCompletorCommit  
 La ventana de finalización llama a estos métodos de devolución de llamada antes y después se confirma, para habilitar el procesamiento previo y posterior al procesamiento de texto.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> interfaz es una versión compartida que se pueden crear de la ventana de finalización estándar que usa el entorno de desarrollo integrado (IDE). Cualquier <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaz puede implementar rápidamente IntelliSense mediante esta interfaz completor.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop>

