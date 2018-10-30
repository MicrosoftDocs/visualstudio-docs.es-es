---
title: Introducción a diagnósticos de gráficos de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59131181-1caa-4b7f-be4b-e84709634edf
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ba62fc129674bd25f97037efdfcdbf7396ea3a6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824937"
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
 La característica opcional de Windows *las herramientas de gráficos* proporciona la infraestructura de captura y reproducción requerida por el diagnóstico de gráficos en Windows 10.  
  
 Para obtener información acerca de cómo instalar las herramientas de gráficos, vea [instalar herramientas de gráficos para Windows 10](#InstallGraphicsTools).  
  
### <a name="windows-81-prerequisites"></a>Requisitos previos de Windows 8.1  
 El Kit de desarrollo de Software (SDK) de Windows para Windows 8.1 proporciona la infraestructura de captura y reproducción requerida por el diagnóstico de gráficos en Windows 8.1 y admite el desarrollo para Windows 8.1 y Windows 8.  
  
 [Descargue el Kit de desarrollo de Software (SDK) de Windows para Windows 8.1](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)  
  
 Para usar una máquina de reproducción remota que ejecute Windows 10 desde una máquina que ejecute Windows 8.1, es necesario instalar el SDK de Windows 10 en la máquina de desarrollo y la característica opcional Herramientas de gráficos en la máquina de reproducción.  
  
##  <a name="InstallGraphicsTools"></a> Instalar las herramientas de gráficos para Windows 10  
 En Windows 10, se proporciona la infraestructura de diagnóstico de gráficos mediante una característica opcional de Windows llamado *las herramientas de gráficos*. Esta característica es necesaria para capturar y reproducir información de gráficos en Windows 10 independientemente de si la aplicación capturada tiene como destino una versión anterior de Windows o de la versión de Direct3D que se use. Puede instalar previamente la característica de herramientas de gráficos o esperar e instalarla cuando se le solicite la primera vez que inicie una sesión de diagnóstico de gráficos desde Visual Studio.  
  
#### <a name="to-install-graphics-tools-for-windows-10"></a>Para instalar las herramientas de gráficos para Windows 10  
  
1. En el **iniciar** menú, elija **configuración**. El **configuración** aparece el cuadro de diálogo.  
  
2. En el **configuración** cuadro de diálogo, elija **sistema**, a continuación, seleccione **aplicaciones instaladas** en la lista de configuraciones del sistema.  
  
3. En el lado derecho de la **configuración** cuadro de diálogo, elija **administrar características opcionales** en **aplicaciones y características instalados**. El **administrar características opcionales** aparece el cuadro de diálogo.  
  
4. En el **administrar características opcionales** cuadro de diálogo, elija **agregar una característica**. Aparece una lista de las características opcionales que se pueden instalar.  
  
5. Seleccione **las herramientas de gráficos** en la lista de características, a continuación, elija **instalar**.  
  
   La característica Herramientas de gráficos también se instala automáticamente al instalar el SDK de Windows 10.  
  
> [!TIP]
>  La característica opcional de herramientas de gráficos de Windows 10 proporciona la funcionalidad de captura y reproducción ligera — por ejemplo, el programa de línea de comandos **dxcap.exe**, que puede usarse en compatibilidad, pruebas y escenarios de diagnóstico en máquinas que no están instaladas las herramientas de desarrollo. Para obtener más información, consulte el [herramienta de captura de línea de comandos](../debugger/command-line-capture-tool.md) tema.  
  
## <a name="using-graphics-diagnostics-for-the-first-time"></a>Usar el diagnóstico de gráficos por primera vez  
 Ahora que tienen todo lo que necesita, ya puede empezar a usar el diagnóstico de gráficos. Tan solo tiene que seguir estos pasos:  
  
### <a name="1---create-a-direct3d-app"></a>1: Crear una aplicación de Direct3D  
 Si ya tiene su propia aplicación de Direct3D para explorar el diagnóstico de gráficos, perfecto. En caso contrario, puede usar uno de los ejemplos de Direct3D disponibles en la Galería de código.  
  
- Para probar el diagnóstico de gráficos con Direct3D 12 en Windows 10 con Visual Studio 2015, pruebe el [ejemplo Direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) para Windows 10.  
  
- Para probar el diagnóstico de gráficos con Direct3D 11 en Windows 10 o Windows 8.1, puede usar el **App DirectX (Windows Universal)** o **App DirectX (Windows 8.1)** plantillas de proyecto. O bien, para hacer algo más interesante, pruebe el [ejemplo del juego marble maze con DirectX](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345) para Windows 8.1.  
  
  Asegúrese de que puede compilar la aplicación antes de continuar.  
  
### <a name="2---start-a-graphics-diagnostics-session"></a>2: Iniciar una sesión de diagnóstico de gráficos  
 Ahora está listo para empezar la primera sesión de diagnóstico de gráficos. En Visual Studio, en el menú principal, elija **depurar, gráficos, Iniciar diagnóstico**, o simplemente presione **ALT+F5**. La aplicación se inicia en diagnóstico de gráficos y muestra las ventanas de sesión de diagnóstico en Visual Studio.  
  
> [!IMPORTANT]
>  Si está ejecutando la aplicación en Windows 10 y todavía no ha instalado la característica opcional de herramientas de gráficos, se le pedirá que lo haga ahora. Debe instalarla para poder usar el diagnóstico de gráficos en Windows 10.  
  
### <a name="3---capture-frames"></a>3: Capturar fotogramas  
 Una vez iniciada la aplicación, ya se pueden capturar fotogramas.  
  
##### <a name="to-capture-single-frames"></a>Para capturar fotogramas individuales  
  
-   En Visual Studio, elija el **Capturar fotograma** botón desde la ventana de sesión de diagnóstico o la barra de herramientas de gráficos. O bien, si la aplicación tiene el foco, simplemente presione **Impr Pant**.  
  
##### <a name="to-capture-a-sequence-of-frames"></a>Para capturar una secuencia de fotogramas  
  
- En Visual Studio, en la ventana de sesión de diagnóstico, establezca **fotogramas para capturar** para el número de fotogramas que desee capturar en secuencia, a continuación, la captura de la secuencia mediante cualquiera de los métodos descritos anteriormente para capturar fotogramas individuales.  
  
   Para capturar fotogramas individuales de nuevo, establezca **fotogramas para capturar** a `1`.  
  
  Cuando haya terminado simplemente capturar fotogramas, salga de la aplicación o elija el **detener** botón desde la barra de herramientas de gráficos o la ventana de sesión de diagnóstico.  
  
### <a name="4--examine-captured-frames-in-the-graphics-analyzer"></a>4: Examinar los fotogramas capturados en el Analizador de gráficos  
 Ahora puede examinar los fotogramas que acaba de capturar. Para empezar a analizar un fotograma, elija el número del fotograma en la ventana de sesión de diagnóstico. Se abrirá en el marco del **analizador de gráficos**, donde puede usar las herramientas de diagnóstico de gráficos para examinar cómo su aplicación usa Direct3D para localizar problemas de representación, o usar el **análisis de fotogramas** herramienta a comprender su rendimiento.  
  
 Si seleccionó el fotograma equivocado en la ventana de la sesión de diagnóstico o desea examinar otro fotograma, puede seleccionar uno nuevo el Analizador de gráficos. En el **destino de la representación** pestaña de la ventana de registro de gráficos, debajo de la imagen de destino de representación, expanda el **lista de fotogramas** y, a continuación, elija un otro fotograma para examinarlo.  
  
 Para obtener más información acerca de cómo usar conjuntamente las herramientas del analizador de gráficos, vea el [ejemplos](../debugger/graphics-diagnostics-examples.md).  
  
## <a name="see-also"></a>Vea también  
 [Direct3D 12 gráficos](http://msdn.microsoft.com/en-us/52094ae3-3b44-4689-9ee7-1ba1b3a779cb)






