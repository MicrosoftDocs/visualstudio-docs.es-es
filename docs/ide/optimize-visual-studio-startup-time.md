---
title: Optimizar el tiempo de inicio de Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 7/20/2017
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
ms.translationtype: HT
ms.sourcegitcommit: c3521e1de25854db012cb91bbe09d9463ecb42c7
ms.openlocfilehash: af1ff0dbeeb30e6b3169c6a94dab8da50085bf20
ms.contentlocale: es-es
ms.lasthandoff: 07/21/2017

---

# <a name="optimize-visual-studio-startup-time"></a>Optimizar el tiempo de inicio de Visual Studio
Lo ideal es que Visual Studio se inicie siempre lo antes posible. En cambio, las ventanas de herramientas abiertas y las extensiones de Visual Studio pueden afectar negativamente al tiempo de inicio porque se cargan automáticamente al arrancar. En la ventana **Administrar el rendimiento de Visual Studio** puede ver qué extensiones y características afectan al tiempo de inicio de Visual Studio y controlar el comportamiento de carga de dichas extensiones y características.

## <a name="control-startup-behavior"></a>Controlar el comportamiento de inicio

Para evitar extender demasiado el tiempo de inicio, Visual Studio 2017 impide la carga de extensiones durante el inicio mediante un enfoque de carga a petición. Con este comportamiento, las extensiones no se abren inmediatamente después de que Visual Studio se inicia, sino solo cuando resulta necesario después del inicio. Además, como las ventanas de herramientas que se han quedado abiertas en una sesión de Visual Studio anterior pueden ralentizar el tiempo de inicio, Visual Studio abre ventanas de herramientas de una manera más inteligente para evitar el impacto en el tiempo de inicio.

Si Visual Studio detecta un inicio lento, aparece un mensaje emergente avisándole de la extensión o la ventana de herramientas que está provocando la ralentización. El mensaje también proporciona un vínculo al cuadro de diálogo **Administrar el rendimiento de Visual Studio**, que también se puede abrir con el comando de menú **Ayuda > Administrar el rendimiento de Visual Studio**.

![Administrar el rendimiento Visual Studio: mensaje emergente en el que se lee "Se ha detectado que la extensión... está ralentizando Visual Studio"](~/docs/ide/media/vside_perfdialog_popup.PNG)

En el cuadro de diálogo se enumeran las ventanas de herramientas y extensiones que afectan negativamente al rendimiento de inicio. Este cuadro de diálogo le permite cambiar la configuración de la ventana de herramientas y de las extensiones para mejorar el rendimiento de inicio.

### <a name="change-extension-settings"></a>Cambio de la configuración de las extensiones

Si una extensión está ralentizando el inicio de Visual Studio, esta aparece en el cuadro de diálogo **Administrar el rendimiento de Visual Studio** cuando selecciona uno de los tipos de extensión. En el cuadro de diálogo se muestra qué extensión afecta al rendimiento de inicio, cuándo se carga una solución y cuándo se escribe en el editor.

![Administrar el rendimiento Visual Studio: vista de extensiones](~/docs/ide/media/vside_perfdialog_extensions.PNG)

Si el impacto en el tiempo de inicio, de carga de soluciones o de escritura en el editor resulta excesivamente alto, deshabilite la extensión para dicho escenario; para ello, seleccione **Deshabilitar**. Siempre puede volver a habilitar la extensión en futuras sesiones con el cuadro de diálogo Administrador de extensiones o Administrar el rendimiento de Visual Studio.

### <a name="change-tool-window-settings"></a>Cambio de la configuración de la ventana de herramientas

Si una ventana de herramientas está ralentizando el inicio de Visual Studio y desea modificar el impacto, puede invalidar su comportamiento; para ello, seleccione una de estas dos opciones en lugar de **Usar comportamiento predeterminado**:

- **No mostrar ventana al inicio:** la ventana de herramientas especificada siempre estará cerrada la próxima vez que abra Visual Studio, incluso si se ha quedado abierta en una sesión anterior. Puede abrir la ventana de herramientas desde el menú correspondiente.
- **Ocultar ventana automáticamente al inicio:** si una ventana de herramientas se ha quedado abierta en una sesión anterior, esta opción contrae el grupo de ventanas de herramientas en el inicio para evitar la inicialización de la ventana de herramientas. Se trata de una buena opción si usa una ventana de herramientas frecuentemente, porque esta todavía está disponible, pero ya no afecta negativamente al tiempo de inicio de Visual Studio.

