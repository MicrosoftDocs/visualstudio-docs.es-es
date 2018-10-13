---
title: Intercepción de comandos del servicio de lenguaje heredado | Documentos de Microsoft
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
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 96a641778811d88c0087a23822ab789e72b066f0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190013"
---
# <a name="intercepting-legacy-language-service-commands"></a>Intercepción de comandos del servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], puede tener los comandos de corte del servicio de lenguaje en caso contrario, controlaría la vista de texto. Esto es útil para el comportamiento específico del idioma que no administra la vista de texto. Puede interceptar estos comandos mediante la adición de uno o varios filtros de comandos para la vista de texto desde el servicio de lenguaje.  
  
## <a name="getting-and-routing-the-command"></a>Introducción y el comando de enrutamiento  
 Un filtro de comandos es un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto que controla ciertas secuencias de caracteres o comandos de teclas. Puede asociar más de un filtro de comando con una vista de texto única. Cada vista de texto mantiene una cadena de filtros de comandos. Después de crear un nuevo filtro de comando, agregue el filtro a la cadena para la vista de texto adecuado.  
  
 Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para agregar el filtro de comando a la cadena. Cuando se llama a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] devuelve otro filtro de comando a la que puede pasar los comandos que no controla el filtro de comando.  
  
 Tiene las siguientes opciones para la gestión de comandos:  
  
-   Controlar el comando y, a continuación, pasar el comando de la sesión en el siguiente filtro de comandos en la cadena.  
  
-   Controlar el comando y no pasan el comando de la sesión en el siguiente filtro de comandos.  
  
-   No controla el comando, pero pasar el comando de la sesión en el siguiente filtro de comandos.  
  
-   Pasar por alto el comando. No se controlan en el filtro actual y no la pasa al siguiente filtro.  
  
 Para obtener información acerca de los comandos que debe controlar el servicio de lenguaje, vea [comandos importantes para los filtros de servicio de lenguaje](../../extensibility/internals/important-commands-for-language-service-filters.md).

