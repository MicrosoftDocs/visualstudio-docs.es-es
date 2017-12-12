---
redirect_url: /visualstudio/ide/microsoft-help-viewer
ms.openlocfilehash: c0b1a114eb157860dd70873929727cc56f1d6514
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
title: "Solución de problemas del Visor de Ayuda | Microsoft Docs" ms.custom: "" ms.date: "11/04/2016" ms.reviewer: "" ms.suite: "" ms.technology: 
  - "vs-help-viewer" ms.tgt_pltfrm: "" ms.topic: "article" helpviewer_keywords: 
  - "Solución de problemas [Visor de Ayuda]"
  - "Visor de Ayuda, solución de problemas" ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12 caps.latest.revision: 13 author: "gewarren" ms.author: "gewarren" manager: ghogen
---
# <a name="troubleshooting-the-help-viewer"></a>Solución de problemas del Visor de Ayuda
En este tema se describen los problemas que pueden surgir con el Visor de Ayuda.  
  
## <a name="audio-doesnt-work"></a>El audio no funciona.  
 El Visor de Ayuda no incluye un reproductor de audio. Si descarga contenido que contiene audio y no ocurre nada al elegir **Reproducir**, instale un reproductor de audio.  
  
## <a name="search-doesnt-work-in-windows-server-2008-windows-server-2008-with-sp1-or-windows-server-2008-r2"></a>La búsqueda no funciona en Windows Server 2008, Windows Server 2008 SP1 o Windows Server 2008 R2.  
 Las características de búsqueda y filtrado en el Visor de Ayuda requieren que el servicio de Windows Search esté instalado y activado. De forma predeterminada, este servicio está desactivado en Windows Server 2008, Windows Server 2008 con Service Pack 1 (SP1) y Windows Server 2008 R2.  
  
#### <a name="to-activate-windows-search-service"></a>Para activar el servicio de Windows Search  
  
1.  Inicie el Administrador del servidor.  
  
2.  En el panel de navegación izquierdo, elija **Roles**.  
  
3.  En el panel Resumen de roles, elija **Agregar rol**.  
  
4.  Elija el rol Servicios de archivo y después elija el botón **Siguiente**.  
  
5.  Elija el servicio de rol de Windows Search.  
  
## <a name="additional-resources"></a>Recursos adicionales  
 Puede obtener más información y proporcionar comentarios sobre el Visor de Ayuda mediante los siguientes recursos:  
  
-   Para enviar comentarios, vea [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) en el sitio web de Microsoft o envíe un correo a [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com).  
  
-   Para más información, busque el foro sobre el [sistema de ayuda y documentación para desarrolladores](http://go.microsoft.com/fwlink/?LinkId=232741).  
  
## <a name="see-also"></a>Vea también
[Guía del administrador del Visor de Ayuda](http://go.microsoft.com/fwlink/?LinkId=243985)