---
title: Optimizar el tiempo de inicio | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 98d54f1e43090e8e1cacf8aecac9eebd18ffcbd7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203804"
---
# <a name="optimize-visual-studio-startup-time"></a>Optimizar el tiempo de inicio de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lo ideal es que Visual Studio se inicie siempre lo antes posible. En cambio, las ventanas de herramientas abiertas y las extensiones de Visual Studio pueden afectar negativamente al tiempo de inicio porque se cargan automáticamente al arrancar. La ventana **Administrar el rendimiento de Visual Studio** le permite no solo ver qué extensiones y características afectan al tiempo de inicio de Visual Studio, sino también determinar su comportamiento de carga para que tenga más control sobre la rapidez con la que Visual Studio se inicia.

## <a name="control-startup-behavior"></a>Controlar el comportamiento de inicio

Para evitar extender el tiempo de inicio, Visual Studio 2017 y posterior evite la carga de extensiones durante el inicio, mediante un enfoque de carga en la demanda. Esto significa que las extensiones no se abren inmediatamente después de que Visual Studio se inicie, sino que se abren asincrónicamente según sea necesario después del inicio. Además, como las ventanas de herramientas que se han quedado abiertas en una sesión de Visual Studio anterior pueden ralentizar el tiempo de inicio, Visual Studio abre ventanas de herramientas de una manera más inteligente para evitar el impacto en el tiempo de inicio.

Si Visual Studio detecta un inicio lento, aparece un mensaje emergente avisándole de la extensión o la ventana de herramientas que está provocando la ralentización. El mensaje también proporciona un vínculo en el cuadro de diálogo **Administrar el rendimiento de Visual Studio**, donde se enumeran las extensiones y las ventanas de herramientas que afectan al rendimiento de inicio. Este cuadro de diálogo le permite cambiar la configuración de la ventana de herramientas y de las extensiones para mejorar el rendimiento de inicio.

![Administrar el rendimiento de Visual Studio: elemento emergente](../ide/media/vside-perfdialog-popup.PNG "Administrar el rendimiento de Visual Studio: elemento emergente")

El **administrar el rendimiento de Visual Studio** cuadro de diálogo tiene dos categorías: **Extensiones** y **herramienta Windows**.

### <a name="control-extensions"></a>Controlar extensiones
Si una extensión está ralentizando el inicio de Visual Studio, la extensión aparece en el cuadro **Administrar el rendimiento de Visual Studio** cuando selecciona uno de los tipos de extensión. Si el impacto en el tiempo de inicio (que aparece en la sección **Impacto**) es inaceptablemente alto, puede seleccionar el botón **Deshabilitar** para deshabilitar siempre la extensión en el inicio. Puede volver a habilitar la extensión en futuras sesiones con el cuadro de diálogo Administrador de extensiones o Administrar el rendimiento de Visual Studio.

![Administrar el rendimiento de Visual Studio: extensiones](../ide/media/vside-perfdialog-extensions.PNG "Administrar el rendimiento de Visual Studio: extensiones")

Además de las extensiones de inicio, también puede deshabilitar las extensiones que se cargan al mismo tiempo que las soluciones o cuando un usuario escribe. Simplemente seleccione el escenario para ver una lista de las extensiones asociadas.

### <a name="control-tool-windows"></a>Controlar las ventanas de herramientas
Si una ventana de herramientas está ralentizando el inicio de Visual Studio, puede optar por dejarla en su comportamiento predeterminado (lo que no le proporciona ningún beneficio en la velocidad de inicio) o puede invalidar este comportamiento seleccionando uno de los dos siguientes:

- **No mostrar ventana al inicio:** Si elige esta opción, la ventana de herramientas especificada siempre se cerrará cuando se abre Visual Studio, incluso si se queda abierto en una sesión anterior. Puede abrir la ventana de herramientas desde el menú.
- **Ocultar ventana automáticamente al inicio:** Si una ventana de herramientas se ha quedado abierta en una sesión anterior, si elige esta opción se contraerá de grupo de la ventana de herramientas en el inicio para evitar la inicialización de la ventana de herramientas. Esta es una buena opción si usa una ventana de herramientas frecuentemente, porque esta todavía está disponible, pero ya no afecta negativamente al tiempo de inicio de Visual Studio.

![Administrar el rendimiento de Visual Studio: ventanas de herramientas](../ide/media/vside-perfdialog-toolwindows.PNG "Administrar el rendimiento de Visual Studio: ventanas de herramientas")

Si cambia de idea más tarde, puede revertir cualquiera de estas opciones en el cuadro de diálogo **Administrar el rendimiento de Visual Studio**. Para abrir el cuadro de diálogo **Administrar el rendimiento de Visual Studio**, pulse **Ayuda**, **Administrar el rendimiento de Visual Studio** en la barra de menús.
