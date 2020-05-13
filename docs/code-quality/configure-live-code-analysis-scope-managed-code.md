---
title: Configurar el ámbito de análisis de código en vivo para el código administrado
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 300e3f276a45cfe2115311c7d27eedce365616cf
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432094"
---
# <a name="how-to-configure-live-code-analysis-scope-for-managed-code"></a>Cómo: Configurar el ámbito de análisis de código en vivo para el código administrado

## <a name="what-is-live-code-analysis-for-managed-code"></a>¿Qué es "Análisis de código en vivo" para código administrado?
Visual Studio ejecuta un montón de análisis de código en vivo, también *denominados análisis*de fondo, mientras edita archivos de código fuente en el editor. Parte de ella se requiere un análisis mínimo para una experiencia de edición de IDE de Visual Studio aceptable. Parte de ella es para mejorar la capacidad de respuesta para las características IDE. Mientras que parte de ella es habilitar la funcionalidad IDE adicional, como diagnósticos y correcciones de código de analizadores Roslyn. En función de la funcionalidad, estos análisis se pueden agrupar de la siguiente manera:

- **Cálculo en segundo plano de diagnósticos:** análisis de errores de proceso, advertencias y sugerencias en archivos de origen. Estos diagnósticos se muestran como entradas en la lista de errores y como ondulaciones en el editor. Se pueden clasificar en dos categorías:
    - Diagnóstico del compilador de Visual Basic y de C.
    - Diagnóstico del analizador Roslyn, que incluye:

        - Analizadores IDE integrados para sugerencias de estilo de código y
        - Paquetes de analizadores de terceros [instalados](./install-roslyn-analyzers.md) para proyectos en la solución actual.

- **Otros análisis**de fondo: análisis para mejorar la capacidad de respuesta y la interacción de Visual Studio para las características IDE. Algunos ejemplos de estos análisis son:
    - Análisis en segundo plano de archivos abiertos.
    - Compilación en segundo plano de proyectos con archivos abiertos para realizar símbolos para mejorar la capacidad de respuesta de ciertas características IDE.
    - Creación de sintaxis y cachés de símbolos.
    - Detectar la asociación de diseñadores para archivos de origen, como formularios, controles, etc.

## <a name="default-analysis-scope"></a>Alcance de análisis predeterminado

De forma predeterminada, el análisis de código en vivo para el cálculo en segundo plano de diagnósticos se ejecuta para todos los archivos que se _abren_ en Visual Studio. Pocos de los otros análisis de _fondo mencionados_ anteriormente se ejecutan para todos los proyectos, que tienen al menos un archivo abierto. Mientras que pocos análisis de fondo se ejecutan para toda la solución.

## <a name="custom-analysis-scope"></a>Alcance de análisis personalizado

El ámbito predeterminado de cada análisis en segundo plano se ha ajustado para obtener la experiencia de usuario, la funcionalidad y el rendimiento óptimos para la mayoría de los escenarios y soluciones del cliente. Sin embargo, hay casos en los que los clientes pueden querer personalizar este ámbito para disminuir o aumentar el análisis en segundo plano. Por ejemplo:

- Modo de ahorro de energía: Si los usuarios se ejecutan con la batería del ordenador portátil, es posible que deseen minimizar el consumo de energía para una mayor duración de la batería. En este escenario, desearía minimizar el análisis en segundo plano.
- Análisis de código bajo demanda: si los usuarios prefieren desactivar la ejecución del analizador en vivo y ejecutar manualmente el análisis de código a petición, desearía minimizar el análisis en segundo plano. Consulte Cómo: Ejecutar manualmente el [análisis de código a petición](./how-to-run-code-analysis-manually-for-managed-code.md).
- Análisis completo de la solución: si los usuarios desean ver siempre todos los diagnósticos en todos los archivos de la solución, independientemente de si están abiertos en el editor o no. En este escenario, desearían maximizar el ámbito de análisis en segundo plano para toda la solución.

A partir de Visual Studio 2019 versión 16.5, los usuarios pueden personalizar explícitamente el ámbito de todos los análisis de código en vivo, incluido el cálculo de diagnósticos, para proyectos de Visual Basic y de C. Los ámbitos de análisis disponibles son:

- **Documento actual:** minimiza el ámbito de análisis de código activo para que solo se ejecute para el archivo actual o visible en el editor.
- **Documentos abiertos:** ámbito de análisis de código en vivo predeterminado, como se describe en la sección anterior.
- **Solución completa:** maximiza el ámbito de análisis de código en vivo que se va a ejecutar para todos los archivos y proyectos de toda la solución.

Puede elegir uno de los ámbitos de análisis personalizados anteriores en el cuadro de diálogo Opciones de herramientas siguiendo estos pasos:

1. Para abrir el cuadro de diálogo **Opciones,** en la barra de menús de Visual Studio, elija**Opciones** **de** > herramientas .

2. En el cuadro de diálogo **Opciones** , elija **Editor** > de**texto C o** **Basic** > **Advanced**.

3. Seleccione el ámbito de **análisis de fondo** deseado para personalizar el ámbito de análisis. Elija **OK** cuando haya terminado.

![Alcance de análisis.](./media/background-analysis-scope.png)

> [!NOTE]
> Antes de Visual Studio 2019 versión 16.5, los usuarios pueden personalizar el ámbito de análisis para el cálculo de diagnóstico a toda la solución mediante la casilla **Habilitar análisis completo** de la solución de herramientas del**Editor** > de texto de**opciones** >  **de** > herramientas**C o** la ficha**Avanzadas** **básicas.** >  No hay compatibilidad para minimizar el ámbito de análisis en segundo plano en versiones anteriores de Visual Studio.

## <a name="automatically-minimize-live-code-analysis-scope"></a>Minimice automáticamente el ámbito de análisis de código en vivo

Si Visual Studio detecta que 200 MB o menos de memoria del sistema está disponible para él, minimiza automáticamente el ámbito de análisis de código en vivo a "Documento actual". Si esto ocurre, aparece una alerta que le informa de que Visual Studio ha deshabilitado algunas características. Un botón le permite volver al ámbito de análisis anterior si lo desea.

![Texto de alerta minimizando el alcance del análisis](./media/fsa_alert.png)

## <a name="see-also"></a>Consulte también

- [Suspensión automática de la característica](./automatic-feature-suspension.md)
- [Solicitud de función de modo de ahorro de energía](https://github.com/dotnet/roslyn/issues/38429)
