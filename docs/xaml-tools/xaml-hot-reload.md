---
title: Escribir y depurar XAML mediante la recarga activa de XAML
description: La recarga activa de XAML, o editar y continuar de XAML, permite realizar cambios en el código XAML mientras se ejecutan las aplicaciones.
ms.date: 09/23/2020
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37d4bc0417d30d64a05cc7f283784d3b23d9adee
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134032"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Escritura y depuración de código XAML en ejecución con Recarga activa de XAML en Visual Studio

La recarga activa de XAML le ayuda a compilar la interfaz de usuario (UI) de la aplicación para UWP o de UWP permitiéndole realizar cambios en el código XAML mientras se ejecuta la aplicación. La recarga activa está disponible en Visual Studio y Blend para Visual Studio. Esta característica le permite compilar y probar incrementalmente el código XAML con la ventaja de que el contexto de datos de la aplicación en ejecución, el estado de autenticación y otras complejidades del mundo real son difíciles de simular durante el tiempo de diseño. Si necesita ayuda para solucionar problemas de recargas activas de XAML, consulte solución de problemas de la [recarga activa de XAML](xaml-hot-reload-troubleshooting.md) en su lugar.

> [!NOTE]
> Si usa Xamarin. Forms, consulte [recarga activa de XAML para Xamarin. Forms](/xamarin/xamarin-forms/xaml/hot-reload).

La recarga activa de XAML es especialmente útil en estos escenarios:

* Corrección de los problemas de la interfaz de usuario encontrados en el código XAML después de que la aplicación se iniciara en modo de depuración.

* Compilar un nuevo componente de interfaz de usuario para una aplicación que está en desarrollo, mientras se aprovecha el contexto de tiempo de ejecución de la aplicación.

|Tipos de aplicación admitidos|Sistema operativo y herramientas|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6 y .NET Core</br>Windows 7 y versiones posteriores |
|Aplicaciones universales de Windows (UWP)|Windows 10 y versiones posteriores, con el [SDK de Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

En la ilustración siguiente se muestra el uso del árbol visual dinámico para abrir el código fuente y, a continuación, la recarga activa de XAML para cambiar el color del botón y el texto del botón.

![Recarga activa de XAML](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> La recarga activa de XAML de Visual Studio solo se admite actualmente cuando se ejecuta la aplicación en Visual Studio o Blend para Visual Studio con el depurador adjunto ( **F5** o **iniciar depuración** ). No puede habilitar esta experiencia mediante [asociar al proceso](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) a menos que [establezca manualmente una variable de entorno](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process).

## <a name="known-limitations"></a>Restricciones conocidas

A continuación se indican las limitaciones conocidas de la recarga activa de XAML. Para evitar cualquier limitación en la que se ejecute, simplemente detenga el depurador y, a continuación, complete la operación.

|Limitación|WPF|UWP|Notas|
|-|-|-|-|
|Cableado de eventos a controles mientras la aplicación se está ejecutando|No compatible|No compatible|Consulte error: error *al comprobar el evento* . Tenga en cuenta que en WPF puede hacer referencia a un controlador de eventos existente. En aplicaciones UWP, no se admite la referencia a un controlador de eventos existente.|
|Crear objetos de recursos en un diccionario de recursos como los de la página o la ventana de la aplicación o *app. Xaml*|Se admite a partir de Visual Studio 2019 Update 2|Compatible.|Ejemplo: agregar un `SolidColorBrush` a un diccionario de recursos para su uso como `StaticResource` .</br>Nota: los recursos estáticos, convertidores de estilo y otros elementos que se escriben en un diccionario de recursos se pueden aplicar/usar al usar la recarga activa de XAML. Solo se admite la creación del recurso.</br> Cambiar la propiedad del Diccionario de recursos `Source` .|
|Agregar nuevos controles, clases, ventanas u otros archivos al proyecto mientras la aplicación se está ejecutando|No compatible|No compatible|Ninguno|
|Administración de paquetes NuGet (agregar, quitar o actualizar paquetes)|No compatible|No compatible|Ninguno|
|Cambiar el enlace de datos que usa la extensión de marcado {x:Bind}|N/D|Se admite a partir de Visual Studio 2019|Esto requiere la versión 1809 de Windows 10 (compilación 10.0.17763). No se admite en Visual Studio 2017 o versiones anteriores.|
|No se admite el cambio de directivas x:Uid|N/A|No admitido|Ninguno|
|Varios procesos | Compatible. | Compatible. | Compatible con Visual Studio 2019, [versión 16,6](/visualstudio/releases/2019/release-notes-v16.6) y versiones posteriores |

## <a name="error-messages"></a>Mensajes de error

Es posible que se produzcan los siguientes errores al usar la recarga activa de XAML.

|Mensaje de error|Descripción|
|-|-|
|Error al comprobar el evento|Error indica que está intentando conectar un evento a uno de los controles, lo que no se admite mientras la aplicación se está ejecutando.|
|Este cambio no es compatible con la recarga activa de XAML y no se aplicará durante la sesión de depuración.|Error indica que el cambio que está intentando no es compatible con la recarga activa de XAML. Detenga la sesión de depuración, realice el cambio y, a continuación, reinicie la sesión de depuración. Si encuentra un escenario no admitido que le gustaría ver como compatible, use la nueva opción "sugerir una característica" de la comunidad de [desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). |

## <a name="see-also"></a>Consulte también

* [Solución de problemas con la recarga activa de XAML](xaml-hot-reload-troubleshooting.md)
* [Recarga activa de XAML para Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload)
* [Editar y continuar (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
