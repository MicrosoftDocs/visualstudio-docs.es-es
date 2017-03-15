---
title: "C&#243;mo: Cambiar el espacio de nombres de los lenguajes espec&#237;ficos de dominio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, espacio de nombres"
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 19
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 19
---
# C&#243;mo: Cambiar el espacio de nombres de los lenguajes espec&#237;ficos de dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede cambiar el espacio de nombres de un lenguaje específico.  Debe realizar el cambio en **Explorador ADSL**, en las propiedades del proyecto paquete de DSL, y del ensamblado.  
  
### Para cambiar el espacio de nombres de un lenguaje específico  
  
1.  En **Explorador ADSL**, haga clic en el nodo de **DSL** .  
  
2.  en la ventana de **Propiedades** , cambie la propiedad de **espacio de nombres** .  
  
3.  Guarde la solución y transformar plantillas.  
  
4.  En el menú de **proyecto** , haga clic **Propiedades del ADSL**.  
  
     Aparecerán las propiedades del proyecto.  
  
5.  Haga clic en la ficha **Aplicación**.  
  
6.  Cambie la propiedad de **espacio de nombres predeterminado** al nuevo espacio de nombres.  
  
7.  Si también desea cambiar el nombre del ensamblado, cambie **Propiedad del nombre del ensamblado.**  
  
8.  Si ha cambiado el nombre, DslPackage abierto \\Package .tt y ha actualizado esta línea:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Si ha escrito código personalizado, asegúrese de cambiar las referencias de espacio de nombres y la clase en los archivos de código.  
  
10. restablezca la instancia de Visual Studio Experimental.  
  
    1.  elimine **\\Users\\***{el nombre}***\\AppData\\Local\\Microsoft\\VisualStudio\\\*Exp**  
  
    2.  en el menú de Windows **Iniciar** , elija **Todos los programas**, **Microsoft Visual Studio 2010 SDK**, **Herramientas**, **Restablezca la instancia Experimental de**.  
  
11. en el menú de **Generar** , elija **Volver a generar solución**.  
  
## Vea también  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/es-es/ca5e84cb-a315-465c-be24-76aa3df276aa)