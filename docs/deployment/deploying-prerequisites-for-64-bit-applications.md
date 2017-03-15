---
title: "Implementar requisitos previos de aplicaciones de 64 bits | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "64 bits [Visual Studio]"
  - "aplicaciones de 64 bits [Visual Studio]"
  - "programación de 64 bits [Visual Studio]"
  - "implementar aplicaciones [Visual Studio], 64 bits"
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Implementar requisitos previos de aplicaciones de 64 bits
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La implementación de ClickOnce admite la instalación de aplicaciones en plataformas de 64 bits.  Las plataformas de destino son **x86** para plataformas de 32 bits, **x64** para máquinas que admiten los conjuntos de instrucciones de AMD64 y EM64T, e **Itanium** para el procesador Itanium de 64 bits.  
  
## Requisitos previos  
 En la tabla siguiente se enumeran los redistribuibles que puede usar como requisitos previos para la instalación de su aplicación de 64 bits.  
  
 Si selecciona un requisito previo que no tiene componentes de 64 bits, podría ver una advertencia que indica que los paquetes seleccionados no están disponibles para la plataforma de 64 bits.  
  
|Redistribuible|Compatibilidad con x64|Compatibilidad con IA64|  
|--------------------|----------------------------|-----------------------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|Sí|No|  
|Bibliotecas en tiempo de ejecución de Visual C\+\+ 2010 \(IA64\)|No|Sí|  
|Bibliotecas en tiempo de ejecución de Visual C\+\+ 2010 \(x64\)|Sí|No|  
|Microsoft .NET Framework 4 \(x86 y x64\)|Sí||  
|Microsoft .NET Framework 4 Client Profile \(x86 y x64\)|Sí||  
  
## Vea también  
 [Implementar aplicaciones, servicios y componentes](../deployment/deploying-applications-services-and-components.md)   
 [Cómo: Instalar requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Aplicaciones de 64 bits](../Topic/64-bit%20Applications.md)