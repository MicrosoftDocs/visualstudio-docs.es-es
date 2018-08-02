---
title: Depuración y proceso de hospedaje | Microsoft Docs
ms.custom: ''
ms.date: 08/01/2018
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
ms.openlocfilehash: 59ef28f5724c12fd9897adbaa9125bafe26beb60
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468265"
---
# <a name="debugging-and-the-hosting-process"></a>Depuración y proceso host
El proceso host de Visual Studio mejora el rendimiento del depurador y permite ofrecer nuevas características de depuración, como la depuración de confianza parcial y la evaluación de expresiones en tiempo de diseño. Si es necesario, puede deshabilitar el proceso host. En las secciones siguientes se describen algunas diferencias entre la depuración con y sin el proceso host.

> [!NOTE]
> En Visual Studio 2017, la opción de depuración mediante el proceso de hospedaje ya no es necesario y se ha quitado. Para obtener más información, consulte [depurar: Visual Studio 2017 objetivos a velocidad de su menos trabajo favorito](https://vslive.com/Blogs/News-and-Tips/2017/02/Debugging-Visual-Studio-2017-aims-to-speed-up-your-least-favorite-job.aspx).

## <a name="partial-trust-debugging-and-click-once-security"></a>Depuración de confianza parcial y seguridad Click Once
 La depuración de confianza parcial requiere el proceso host. Si se deshabilita el proceso host, la depuración de confianza parcial no funcionará aunque la seguridad de confianza parcial esté habilitada en la página **Seguridad** de **Propiedades del proyecto**. Para obtener más información, consulte [Cómo: depurar una aplicación de confianza parcial](../debugger/how-to-debug-a-partial-trust-application.md).

## <a name="design-time-expression-evaluation"></a>Evaluación de expresiones en tiempo de diseño
 La expresión en tiempo de diseño siempre utiliza el proceso host. Al deshabilitar el proceso host en **Propiedades del proyecto** , se deshabilita la evaluación de expresiones en tiempo de diseño para los proyectos de biblioteca de clases. Para otros tipos de proyecto, la evaluación de expresiones en tiempo de diseño no se deshabilita. En vez de esto, Visual Studio inicia el archivo ejecutable real y lo utiliza para la evaluación en tiempo de diseño sin el proceso host. Esta diferencia podría generar resultados diferentes.

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Diferencias de AppDomain.CurrentDomain.FriendlyName
 `AppDomain.CurrentDomain.FriendlyName` devuelve resultados diferentes que dependen de si está habilitado el proceso host. Si se llama a `AppDomain.CurrentDomain.FriendlyName` con el proceso de host habilitado, devuelve *app_name*`.vhost.exe`. Si se llama con el proceso de host deshabilitado, devuelve *app_name*`.exe`.

## <a name="assemblygetcallingassemblyfullname-differences"></a>Diferencias de Assembly.GetCallingAssembly ().FullName
 `Assembly.GetCallingAssembly().FullName` devuelve resultados diferentes que dependen de si está habilitado el proceso host. Si se llama a `Assembly.GetCallingAssembly().FullName` con el proceso host habilitado, devuelve `mscorlib`. Si se llama a `Assembly.GetCallingAssembly().FullName` con el proceso host deshabilitado, devuelve el nombre de la aplicación.

## <a name="see-also"></a>Vea también

- [Cómo: Depurar una aplicación de confianza parcial](../debugger/how-to-debug-a-partial-trust-application.md)