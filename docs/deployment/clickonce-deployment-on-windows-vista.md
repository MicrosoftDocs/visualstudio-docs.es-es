---
title: Implementación de ClickOnce en Windows Vista | Microsoft Docs
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
ms.openlocfilehash: 0389665349ae9c39a0f820bc047af6cc4db2b683
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867538"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Implementación de ClickOnce en Windows Vista

Creación de aplicaciones en Visual Studio para Control de cuentas de usuario (UAC) en Windows Vista normalmente genera un manifiesto incrustado, como datos binarias codificados XML en archivo ejecutable de la aplicación.  Aplicaciones ClickOnce y COM sin registro requieren un manifiesto externo, por lo que Visual Studio genera un archivo para estos proyectos que contiene los datos UAC en lugar de un manifiesto incrustado. Para las implementaciones de ClickOnce y COM sin registro, Visual Studio usa la información de un archivo denominado *app.manifest* para generar información de manifiesto de UAC externo. Todos los demás casos, Visual Studio incrusta los datos UAC en el archivo ejecutable de la aplicación. 

Visual Studio proporciona las siguientes opciones para la generación de manifiestos:  
  
- Use un manifiesto incrustado. Incrustar datos de UAC en el archivo ejecutable de la aplicación y ejecute como un usuario normal.  
  
   Se trata de la configuración predeterminada (a menos que use ClickOnce). Este valor es compatible con la forma habitual en que funciona Visual Studio en Windows Vista, con la generación de una instancia interna y externa manifiesto mediante `AsInvoker`.  
  
- Use un manifiesto externo. Generar un manifiesto externo mediante *app.manifest*.  
  
   Esto genera únicamente el manifiesto externo mediante el uso de la información de *app.manifest*. Al publicar una aplicación mediante ClickOnce o COM sin registro, Visual Studio agrega *app.manifest* al proyecto y, a continuación, agrega esta opción.  
  
- Usar ningún manifiesto. Crear la aplicación sin un manifiesto.  
  
   Este enfoque también es conocido como *virtualización*. Use esta opción para la compatibilidad con las aplicaciones existentes de versiones anteriores de Visual Studio.  
  
  Las nuevas propiedades están disponibles en el **aplicación** página del Diseñador de proyectos (proyectos de Visual C# solo) y en el formato de archivo de proyecto de MSBuild.  
  
  El método para configurar la generación del manifiesto de UAC en el IDE de Visual Studio difiere según el tipo de proyecto (Visual C# o Visual Basic).  
  
  * Para obtener información sobre cómo configurar proyectos de Visual C# para la generación de manifiestos, consulte [Application Page, Project Designer (C#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  * Para obtener información sobre cómo configurar proyectos de Visual Basic para la generación de manifiestos, consulte [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Permisos de usuario y Visual Studio](https://msdn.microsoft.com/library/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Página de aplicación, Diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Página de aplicación, Diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)