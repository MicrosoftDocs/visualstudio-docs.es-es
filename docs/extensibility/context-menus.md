---
title: "Menús contextuales | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 69048a35514ac35556e04ed5266ff58b21b31e0d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="context-menus"></a>Menús contextuales
Menús contextuales se muestran cuando un usuario hace clic con un botón en una región activa del área cliente y borrar cuando se suelta el botón secundario del mouse.  
  
## <a name="editor-context-menus"></a>Menús contextuales del editor  
 Interceptando `ECMD_SHOWCONTEXTMENU`, el servicio de lenguaje puede controlar los menús contextuales que aparecerá en el editor. Para mostrar su propio menú contextual, controlar este comando cuando se pasa a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Si no controla este comando, el IDE muestra un menú contextual estándar proporcionado para el editor. También puede controlar el contenido del menú contextual en una base por marcador. Para obtener más información sobre esto, consulte [usar marcadores de texto con la API heredado](../extensibility/using-text-markers-with-the-legacy-api.md) y [interceptando comandos del servicio de lenguaje heredado](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar un servicio de lenguaje heredado](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Ampliación de menús y comandos](../extensibility/extending-menus-and-commands.md)