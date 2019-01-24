---
title: Menús contextuales | Microsoft Docs
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
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: efd4e1c80b9af2a0d73730f0bd7d741cd877fb07
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796849"
---
# <a name="context-menus"></a>Menús contextuales
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Menús contextuales se muestran cuando un usuario del botón secundario en una región activa del área de cliente y borrar cuando se suelta el botón secundario del mouse.  
  
## <a name="editor-context-menus"></a>Menús contextuales del editor  
 Mediante la interceptación `ECMD_SHOWCONTEXTMENU`, el servicio de lenguaje puede controlar los menús contextuales que se mostrarán en el editor. Para mostrar su propio menú contextual, controlar este comando cuando se pasa en su <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Si no controla este comando, el IDE muestra un menú estándar de contexto proporcionado para el editor. También puede controlar el contenido del menú contextual en una base por marcador. Para obtener más información al respecto, consulte [utilizando marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md) y [intercepción de comandos del servicio de lenguaje heredado](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar un servicio de lenguaje heredado](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Ampliación de menús y comandos](../extensibility/extending-menus-and-commands.md)

