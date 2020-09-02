---
title: Introducción con Diagnóstico de gráficos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 59131181-1caa-4b7f-be4b-e84709634edf
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9056fdae9d0eff55c572d8e38503d88269dbde3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704707"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Introducción al Diagnóstico de gráficos de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En esta sección se explicará cómo usar el diagnóstico de gráficos por primera vez, se capturarán fotogramas en una aplicación de Direct3D y se examinarán esos fotogramas en el Analizador de gráficos.

## <a name="requirements"></a>Requisitos
 Para usar el diagnóstico de gráficos en Visual Studio 2015, debe tener una de estas ediciones:

- Visual Studio 2015 Enterprise

- Visual Studio 2015 Professional

- Visual Studio 2015 Community

  [!INCLUDE[downloadvs](../includes/downloadvs-md.md)]

### <a name="windows-10-prerequisites"></a>Requisitos previos de Windows 10
 La característica opcional de Windows *Herramientas de gráficos* proporciona la infraestructura de captura y reproducción requerida por el Diagnóstico de gráficos de Windows 10.

 Para obtener información sobre cómo instalar las herramientas de gráficos, vea la sección [Instalación de las herramientas de gráficos para Windows 10](#InstallGraphicsTools).

### <a name="windows-81-prerequisites"></a>Requisitos previos de Windows 8.1
 El Kit de desarrollo de Software (SDK) de Windows para Windows 8.1 proporciona la infraestructura de captura y reproducción requerida por el diagnóstico de gráficos en Windows 8.1 y admite el desarrollo para Windows 8.1 y Windows 8.

 [Descargue el kit de desarrollo de software (SDK) de Windows para Windows 8.1](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)

 Para usar una máquina de reproducción remota que ejecute Windows 10 desde una máquina que ejecute Windows 8.1, es necesario instalar el SDK de Windows 10 en la máquina de desarrollo y la característica opcional Herramientas de gráficos en la máquina de reproducción.

## <a name="install-graphics-tools-for-windows-10"></a><a name="InstallGraphicsTools"></a> Instalación de las herramientas de gráficos para Windows 10
 En Windows 10, la infraestructura de diagnóstico de gráficos proporciona una característica opcional de Windows denominada *Herramientas de gráficos*. Esta característica es necesaria para capturar y reproducir información de gráficos en Windows 10 independientemente de si la aplicación capturada tiene como destino una versión anterior de Windows o de la versión de Direct3D que se use. Puede instalar previamente la característica de herramientas de gráficos o esperar e instalarla cuando se le solicite la primera vez que inicie una sesión de diagnóstico de gráficos desde Visual Studio.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Para instalar las herramientas de gráficos para Windows 10

1. En el menú **Inicio** , elija **configuración**. Aparece el cuadro de diálogo de **configuración** .

2. En el cuadro de diálogo **configuración** , elija **sistema**y, a continuación, seleccione **aplicaciones instaladas** en la lista de configuraciones del sistema.

3. En el lado derecho del cuadro de diálogo **configuración** , elija **administrar características opcionales** en **aplicaciones y características instaladas**. Aparece el cuadro de diálogo **Administrar características opcionales**.

4. En el cuadro de diálogo **Administrar características opcionales**, elija **Agregar una característica**. Aparece una lista de las características opcionales que se pueden instalar.

5. Seleccione **Herramientas de gráficos** en la lista de características y luego elija **Instalar**.

   La característica Herramientas de gráficos también se instala automáticamente al instalar el SDK de Windows 10.

> [!TIP]
> La característica opcional Herramientas de gráficos de Windows 10 proporciona la funcionalidad de captura y reproducción ligera (por ejemplo, el programa de captura de línea de comandos **dxcap.exe**) que se puede usar en escenarios de compatibilidad, pruebas y diagnóstico en máquinas donde no están instaladas las herramientas de desarrollador. Para obtener más información, vea el tema [Herramienta de captura de línea de comandos](../debugger/command-line-capture-tool.md).

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Usar el diagnóstico de gráficos por primera vez
 Ahora que tienen todo lo que necesita, ya puede empezar a usar el diagnóstico de gráficos. Tan solo tiene que seguir estos pasos:

### <a name="1---create-a-direct3d-app"></a>1: Crear una aplicación de Direct3D
 Si ya tiene su propia aplicación de Direct3D para explorar el diagnóstico de gráficos, perfecto. En caso contrario, puede usar uno de los ejemplos de Direct3D disponibles en la Galería de código.

- Para probar Diagnóstico de gráficos con Direct3D 12 en Windows 10 con Visual Studio 2015, pruebe el [ejemplo de UAP de Direct3D 12](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) para Windows 10.

- Para probar Diagnóstico de gráficos con Direct3D 11 en Windows 10 o Windows 8.1, puede usar las plantillas de proyecto **aplicación DirectX (Windows universal)** o  **aplicación DirectX (Windows 8.1)** . O bien, para algo más interesante, pruebe el [ejemplo de juego de DirectX Marble Maze](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345) para Windows 8.1.

  Asegúrese de que puede compilar la aplicación antes de continuar.

### <a name="2---start-a-graphics-diagnostics-session"></a>2: Iniciar una sesión de diagnóstico de gráficos
 Ahora está listo para empezar la primera sesión de diagnóstico de gráficos. En el menú principal de Visual Studio, elija **depurar, gráficos, iniciar diagnóstico**o simplemente presione **Alt + F5**. La aplicación se inicia en diagnóstico de gráficos y muestra las ventanas de sesión de diagnóstico en Visual Studio.

> [!IMPORTANT]
> Si está ejecutando la aplicación en Windows 10 y todavía no ha instalado la característica opcional de herramientas de gráficos, se le pedirá que lo haga ahora. Debe instalarla para poder usar el diagnóstico de gráficos en Windows 10.

### <a name="3---capture-frames"></a>3: Capturar fotogramas
 Una vez iniciada la aplicación, ya se pueden capturar fotogramas.

##### <a name="to-capture-single-frames"></a>Para capturar fotogramas individuales

- En Visual Studio, elija el botón **Capturar fotograma** en la barra de herramientas de gráficos o la ventana de sesión de diagnóstico. O bien, si la aplicación tiene el foco, simplemente presione **Imprimir pantalla**.

##### <a name="to-capture-a-sequence-of-frames"></a>Para capturar una secuencia de fotogramas

- En Visual Studio, en la ventana de la sesión de diagnóstico, establezca el **Número de fotogramas para capturar** en el número de fotogramas que quiera capturar en secuencia; a continuación, capture la secuencia mediante cualquiera de los métodos descritos anteriormente para capturar fotogramas individuales.

   Para capturar fotogramas únicos de nuevo, establezca los **fotogramas que se van a capturar** en `1` .

  Cuando termine de capturar fotogramas, salga de la aplicación o elija el botón **Detener** en la barra de herramientas de gráficos o en la ventana de sesión de diagnóstico.

### <a name="4--examine-captured-frames-in-the-graphics-analyzer"></a>4: Examinar los fotogramas capturados en el Analizador de gráficos
 Ahora puede examinar los fotogramas que acaba de capturar. Para empezar a analizar un fotograma, elija el número del fotograma en la ventana de sesión de diagnóstico. El fotograma se abrirá en el **Analizador de gráficos**, donde puede usar las herramientas de Diagnóstico de gráficos para examinar cómo su aplicación usa Direct3D para localizar problemas de representación, o usar la herramienta **Análisis de fotogramas** para estudiar su rendimiento.

 Si seleccionó el fotograma equivocado en la ventana de la sesión de diagnóstico o desea examinar otro fotograma, puede seleccionar uno nuevo el Analizador de gráficos. En la pestaña **Destino de la representación** de la ventana de registro de gráficos, debajo de la imagen del destino de representación, expanda la **Lista de fotogramas** y, a continuación, elija otro fotograma para examinarlo.

 Para obtener más información sobre cómo usar conjuntamente las herramientas del Analizador de gráficos, vea [Ejemplos](../debugger/graphics-diagnostics-examples.md).

## <a name="see-also"></a>Consulte también
 [Gráficos de Direct3D 12](https://msdn.microsoft.com/52094ae3-3b44-4689-9ee7-1ba1b3a779cb)
