---
title: "Implementaci&#243;n de ClickOnce en Windows Vista | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implementación ClickOnce, Windows"
  - "generación de manifiestos"
  - "generación de manifiesto UAC"
  - "Windows, implementación ClickOnce"
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# Implementaci&#243;n de ClickOnce en Windows Vista
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Al compilar aplicaciones en Visual Studio para el Control de cuentas de usuario \(UAC\) en Windows Vista, normalmente se genera un manifiesto incrustado, codificado en forma de datos XML binarios, en el archivo ejecutable de la aplicación.  Dado que las aplicaciones ClickOnce y COM sin registro requieren un manifiesto externo, Visual Studio genera un archivo para estos tipos de proyectos que contiene los datos de UAC en lugar de un manifiesto incrustado.  De forma predeterminada, Visual Studio utiliza información de un archivo denominado app.manifest para generar información del manifiesto de UAC externo \(para implementación de ClickOnce y COM sin registro\), o para incrustarlo en el archivo ejecutable de la aplicación \(en todos los demás casos\).  Visual Studio proporciona las opciones siguientes para la generación de manifiestos:  
  
-   Usar un manifiesto incrustado.  Incruste los datos de UAC en el archivo ejecutable de la aplicación y ejecútelo como un usuario normal.  
  
     Este es el valor predeterminado \(a menos que use ClickOnce\).  Este valor admitirá la forma habitual de funcionamiento de Visual Studio en Windows Vista; es decir, la generación de un manifiesto interno y externo, usando `AsInvoker` ambos manifiestos.  
  
-   Usar un manifiesto externo.  Genere un manifiesto externo utilizando app.manifest.  
  
     Así se genera únicamente el manifiesto externo usando la información en app.manifest.  Cuando se publica una aplicación mediante el uso de ClickOnce o COM sin registro, Visual Studio agrega app.manifest al proyecto y agrega esta opción.  
  
-   No usar ningún manifiesto.  Cree la aplicación sin un manifiesto.  
  
     Este enfoque también se conoce como *virtualización*.  Use esta opción si desea que haya compatibilidad con aplicaciones existentes de versiones anteriores de Visual Studio.  
  
 Las nuevas propiedades están disponibles en la página **Aplicación** del Diseñador de proyectos \(solo para proyectos de Visual C\#\) y en el formato de archivo de proyecto de MSBuild.  
  
 Observe que el método para configurar la generación de manifiestos de UAC en el IDE de Visual Studio difiere en función del tipo de proyecto \(Visual C\# y Visual Basic\).  
  
 Para obtener información sobre cómo configurar proyectos de Visual C\# para la generación de manifiestos, vea [Página de aplicación, Diseñador de proyectos \(C\#\)](../ide/reference/application-page-project-designer-csharp.md).  
  
 Para obtener información sobre cómo configurar proyectos de Visual Basic para la generación de manifiestos, vea [Aplicación \(Página, Diseñador de proyectos\) \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [User Permissions and Visual Studio](http://msdn.microsoft.com/es-es/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Página de aplicación, Diseñador de proyectos \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)   
 [Aplicación \(Página, Diseñador de proyectos\) \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)