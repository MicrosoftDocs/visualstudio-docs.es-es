---
title: 'Cómo: usar el registro de actividad | Microsoft Docs'
description: Los VSPackages pueden escribir mensajes en el registro de actividad. Obtenga información sobre cómo usar el registro de actividades para depurar VSPackages en entornos comerciales.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6f2fa3bec68a40ca2157281205781900b6f4d050
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883355"
---
# <a name="how-to-use-the-activity-log"></a>Cómo: usar el registro de actividad
Los VSPackages pueden escribir mensajes en el registro de actividad. Esta característica es especialmente útil para depurar VSPackages en entornos comerciales.

> [!TIP]
> El registro de actividad está siempre activado. Visual Studio mantiene un búfer rodante de las últimas 100 entradas, así como las 10 primeras entradas, que tienen información de configuración general.

## <a name="to-write-an-entry-to-the-activity-log"></a>Para escribir una entrada en el registro de actividad

1. Inserte este código en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método o en cualquier otro método excepto en el constructor VSPackage:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Este código obtiene el <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> servicio y lo convierte en una <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> escribe una entrada informativa en el registro de actividad utilizando el contexto de la referencia cultural actual.

2. Cuando se carga el VSPackage (normalmente cuando se invoca un comando o se abre una ventana), el texto se escribe en el registro de actividad.

## <a name="to-examine-the-activity-log"></a>Para examinar el registro de actividad

1. Ejecute Visual Studio con el modificador de la línea de comandos [/log](../ide/reference/log-devenv-exe.md) para escribir ActivityLog.xml en el disco durante la sesión.

2. Después de cerrar Visual Studio, busque el registro de actividad en la subcarpeta de Visual Studio Data:

   <em> *% AppData%</em>\Microsoft\VisualStudio \\ \<version>\ActivityLog.xml*.

3. Abra el registro de actividades con cualquier editor de texto. Esta es una entrada típica:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Programación sólida

Dado que el registro de actividad es un servicio, el registro de actividad no está disponible en el constructor VSPackage.

Debe obtener el registro de actividad justo antes de escribir en él. No almacene en caché ni guarde el registro de actividad para su uso futuro.

## <a name="see-also"></a>Vea también

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Solución de problemas de VSPackages](../extensibility/troubleshooting-vspackages.md)
- [VSPackages](../extensibility/internals/vspackages.md)
