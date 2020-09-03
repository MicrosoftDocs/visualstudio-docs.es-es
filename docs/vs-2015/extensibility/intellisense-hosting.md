---
title: Hospedaje de IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5c378aec6822a436de0d8fc2656fcac7be4149f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203896"
---
# <a name="intellisense-hosting"></a>Hospedaje de IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio permite el hospedaje de IntelliSense. El hospedaje de IntellSense permite proporcionar IntelliSense para el código que no está hospedado en el editor de texto de Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Uso de hospedaje de IntelliSense  
 En Visual Studio, cualquier código que tenga acceso a un conjunto de finalizaciones y un búfer de texto puede obtener ventanas de IntelliSense desde cualquier lugar de la interfaz de usuario (UI). Algunos escenarios de ejemplo de esto son la finalización en la ventana **inspección** o en el campo condición de una ventana Propiedades de punto de interrupción.  
  
### <a name="implementation-interfaces"></a>Interfaces de implementación  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Cualquier componente de la interfaz de usuario que hospede ventanas emergentes de IntelliSense debe ser compatible con la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaz. La vista de texto del editor principal predeterminado incluye una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> implementación de la interfaz estándar para conservar la funcionalidad actual de IntelliSense. En su mayor parte, los métodos de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaz representan un subconjunto de lo que se implementa en la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz. El subconjunto incluye el control de la interfaz de usuario de IntelliSense, el símbolo de intercalación y la manipulación de selección y la funcionalidad de reemplazo de texto Además, la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaz permite separar IntelliSense "asunto" y "contexto" para que se pueda proporcionar IntelliSense para los sujetos que no existen directamente en el búfer de texto que se usa para el contexto.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 Un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> proveedor de interfaz debe implementar el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> método para permitir que un cliente determine qué tipo de características de IntelliSense admite el host.  
  
 A continuación se resumen las marcas de host, definidas en [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md).  
  
|Marca de host de IntelliSense|Descripción|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|La configuración de esta marca significa que el búfer de contexto es de solo lectura y la edición solo se produce en el texto del asunto.|  
|IHF_NOSEPERATESUBJECT|Establecer esta marca significa que no hay ningún asunto independiente de IntelliSense. El sujeto existe en el búfer de contexto, como en el sistema tradicional de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> IntelliSense.|  
|IHF_SINGLELINESUBJECT|Establecer esta marca significa que el sujeto no es compatible con varias líneas, por ejemplo, en una edición de una sola línea en la ventana **inspección** .|  
|IHF_FORCECOMMITTOCONTEXT|Si se establece esta marca y se debe actualizar el búfer de contexto, el host permite omitir la marca de solo lectura en el búfer de contexto y editar para continuar.|  
|IHF_OVERTYPE|La edición (en asunto o contexto) debe realizarse en modo de sobretipo.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost. BeforeCompletorCommit y IVsIntellisenseHost. AfterCompletorCommit  
 La ventana de finalización llama a estos métodos de devolución de llamada antes y después de confirmar el texto para habilitar el procesamiento previo y el procesamiento posterior.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> interfaz es una versión cocreatable de la ventana de finalización estándar que usa el entorno de desarrollo integrado (IDE). Cualquier <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaz puede implementar rápidamente IntelliSense mediante el uso de esta interfaz de completor.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
