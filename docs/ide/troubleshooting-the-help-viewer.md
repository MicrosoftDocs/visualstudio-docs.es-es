---
title: "Soluci&#243;n de problemas del Visor de Ayuda | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visor de Ayuda 2.0, solucionar problemas"
  - "solución de problemas [Visor de Ayuda 2.0]"
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Soluci&#243;n de problemas del Visor de Ayuda
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se describen los problemas que pueden producirse con el Visor de Ayuda.  
  
## El audio no funciona.  
 El Visor de Ayuda no incluye un reproductor de audio.  Si descarga contenido que contiene audio y no sucede nada al elegir **Reproducir**, instale un reproductor de audio.  
  
## La búsqueda no funciona en Windows Server 2008, Windows Server 2008 con SP1 o Windows Server 2008 R2.  
 Las características de búsqueda y filtro del Visor de Ayuda necesitan que el servicio Windows Search esté instalado y activado.  De forma predeterminada, este servicio está desactivado en Windows Server 2008, Windows Server 2008 con Service Pack 1 \(SP1\) y Windows Server 2008 R2.  
  
#### Para activar el servicio Windows Search  
  
1.  Inicie el Administrador del servidor.  
  
2.  En el panel de navegación izquierdo, elija **Roles**.  
  
3.  En el panel Resumen de roles, elija **Agregar rol**.  
  
4.  Elija el rol Servicios de archivo y, a continuación, elija el botón **Siguiente**.  
  
5.  Elija el servicio de roles del servicio Windows Search.  
  
## Recursos adicionales  
 Puede obtener más información y proporcionar comentarios sobre el Visor de Ayuda mediante los recursos siguientes:  
  
-   Para proporcionar comentarios, vea [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) en el sitio web de Microsoft o envíe un correo electrónico a [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com).  
  
-   Para obtener más información, vea el foro [Sistema de ayuda y documentación para desarrolladores](http://go.microsoft.com/fwlink/?LinkId=232741) y el blog [Profesionales de la ayuda](http://go.microsoft.com/fwlink/?LinkId=232743).  
  
## Vea también  
 [Guía del administrador del Visor de Ayuda 2.1](http://go.microsoft.com/fwlink/?LinkId=243985)