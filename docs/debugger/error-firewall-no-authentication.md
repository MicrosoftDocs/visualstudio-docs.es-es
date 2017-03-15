---
title: "Error: Firewall sin autenticaci&#243;n | Microsoft Docs"
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
  - "vs.debug.error.firewall.noauth"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: dda1acb8-bed7-4bc8-9991-9cdc49c2ac1e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Error: Firewall sin autenticaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El firewall de conexión a Internet en el equipo remoto no está configurado para permitir la depuración remota.  Para la depuración remota con `No Authentication`, msvsmon.exe se debe agregar a la lista de excepciones.  Puede que también resulte necesario abrir algunos puertos IPSEC.  
  
> [!NOTE]
>  El depurador remoto puede configurar automáticamente el Firewall de Windows.  Si se utiliza un firewall distinto al Firewall de Windows, por ejemplo software o hardware de terceros, el firewall se debe configurar manualmente para permitir la depuración remota.  Para ello, permita el tráfico en los puertos TCP\/IP en los que escuche msvsmon.exe.  De forma predeterminada, estos son los puertos 4018 y 4019, donde 4018 se utiliza en todos los sistemas operativos y 4019 se usa únicamente en Windows x64 para permitir la depuración de procesos x86.  
  
 Para obtener más información, vea [Configurar las herramientas remotas en el dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).