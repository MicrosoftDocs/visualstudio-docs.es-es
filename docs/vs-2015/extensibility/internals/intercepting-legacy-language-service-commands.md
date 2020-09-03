---
title: Interceptando comandos de servicio de lenguaje heredado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6510df2cc9cc1e504f09af033548e0d1c9b4ae74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195011"
---
# <a name="intercepting-legacy-language-service-commands"></a>Intercepción de comandos del servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , puede hacer que el servicio de lenguaje intercepte los comandos que la vista de texto controlaría de otro modo. Esto resulta útil para el comportamiento específico del lenguaje que no administra la vista de texto. Puede interceptar estos comandos agregando uno o más filtros de comandos a la vista de texto desde el servicio de lenguaje.  
  
## <a name="getting-and-routing-the-command"></a>Obtener y enrutar el comando  
 Un filtro de comandos es un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto que supervisa ciertas secuencias de caracteres o comandos de clave. Puede asociar más de un filtro de comandos a una sola vista de texto. Cada vista de texto mantiene una cadena de filtros de comandos. Después de crear un nuevo filtro de comandos, agregue el filtro a la cadena de la vista de texto correspondiente.  
  
 Llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para agregar el filtro de comandos a la cadena. Cuando se llama a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> , [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] devuelve otro filtro de comandos al que se pueden pasar los comandos que el filtro de comandos no controla.  
  
 Tiene las siguientes opciones para el control de comandos:  
  
- Controle el comando y, a continuación, pase el comando al siguiente filtro de comandos de la cadena.  
  
- Controle el comando y no pase el comando al siguiente filtro de comandos.  
  
- No controle el comando, pero pase el comando al siguiente filtro de comandos.  
  
- Omitir el comando. No lo controle en el filtro actual y no lo pase al siguiente filtro.  
  
  Para obtener información acerca de los comandos que debe controlar el servicio de lenguaje, consulte [comandos importantes para filtros del servicio de lenguaje](../../extensibility/internals/important-commands-for-language-service-filters.md).
