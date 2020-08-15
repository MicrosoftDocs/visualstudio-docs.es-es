---
title: Configurar el ámbito de análisis de código activo para código administrado
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6df882d50d0c1d052191246605af856743ffdf3d
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2020
ms.locfileid: "88249182"
---
# <a name="how-to-configure-live-code-analysis-scope-for-managed-code"></a>Cómo: configurar el ámbito de análisis de código activo para código administrado

## <a name="what-is-live-code-analysis-for-managed-code"></a>¿Qué es el "Análisis de código activo" para código administrado?
Visual Studio ejecuta una serie de análisis de código activos, también denominado *análisis en segundo plano*, mientras se editan archivos de código fuente en el editor. Algunos de ellos son un análisis mínimo necesario para una experiencia aceptable de edición del IDE de Visual Studio. Algunas de ellas son para mejorar la capacidad de respuesta de las características del IDE. Aunque parte de ellos es habilitar la funcionalidad adicional del IDE, como las correcciones de código y diagnóstico de los analizadores de Roslyn. En función de la funcionalidad, estos análisis se pueden agrupar de la manera siguiente:

- **Cálculo en segundo plano de diagnósticos**: análisis para calcular los errores, las advertencias y las sugerencias en los archivos de código fuente. Estos diagnósticos se muestran como entradas en la lista de errores y como líneas onduladas en el editor. Se pueden clasificar en dos categorías:
  - Diagnóstico del compilador de C# y Visual Basic
  - Diagnósticos del analizador de Roslyn, que incluye:

    - Analizadores integrados del IDE para sugerencias de estilo de código y
    - Paquetes de analizador de terceros [instalados](./install-roslyn-analyzers.md) para los proyectos de la solución actual.

- **Otros análisis en segundo plano**: análisis para mejorar la capacidad de respuesta y la interacción de Visual Studio para las características del IDE. Algunos ejemplos de estos análisis son:
  - Análisis en segundo plano de archivos abiertos.
  - Compilación en segundo plano de proyectos con archivos abiertos para obtener los símbolos para mejorar la capacidad de respuesta de ciertas características del IDE.
  - Compilar la sintaxis y las memorias caché de símbolos.
  - Detección de la Asociación del diseñador para los archivos de código fuente, como formularios, controles, etc.

## <a name="default-analysis-scope"></a>Ámbito de análisis predeterminado

De forma predeterminada, el análisis de código activo para el cálculo en segundo plano de diagnósticos se ejecuta para todos los archivos que se _abren_ en Visual Studio. Algunos de los _demás análisis en segundo plano_ mencionados anteriormente se ejecutan para todos los proyectos, que tienen al menos un archivo abierto. Aunque pocos análisis en segundo plano se ejecutan para toda la solución.

## <a name="custom-analysis-scope"></a>Ámbito de análisis personalizado

El ámbito predeterminado de cada análisis en segundo plano se ha optimizado para mejorar la experiencia del usuario, la funcionalidad y el rendimiento de la mayoría de las soluciones y los escenarios de clientes. Sin embargo, hay casos en los que es posible que los clientes deseen personalizar este ámbito para reducir o aumentar el análisis en segundo plano. Por ejemplo:

- Modo de ahorro de energía: si los usuarios se ejecutan en la batería del portátil, pueden querer minimizar el consumo de energía durante una mayor duración de la batería. En este escenario, sería conveniente minimizar el análisis en segundo plano.
- Análisis de código a petición: si los usuarios prefieren desactivar la ejecución del analizador en vivo y ejecutar manualmente el análisis de código a petición, querrán minimizar el análisis en segundo plano. Vea [Cómo: ejecutar manualmente el análisis de código a petición](./how-to-run-code-analysis-manually-for-managed-code.md).
- Análisis completo de la solución: si los usuarios quieren ver siempre todos los diagnósticos de todos los archivos de la solución, independientemente de si están abiertos en el editor o no. En este escenario, sería conveniente maximizar el ámbito de análisis en segundo plano a toda la solución.

A partir de la versión 16,5 de Visual Studio 2019, los usuarios pueden personalizar explícitamente el ámbito de todo el análisis de código activo, incluido el cálculo de diagnósticos, para los proyectos de C# y Visual Basic. Los ámbitos de análisis disponibles son:

- **Documento actual**: minimiza el ámbito de análisis de código activo para que solo se ejecute para el archivo actual o visible en el editor.
- **Abrir documentos**: el ámbito predeterminado de análisis de código activo, como se describe en la sección anterior.
- **Solución completa**: maximiza el ámbito de análisis de código activo que se ejecutará para todos los archivos y proyectos de toda la solución.

Puede elegir uno de los ámbitos de análisis personalizado anteriores en el cuadro de diálogo Opciones de herramientas siguiendo estos pasos:

1. Para abrir el cuadro de diálogo **Opciones** , en la barra de menús de Visual Studio, elija **herramientas**  >  **Opciones**.

2. En el cuadro de diálogo **Opciones** , elija **Editor de texto**  >  **C#** o **básico**  >  **avanzado**.

3. Seleccione el **ámbito de análisis en segundo plano** deseado para personalizar el ámbito de análisis. Elija **Aceptar** cuando haya terminado.

![Ámbito de análisis.](./media/background-analysis-scope.png)

> [!NOTE]
> Antes de la versión 16,5 de Visual Studio 2019, los usuarios pueden personalizar el ámbito de análisis para el cálculo de diagnósticos en toda la solución mediante la casilla habilitar el análisis de la **solución completa** en **herramientas**  >  **Opciones**  >  **Editor de texto**  >  **C#** o en la **Basic**  >  pestaña**Opciones avanzadas** básicas. No se admite el minimizar el ámbito de análisis en segundo plano en versiones anteriores de Visual Studio.

## <a name="automatically-minimize-live-code-analysis-scope"></a>Minimizar automáticamente el ámbito de análisis de código activo

Si Visual Studio detecta que 200 MB o menos de memoria del sistema está disponible, minimiza automáticamente el ámbito de análisis de código activo en "documento actual". Si esto ocurre, aparecerá una alerta que le informa de que Visual Studio ha deshabilitado algunas características. Un botón le permite volver al ámbito de análisis anterior si lo desea.

![Texto de alerta que minimiza el ámbito de análisis](./media/fsa_alert.png)

## <a name="see-also"></a>Vea también

- [Suspensión automática de la característica](./automatic-feature-suspension.md)
- [Solicitud de característica del modo de ahorro de energía](https://github.com/dotnet/roslyn/issues/38429)
