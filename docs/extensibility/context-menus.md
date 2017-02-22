---
title: "Men&#250;s contextuales | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - menús contextuales"
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Men&#250;s contextuales
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se muestran los menús contextuales cuando los clic con el botón secundario de un usuario en un área activa del área cliente y claros cuando se suelta el botón secundario del mouse.  
  
## Menús contextuales del editor  
 Interceptando `ECMD_SHOWCONTEXTMENU`, el servicio de lenguaje puede controlar los menús contextuales que se mostrarán en el editor.  Para mostrar dispone del menú contextual, utilice este comando cuando se pasan en <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>.  Si no controla este comando, después el IDE muestra un menú contextual estándar proporcionado para el editor.  También puede controlar el contenido del menú contextual de por\-marcador.  Para obtener más información al respecto, vea [Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md) y [Intercepción de comandos del servicio de lenguaje heredado](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## Vea también  
 [Desarrollar un servicio de lenguaje](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Comandos y menús de extensión](../extensibility/extending-menus-and-commands.md)