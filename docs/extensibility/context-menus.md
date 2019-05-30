---
title: Menús contextuales | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5534d0895e35e252364b491858a694a1f5b726a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341729"
---
# <a name="context-menus"></a>Menús contextuales
Menús contextuales se muestran cuando un usuario del botón secundario en una región activa del área de cliente y borrar cuando se suelta el botón secundario del mouse.

## <a name="editor-context-menus"></a>Menús contextuales del Editor
 Mediante la interceptación `ECMD_SHOWCONTEXTMENU`, el servicio de lenguaje puede controlar los menús contextuales que se mostrarán en el editor. Para mostrar su propio menú contextual, controlar este comando cuando se pasa en su <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Si no controla este comando, el IDE muestra un menú estándar de contexto proporcionado para el editor. También puede controlar el contenido del menú contextual en una base por marcador. Para obtener más información al respecto, consulte [usar marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md) y [interceptar los comandos del servicio de lenguaje heredado](../extensibility/internals/intercepting-legacy-language-service-commands.md).

## <a name="see-also"></a>Vea también
- [Desarrollar un servicio de lenguaje heredado](../extensibility/internals/developing-a-legacy-language-service.md)
- [Extender los menús y comandos](../extensibility/extending-menus-and-commands.md)