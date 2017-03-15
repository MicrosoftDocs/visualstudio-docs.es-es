---
title: "TargetCLR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# TargetCLR
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción **TargetCLR** especifica la versión de Common Language Runtime \(CLR\) para la generación de perfiles cuando se carga más de una versión de CLR en una aplicación.  
  
 De manera predeterminada, las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se dirigen a la primera versión de CLR cargada por la aplicación.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### Parámetros  
 `ClrVersion`  
 Número de versión de CLR.  Utilice el formato de versión **vN.N.NNNNN**.  
  
## Opciones necesarias  
 La opción **TargetCLR** solamente se puede usar con las opciones **Launch** o **Attach**.  
  
 **Launch:** `AppName`  
 Inicia la aplicación especificada y la generación de perfiles.  
  
 **Attach:** `PID`  
 Empieza a generar perfiles para el proceso especificado.  
  
## Ejemplo  
 En este ejemplo, la opción TargetCLR se utiliza para asegurarse de que se realiza la generación de perfiles para la versión 4.0.11003 de CLR.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```