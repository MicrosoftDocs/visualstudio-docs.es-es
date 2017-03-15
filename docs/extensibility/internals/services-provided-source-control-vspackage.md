---
title: "Servicios proporcionados (VSPackage del Control de c&#243;digo fuente) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Servicios de paquetes de control de código fuente"
  - "paquetes de control de código fuente, servicios"
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Servicios proporcionados (VSPackage del Control de c&#243;digo fuente)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los servicios son el mecanismo principal a través del que la funcionalidad se comparte entre VSPackages y entre el entorno de desarrollo integrado de \(IDE\) Visual Studio y su VSPackages instalado.  Para la descripción detallada de servicios y de importancia en el IDE de Visual Studio, vea[Utilizar y proporcionar servicios](../../extensibility/using-and-providing-services.md).  
  
## El servicio de control de código fuente  
 Visual Studio proporciona dos niveles de servicios, servicios de IDE\-nivel y servicios de paquete\-nivel.  El IDE de Visual Studio proporciona nativo servicios de IDE\-nivel.  El paquete de control de código fuente utiliza algunos de estos servicios.  El paquete de control de código fuente como VSPackage comparte su funcionalidad de control de código fuente proporcionando un servicio privado de control de código fuente específicas.  El paquete de control de código fuente encapsula el conjunto de interfaces CONTROL\-relacionadas de origen implementadas por ella en forma de contrato que se puede utilizar en el IDE de Visual Studio.  
  
## Vea también  
 [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)