---
title: "Tareas Editar y Continuar no admitidas para F# | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Depurar [F#], Editar y continuar"
  - "Editar y continuar [F#]"
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Tareas Editar y Continuar no admitidas para F# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

No se admite Editar y continuar al depurar código de F\#.  Es posible editar código de F\# durante una sesión de depuración pero se debería evitar.  Los cambios de código no se aplican durante la sesión de depuración.  Por consiguiente, si se realizan cambios en el código de F\# durante la depuración, el código fuente no se corresponderá con el código objeto de la depuración.