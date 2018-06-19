---
title: Interceptar comandos del servicio de lenguaje heredado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 38f025e9dab6f93d87660a59421cbd778c92165a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129123"
---
# <a name="intercepting-legacy-language-service-commands"></a>Interceptar comandos del servicio de lenguaje heredado
Con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], puede hacer que los comandos de intercept de servicio de lenguaje que en caso contrario, controlaría la vista de texto. Esto es útil para el comportamiento específico del idioma que no administra la vista de texto. Puede interceptar estos comandos mediante la adición de uno o más filtros de comandos a la vista de texto de su servicio de lenguaje.  
  
## <a name="getting-and-routing-the-command"></a>Obtener y enrutamiento el comando  
 Un filtro de comandos es un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objetos que supervisa de ciertas secuencias de caracteres o los comandos de teclas. Puede asociar más de un filtro de comandos a una vista de solo texto. Cada vista de texto mantiene los filtros de una cadena de comando. Después de crear un nuevo filtro de comandos, agregue el filtro a la cadena para la vista de texto adecuado.  
  
 Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para agregar el filtro de comando a la cadena. Cuando se llama a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] devuelve otro filtro de comandos a la que se pueden pasar los comandos que no controla el filtro de comando.  
  
 Tiene las siguientes opciones para la gestión de comandos:  
  
-   Controlar el comando y, a continuación, pasar el comando en el siguiente filtro de comandos en la cadena.  
  
-   Controlar el comando y no pasan el comando en el siguiente filtro de comandos.  
  
-   No se debe administrar el comando, pero pasar el comando en el siguiente filtro de comandos.  
  
-   Pasar por alto el comando. No se controlan en el filtro actual y no la pasa al siguiente filtro.  
  
 Para obtener información acerca de los comandos que se debe administrar el servicio de lenguaje, vea [comandos importantes para los filtros de servicio de lenguaje](../../extensibility/internals/important-commands-for-language-service-filters.md).