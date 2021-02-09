---
title: Depuración o deshabilitación de código de proyecto en el Diseñador XAML
description: Obtenga información sobre cómo depurar o deshabilitar el código de proyecto en el Diseñador XAML, incluida la forma de depurar código de proyecto en ejecución en otra instancia de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: e03c33de81727c333db8f662232e669e37e78f59
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921768"
---
# <a name="debug-or-disable-project-code-in-xaml-designer"></a>Depuración o deshabilitación de código de proyecto en el Diseñador XAML

En muchos casos, las excepciones no controladas del Diseñador XAML pueden deberse a un código de proyecto que intenta acceder a propiedades o métodos que devuelven valores distintos o funcionan de manera diferente cuando se ejecuta la aplicación en el diseñador. Puede depurar el código del proyecto en otra instancia de Visual Studio para resolver estas excepciones o evitarlas temporalmente al deshabilitar el código del proyecto en el diseñador.

El código del proyecto incluye:

- Controles personalizados y controles de usuario

- Bibliotecas de clases

- Convertidores de valores

- Enlaces con datos en tiempo de diseño generados a partir de código del proyecto

Cuando se deshabilita el código del proyecto, Visual Studio muestra marcadores de posición. Por ejemplo, Visual Studio muestra el nombre de la propiedad para un enlace donde los datos ya no están disponibles o un marcador de posición para un control que ya no se ejecuta.

![Cuadro de diálogo de excepción no controlada](media/xaml_unhandledexception.png)

## <a name="to-determine-if-project-code-is-causing-an-exception"></a>Para determinar si el código del proyecto está provocando una excepción

1. En el cuadro de diálogo de excepción no controlada, elija el vínculo **Haga clic aquí para recargar el diseñador** .

2. En la barra de menús, elija **depurar**  >  **iniciar depuración** para compilar y ejecutar la aplicación.

     Si la aplicación se compila y se ejecuta correctamente, la excepción en tiempo de diseño puede deberse a que su código de proyecto se está ejecutando en el diseñador.

## <a name="to-debug-project-code-running-in-the-designer"></a>Para depurar código de proyecto que se ejecuta en el diseñador

1. En el cuadro de diálogo de excepción no controlada, elija el vínculo **Haga clic aquí para deshabilitar la ejecución de código del proyecto y volver a cargar el diseñador** .

2. En el Administrador de tareas de Windows, elija el botón **Finalizar tarea** para cerrar todas las instancias del Diseñador de XAML de Visual Studio que se estén ejecutando actualmente.

     ![Instancias del diseñador de XAML en el Administrador de tareas](media/xaml_taskmanager.png)

3. En Visual Studio, abra la página XAML, que contiene el código o el control que desea depurar.

4. Abra una nueva instancia de Visual Studio, y luego abra una segunda instancia del proyecto.

5. Establezca un punto de interrupción en el código del proyecto.

6. En la nueva instancia de Visual Studio, en la barra de menús, elija **depurar**  >  **asociar al proceso**.

7. En el cuadro de diálogo **Asociar al proceso** , en la lista **Procesos disponibles** , elija **XDesProc.exe** y luego seleccione el botón **Asociar** .

     ![El proceso del diseñador de XAML](media/xaml_attach.png)

     Este es el proceso para el Diseñador XAML en la primera instancia de Visual Studio.

8. En la primera instancia de Visual Studio, en la barra de menús, elija **depurar**  >  **iniciar depuración**.

     Ahora puede entrar en el código que se ejecuta en el diseñador.

## <a name="to-disable-project-code-in-the-designer"></a>Para deshabilitar el código del proyecto en el diseñador

- En el cuadro de diálogo de excepción no controlada, elija el vínculo **Haga clic aquí para deshabilitar la ejecución de código del proyecto y volver a cargar el diseñador** .

- Como alternativa, en la barra de herramientas en el **Diseñador XAML**, haga clic en el botón **Deshabilitar código de proyecto**.

     ![Botón para deshabilitar el código de proyecto](media/xaml_disablecode.png)

     Puede alternar el botón de nuevo para volver a habilitar el código del proyecto.

    > [!NOTE]
    > Para proyectos destinados a procesadores X64 o ARM, Visual Studio no puede ejecutar el código del proyecto en el diseñador, por lo que el botón **Deshabilitar código de proyecto** está deshabilitado en el diseñador.

- Cualquiera de las opciones hace que el diseñador se vuelva a cargar, y luego deshabilita todo el código para el proyecto asociado.

    > [!NOTE]
    > Deshabilitar el código del proyecto puede provocar una pérdida de datos en tiempo de diseño. Una alternativa es depurar el código que se ejecuta en el diseñador.

## <a name="control-display-options"></a>Opciones de visualización de controles

> [!NOTE]
> **Opciones de visualización de controles** solo está disponible para aplicaciones de Plataforma universal de Windows que tienen como destino Windows 10 Fall Creators Update (compilación 16299) o posterior. La característica **Opciones de visualización de controles** está disponible en Visual Studio 2017, versión 15.9 o posterior.

En el diseñador XAML, puede cambiar las opciones de visualización de controles para que solo se muestren los controles de plataforma desde Windows SDK. Esto puede mejorar la confiabilidad del diseñador XAML.

Para cambiar las opciones de visualización de controles, haga clic en el icono que se encuentra en la parte inferior izquierda de la ventana del diseñador y, luego, seleccione una opción en **Opciones de visualización de controles**:

![Opciones de visualización de controles](media/control_display_options.png)

Cuando selecciona **Mostrar solo los controles de la plataforma**, todos los controles personalizados que provienen de los SDK, controles de usuario de cliente, etc. no se representarán por completo. En su lugar, los reemplazan controles de reserva para mostrar el tamaño y la posición del control.

## <a name="see-also"></a>Vea también

- [Diseño de XAML en Visual Studio y Blend para Visual Studio](designing-xaml-in-visual-studio.md)
