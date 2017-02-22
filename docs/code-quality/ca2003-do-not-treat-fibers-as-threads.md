---
title: "CA2003: No tratar fibras como subprocesos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2003"
  - "DoNotTreatFibersAsThreads"
helpviewer_keywords: 
  - "CA2003"
  - "DoNotTreatFibersAsThreads"
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2003: No tratar fibras como subprocesos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotTreatFibersAsThreads|  
|Identificador de comprobación|CA2003|  
|Categoría|Microsoft.Reliability|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un subproceso administrado se trata como un subproceso de Win32.  
  
## Descripción de la regla  
 No presuponga que un subproceso administrado es un subproceso de Win32.  Es una fibra.  Common Language Runtime \(CLR\) ejecutará los subprocesos administrados como fibras en el contexto de subprocesos reales que posee SQL.  Estos subprocesos se pueden compartir entre los AppDomains e incluso entre las bases de datos en el proceso de SQL Server.  El uso del almacenamiento local de subprocesos administrados funciona, pero no puede utilizarse el almacenamiento local de subprocesos no administrados ni suponerse que el código se vaya a ejecutar de nuevo en el subproceso del SO actual.  No cambie valores como por ejemplo la configuración regional del subproceso.  No llame a CreateCriticalSection ni a CreateMutex mediante P\/Invoke porque requieren que el subproceso que entra en un bloqueo también salga de él.  Dado que esto no sucede cuando se utilizan fibras, las secciones críticas de Win32 y las exclusiones mutuas no tendrán utilidad alguna en SQL.  Puede utilizar sin ningún riesgo la mayor parte del estado en un objeto System.Thread administrado.  Esto incluye el almacenamiento local de subprocesos administrado y la referencia cultural de la interfaz de usuario \(IU\) actual del subproceso.  Sin embargo, a causa del modelo de programación, no podrá cambiar la referencia cultural actual de un subproceso cuando use SQL; esto se lleva a cabo mediante un nuevo permiso.  
  
## Cómo corregir infracciones  
 Examine su uso de los subprocesos y modifique el código en consecuencia.  
  
## Cuándo suprimir advertencias  
 Esta regla no se debe suprimir.