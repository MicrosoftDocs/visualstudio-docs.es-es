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
ms.openlocfilehash: e25f9da960b1de8acb1950b2bdd3ab7e61409f17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675472"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Implementación de ClickOnce en Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La compilación de aplicaciones en Visual Studio para el control de cuentas de usuario (UAC) en Windows Vista normalmente genera un manifiesto incrustado, codificado como datos XML binarios en el archivo ejecutable de la aplicación. Dado que ClickOnce y las aplicaciones COM sin registro requieren un manifiesto externo, Visual Studio genera un archivo para estos tipos de proyectos que contienen los datos de UAC en lugar de un manifiesto incrustado. De forma predeterminada, Visual Studio usa información de un archivo denominado app. manifest para generar información de manifiesto de UAC externa (para ClickOnce y la implementación COM sin registro) o para incrustarla en el archivo ejecutable de la aplicación (para todos los demás casos). Visual Studio proporciona las siguientes opciones para la generación de manifiestos:  
  
- Usar un manifiesto incrustado. Inserte los datos de UAC en el archivo ejecutable de la aplicación y ejecútelo como usuario normal.  
  
   Esta es la configuración predeterminada (a menos que use ClickOnce). Esta configuración será compatible con la manera habitual en la que Visual Studio funciona en Windows Vista; es decir, la generación de un manifiesto interno y externo, ambos usando `AsInvoker` .  
  
- Use un manifiesto externo. Genere un manifiesto externo mediante app. manifest.  
  
   Esto genera solo el manifiesto externo mediante la información de App. manifest. Al publicar una aplicación mediante ClickOnce o COM sin registro, Visual Studio agrega app. manifest al proyecto y agrega esta opción.  
  
- No usar ningún manifiesto. Cree la aplicación sin un manifiesto.  
  
   Este enfoque también se conoce como *Virtualización*. Use esta opción para la compatibilidad con las aplicaciones existentes de versiones anteriores de Visual Studio.  
  
  Las nuevas propiedades están disponibles en la página **aplicación** del diseñador de proyectos (solo para proyectos de Visual C#) y en el formato de archivo de proyecto de MSBuild.  
  
  Tenga en cuenta que el método para configurar la generación de manifiestos de UAC en el IDE de Visual Studio difiere en función del tipo de proyecto (Visual C# y Visual Basic).  
  
  Para obtener información sobre la configuración de proyectos de Visual C# para la generación de manifiestos, vea [Página de aplicación, diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  Para obtener información sobre cómo configurar proyectos de Visual Basic para la generación de manifiestos, vea [Página de aplicación, diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Consulte también  
 [Seguridad e implementación de ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Permisos de usuario y Visual Studio](https://msdn.microsoft.com/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Página de aplicación, diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Página de aplicación, Diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
