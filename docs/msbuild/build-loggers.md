---
title: Registradores de compilación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e1faf28c05dec58117e5d34e21e7c8020ad3a4d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894292"
---
# <a name="build-loggers"></a>Registradores de compilación
Los registradores proporcionan un método para personalizar el resultado de la compilación y de mostrar mensajes, errores o advertencias en respuesta a eventos de compilación específicos. Cada registrador se implementa como una clase .NET que implementa la interfaz <xref:Microsoft.Build.Framework.ILogger>, que se define en el ensamblado *Microsoft.Build.Framework.dll*.  
  
 Existen dos métodos que se pueden utilizar al implementar un registrador:  
  
- Implementar la interfaz <xref:Microsoft.Build.Framework.ILogger> directamente.  
  
- Derivar la clase de la clase del asistente, <xref:Microsoft.Build.Utilities.Logger>, que se define en el ensamblado *Microsoft.Build.Utilities.dll*. <xref:Microsoft.Build.Utilities.Logger> implementa <xref:Microsoft.Build.Framework.ILogger> y proporciona implementaciones predeterminadas de algunos miembros <xref:Microsoft.Build.Framework.ILogger>.  
  
  En este tema se explica cómo escribir un registrador simple que se deriva de <xref:Microsoft.Build.Utilities.Logger> y muestra mensajes en la consola en respuesta a ciertos eventos de compilación.  
  
## <a name="register-for-events"></a>Registrarse en eventos  
 El propósito de un registrador consiste en recopilar información relacionada con la progresión del proceso de compilación atendiendo a la notificación del motor de compilación y, a continuación, elaborar informes con dicha información para que resulte útil. Todos los registradores deben invalidar el método <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>, que es donde se registra el registrador de eventos. En este ejemplo, el registrador se registra para los eventos <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> y <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]  
  
## <a name="respond-to-events"></a>Responder a eventos  
 Ahora que el registrador está registrado para eventos concretos, es necesario controlar dichos eventos cuando se producen. Para los eventos <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> y <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> eventos, el registrador simplemente escribe una frase corta y el nombre del archivo del proyecto implicado en el evento. Todos los mensajes del registrador se escriben en la ventana de la consola.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]  
  
## <a name="respond-to-logger-verbosity-values"></a>Responder a valores de detalle del registrador  
 En algunos casos, es posible que solo se desee registrar información de un evento si el modificador **-verbosity** de MSBuild.exe contiene un determinado valor. En este ejemplo, el controlador de eventos <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> solo registra un mensaje si la propiedad <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A>, que se establece mediante el modificador **-verbosity**, es igual a <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]  
  
## <a name="specify-a-logger"></a>Especificar un registrador  
 Cuando el registrador se compila en un ensamblado, es necesario indicar a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que utilice dicho registrador durante las compilaciones. Esto se hace con el modificador **-logger** con *MSBuild.exe*. Para obtener más información sobre los modificadores disponibles para *MSBuild.exe*, vea [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  
  
 La siguiente línea de comandos compila el proyecto *MyProject.csproj* y usa la clase de registrador implementada en *SimpleLogger.dll*. El modificador **-nologo** oculta la pancarta y el mensaje de copyright y el modificador **-noconsolelogger** deshabilita el registrador de consola de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] predeterminado.  
  
```cmd  
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll  
```  
  
 La siguiente línea de comandos compila el proyecto con el mismo registrador, pero con un nivel `Verbosity` de `Detailed`.  
  
```cmd  
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed  
```  

## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 El ejemplo siguiente contiene el código completo del registrador.  
  
### <a name="code"></a>Código  
 [!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 El ejemplo siguiente muestra cómo implementar un registrador que escribe el registro en un archivo en lugar de mostrarlo en la ventana de la consola.  
  
### <a name="code"></a>Código  
 [!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]  
  
## <a name="see-also"></a>Vea también  
 [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)