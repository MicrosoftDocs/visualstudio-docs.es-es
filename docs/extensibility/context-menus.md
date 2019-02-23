---
title: Menús contextuales | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19838bbc1dfeeb0a0df9e1e1ce409557b6a28f1e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722384"
---
# <a name="context-menus"></a>Menús contextuales
Menús contextuales se muestran cuando un usuario del botón secundario en una región activa del área de cliente y borrar cuando se suelta el botón secundario del mouse.

## <a name="editor-context-menus"></a>Menús contextuales del Editor
 Mediante la interceptación `ECMD_SHOWCONTEXTMENU`, el servicio de lenguaje puede controlar los menús contextuales que se mostrarán en el editor. Para mostrar su propio menú contextual, controlar este comando cuando se pasa en su <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Si no controla este comando, el IDE muestra un menú estándar de contexto proporcionado para el editor. También puede controlar el contenido del menú contextual en una base por marcador. Para obtener más información al respecto, consulte [usar marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md) y [interceptar los comandos del servicio de lenguaje heredado](../extensibility/internals/intercepting-legacy-language-service-commands.md).

## <a name="see-also"></a>Vea también
- [Desarrollar un servicio de lenguaje heredado](../extensibility/internals/developing-a-legacy-language-service.md)
- [Extender los menús y comandos](../extensibility/extending-menus-and-commands.md)