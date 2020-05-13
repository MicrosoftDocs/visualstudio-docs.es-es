---
title: 'Cómo: Usar el registro de actividad ( Activity Log) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64986be303370cf8c9048612ff3d44e82e96805a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710579"
---
# <a name="how-to-use-the-activity-log"></a>Cómo: Usar el registro de actividad
VSPackages puede escribir mensajes en el registro de actividad. Esta característica es especialmente útil para depurar VSPackages en entornos comerciales.

> [!TIP]
> El registro de actividad siempre está activado. Visual Studio mantiene un búfer móvil de las últimas 100 entradas, así como las primeras 10 entradas, que tienen información de configuración general.

## <a name="to-write-an-entry-to-the-activity-log"></a>Para escribir una entrada en el registro de actividad

1. Inserte este código <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> en el método o en cualquier otro método excepto el constructor VSPackage:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Este código obtiene <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> el servicio y <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> lo convierte en una interfaz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>escribe una entrada informativa en el registro de actividad utilizando el contexto cultural actual.

2. Cuando se carga el VSPackage (normalmente cuando se invoca un comando o se abre una ventana), el texto se escribe en el registro de actividad.

## <a name="to-examine-the-activity-log"></a>Para examinar el registro de actividad

1. Ejecute Visual Studio con el modificador de línea de comandos [/Log](../ide/reference/log-devenv-exe.md) para escribir ActivityLog.xml en el disco durante la sesión.

2. Después de cerrar Visual Studio, busque el registro de actividad en la subcarpeta para los datos de Visual Studio:

   <em> *%AppData%</em>> .\\\<*

3. Abra el registro de actividad con cualquier editor de texto. Aquí está una entrada típica:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Programación sólida

Dado que el registro de actividad es un servicio, el registro de actividad no está disponible en el constructor de VSPackage.

Debe obtener el registro de actividad justo antes de escribir en él. No almacene en caché ni guarde el registro de actividad para usarlo en el futuro.

## <a name="see-also"></a>Vea también

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Solución de problemas de VSPackages](../extensibility/troubleshooting-vspackages.md)
- [VSPackages](../extensibility/internals/vspackages.md)
