---
title: 'Tutorial: Captura de información de gráficos mediante programación | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7533c205b95b016c43bd2eef614b4c2825596e74
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835659"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Tutorial: Captura de información de gráficos mediante programación
Puede utilizar el Diagnóstico de gráficos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para capturar mediante programación información de gráficos desde la aplicación Direct3D.

La captura mediante programación es útil en escenarios tales como:

- Al iniciar la captura cuando la aplicación de gráficos no usa la cadena de intercambio (por ejemplo, cuando se representa en una textura).

- Al iniciar la captura cuando la aplicación no se representa (por ejemplo, cuando usa DirectCompute para hacer cálculos).

- Llame a `CaptureCurrentFrame` cuando un problema de representación sea difícil de anticipar y de capturar en pruebas manuales, pero se pueda predecir mediante programación con información sobre el estado de la aplicación en tiempo de ejecución.

## <a name="programmatic-capture-in-windows-10"></a><a name="CaptureDX11_2"></a> Captura mediante programación en Windows 10
En esta parte del tutorial se explica la captura mediante programación en aplicaciones que usan la API DirectX 11.2 en Windows 10, que emplea el método de captura robusta.

Esta sección muestra cómo realizar estas tareas:

- Preparación de la aplicación para el uso de la captura mediante programación

- Obtención de la interfaz IDXGraphicsAnalysis

- Capturar información de gráficos

> [!NOTE]
> Las implementaciones previas de la captura mediante programación dependían de Herramientas remotas para Visual Studio para ofrecer la funcionalidad de captura.

### <a name="preparing-your-app-to-use-programmatic-capture"></a>Preparación de la aplicación para el uso de la captura mediante programación
Para usar la captura mediante programación en la aplicación, debe incluir los encabezados necesarios. Estos encabezados forman parte del SDK de Windows 10.

##### <a name="to-include-programmatic-capture-headers"></a>Cómo incluir encabezados de captura mediante programación

- Incluya estos encabezados en el archivo fuente donde define la interfaz IDXGraphicsAnalysis:

    ```cpp
    #include <DXGItype.h>
    #include <dxgi1_2.h>
    #include <dxgi1_3.h>
    #include <DXProgrammableCapture.h>
    ```

    > [!IMPORTANT]
    > No incluya el archivo de encabezado vsgcapture.h, que admite la captura mediante programación en Windows 8.0 y versione anteriores, para efectuar la captura mediante programación en las aplicaciones de Windows 10. Este encabezado es incompatible con DirectX 11.2. Si este archivo se incluye después de incluir el encabezado d3d11_2.h, el compilador emite una advertencia. Si vsgcapture.h se incluye antes que d3d11_2.h, la aplicación no se iniciará.

    > [!NOTE]
    > Si tiene instalada la versión del SDK de DirectX de junio de 2010 en su equipo y la ruta de acceso de inclusión de su proyecto contiene `%DXSDK_DIR%includex86`, muévalo al final de la ruta de acceso de inclusión. Haga lo mismo para la ruta de la biblioteca.

### <a name="getting-the-idxgraphicsanalysis-interface"></a>Obtención de la interfaz IDXGraphicsAnalysis
Antes de poder capturar información gráfica desde DirectX 11.2, debe obtener la interfaz de depuración DXGI.

> [!IMPORTANT]
> Al usar la captura mediante programación debe seguir ejecutando la aplicación en diagnóstico de gráficos (Alt+F5 en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) o bajo la [Herramienta de captura de línea de comandos](command-line-capture-tool.md).

##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Cómo obtener la interfaz IDXGraphicsAnalysis

- Utilice el código siguiente para enlazar la interfaz IDXGraphicsAnalysis a la interfaz de depuración DXGI.

  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));
  ```

  Asegúrese de comprobar el valor `HRESULT` devuelto por [DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) para garantizar que obtiene una interfaz válida antes de usarla:

  ```cpp
  if (FAILED(getAnalysis))
  {
      // Abort program or disable programmatic capture in your app.
  }
  ```

  > [!NOTE]
  > Si `DXGIGetDebugInterface1` devuelve `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`), asegúrese de que la aplicación se esté ejecutando en Diagnóstico de gráficos (Alt+F5 en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).

### <a name="capturing-graphics-information"></a>Capturar información de gráficos
Tenga en cuenta que tiene una interfaz `IDXGraphicsAnalysis` válida, puede utilizar `BeginCapture` y `EndCapture` para capturar información de gráficos.

##### <a name="to-capture-graphics-information"></a>Cómo capturar información de gráficos

- Para empezar a capturar información de gráficos, utilice `BeginCapture`:

    ```cpp
    ...
    pGraphicsAnalysis->BeginCapture();
    ...
    ```

    La captura empieza inmediatamente cuando se llama a `BeginCapture` ; no espera a que empiece el fotograma siguiente. La captura se detiene cuando el fotograma actual se presenta o cuando llama a `EndCapture`:

    ```cpp
    ...
    pGraphicsAnalysis->EndCapture();
    ...
    ```

- Después de la llamada a `EndCapture`, libere el objeto gráfico.

## <a name="next-steps"></a>Pasos siguientes
Este tutorial le ha mostrado cómo capturar información de gráficos mediante programación. El paso siguiente puede ser:

- Aprender cómo analizar la información de gráficos capturada utilizando la herramienta Diagnóstico de gráficos. Vea [Información general](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>Vea también
- [Tutorial: Captura de información de gráficos](walkthrough-capturing-graphics-information.md)
- [Capturing Graphics Information](capturing-graphics-information.md)
- [Herramienta de captura de línea de comandos](command-line-capture-tool.md)
