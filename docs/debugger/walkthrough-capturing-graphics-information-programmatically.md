---
title: "Tutorial: Capturar informaci&#243;n de gr&#225;ficos mediante programaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5adeff9-afaf-4047-b5ce-ef0aefe710eb
caps.latest.revision: 21
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Tutorial: Capturar informaci&#243;n de gr&#225;ficos mediante programaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede utilizar el Diagnóstico de gráficos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para capturar mediante programación información de gráficos desde la aplicación Direct3D.  
  
 La captura mediante programación es útil en escenarios tales como:  
  
-   Al iniciar la captura cuando la aplicación de gráficos no usa la cadena de intercambio \(por ejemplo, cuando se representa en una textura\).  
  
-   Al iniciar la captura cuando la aplicación no se representa \(por ejemplo, cuando usa DirectCompute para hacer cálculos\).  
  
-   Llame a `CaptureCurrentFrame` cuando un problema de representación sea difícil de anticipar y de capturar en pruebas manuales, pero se puede predecir mediante programación usando información sobre el estado de la aplicación en tiempo de ejecución.  
  
##  <a name="CaptureDX11_2"></a> Captura mediante programación en Windows 8.1  
 En esta parte del tutorial se explica la captura mediante programación en aplicaciones que usan la API DirectX 11.2 en Windows 8.1, que emplea el método de captura robusta. Para obtener información sobre cómo utilizar la captura mediante programación en aplicaciones que utilicen versiones anteriores de DirectX en Windows 8.0, vea [Captura mediante programación en Windows 8.0 y versiones anteriores](#CaptureDX11_1) más adelante en este tutorial.  
  
 Esta sección muestra cómo realizar estas tareas:  
  
-   Preparación de la aplicación para el uso de la captura mediante programación  
  
-   Obtención de la interfaz IDXGraphicsAnalysis  
  
-   Capturar información de gráficos  
  
> [!NOTE]
>  Las implementaciones previas de la captura mediante programación dependían de Herramientas remotas para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para ofrecer la funcionalidad de captura, pero Windows 8.1 admite la captura directamente con Direct3D 11.2. El resultado es que ya no debe instalar las Herramientas remotas para la captura mediante programación en Windows 8.1.  
  
### Preparación de la aplicación para el uso de la captura mediante programación  
 Para usar la captura mediante programación en la aplicación, debe incluir los encabezados necesarios. Estos encabezados forman parte del SDK de Windows 8.1.  
  
##### Cómo incluir encabezados de captura mediante programación  
  
-   Incluya estos encabezados en el archivo fuente donde define la interfaz IDXGraphicsAnalysis:  
  
    ```  
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    >  No incluya el archivo de encabezado `vsgcapture.h` \(que admite la captura mediante programación en Windows 8.0 y versiones anteriores\) para efectuar la captura mediante programación en las aplicaciones de Windows 8.1. Este encabezado es incompatible con DirectX 11.2. Si este archivo se incluye después de incluir el encabezado `d3d11_2`, el compilador emite una advertencia. Si `vsgcapture.h` se incluye antes que `d3d11_2`, la aplicación no se iniciará.  
  
    > [!NOTE]
    >  Si tiene instalada la versión del SDK de DirectX de junio de 2010 en su equipo y la ruta de acceso de inclusión de su proyecto contiene `%DXSDK_DIR%include\x86`, muévalo al final de la ruta de acceso de inclusión. Haga lo mismo para la ruta de la biblioteca.  
  
#### Windows Phone 8,1  
 Dado que el SDK de Windows Phone 8.1 no incluye el encabezado `DXProgrammableCapture.h`, deberá definir la interfaz `IDXGraphicsAnalysis` de manera que pueda usar los métodos `BeginCapture()` y `EndCapture()`. Incluya los demás encabezados tal y como se describe en la sección anterior.  
  
###### Cómo definir la interfaz IDXGraphicsAnalysis  
  
-   Defina la interfaz IDXGraphicsAnalysis en el mismo archivo en el que ha incluido los archivos de encabezado.  
  
    ```  
    interface DECLSPEC_UUID("9f251514-9d4d-4902-9d60-18988ab7d4b5") DECLSPEC_NOVTABLE  
    IDXGraphicsAnalysis : public IUnknown  
    {  
        STDMETHOD_(void, BeginCapture)() PURE;  
        STDMETHOD_(void, EndCapture)() PURE;  
    };  
    ```  
  
 Por comodidad, puede realizar estos pasos en un archivo de encabezado nuevo y, a continuación, incluirlo donde la aplicación lo necesite.  
  
### Obtención de la interfaz IDXGraphicsAnalysis  
 Antes de poder capturar información gráfica desde DirectX 11.2, debe obtener la interfaz de depuración DXGI.  
  
> [!IMPORTANT]
>  Al usar la captura mediante programación debe seguir ejecutando la aplicación en diagnóstico de gráficos \(Alt\+F5 en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\).  
  
##### Cómo obtener la interfaz IDXGraphicsAnalysis  
  
-   Utilice el código siguiente para enlazar la interfaz IDXGraphicsAnalysis a la interfaz de depuración DXGI.  
  
    ```  
    IDXGraphicsAnalysis* pGraphicsAnalysis;  
    HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
    ```  
  
     Asegúrese de comprobar el `HRESULT` devuelto por `DXGIGetDebugInterface1` para garantizar que obtiene una interfaz válida antes de utilizarla:  
  
    ```  
    if (FAILED(getAnalysis))  
    {  
        // Abort program or disable programmatic capture in your app.  
    }  
    ```  
  
    > [!NOTE]
    >  Si `DXGIGetDebugInterface1` devuelve `E_NOINTERFACE` \(`error: E_NOINTERFACE No se admite dicha interfaz`\), asegúrese de que la aplicación se esté ejecutando en Diagnóstico de gráficos \(Alt\+F5 en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\).  
  
### Capturar información de gráficos  
 Tenga en cuenta que tiene una interfaz `IDXGraphicsAnalysis` válida, puede utilizar `BeginCapture` y `EndCapture` para capturar información de gráficos.  
  
##### Cómo capturar información de gráficos  
  
-   Para empezar a capturar información de gráficos, utilice `BeginCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     La captura empieza inmediatamente cuando se llama a `BeginCapture`; no espera a que empiece el fotograma siguiente. La captura se detiene cuando el fotograma actual se presenta o cuando llama a `EndCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  
  
##  <a name="CaptureDX11_1"></a> Captura mediante programación en Windows 8.0 y versiones anteriores  
 Esta parte del tutorial explica la captura mediante programación en aplicaciones para Windows 8.0 y versiones anteriores que usan la API DirectX 11.1, que emplea el método de captura heredada. Para obtener información sobre cómo utilizar la captura mediante programación en aplicaciones que utilicen DirectX 11.2 en Windows 8.1, vea [Captura mediante programación en Windows 8.1](#CaptureDX11_2) más arriba en este tutorial.  
  
 Esta parte muestra las tareas siguientes:  
  
-   Preparación del equipo para el uso de la captura mediante programación  
  
-   Preparación de la aplicación para el uso de la captura mediante programación  
  
-   Configuración del nombre y la ubicación del archivo de registro de gráficos  
  
-   Uso de la API `CaptureCurrentFrame`  
  
### Preparación del equipo para el uso de la captura mediante programación  
 La API de captura mediante programación utiliza Herramientas remotas para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para ofrecer la funcionalidad de captura. El equipo en el que se ejecuta la aplicación debe tener instaladas las herramientas remotas, incluso si utiliza la captura mediante programación en el ordenador local.[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no tiene que estar ejecutándose cuando realiza la captura mediante programación en un equipo local.  
  
 Para utilizar las API de captura remota en una aplicación que se ejecuta en un equipo, primero debe instalar las Herramientas remotas para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en ese equipo. Cada versión de las herramientas remotas admite diferentes plataformas de hardware. Para más información sobre cómo instalar las herramientas remotas, vea la [página de descargas de herramientas remotas](http://go.microsoft.com/fwlink/p/?LinkId=246691) en el sitio web de descargas de Microsoft.  
  
 Otra opción es que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instale los componentes necesarios para realizar la captura remota para aplicaciones de 32 bits.  
  
> [!NOTE]
>  Como la mayoría de las aplicaciones de escritorio para Windows, incluyendo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], no son compatibles con [!INCLUDE[win8](../debugger/includes/win8_md.md)] en dispositivos ARM, utilizar Herramientas remotas para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] junto con la API de captura mediante programación es la única manera de capturar diagnósticos de gráficos en dispositivos ARM.  
  
### Preparación de la aplicación para el uso de la captura mediante programación  
 Para utilizar las herramientas de Diagnóstico de gráficos, antes debe capturar la información gráfica en la que se basa. Puede capturar la información mediante programación utilizando la API `CaptureCurrentFrame`.  
  
##### Preparación de la aplicación para capturar información de gráficos mediante programación  
  
1.  Asegúrese de que el encabezado `vsgcapture.h` se incluye en el código fuente de la aplicación. Puede incluirse en una sola ubicación, por ejemplo, en el archivo de código fuente en el que llamará a la API de captura mediante programación, o en un archivo de encabezado precompilado para llamar a la API desde varios archivos de código fuente.  
  
2.  En el código fuente de la aplicación, cuando quiera capturar el resto del fotograma actual, llame a `g_pVsgDbg->CaptureCurrentFrame()`. Este método no toma ningún parámetro y no devuelve ningún valor.  
  
### Configuración del nombre y la ubicación del archivo de registro de gráficos  
 El registro de gráficos se crea en la ubicación que está definida por las macros `DONT_SAVE_VSGLOG_TO_TEMP` y `VSG_DEFAULT_RUN_FILENAME`.  
  
##### Configuración del nombre y la ubicación del archivo de registro de gráficos  
  
-   Para evitar que el registro de gráficos se escriba en el directorio temporal, antes de la línea `#include <vsgcapture.h>`, agregue el código siguiente:  
  
    ```  
    #define DONT_SAVE_VSGLOG_TO_TEMP  
    ```  
  
     Puede definir este valor para escribir el registro de gráficos en una ubicación relacionada con el directorio de trabajo o con una ruta absoluta si la definición de `VSG_DEFAULT_RUN_FILENAME` es una ruta absoluta.  
  
-   Para guardar el registro de gráficos en una ubicación diferente o asignarle un nombre diferente, antes de la línea `#include <vsgcapture.h>`, agregue el código siguiente:  
  
    ```  
    #define VSG_DEFAULT_RUN_FILENAME <filename>  
    ```  
  
     Si no realiza este paso, el nombre del archivo será default.vsglog. Si no define `DONT_SAVE_VSGLOG_TO_TEMP`, la ubicación del archivo estará relacionada con el directorio temporal; de lo contrario, estará relacionada con el directorio de trabajo u otra ubicación si ha especificado un nombre de archivo absoluto.  
  
 Para las aplicaciones de [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)], la ubicación del directorio temporal es específica para cada usuario y aplicación y normalmente se encuentra en una ubicación como C:\\users\\*username*\\AppData\\Local\\Packages\\*nombre de familia del paquete*\\TempState\\. Para las aplicaciones de escritorio, la ubicación del directorio temporal es específica para cada usuario y normalmente se encuentra en una ubicación como C:\\Users\\*username*\\AppData\\Local\\Temp\\.  
  
