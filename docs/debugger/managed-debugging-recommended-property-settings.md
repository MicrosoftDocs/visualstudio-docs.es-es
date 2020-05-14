---
title: Valores de propiedad de depurador recomendados para C#, VB | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 07c63a70de9d633ccd73d1d0d3bd23196d421543
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731369"
---
# <a name="managed-debugging-recommended-property-settings"></a>Depuración administrada: Valores de propiedad recomendados
Algunas propiedades se deben establecer de la misma manera para todos los escenarios de depuración administrados.

 En las siguientes tablas se muestran los valores de propiedades recomendados.

 Los valores no incluidos en esta lista pueden variar entre los diferentes tipos de proyectos administrados. Por ejemplo, **Acción de inicio** se establecerá de manera diferente en un proyecto de Windows Forms que en un proyecto de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Propiedades de configuración en la ficha Generar (C#) o Compilar (Visual Basic)

|**Nombre de la propiedad**|**Configuración**|
|-----------------------|-----------------|
|**Definir constante DEBUG**|C# y F#: active la casilla. Esto permite que la aplicación utilice la clase Debug.|
|**Definir constante TRACE**|C# y F#: active la casilla. Esto permite que la aplicación utilice la clase Trace.|
|**Optimizar código**|C#, F# y Visual Basic: se establece en Falso. El código optimizado es más difícil de depurar, puesto que las instrucciones generadas no se corresponden directamente con las instrucciones de código fuente. Si detecta que el programa tiene un error que solo aparece en código optimizado, puede activar esta configuración, pero recuerde que el código que se muestra en la ventana **Desensamblado** se genera a partir de código optimizado que tal vez no coincida con lo que aparece en el Editor de código. Para depurar el código optimizado, debe desactivar Sólo mi código. (Vea [Restringir la ejecución paso a paso a Solo mi código](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)).<br /><br /> Para obtener más información, vea [Configuración del proyecto para configuraciones de depuración de C#](../debugger/project-settings-for-csharp-debug-configurations.md) o [Configuración del proyecto para una configuración de depuración de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|
|**Ruta de acceso de salida**|Establézcalo en bin\Debug\\.|
|**Opciones de compilación avanzadas**|Solo Visual Basic. Haga clic en **Avanzadas** para establecer las propiedades avanzadas que se describen en la tabla siguiente.|

### <a name="advanced-compiler-settings-dialog-box"></a>Cuadro de diálogo Configuración de compilador avanzada

|**Nombre de la propiedad**|**Configuración**|
|-----------------------|-----------------|
|**Habilitar optimizaciones**|Se establece en false por los motivos especificados en la opción **Optimizar código** de la tabla anterior.|
|**Generar información de depuración**|Active esta casilla para que se establezca el marcador /DEBUG cuando se realice la compilación, lo que generará la información necesaria para facilitar la depuración.|
|**Definir constante DEBUG**|Active esta casilla para definir la constante `DEBUG`, que permite que la aplicación utilice la clase <xref:System.Diagnostics.Debug>.|
|**Definir constante TRACE**|Active esta casilla para definir la constante `TRACE`, que permite que la aplicación utilice la clase <xref:System.Diagnostics.Trace>.|

## <a name="see-also"></a>Vea también
- [Depurar código administrado](../debugger/debugging-managed-code.md)
- [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)