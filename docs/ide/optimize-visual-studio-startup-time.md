---
title: Optimizar el tiempo de inicio de Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/09/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 4
author: kempb
ms.author: kempb
manager: ghogen
f1_keywords:
- vs.performancecenter
translationtype: Human Translation
ms.sourcegitcommit: ba88bad0753653dcde8a4d28b4dd1c71522d6506
ms.openlocfilehash: 435197f1536dc9006691c0f2e58fafd0fcf27718
ms.lasthandoff: 02/22/2017

---
# <a name="optimize-visual-studio-startup-time"></a>Optimizar el tiempo de inicio de Visual Studio
Lo ideal es que Visual Studio se inicie siempre lo antes posible. En cambio, las ventanas de herramientas abiertas y las extensiones de Visual Studio pueden afectar negativamente al tiempo de inicio porque se cargan automáticamente al arrancar. La ventana **Administrar el rendimiento de Visual Studio** le permite no solo ver qué extensiones y características afectan al tiempo de inicio de Visual Studio, sino también determinar su comportamiento de carga para que tenga más control sobre la rapidez con la que Visual Studio se inicia.

## <a name="control-startup-behavior"></a>Controlar el comportamiento de inicio

Para evitar extender demasiado el tiempo de inicio, Visual Studio 2017 RC impide la carga de extensiones durante el inicio mediante un enfoque de carga a petición. Esto significa que las extensiones no se abren inmediatamente después de que Visual Studio se inicie, sino que se abren asincrónicamente según sea necesario después del inicio. Además, como las ventanas de herramientas que se han quedado abiertas en una sesión de Visual Studio anterior pueden ralentizar el tiempo de inicio, Visual Studio abre ventanas de herramientas de una manera más inteligente para evitar el impacto en el tiempo de inicio.

Si Visual Studio detecta un inicio lento, aparece un mensaje emergente avisándole de la extensión o la ventana de herramientas que está provocando la ralentización. El mensaje también proporciona un vínculo en el cuadro de diálogo **Administrar el rendimiento de Visual Studio**, donde se enumeran las extensiones y las ventanas de herramientas que afectan al rendimiento de inicio. Este cuadro de diálogo le permite cambiar la configuración de la ventana de herramientas y de las extensiones para mejorar el rendimiento de inicio.

![Administrar el rendimiento de Visual Studio: elemento emergente](../ide/media/vside_perfdialog_popup.PNG "Administrar el rendimiento de Visual Studio: elemento emergente")

El cuadro de diálogo **Administrar el rendimiento de Visual Studio** tiene dos categorías: **Extensiones** y **Ventanas de herramientas**.

### <a name="control-extensions"></a>Controlar extensiones
Si una extensión está ralentizando el inicio de Visual Studio, la extensión aparece en el cuadro **Administrar el rendimiento de Visual Studio** cuando selecciona uno de los tipos de extensión. Si el impacto en el tiempo de inicio (que aparece en la sección **Impacto**) es inaceptablemente alto, puede seleccionar el botón **Deshabilitar** para deshabilitar siempre la extensión en el inicio. Puede volver a habilitar la extensión en futuras sesiones con el cuadro de diálogo Administrador de extensiones o Administrar el rendimiento de Visual Studio.

![Administrar el rendimiento de Visual Studio: extensiones](../ide/media/vside_perfdialog_extensions.PNG "Administrar el rendimiento de Visual Studio: extensiones")

Además de las extensiones de inicio, también puede deshabilitar las extensiones que se cargan al mismo tiempo que las soluciones o cuando un usuario escribe. Simplemente seleccione el escenario para ver una lista de las extensiones asociadas.

### <a name="control-tool-windows"></a>Controlar las ventanas de herramientas
Si una ventana de herramientas está ralentizando el inicio de Visual Studio, puede optar por dejarla en su comportamiento predeterminado (lo que no le proporciona ningún beneficio en la velocidad de inicio) o puede invalidar este comportamiento seleccionando uno de los dos siguientes:

- **No mostrar ventana al inicio:** Si elige esta opción, la ventana de herramientas especificada siempre estará cerrada cuando abra Visual Studio, incluso si se ha quedado abierta en una sesión anterior. Puede abrir la ventana de herramientas desde el menú.
- **Ocultar ventana automáticamente al inicio:** Si una ventana de herramientas se ha quedado abierta en una sesión anterior, al elegir esta opción se contraerá el grupo de ventanas de herramientas en el inicio para evitar la inicialización de la ventana de herramientas. Esta es una buena opción si usa una ventana de herramientas frecuentemente, porque esta todavía está disponible, pero ya no afecta negativamente al tiempo de inicio de Visual Studio.