> [!NOTE]
>  Para escribir una ubicación concreta, debe tener permisos para escribir en esa ubicación; de lo contrario, se produce un error. Tenga en cuenta que las aplicaciones de [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] son más restringidas que las aplicaciones de escritorio en cuanto a dónde pueden escribir datos y es posible que requieran configuración adicional para escribir en determinadas ubicaciones.  
  
### Captura de la información de gráficos  
 Después de preparar la aplicación para la captura mediante programación y opcionalmente configurar la ubicación y el nombre del archivo de registro de gráficos, compile la aplicación y, a continuación, ejecútela o depúrela para capturar datos; no inicie el diagnóstico de gráficos desde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cuando utilice la API de captura mediante programación. El registro de gráficos se escribe en la ubicación que usted especifique. Si quiere mantener esta versión del registro, muévala a otra ubicación; de lo contrario, se sobrescribirá cuando vuelva a ejecutar la aplicación.  
  
> [!TIP]
>  También puede capturar información de gráficos manualmente mientras utiliza la captura mediante programación: con el foco en la aplicación, pulse **Imprimir pantalla**. Puede utilizar esta técnica para capturar información de gráficos adicional que la API de captura mediante programación no capture.  
  
## Pasos siguientes  
 Este tutorial le ha mostrado cómo capturar información de gráficos mediante programación. El paso siguiente puede ser:  
  
-   Aprender cómo analizar la información de gráficos capturada utilizando la herramienta Diagnóstico de gráficos. Vea [Información general](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## Vea también  
 [Capturar información de gráficos](../debugger/capturing-graphics-information.md)   
 [Tutorial: Capturar información de gráficos](../debugger/walkthrough-capturing-graphics-information.md)