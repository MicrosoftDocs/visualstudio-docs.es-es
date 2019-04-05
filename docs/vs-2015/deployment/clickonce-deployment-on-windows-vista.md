---
title: Implementación de ClickOnce en Windows Vista | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 15af68e52a902003cd483cb6705ab4ded947f1a2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996871"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Implementación de ClickOnce en Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Creación de aplicaciones en Visual Studio para Control de cuentas de usuario (UAC) en Windows Vista normalmente genera un manifiesto incrustado, como datos binarias codificados XML en archivo ejecutable de la aplicación. Dado que las aplicaciones ClickOnce y COM sin registro requieren un manifiesto externo, Visual Studio genera un archivo para estos tipos de proyectos que contiene los datos UAC en lugar de un manifiesto incrustado. De forma predeterminada, Visual Studio usa información de un archivo denominado app.manifest para generar información de manifiesto de UAC externo (para la implementación de ClickOnce y COM sin registro), o que lo inserte en el archivo ejecutable de la aplicación (para todos los demás casos). Visual Studio proporciona las siguientes opciones para la generación de manifiestos:  
  
- Use un manifiesto incrustado. Incrustar datos de UAC en el archivo ejecutable de la aplicación y ejecutar como usuario normal.  
  
   Se trata de la configuración predeterminada (a menos que use ClickOnce). Esta configuración será compatible con la forma habitual en que funciona Visual Studio en Windows Vista; es decir, la generación de un manifiesto interno y externo, ambos usan `AsInvoker`.  
  
- Use un manifiesto externo. Genere un manifiesto externo utilizando app.manifest.  
  
   Esto genera únicamente el manifiesto externo mediante el uso de la información en app.manifest. Al publicar una aplicación mediante ClickOnce o COM sin registro, Visual Studio agrega app.manifest al proyecto y agrega esta opción.  
  
- Usar ningún manifiesto. Crear la aplicación sin un manifiesto.  
  
   Este enfoque también es conocido como *virtualización*. Use esta opción para la compatibilidad con las aplicaciones existentes de versiones anteriores de Visual Studio.  
  
  Las nuevas propiedades están disponibles en el **aplicación** página del Diseñador de proyectos (proyectos de Visual C# solo) y en el formato de archivo de proyecto de MSBuild.  
  
  Tenga en cuenta que el método para configurar la generación del manifiesto de UAC en el IDE de Visual Studio difiere según el tipo de proyecto (Visual C# y Visual Basic).  
  
  Para obtener información sobre cómo configurar proyectos de Visual C# para la generación de manifiestos, consulte [Application Page, Project Designer (C#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  Para obtener información sobre cómo configurar proyectos de Visual Basic para la generación de manifiestos, consulte [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Los permisos de usuario y Visual Studio](http://msdn.microsoft.com/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Página de aplicación, Diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Página de aplicación, Diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
