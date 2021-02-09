---
title: Solución de problemas con la recarga activa de XAML
description: Solucione los problemas que puedan surgir con la recarga activa de XAML.
ms.date: 09/04/2019
ms.topic: troubleshooting
helpviewer_keywords:
- xaml edit and continue, troubleshooting
- xaml hot reload, troubleshooting
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e13fd71c9d53ef49d7f7372986bfabc29c62747
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890453"
---
# <a name="troubleshooting-xaml-hot-reload"></a>Solución de problemas con la recarga activa de XAML

Esta guía de solución de problemas incluye instrucciones detalladas que deben resolver la mayoría de los problemas que impiden que la recarga activa de XAML funcione correctamente.

La recarga activa de XAML es compatible con aplicaciones de WPF y UWP. Para obtener más información sobre los requisitos del sistema operativo y las herramientas, vea [escribir y depurar código XAML en ejecución con la recarga activa de XAML](xaml-hot-reload.md).

## <a name="hot-reload-is-not-available"></a>La recarga activa no está disponible

Si ve el mensaje "la recarga activa no está disponible" en la barra de herramientas de la aplicación durante la depuración de la aplicación, siga las instrucciones que se describen en este artículo para resolver el problema.

## <a name="verify-that-xaml-hot-reload-is-enabled"></a>Comprobar que la recarga activa de XAML está habilitada

La característica está habilitada de forma predeterminada. Cuando empiece a depurar la aplicación, asegúrese de que ve la barra de herramientas de la aplicación, que confirma que la recarga activa de XAML está disponible:

![Recarga activa de XAML disponible](../debugger/media/xaml-hot-reload-available.png)

Si no ve la barra de herramientas en la aplicación, abra opciones de **depuración**  >    >  **General**. Asegúrese de que están seleccionadas las dos opciones, **habilitar las herramientas de depuración de la interfaz de usuario para XAML** y **Habilitar la recarga activa de XAML** .

![Captura de pantalla de la ventana Opciones de depuración de Visual Studio. Se seleccionan las opciones generales de depuración y se activa la opción Habilitar recarga activa de XAML.](../debugger/media/xaml-hot-reload-enable.png)

Si estas opciones están seleccionadas, vaya al árbol visual dinámico (**depurar**  >    >  **árbol visual** de Windows Live) y asegúrese de que la opción **Mostrar herramientas en tiempo de ejecución en la aplicación** (en el extremo izquierdo) está seleccionada.

![Captura de pantalla de la barra de herramientas en la parte superior de la ventana del árbol visual activo con el botón "Mostrar herramientas en tiempo de ejecución en la aplicación" seleccionado.](../debugger/media/xaml-hot-reload-show-runtime-tools.png)

## <a name="verify-that-you-use-start-debugging-rather-than-attach-to-process"></a>Compruebe que usa iniciar depuración en lugar de asociar al proceso.

La recarga activa de XAML requiere que la variable de entorno `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` esté establecida en 1 en el momento en que se inicia la aplicación. Visual Studio lo establece automáticamente como parte del comando **depurar**  >  **iniciar depuración** (o **F5**). Si desea usar la recarga activa de XAML con el comando **depurar**  >  **asociar al proceso** en su lugar, establezca la variable de entorno usted mismo.

> [!NOTE]
> Para establecer una variable de entorno, use el botón Inicio para buscar "variable de entorno" y elija **editar las variables de entorno del sistema**. En el cuadro de diálogo que se abre, elija **variables de entorno**, agréguelo como variable de usuario y establezca el valor en `1` . Para limpiar, quite la variable cuando termine la depuración.

## <a name="verify-that-your-msbuild-properties-are-correct"></a>Comprobar que las propiedades de MSBuild son correctas

De forma predeterminada, la información de origen se incluye en una configuración de depuración. Se controla mediante las propiedades de MSBuild en los archivos de proyecto (por ejemplo, *. csproj). En WPF, la propiedad es `XamlDebuggingInformation` , que debe establecerse en `True` . En el caso de UWP, la propiedad es `DisableXbfLineInfo` , que debe establecerse en `False` . Por ejemplo:

WPF:

`<XamlDebuggingInformation>True</XamlDebuggingInformation>`

UWP

`<DisableXbfLineInfo>False</DisableXbfLineInfo>`

## <a name="verify-that-you-are-using-the-correct-build-configuration-name"></a>Compruebe que está usando el nombre de la configuración de compilación correcto

Debe establecer manualmente la propiedad de MSBuild correcta para admitir la recarga activa de XAML (consulte la sección anterior), o bien debe usar el nombre de la configuración de compilación predeterminada (depurar). Si no establece la propiedad de MSBuild correctamente, el nombre de una configuración de compilación personalizada no funcionará ni se generará una versión de lanzamiento.

## <a name="verify-that-your-xaml-file-has-no-errors"></a>Comprobar que el archivo XAML no tiene errores

Si el archivo XAML muestra errores en el **lista de errores**, es posible que la recarga activa de XAML no funcione.

## <a name="see-also"></a>Vea también

[Escribir y depurar código XAML en ejecución con recarga activa de XAML](xaml-hot-reload.md)
