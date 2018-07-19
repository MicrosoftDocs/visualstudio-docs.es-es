---
title: 'Tutorial: Capturar información de gráficos mediante programación | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 641e98d1bbe5d54f69f458cec6642ceac484eff1
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433223"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Tutorial: Capturar información de gráficos mediante programación
Puede utilizar el Diagnóstico de gráficos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para capturar mediante programación información de gráficos desde la aplicación Direct3D.  
  
 La captura mediante programación es útil en escenarios tales como:  
  
-   Al iniciar la captura cuando la aplicación de gráficos no usa la cadena de intercambio (por ejemplo, cuando se representa en una textura).  
  
-   Al iniciar la captura cuando la aplicación no se representa (por ejemplo, cuando usa DirectCompute para hacer cálculos).  
  
-   Llame a `CaptureCurrentFrame`cuando un problema de representación sea difícil de anticipar y de capturar en pruebas manuales, pero se puede predecir mediante programación usando información sobre el estado de la aplicación en tiempo de ejecución.  
  
##  <a name="CaptureDX11_2"></a> Captura mediante programación en Windows 10  
 Esta parte del tutorial explica la captura mediante programación en aplicaciones que usan la API DirectX 11.2 en Windows 10, que usa el método de captura robusta.
  
 Esta sección muestra cómo realizar estas tareas:  
  
-   Preparación de la aplicación para el uso de la captura mediante programación  
  
-   Obtención de la interfaz IDXGraphicsAnalysis  
  
-   Capturar información de gráficos  
  
> [!NOTE]
>  Las implementaciones previas de captura mediante programación dependían de herramientas remotas para Visual Studio para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para proporcionar funcionalidad de captura.
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Preparación de la aplicación para el uso de la captura mediante programación  
 Para usar la captura mediante programación en la aplicación, debe incluir los encabezados necesarios. Estos encabezados forman parte del SDK de Windows 10.  
  
##### <a name="to-include-programmatic-capture-headers"></a>Cómo incluir encabezados de captura mediante programación  
  
-   Incluya estos encabezados en el archivo fuente donde define la interfaz IDXGraphicsAnalysis:  
  
    ```cpp
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    >  No incluya el encabezado archivo vsgcapture.h—which admite captura mediante programación en Windows 8.0 y versiones anteriores, para realizar la captura mediante programación en las aplicaciones de Windows 10. Este encabezado es incompatible con DirectX 11.2. Si este archivo se incluye después de que se incluye el encabezado d3d11_2.h, el compilador emite una advertencia. Si se incluye vsgcapture.h antes d3d11_2.h, no se iniciará la aplicación.  
  
    > [!NOTE]
    >  Si tiene instalada la versión del SDK de DirectX de junio de 2010 en su equipo y la ruta de acceso de inclusión de su proyecto contiene `%DXSDK_DIR%includex86`, muévalo al final de la ruta de acceso de inclusión. Haga lo mismo para la ruta de la biblioteca.  
  
### <a name="getting-the-idxgraphicsanalysis-interface"></a>Obtención de la interfaz IDXGraphicsAnalysis  
 Antes de poder capturar información gráfica desde DirectX 11.2, debe obtener la interfaz de depuración DXGI.  
  
> [!IMPORTANT]
>  Cuando se usa la captura mediante programación, aun así, debe ejecutar la aplicación en diagnóstico de gráficos (ALT+F5 en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) o en el [herramienta de captura de línea de comandos](command-line-capture-tool.md).  
  
##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Cómo obtener la interfaz IDXGraphicsAnalysis  
  
-   Utilice el código siguiente para enlazar la interfaz IDXGraphicsAnalysis a la interfaz de depuración DXGI.  
  
    ```cpp
    IDXGraphicsAnalysis* pGraphicsAnalysis;  
    HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
    ```  
  
     No olvide consultar la `HRESULT` devuelto por [DXGIGetDebugInterface1](https://msdn.microsoft.com/library/windows/desktop/dn457937(v=vs.85).aspx) para asegurarse de obtener una interfaz válida antes de usarlo:  
  
    ```cpp
    if (FAILED(getAnalysis))  
    {  
        // Abort program or disable programmatic capture in your app.  
    }  
    ```  
  
    > [!NOTE]
    >  Si `DXGIGetDebugInterface1` devuelve `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`), asegúrese de que la aplicación se esté ejecutando en Diagnóstico de gráficos (Alt+F5 en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).  
  
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

- Después de llamar a `EndCapture`, liberar el objeto de gráficos. 
  
## <a name="next-steps"></a>Pasos siguientes  
 Este tutorial le ha mostrado cómo capturar información de gráficos mediante programación. El paso siguiente puede ser:  
  
-   Aprender cómo analizar la información de gráficos capturada utilizando la herramienta Diagnóstico de gráficos. Consulte [Introducción](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Capturar información de gráficos](walkthrough-capturing-graphics-information.md)   
 [Capturar información de gráficos](capturing-graphics-information.md)   
 [Herramienta de captura de línea de comandos](command-line-capture-tool.md)
