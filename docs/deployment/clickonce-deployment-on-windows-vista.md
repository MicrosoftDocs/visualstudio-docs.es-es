---
title: Implementación de ClickOnce en Windows Vista | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c546d7e4287fc47a3770baa306a43a1631be2f06
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31558937"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Implementación de ClickOnce en Windows Vista
Compilar aplicaciones en Visual Studio para Control de cuentas de usuario (UAC) en Windows Vista normalmente genera un manifiesto incrustado, como datos binarias codifican XML en archivo ejecutable de la aplicación. Dado que las aplicaciones ClickOnce y COM sin registro requieren un manifiesto externo, Visual Studio genera un archivo para estos tipos de proyectos que contienen los datos UAC en lugar de un manifiesto incrustado. De forma predeterminada, Visual Studio usa información en un archivo denominado app.manifest para generar la información de manifiesto UAC externa (para la implementación de ClickOnce y COM sin registro), o para incrustar en el archivo ejecutable de la aplicación (para todos los demás casos). Visual Studio proporciona las siguientes opciones para la generación de manifiestos:  
  
-   Use un manifiesto incrustado. Incrustar los datos UAC en el archivo ejecutable de la aplicación y ejecutar como usuario normal.  
  
     Se trata de la configuración predeterminada (a menos que use ClickOnce). Esta configuración será compatible con la forma habitual en que funciona en Visual Studio en Windows Vista; es decir, la generación del manifiesto interno y externo, ambos usando `AsInvoker`.  
  
-   Use un manifiesto externo. Genere un manifiesto externo utilizando app.manifest.  
  
     Esto genera únicamente el manifiesto externo usando la información en app.manifest. Al publicar una aplicación mediante ClickOnce o COM sin registro, Visual Studio agrega app.manifest al proyecto y agrega esta opción.  
  
-   No usar ningún manifiesto. Crear la aplicación sin un manifiesto.  
  
     Este enfoque también se denomina es *virtualización*. Utilice esta opción para la compatibilidad con las aplicaciones existentes de versiones anteriores de Visual Studio.  
  
 Las nuevas propiedades están disponibles en la **aplicación** página del Diseñador de proyectos (proyectos de Visual C# sólo) y en el formato de archivo de proyecto de MSBuild.  
  
 Tenga en cuenta que el método para configurar la generación de manifiestos de UAC en el IDE de Visual Studio difiere según el tipo de proyecto (Visual C# y Visual Basic).  
  
 Para obtener información sobre cómo configurar proyectos de Visual C# para la generación de manifiestos, consulte [Application Page, Project Designer (C#)](../ide/reference/application-page-project-designer-csharp.md).  
  
 Para obtener información sobre cómo configurar proyectos de Visual Basic para la generación de manifiestos, consulte [página de aplicación, Diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Permisos de usuario y Visual Studio](http://msdn.microsoft.com/en-us/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Página de aplicación, Diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Página de aplicación, Diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)