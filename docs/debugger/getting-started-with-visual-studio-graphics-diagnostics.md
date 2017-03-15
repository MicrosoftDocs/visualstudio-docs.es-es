---
title: "Introducci&#243;n al Diagn&#243;stico de gr&#225;ficos de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59131181-1caa-4b7f-be4b-e84709634edf
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Introducci&#243;n al Diagn&#243;stico de gr&#225;ficos de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En esta sección se explicará cómo usar el diagnóstico de gráficos por primera vez, se capturarán fotogramas en una aplicación de Direct3D y se examinarán esos fotogramas en el Analizador de gráficos.  
  
## Requisitos  
 Para usar el diagnóstico de gráficos en Visual Studio 2015, debe tener una de estas ediciones:  
  
-   Visual Studio 2015 Enterprise  
  
-   Visual Studio 2015 Professional  
  
-   Visual Studio 2015 Community  
  
 [!INCLUDE[downloadvs](../debugger/includes/downloadvs_md.md)]  
  
### Requisitos previos de Windows 10  
 La característica opcional de Windows *Herramientas de gráficos* proporciona la infraestructura de captura y reproducción requerida por el Diagnóstico de gráficos de Windows 10.  
  
 Para obtener información sobre cómo instalar las herramientas de gráficos, vea la sección [Instalar las herramientas de gráficos para Windows 10](#InstallGraphicsTools).  
  
### Requisitos previos de Windows 8.1  
 El Kit de desarrollo de Software \(SDK\) de Windows para Windows 8.1 proporciona la infraestructura de captura y reproducción requerida por el diagnóstico de gráficos en Windows 8.1 y admite el desarrollo para Windows 8.1 y Windows 8.  
  
 [Descargar el Kit de desarrollo de software \(SDK\) para Windows 8.1](https://msdn.microsoft.com/es-es/windows/desktop/bg162891.aspx)  
  
 Para usar una máquina de reproducción remota que ejecute Windows 10 desde una máquina que ejecute Windows 8.1, es necesario instalar el SDK de Windows 10 en la máquina de desarrollo y la característica opcional Herramientas de gráficos en la máquina de reproducción.  
  
##  <a name="InstallGraphicsTools"></a> Instalar las herramientas de gráficos para Windows 10  
 En Windows 10, la infraestructura de diagnóstico de gráficos proporciona una característica opcional de Windows denominada *Herramientas de gráficos*.  Esta característica es necesaria para capturar y reproducir información de gráficos en Windows 10 independientemente de si la aplicación capturada tiene como destino una versión anterior de Windows o de la versión de Direct3D que se use.  Puede instalar previamente la característica de herramientas de gráficos o esperar e instalarla cuando se le solicite la primera vez que inicie una sesión de diagnóstico de gráficos desde Visual Studio.  
  
#### Para instalar las herramientas de gráficos para Windows 10  
  
1.  En el menú **Inicio**, elija **Configuración**.  Aparece el cuadro de diálogo **Configuración**.  
  
2.  En el cuadro de diálogo **Configuración**, elija **Sistema** y luego seleccione **Aplicaciones instaladas** en la lista de configuración del sistema.  
  
3.  En el lado derecho del cuadro de diálogo **Configuración**, elija **Administrar características opcionales** en **Aplicaciones y características instaladas**.  Aparece el cuadro de diálogo **Administrar características opcionales**.  
  
4.  En el cuadro de diálogo **Administrar características opcionales**, elija **Agregar una característica**.  Aparece una lista de las características opcionales que se pueden instalar.  
  
5.  Seleccione **Herramientas de gráficos** en la lista de características y luego elija **Instalar**.  
  
 La característica Herramientas de gráficos también se instala automáticamente al instalar el SDK de Windows 10.  
  
> [!TIP]
>  La característica opcional Herramientas de gráficos de Windows 10 proporciona la funcionalidad de captura y reproducción ligera —por ejemplo, el programa de captura de línea de comandos **dxcap.exe**— que se puede usar en escenarios de compatibilidad, pruebas y diagnóstico en máquinas donde no están instaladas las herramientas de desarrollador.  Para obtener más información, vea el tema [Herramienta de captura de línea de comandos](../debugger/command-line-capture-tool.md).  
  
## Usar el diagnóstico de gráficos por primera vez  
 Ahora que tienen todo lo que necesita, ya puede empezar a usar el diagnóstico de gráficos.  Tan solo tiene que seguir estos pasos:  
  
### 1: Crear una aplicación de Direct3D  
 Si ya tiene su propia aplicación de Direct3D para explorar el diagnóstico de gráficos, perfecto.  En caso contrario, puede usar uno de los ejemplos de Direct3D disponibles en la Galería de código.  
  
-   Para probar el diagnóstico de gráficos con Direct3D 12 en Windows 10 mediante Visual Studio de 2015, siga el [ejemplo Direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) para Windows 10.  
  
-   Para probar el diagnóstico de gráficos con Direct3D 11 en Windows 10 o Windows 8.1, puede usar las plantillas de proyecto de **Aplicación DirectX \(Windows Universal\)** o **Aplicación DirectX \(Windows 8.1\)**.  O bien, si desea algo más interesante, pruebe el [ejemplo de juego de laberinto de DirectX](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345) para Windows 8.1.  
  
 Asegúrese de que puede compilar la aplicación antes de continuar.  
  
### 2: Iniciar una sesión de diagnóstico de gráficos  
 Ahora está listo para empezar la primera sesión de diagnóstico de gráficos.  En el menú principal de Visual Studio, elija **Depurar, Gráficos, Iniciar diagnóstico** o simplemente presione **ALT\+F5**.  La aplicación se inicia en diagnóstico de gráficos y muestra las ventanas de sesión de diagnóstico en Visual Studio.  
  
> [!IMPORTANT]
>  Si está ejecutando la aplicación en Windows 10 y todavía no ha instalado la característica opcional de herramientas de gráficos, se le pedirá que lo haga ahora.  Debe instalarla para poder usar el diagnóstico de gráficos en Windows 10.  
  
### 3: Capturar fotogramas  
 Una vez iniciada la aplicación, ya se pueden capturar fotogramas.  
  
##### Para capturar fotogramas individuales  
  
-   En Visual Studio, elija el botón **Capturar fotograma** en la barra de herramientas de gráficos o la ventana de sesión de diagnóstico.  O bien, si la aplicación tiene el foco, simplemente presione **Impr Pant**.  
  
##### Para capturar una secuencia de fotogramas  
  
-   En Visual Studio, en la ventana de la sesión de diagnóstico, establezca el **Número de fotogramas para capturar** en el número de fotogramas que desee capturar en secuencia; a continuación, capture la secuencia mediante cualquiera de los métodos descritos anteriormente para capturar fotogramas individuales.  
  
     Para volver a capturar fotogramas individuales, establezca **Número de fotogramas para capturar** en `1`.  
  
 Cuando termine de capturar fotogramas, salga de la aplicación o elija el botón **Detener** en la barra de herramientas de gráficos o en la ventana de sesión de diagnóstico.  
  
### 4: Examinar los fotogramas capturados en el Analizador de gráficos  
 Ahora puede examinar los fotogramas que acaba de capturar.  Para empezar a analizar un fotograma, elija el número del fotograma en la ventana de sesión de diagnóstico.  El fotograma se abrirá en el **Analizador de gráficos**, donde puede usar las herramientas de diagnóstico de gráficos para examinar cómo su aplicación usa Direct3D para localizar problemas de representación, o usar la herramienta **Análisis de fotogramas** para estudiar su rendimiento.  
  
 Si seleccionó el fotograma equivocado en la ventana de la sesión de diagnóstico o desea examinar otro fotograma, puede seleccionar uno nuevo el Analizador de gráficos.  En la pestaña **Destino de la representación** de la ventana de registro de gráficos, debajo de la imagen del destino de representación, expanda la **Lista de fotogramas** y, a continuación, elija otro fotograma para examinarlo.  
  
 Para obtener más información sobre cómo usar conjuntamente las herramientas del Analizador de gráficos, vea los [Ejemplos de diagnóstico de gráficos](../debugger/graphics-diagnostics-examples.md).  
  
## Vea también  
 [Gráficos de Direct3D 12](http://msdn.microsoft.com/es-es/52094ae3-3b44-4689-9ee7-1ba1b3a779cb)