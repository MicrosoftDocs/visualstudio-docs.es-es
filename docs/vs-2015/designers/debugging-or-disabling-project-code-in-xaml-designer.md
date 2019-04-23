---
title: Depurar o deshabilitar el código del proyecto en el Diseñador XAML | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8773b9f80299c1a46b6a57506d09f9f4ca32b998
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060779"
---
# <a name="debugging-or-disabling-project-code-in-xaml-designer"></a>Depurar o deshabilitar el código del proyecto en el Diseñador XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En muchos casos, las excepciones no controladas en el Diseñador XAML pueden deberse a un código de proyecto que intenta tener acceso a propiedades o métodos que devuelven valores distintos o funcionan de manera diferente cuando se ejecuta la aplicación en el diseñador. Puede depurar el código del proyecto en otra instancia de Visual Studio para resolver estas excepciones o impedirlos temporalmente deshabilitando el código del proyecto en el diseñador.  
  
 El código del proyecto incluye:  
  
- Controles personalizados y controles de usuario  
  
- Bibliotecas de clases  
  
- Convertidores de valores  
  
- Enlaces con datos en tiempo de diseño generados a partir de código del proyecto  
  
  Cuando se deshabilita el código del proyecto, Visual Studio mostrará los marcadores de posición, como el nombre de la propiedad para un enlace donde los datos ya no están disponibles; o un marcador de posición para un control que no esté en ejecución.  
  
  ![Cuadro de diálogo de excepción no controlada](../designers/media/xaml-unhandledexception.png "XAML_UnhandledException")  
  
#### <a name="to-determine-if-project-code-is-causing-an-exception"></a>Para determinar si el código del proyecto está provocando una excepción  
  
1. En el cuadro de diálogo de excepción no controlada, elija el vínculo **Haga clic aquí para recargar el diseñador** .  
  
2. En la barra de menús, elija **Depurar**, **Iniciar depuración** para compilar y ejecutar la aplicación.  
  
     Si la aplicación se compila y se ejecuta correctamente, la excepción en tiempo de diseño puede deberse a que su código de proyecto se está ejecutando en el diseñador.  
  
#### <a name="to-debug-project-code-running-in-the-designer"></a>Para depurar código de proyecto que se ejecuta en el diseñador  
  
1. En el cuadro de diálogo de excepción no controlada, elija el vínculo **Haga clic aquí para deshabilitar la ejecución de código del proyecto y volver a cargar el diseñador** .  
  
2. En el Administrador de tareas de Windows, elija el botón **Finalizar tarea** para cerrar todas las instancias del Diseñador de XAML de Visual Studio que se estén ejecutando actualmente.  
  
     ![Instancias del diseñador de XAML en el Administrador de tareas](../designers/media/xaml-taskmanager.png "XAML_TaskManager")  
  
3. En Visual Studio, abra la página XAML, que contiene el código o el control que desea depurar.  
  
4. Abra una nueva instancia de Visual Studio, y luego abra una segunda instancia del proyecto.  
  
5. Establezca un punto de interrupción en el código del proyecto.  
  
6. En la nueva instancia de Visual Studio, en la barra de menús, elija **Depurar**, **Asociar al proceso**.  
  
7. En el cuadro de diálogo **Asociar al proceso** , en la lista **Procesos disponibles** , elija **XDesProc.exe**y luego seleccione el botón **Asociar** .  
  
     ![El proceso del diseñador de XAML](../designers/media/xaml-attach.png "XAML_Attach")  
  
     Este es el proceso para el Diseñador XAML en la primera instancia de Visual Studio.  
  
8. En la primera instancia de Visual Studio, en la barra de menús, elija **Depurar**, **Iniciar depuración**.  
  
     Ahora puede entrar en el código que se ejecuta en el diseñador.  
  
#### <a name="to-disable-project-code-in-the-designer"></a>Para deshabilitar el código del proyecto en el diseñador  
  
- En el cuadro de diálogo de excepción no controlada, elija el vínculo **Haga clic aquí para deshabilitar la ejecución de código del proyecto y volver a cargar el diseñador** .  
  
- Como alternativa, en la barra de herramientas en el Diseñador XAML, elija la opción **Deshabilitar código de proyecto** .  
  
     ![Botón Deshabilitar el código de proyecto](../designers/media/xaml-disablecode.png "XAML_DisableCode")  
  
     Puede alternar el botón de nuevo para volver a habilitar el código del proyecto.  
  
    > [!NOTE]
    >  Para proyectos destinados a procesadores X64 o ARM, Visual Studio no puede ejecutar el código del proyecto en el diseñador, por lo que el botón **Deshabilitar código de proyecto** está deshabilitado en el diseñador.  
  
- Cualquiera de las opciones hará que el diseñador se vuelva a cargar, y luego deshabilitará todo el código para el proyecto asociado.  
  
    > [!NOTE]
    >  Deshabilitar el código del proyecto puede provocar una pérdida de datos en tiempo de diseño. Una alternativa es depurar el código que se ejecuta en el diseñador.  
  
## <a name="see-also"></a>Vea también  
 [Diseño de XAML en Visual Studio y Blend para Visual Studio](../designers/designing-xaml-in-visual-studio.md)
