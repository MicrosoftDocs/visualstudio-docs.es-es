---
title: "Depuraci&#243;n y proceso host | Microsoft Docs"
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
  - "depurar [Visual Studio], proceso de alojamiento"
  - "proceso de alojamiento"
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depuraci&#243;n y proceso host
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El proceso host de Visual Studio mejora el rendimiento del depurador y permite ofrecer nuevas características de depuración, como la depuración de confianza parcial y la evaluación de expresiones en tiempo de diseño. Si es necesario, puede deshabilitar el proceso host. Para obtener más información, consulta [Cómo: Deshabilitar el proceso de alojamiento](../ide/how-to-disable-the-hosting-process.md). En las secciones siguientes se describen algunas diferencias entre la depuración con y sin el proceso host.  
  
## Depuración de confianza parcial y seguridad Click Once  
 La depuración de confianza parcial requiere el proceso host. Si se deshabilita el proceso host, la depuración de confianza parcial no funcionará aunque la seguridad de confianza parcial esté habilitada en la página **Seguridad** de **Propiedades del proyecto**. Para obtener más información, vea [Cómo: Deshabilitar el proceso de alojamiento](../ide/how-to-disable-the-hosting-process.md) y [Cómo: Depurar una aplicación de confianza parcial](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## Evaluación de expresiones en tiempo de diseño  
 La expresión en tiempo de diseño siempre utiliza el proceso host. Al deshabilitar el proceso host en **Propiedades del proyecto**, se deshabilita la evaluación de expresiones en tiempo de diseño para los proyectos de biblioteca de clases. Para otros tipos de proyecto, la evaluación de expresiones en tiempo de diseño no se deshabilita. En vez de esto, Visual Studio inicia el archivo ejecutable real y lo utiliza para la evaluación en tiempo de diseño sin el proceso host. Esta diferencia podría generar resultados diferentes.  
  
## Diferencias de AppDomain.CurrentDomain.FriendlyName  
 `AppDomain.CurrentDomain.FriendlyName` devuelve resultados diferentes que dependen de si está habilitado el proceso host. Si se llama a `AppDomain.CurrentDomain.FriendlyName` con el proceso de host habilitado, devuelve *app\_name*`.vhost.exe`. Si se llama con el proceso de host deshabilitado, devuelve *app\_name*`.exe`.  
  
## Diferencias de Assembly.GetCallingAssembly \(\).FullName  
 `Assembly.GetCallingAssembly().FullName` devuelve resultados diferentes que dependen de si está habilitado el proceso host. Si se llama a `Assembly.GetCallingAssembly().FullName` con el proceso host habilitado, devuelve `mscorlib`. Si se llama a `Assembly.GetCallingAssembly().FullName` con el proceso host deshabilitado, devuelve el nombre de la aplicación.  
  
## Vea también  
 [Proceso de alojamiento \(vshost.exe\)](../ide/hosting-process-vshost-exe.md)   
 [Cómo: Depurar una aplicación de confianza parcial](../debugger/how-to-debug-a-partial-trust-application.md)   
 [Cómo: Deshabilitar el proceso de alojamiento](../ide/how-to-disable-the-hosting-process.md)