![Administrar el rendimiento de Visual Studio: ventanas de herramientas](../ide/media/vside_perfdialog_toolwindows.PNG "Administrar el rendimiento de Visual Studio: ventanas de herramientas")

Si cambia de idea más tarde, puede revertir cualquiera de estas opciones en el cuadro de diálogo **Administrar el rendimiento de Visual Studio**. Para abrir el cuadro de diálogo **Administrar el rendimiento de Visual Studio**, pulse **Ayuda**, **Administrar el rendimiento de Visual Studio** en la barra de menús.

## <a name="speed-up-solution-load"></a>Acelerar la carga de la solución

Visual Studio 2017 RC presenta una nueva característica denominada **Carga de solución ligera** que reduce la cantidad de tiempo y memoria necesaria para cargar soluciones grandes en el IDE. Si tiene una solución grande que contiene muchos proyectos de C#, VB o C++, probablemente verá una ventaja de rendimiento sustancial si habilita la carga de solución ligera.

Como algunas de las características del IDE no están completamente disponibles cuando la carga de solución ligera está habilitada, la característica está desactivada de manera predeterminada. Las siguientes secciones le ayudarán a decidir si habilitar esta característica o no.

### <a name="enable-lightweight-solution-load"></a>Habilitar la carga de solución ligera

Puede habilitar la carga de solución ligera para el IDE como un conjunto o para soluciones individuales. Para habilitar la carga de solución ligera para el IDE completo, vaya a **Herramientas**, **Opciones** y, después, vaya a la sección **Proyectos y soluciones**.

![Cuadro de diálogo Opciones de herramientas](../ide/media/VSIDE_LightweightSolutionLoad.png)

Para habilitar la carga de solución ligera en una solución individual, pulse el nodo de solución de nivel superior en el Explorador de soluciones.  En la ventana Propiedades, seleccione uno de los siguientes valores para la propiedad **Carga ligera**.

- **Habilitada:** la carga de solución ligera se habilitará para esta solución independientemente de la configuración del IDE.
- **Deshabilitada:** la carga de solución ligera se deshabilitará para esta solución independientemente de la configuración del IDE.
- **Predeterminada:** el comportamiento de la carga de solución ligera dependerá de la configuración del IDE.

![Explorador de soluciones](../ide/media/VSIDE_LSL Solution Setting.png)

Cuando cambia la configuración de la carga de solución ligera, el cambio surte efecto la próxima vez que se carga la solución. No necesita reiniciar el IDE.

### <a name="automatically-enable-lightweight-solution-load"></a>Habilitar la carga de solución ligera automáticamente

Cuando abra una solución grande en Visual Studio 2017 RC, puede ver un mensaje emergente que le ofrece habilitar la carga de solución ligera. El mensaje solo aparece para las soluciones que contengan muchos proyectos de C#, VB o C++. Seleccionar el comando **enable** habilitará la carga de solución ligera solo para esa solución. La configuración del IDE no cambiará.

![Ventana emergente](../ide/media/VSIDE_LSL Popup.png)

Puede deshabilitar la carga de solución ligera más tarde en la ventana Propiedades de la solución.

### <a name="lightweight-solution-load-limitations"></a>Limitaciones de la carga de solución ligera
Muchas características del IDE están completamente disponibles cuando se habilita la carga de solución ligera. En cambio, algunas características del IDE y extensiones de terceros puede que no sean completamente compatibles.  Las siguientes características no funcionan cuando la carga de solución ligera está habilitada:

#### <a name="third-party-extensions"></a>Extensiones de terceros
Es posible que algunas extensiones no tengan el comportamiento esperado cuando Carga de solución ligera esté habilitada.

#### <a name="edit-and-continue"></a>Editar y continuar
La opción Editar y continuar no funciona en proyectos que no se cargan al iniciar la depuración. Los archivos que se incluyen en dicho proyecto serán de solo lectura y se notificará un error de que el proyecto no se ha cargado si se ha intentado realizar una modificación.

#### <a name="f-support"></a>Compatibilidad con F#
Cuando se habilita la carga de solución ligera, los proyectos de F# no pueden compilarse correctamente y es posible que los símbolos no estén completamente disponibles en GoTo.

