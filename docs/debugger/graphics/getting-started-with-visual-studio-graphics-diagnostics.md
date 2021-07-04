---
title: Introducción a Diagnóstico de gráficos de Visual Studio | Microsoft Docs
description: Prepárese para usar Diagnóstico de gráficos por primera vez y, después, capture fotogramas de una aplicación de Direct3D y examínelos en el Analizador de gráficos.
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 70512b4df3be7f11973af244c336b22c59c90f8f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387611"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Introducción al Diagnóstico de gráficos de Visual Studio
En esta sección se explicará cómo usar el diagnóstico de gráficos por primera vez, se capturarán fotogramas en una aplicación de Direct3D y se examinarán esos fotogramas en el Analizador de gráficos.

## <a name="requirements"></a>Requisitos
 Para utilizar Diagnóstico de gráficos en Visual Studio, debe usar Visual Studio Enterprise, Professional o Community.  Otras ediciones, incluida Visual Studio Code, no incluyen esta característica.

 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]

### <a name="windows-10-prerequisites"></a>Requisitos previos de Windows 10
 La característica opcional de Windows *Herramientas de gráficos* proporciona la infraestructura de captura y reproducción requerida por el Diagnóstico de gráficos de Windows 10.

 Para obtener información sobre cómo instalar las herramientas de gráficos, vea la sección [Instalación de las herramientas de gráficos para Windows 10](#InstallGraphicsTools).

## <a name="install-graphics-tools-for-windows-10"></a><a name="InstallGraphicsTools"></a> Instalación de las herramientas de gráficos para Windows 10
 En Windows 10, la infraestructura de diagnóstico de gráficos proporciona una característica opcional de Windows denominada *Herramientas de gráficos*. Esta característica es necesaria para capturar y reproducir información de gráficos en Windows 10 independientemente de si la aplicación capturada tiene como destino una versión anterior de Windows o de la versión de Direct3D que se use. Puede instalar previamente la característica de herramientas de gráficos o esperar e instalarla cuando se le solicite la primera vez que inicie una sesión de diagnóstico de gráficos desde Visual Studio.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Para instalar las herramientas de gráficos para Windows 10

1. En Buscar, escriba **Aplicaciones y características** y, a continuación, abra la configuración de **Aplicaciones y características**.

2. En el lado derecho de la configuración de **Aplicaciones y características**, seleccione **Características opcionales**, en **Aplicaciones y características**.

   Se mostrará la configuración de **Características opcionales**.

3. En la configuración de **Características opcionales**, seleccione **Agregar una característica**. Aparece una lista de las características opcionales que se pueden instalar.

4. Seleccione **Herramientas de gráficos** en la lista de características y luego elija **Instalar**.

   La característica Herramientas de gráficos también se instala automáticamente al instalar el SDK de Windows 10.

> [!TIP]
> La característica opcional Herramientas de gráficos de Windows 10 proporciona la funcionalidad de captura y reproducción ligera (por ejemplo, el programa de captura de línea de comandos **dxcap.exe**) que se puede usar en escenarios de compatibilidad, pruebas y diagnóstico en máquinas donde no están instaladas las herramientas de desarrollador. Para obtener más información, vea el tema [Herramienta de captura de línea de comandos](command-line-capture-tool.md).

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Usar el diagnóstico de gráficos por primera vez
 Ahora que tienen todo lo que necesita, ya puede empezar a usar el diagnóstico de gráficos. Tan solo tiene que seguir estos pasos:

### <a name="1---create-a-direct3d-app"></a>1: Crear una aplicación de Direct3D

Si ya tiene su propia aplicación de Direct3D para explorar Diagnóstico de gráficos, perfecto. Si no es así, puede usar cualquiera de los medios siguientes:

::: moniker range=">=vs-2019"
Descargue un ejemplo desde [Ejemplo de juego de Direct3D](/samples/microsoft/windows-universal-samples/simple3dgamedx/).
::: moniker-end
::: moniker range="vs-2017"
- Las plantillas de proyecto de las aplicaciones **DirectX 11 (Windows universal)** o **DirectX 12 (Windows universal)** para Windows 10.
- [Muestra de Direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) para Windows 10.
::: moniker-end

Asegúrese de que puede compilar y ejecutar la aplicación antes de continuar. Elija **Compilar** > **Compilar solución** para asegurarse de que se compila sin errores. A continuación, elija **Depurar** > **Iniciar sin depurar** (**Ctrl + F5**) para asegurarse de que se ejecuta correctamente. Dependiendo de la máquina que esté probando con la herramienta, puede que necesite ajustar la plataforma y el destino de depuración para el ejemplo. Por ejemplo, para probarla en la plataforma x64 en el equipo host de Visual Studio, elija **x64** como la plataforma de la solución y **Equipo local** como el destino de depuración. 

### <a name="2---start-a-graphics-diagnostics-session"></a>2: Iniciar una sesión de diagnóstico de gráficos
 Ahora está listo para empezar la primera sesión de diagnóstico de gráficos. En el menú principal de Visual Studio, seleccione **Depurar, Gráficos, Iniciar depuración de gráficos** o simplemente presione **Alt+F5**. La aplicación se inicia en diagnóstico de gráficos y muestra las ventanas de sesión de diagnóstico en Visual Studio.

> [!IMPORTANT]
> Si está ejecutando la aplicación en Windows 10 y todavía no ha instalado la característica opcional de herramientas de gráficos, se le pedirá que lo haga ahora. Debe instalarla para poder usar el diagnóstico de gráficos en Windows 10.

### <a name="3---capture-frames"></a>3: Capturar fotogramas
 Una vez iniciada la aplicación, ya se pueden capturar fotogramas.

#### <a name="to-capture-single-frames"></a>Para capturar fotogramas individuales

- En Visual Studio, elija el botón **Capturar fotograma** en la barra de herramientas de gráficos o la ventana de sesión de diagnóstico. O bien, si el foco se encuentra sobre la aplicación, presione la tecla **Imprimir pantalla** en el teclado.

#### <a name="to-capture-a-sequence-of-frames"></a>Para capturar una secuencia de fotogramas

- En Visual Studio, en la ventana de la sesión de diagnóstico, establezca el **Número de fotogramas para capturar** en el número de fotogramas que quiera capturar en secuencia; a continuación, capture la secuencia mediante cualquiera de los métodos descritos anteriormente para capturar fotogramas individuales.

   Para volver a capturar fotogramas individuales, establezca **Número de fotogramas para capturar** en *1*.

  Cuando termine de capturar fotogramas, salga de la aplicación o elija el botón **Detener** en la barra de herramientas de gráficos o en la ventana de sesión de diagnóstico.

### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4: Examinar los fotogramas capturados en el Analizador de gráficos
 Ahora puede examinar los fotogramas que acaba de capturar. Para empezar a analizar un fotograma, elija el número del fotograma en la ventana de sesión de diagnóstico. El fotograma se abrirá en el **Analizador de gráficos**, donde puede usar las herramientas de Diagnóstico de gráficos para examinar cómo su aplicación usa Direct3D para localizar problemas de representación, o usar la herramienta **Análisis de fotogramas** para estudiar su rendimiento.

 Si seleccionó el fotograma equivocado en la ventana de la sesión de diagnóstico o desea examinar otro fotograma, puede seleccionar uno nuevo el Analizador de gráficos. En la pestaña **Destino de la representación** de la ventana de registro de gráficos, debajo de la imagen del destino de representación, expanda la **Lista de fotogramas** y, a continuación, elija otro fotograma para examinarlo.

 Para obtener más información sobre cómo usar conjuntamente las herramientas del Analizador de gráficos, vea [Ejemplos](graphics-diagnostics-examples.md).

## <a name="see-also"></a>Vea también
- [Gráficos de Direct3D 12](/windows/desktop/direct3d12/direct3d-12-graphics)