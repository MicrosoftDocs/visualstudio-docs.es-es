---
title: Escribir y depurar XAML con recarga activo de XAML
description: Volver a cargar XAML activo o XAML, editar y continuar, permite realizar cambios en el código XAML durante la ejecución de aplicaciones
ms.custom: ''
ms.date: 02/28/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a002c3876eecf0f31a8d104fa235b1208af90699
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57875263"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Escribir y depurar código XAML en ejecución con la recarga de acceso frecuente de XAML en Visual Studio

XAML Visual Studio activo recargar le ayuda a generar la interfaz de usuario de aplicación WPF o UWP por lo que le permite realizar cambios en el código XAML mientras se ejecuta la aplicación. Esta característica le permite compilar y probar código XAML con la ventaja de contexto de datos de la aplicación en ejecución, el estado de autenticación y otro complejidad del mundo real que es difícil simular durante el tiempo de diseño de forma incremental.

Recarga de acceso frecuente de XAML es especialmente útil en estos escenarios:

* Solución de problemas de la interfaz de usuario que se encuentra en el código XAML después de la aplicación se inició en modo de depuración.

* Crear un nuevo componente de interfaz de usuario para una aplicación que está en desarrollo, al tiempo que aprovecha el contexto de la aplicación en tiempo de ejecución.

|Tipos de aplicaciones compatibles|Sistema operativo y herramientas|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+</br>Windows 7 y versiones posteriores |
|Aplicaciones universales de Windows (UWP)|Windows 10 y versiones posteriores, con el [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

> [!NOTE]
> Recarga activo de Visual Studio XAML está actualmente solo se admite cuando se ejecuta la aplicación en Visual Studio con el depurador asociado (**F5** o **iniciar la depuración**). No se puede habilitar esta experiencia usando *asociar al proceso*.

## <a name="known-limitations"></a>Limitaciones conocidas

Los siguientes son conocidos de las limitaciones de XAML "hot" volver a cargar. Para evitar cualquier limitación que pueden surgir, detiene al depurador y, a continuación, completar la operación.

|Limitación|WPF|UWP|Notas|
|-|-|-|-|
|Eventos y los controles mientras se ejecuta la aplicación|No admitido|No compatibles|Vea el error: *asegurarse de error del evento*|
|Creación de objetos de recursos en un diccionario de recursos, como las de la ventana de la página de la aplicación o *App.xaml*|No admitido|Compatible|Ejemplo: agregar un ```SolidColorBrush``` en un diccionario de recursos para su uso como un ```StaticResource```.</br>Nota: Recursos estáticos, los convertidores de tipos de estilo y otros elementos que se escriben en un diccionario de recursos pueden ser aplicado o utilizado durante el uso de recarga XAML activo. No se admite solo la creación del recurso.</br> Cambiar el diccionario de recursos ```Source``` propiedad.| 
|Adición de nuevos controles, clases, windows u otros archivos al proyecto mientras se está ejecutando la aplicación|No admitido|No admitido|Ninguna|
|Administrar paquetes de NuGet (agregar, quitar o actualizar paquetes)|No admitido|No admitido|Ninguna|
|Cambiar el enlace de datos que usa la extensión de marcado {x: Bind}|N/D|Compatible con Visual Studio de 2019 y versiones posteriores|No se admite en Visual Studio de 2018 o versiones anteriores|

## <a name="error-messages"></a>Mensajes de error

Puede encontrarse los siguientes errores al usar la recarga XAML activo.

|Mensaje de error|Descripción|
|-|-|-|
|Asegúrese de evento de error|Error indica que está intentando conectar un evento a uno de los controles, que no se admite mientras se ejecuta la aplicación.|
|Editar y continuar de XAML no ha encontrado elementos para actualizar.|Error se produce cuando se edita XAML que recargar frecuente no se puede actualizar en la aplicación.</br> A veces, este error puede corregirse mediante el uso de la aplicación en ejecución para navegar a una vista que se usa el XAML.</br> En ocasiones, este error significa que no se puede aplicar el cambio específico hasta que reinicie la sesión de depuración. |
|Este cambio no se admite durante una sesión de depuración.|Error indica que el cambio que está intentando no es compatible con la recarga XAML activo. Detener la sesión de depuración, realizar el cambio y, a continuación, reinicie la sesión de depuración.|