---
title: Interceptando comandos de servicio de lenguaje heredados ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5206bced8b4bfae32498434765e5c3f61801b386
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707453"
---
# <a name="intercepting-legacy-language-service-commands"></a>Intercepción de comandos del servicio de lenguaje heredado
Con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], puede tener los comandos de interceptación del servicio de lenguaje que la vista de texto manejaría de otro modo. Esto es útil para el comportamiento específico del idioma que la vista de texto no administra. Puede interceptar estos comandos agregando uno o varios filtros de comandos a la vista de texto desde el servicio de lenguaje.

## <a name="getting-and-routing-the-command"></a>Obtención y enrutamiento del comando
 Un filtro de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> comandos es un objeto que supervisa determinadas secuencias de caracteres o comandos de teclado. Puede asociar más de un filtro de comandos a una sola vista de texto. Cada vista de texto mantiene una cadena de filtros de comandos. Después de crear un nuevo filtro de comandos, agregue el filtro a la cadena para la vista de texto adecuada.

 Llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> en el para agregar el filtro de comandos a la cadena. Cuando se <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] llama a , devuelve otro filtro de comandos al que puede pasar los comandos que el filtro de comandos no controla.

 Dispone de las siguientes opciones para el control de comandos:

- Controle el comando y, a continuación, pase el comando al siguiente filtro de comandos de la cadena.

- Controle el comando y no pase el comando al siguiente filtro de comandos.

- No controle el comando, pero pase el comando al siguiente filtro de comandos.

- Ignore el comando. No lo maneje en el filtro actual y no lo pase al siguiente filtro.

  Para obtener información sobre qué comandos debe controlar el servicio de lenguaje, consulte [Comandos importantes para filtros](../../extensibility/internals/important-commands-for-language-service-filters.md)de servicio de lenguaje .
