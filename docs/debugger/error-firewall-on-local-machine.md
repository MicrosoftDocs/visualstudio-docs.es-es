---
title: "Error: Firewall en el equipo local | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.firewall.localmachine"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Error: Firewall en el equipo local
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El firewall de conexión a Internet en el equipo local, el equipo donde ejecuta Visual Studio, no está configurado para permitir la depuración remota.  Para una depuración remota administrada o nativa con el transporte predeterminado, el puerto TCP 135 debe estar abierto para el tráfico DCOM.  Compartir impresoras y archivos debe estar abierto y devenv.exe se debe agregar a la lista de excepciones.  Puede que también resulte necesario abrir algunos puertos IPSEC.  
  
 Para obtener más información, vea [Configurar las herramientas remotas en el dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).