![Administrar el rendimiento Visual Studio: vista de ventanas de herramientas](~/docs/ide/media/vside_perfdialog_toolwindows.PNG)

Siempre puede volver a este cuadro de diálogo en cualquier momento para cambiar la configuración de una ventana de herramientas concreta.

## <a name="speed-up-solution-load"></a>Acelerar la carga de la solución

Visual Studio 2017 admite la **carga de solución ligera**, una característica que reduce la cantidad de tiempo y memoria necesaria para cargar soluciones grandes en el IDE. Si tiene una solución grande que contiene muchos proyectos de C#, VB y C++, probablemente verá una ventaja de rendimiento sustancial si habilita la carga de solución ligera.

Como algunas de las características del IDE no están completamente disponibles cuando la carga de solución ligera está habilitada, la característica está desactivada de manera predeterminada. Las siguientes secciones ayudan a decidir si habilitar esta característica o no.

### <a name="enable-lightweight-solution-load"></a>Habilitar la carga de solución ligera

Puede habilitar la carga de solución ligera para el IDE como un conjunto o para soluciones individuales.

Para cambiar la carga de solución ligera en la configuración de todos los proyectos y soluciones, vaya a **Herramientas > Opciones > Proyectos y soluciones > General** y seleccione una de las tres opciones de carga:

![Cuadro de diálogo Opciones de herramientas](~/docs/ide/media/VSIDE_LightweightSolutionLoad.png)

- **Permitir que Visual Studio elija lo mejor para mi solución**: Visual Studio determina si se debe aplicar la carga de solución ligera al analizar cada solución cuando se abre. 
- **Habilitar:** se habilita la carga de solución ligera para esta solución, con independencia de la configuración del IDE.
- **Deshabilitar:** se deshabilita la carga de solución ligera para esta solución, con independencia de la configuración del IDE.

Para habilitar la carga de solución ligera en una solución individual, seleccione el nodo de solución de nivel superior en el Explorador de soluciones. En la ventana **Propiedades**, seleccione **Predeterminada**, **Habilitada** o **Deshabilitada** para la propiedad **Carga ligera**.

![Explorador de soluciones](~/docs/ide/media/VSIDE_LSL Solution Setting.png)

También puede hacer clic con el botón derecho en el nodo de solución de nivel superior en el Explorador de soluciones y seleccionar **Habilitar la carga de solución ligera** (si la característica está deshabilitada actualmente) o **Deshabilitar la carga de solución ligera** (si la característica está habilitada actualmente):

Cuando cambia la configuración de la carga de solución ligera, el cambio surte efecto la próxima vez que se carga la solución. No necesita reiniciar el IDE.

### <a name="automatically-enable-lightweight-solution-load"></a>Habilitar la carga de solución ligera automáticamente

Cuando abra una solución grande en Visual Studio 2017, puede ver un mensaje emergente que le ofrece habilitar la carga de solución ligera. El mensaje aparece solo para las soluciones que contienen muchos proyectos de C#, VB o C++. Al seleccionar **Habilitar**, se activa la carga de solución ligera solo para dicha solución. La configuración del IDE no varía.

![Ventana emergente](~/docs/ide/media/VSIDE_LSL Popup.png)

Puede deshabilitar la carga de solución ligera más tarde en la ventana **Propiedades** de la solución.

### <a name="limitations"></a>Limitaciones

Muchas características del IDE están completamente disponibles cuando se habilita la carga de solución ligera. En cambio, algunas características del IDE y extensiones de terceros pueden no ser completamente compatibles.  Las siguientes características no funcionan cuando la carga de solución ligera está habilitada:

- Algunas extensiones de terceros pueden no comportarse según lo esperado cuando la carga de solución ligera está habilitada.
- La opción Editar y continuar no funciona en proyectos que no se cargan al iniciar la depuración. Los archivos incluidos en dicho proyecto son de solo lectura y se notifica un error de que el proyecto no se ha cargado si se ha intentado realizar una modificación.
- Cuando se habilita la carga de solución ligera, los proyectos de F# no pueden compilarse correctamente y es posible que los símbolos no estén completamente disponibles en GoTo.

