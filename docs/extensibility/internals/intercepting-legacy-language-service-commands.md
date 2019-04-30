---
title: Intercepción de comandos del servicio de lenguaje heredado | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eb53de9cf4d3056d9a07a915267391de27b753fb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909619"
---
# <a name="intercepting-legacy-language-service-commands"></a>Intercepción de comandos del servicio de lenguaje heredado
Con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], puede tener los comandos de corte del servicio de lenguaje en caso contrario, controlaría la vista de texto. Esto es útil para el comportamiento específico del idioma que no administra la vista de texto. Puede interceptar estos comandos mediante la adición de uno o varios filtros de comandos para la vista de texto desde el servicio de lenguaje.

## <a name="getting-and-routing-the-command"></a>Introducción y el comando de enrutamiento
 Un filtro de comandos es un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto que controla ciertas secuencias de caracteres o comandos de teclas. Puede asociar más de un filtro de comando con una vista de texto única. Cada vista de texto mantiene una cadena de filtros de comandos. Después de crear un nuevo filtro de comando, agregue el filtro a la cadena para la vista de texto adecuado.

 Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para agregar el filtro de comando a la cadena. Cuando se llama a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] devuelve otro filtro de comando a la que puede pasar los comandos que no controla el filtro de comando.

 Tiene las siguientes opciones para la gestión de comandos:

- Controlar el comando y, a continuación, pasar el comando de la sesión en el siguiente filtro de comandos en la cadena.

- Controlar el comando y no pasan el comando de la sesión en el siguiente filtro de comandos.

- No controla el comando, pero pasar el comando de la sesión en el siguiente filtro de comandos.

- Pasar por alto el comando. No se controlan en el filtro actual y no la pasa al siguiente filtro.

  Para obtener información acerca de los comandos que debe controlar el servicio de lenguaje, vea [comandos importantes para los filtros de servicio de lenguaje](../../extensibility/internals/important-commands-for-language-service-filters.md).