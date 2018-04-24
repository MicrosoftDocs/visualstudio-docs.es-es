---
title: Depuración y proceso host | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04d6500ba45b10a4cc6a309e7f60872febc19736
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="debugging-and-the-hosting-process"></a>Depuración y proceso host
El proceso host de Visual Studio mejora el rendimiento del depurador y permite ofrecer nuevas características de depuración, como la depuración de confianza parcial y la evaluación de expresiones en tiempo de diseño. Si es necesario, puede deshabilitar el proceso host. Para obtener más información, consulta [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md). En las secciones siguientes se describen algunas diferencias entre la depuración con y sin el proceso host.  
  
## <a name="partial-trust-debugging-and-click-once-security"></a>Depuración de confianza parcial y seguridad Click Once  
 La depuración de confianza parcial requiere el proceso host. Si se deshabilita el proceso host, la depuración de confianza parcial no funcionará aunque la seguridad de confianza parcial esté habilitada en la página **Seguridad** de **Propiedades del proyecto**. Para obtener más información, vea [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md) y [How to: Debug a Partial Trust Application](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## <a name="design-time-expression-evaluation"></a>Evaluación de expresiones en tiempo de diseño  
 La expresión en tiempo de diseño siempre utiliza el proceso host. Al deshabilitar el proceso host en **Propiedades del proyecto** , se deshabilita la evaluación de expresiones en tiempo de diseño para los proyectos de biblioteca de clases. Para otros tipos de proyecto, la evaluación de expresiones en tiempo de diseño no se deshabilita. En vez de esto, Visual Studio inicia el archivo ejecutable real y lo utiliza para la evaluación en tiempo de diseño sin el proceso host. Esta diferencia podría generar resultados diferentes.  
  
## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Diferencias de AppDomain.CurrentDomain.FriendlyName  
 `AppDomain.CurrentDomain.FriendlyName` devuelve resultados diferentes que dependen de si está habilitado el proceso host. Si se llama a `AppDomain.CurrentDomain.FriendlyName` con el proceso de host habilitado, devuelve *app_name*`.vhost.exe`. Si se llama con el proceso de host deshabilitado, devuelve *app_name*`.exe`.  
  
## <a name="assemblygetcallingassemblyfullname-differences"></a>Diferencias de Assembly.GetCallingAssembly ().FullName  
 `Assembly.GetCallingAssembly().FullName` devuelve resultados diferentes que dependen de si está habilitado el proceso host. Si se llama a `Assembly.GetCallingAssembly().FullName` con el proceso host habilitado, devuelve `mscorlib`. Si se llama a `Assembly.GetCallingAssembly().FullName` con el proceso host deshabilitado, devuelve el nombre de la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Proceso de alojamiento (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Cómo: depurar una aplicación de confianza parcial](../debugger/how-to-debug-a-partial-trust-application.md)   
 [Cómo: Deshabilitar el proceso de alojamiento](../ide/how-to-disable-the-hosting-process.md)