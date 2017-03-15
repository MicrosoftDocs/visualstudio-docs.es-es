---
title: "COM Interop registration failed | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_register_com2"
ms.assetid: d1b81f8e-66d7-4cfc-96ff-f1436a8f854a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# COM Interop registration failed
Hay un error en el registro de un ensamblado que expone funcionalidades a clientes COM.  El proceso de compilación no finalizará correctamente si ocurre este error.  
  
 Los ensamblados pueden exponer objetos a los clientes COM.  El sistema del proyecto proporciona una propiedad para registrar clases expuestas para interoperabilidad COM, así como para generar y registrar una biblioteca de tipos, de forma que estas clases se puedan utilizar en los lenguajes de scripting y en Visual Basic 6.  
  
 Vea la página de propiedades **Compilar** en la carpeta **Propiedades de configuración** para obtener acceso a la propiedad **Registrar para interoperabilidad COM**.  
  
 Entre las posibles razones del error se incluyen:  
  
-   Incapacidad para generar una biblioteca de tipos para el ensamblado.  Puede que se trate de un problema de espacio en el disco o de un problema de bloqueo de archivos en el que Visual Studio o algún otro proceso bloquea la biblioteca de tipos.  Además, puede que las bibliotecas de tipos para los ensamblados a los que se hace referencia no se registren correctamente en el sistema.  
  
-   Incapacidad para registrar la biblioteca de tipos generada.  Puede que se trate de un problema de permisos en el Registro.  
  
-   Incapacidad para registrar clases en el ensamblado.  Puede que se trate de un problema de permisos en el Registro.  
  
 **Para corregir este error**  
  
-   Cree espacio disponible en disco en el equipo.  
  
-   Si existe un problema de bloqueo de archivos, reinicie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Asegúrese de que inicia la sesión como administrador o como miembro de un grupo que tenga acceso al Registro.  
  
## Vea también  
 [Interoperabilidad COM en aplicaciones .NET Framework](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)