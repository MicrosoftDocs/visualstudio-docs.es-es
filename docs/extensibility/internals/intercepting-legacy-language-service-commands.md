---
title: Interceptando comandos de servicio de lenguaje heredado | Microsoft Docs
description: Obtenga información sobre cómo usar los filtros de comandos en Visual Studio para interceptar comandos del servicio de lenguaje heredado y agregar un comportamiento específico del lenguaje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8d7af9ff4a8f04382cff4999b8c57549f3da3db7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074696"
---
# <a name="intercepting-legacy-language-service-commands"></a>Intercepción de comandos del servicio de lenguaje heredado
Con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , puede hacer que el servicio de lenguaje intercepte los comandos que la vista de texto controlaría de otro modo. Esto resulta útil para el comportamiento específico del lenguaje que no administra la vista de texto. Puede interceptar estos comandos agregando uno o más filtros de comandos a la vista de texto desde el servicio de lenguaje.

## <a name="getting-and-routing-the-command"></a>Obtener y enrutar el comando
 Un filtro de comandos es un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto que supervisa ciertas secuencias de caracteres o comandos de clave. Puede asociar más de un filtro de comandos a una sola vista de texto. Cada vista de texto mantiene una cadena de filtros de comandos. Después de crear un nuevo filtro de comandos, agregue el filtro a la cadena de la vista de texto correspondiente.

 Llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para agregar el filtro de comandos a la cadena. Cuando se llama a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> , [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] devuelve otro filtro de comandos al que se pueden pasar los comandos que el filtro de comandos no controla.

 Tiene las siguientes opciones para el control de comandos:

- Controle el comando y, a continuación, pase el comando al siguiente filtro de comandos de la cadena.

- Controle el comando y no pase el comando al siguiente filtro de comandos.

- No controle el comando, pero pase el comando al siguiente filtro de comandos.

- Omitir el comando. No lo controle en el filtro actual y no lo pase al siguiente filtro.

  Para obtener información acerca de los comandos que debe controlar el servicio de lenguaje, consulte [comandos importantes para filtros del servicio de lenguaje](../../extensibility/internals/important-commands-for-language-service-filters.md).
