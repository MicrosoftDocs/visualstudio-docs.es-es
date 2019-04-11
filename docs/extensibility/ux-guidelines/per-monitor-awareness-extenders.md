---
title: Compatibilidad con reconocimiento de Monitor para que los extensores de Visual Studio
titleSuffix: ''
description: Obtenga información sobre la compatibilidad del nuevo extensor por monitor-reconocimiento disponible en Visual Studio de 2019.
ms.date: 04/09/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
ms.assetid: ''
author: rub8n
ms.author: rurios
manager: anthc
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- multiple
ms.openlocfilehash: 42de73a29e053066c0fbeca72ca3511b58b2fa7e
ms.sourcegitcommit: 0a2fdc23faee77187e10a1c19665ba5a1ac68e72
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477691"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Compatibilidad con reconocimiento de Monitor para que los extensores de Visual Studio

Las versiones anteriores a Visual Studio de 2019 tenían su contexto de reconocimiento de PPP establecido para la cuenta del sistema, en lugar de una cuenta de monitor de PPP (PMA). Que se ejecuta en el sistema de reconocimiento dan como resultado una experiencia visual degradado (p. ej. borrosas fuentes o iconos) cada vez que Visual Studio se tenía que procesar en varios monitores con factores de escala diferentes o remoto en equipos con configuraciones de pantalla diferente (por ejemplo, diferentes Windows escalado).

El contexto de reconocimiento de PPP de 2019 de Visual Studio es el conjunto como Visual Studio tener en cuenta, lo que permite representar según la configuración de la pantalla donde se hospeda por monitor en lugar de una configuración genérica definida por el sistema. En última instancia, traducir en una interfaz de usuario nítida para las áreas de superficie que implementar la compatibilidad con PMA.

Hacer referencia a la [desarrollo de aplicaciones de escritorio de alto PPP en Windows](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) documentación para obtener más información acerca de los términos y el escenario global se trata en este documento.

## <a name="quickstart"></a>Inicio rápido
- Asegúrese de que Visual Studio se ejecuta en modo PMA (consulte **habilitar PMA**)

- Valide la extensión de funciona correctamente entre un conjunto de escenarios comunes (vea **probar sus extensiones para problemas PMA**)

- Si encuentra problemas, se le debe para agregar el nuevo paquete de NuGet PMA, diagnosticar y solucionar problemas con las estrategias y las recomendaciones descritas en este documento

## <a name="enabling-pma"></a>Habilitar PMA
Para habilitar PMA en Visual Studio, deben cumplirse los siguientes requisitos:
1)  10 de abril de 2018 de Windows Update (v1803, RS4) o posterior
2)  .NET framework 4.8 RTM o posterior (actualmente se distribuye como vista previa independiente o paquete reciente Insider de Windows en las versiones)
3)  2019 de Visual Studio con el ["Optimizar el procesamiento de las pantallas con densidades de píxeles diferente"](https://docs.microsoft.com/visualstudio/ide/reference/general-environment-options-dialog-box?view=vs-2019) opción habilitada

Una vez que se cumplen estos requisitos, Visual Studio habilitará automáticamente PMA a través del proceso.

## <a name="testing-your-extensions-for-pma-issues"></a>Probar las extensiones para PMA problemas

Visual Studio admite oficialmente los marcos de IU de HTML/JS, Win32, Windows Forms y WPF. Cuando Visual Studio se pone en modo PMA, las pilas de interfaz de usuario diferentes comportan de manera diferente. Por lo tanto, con independencia del marco de interfaz de usuario, se recomienda que se realiza un paso de prueba para asegurarse de que todos los de la interfaz de usuario es compatible con PMA.

Independientemente de la plataforma de interfaz de usuario es compatible su extensión, se recomienda validar los escenarios comunes siguientes:

1. Cambiar el factor de escala de un entorno único monitor mientras la aplicación se está ejecutando *
    - Este escenario le ayuda a comprobar que la interfaz de usuario está respondiendo al cambio de PPP de Windows dinámico

2. Acoplar o desacoplar un equipo portátil donde se establece un monitor que está conectado a la réplica principal y el monitor que está conectado tiene un factor de escala diferente de la principal mientras se ejecuta la aplicación.
    - Este escenario le ayuda a que la interfaz de usuario responde a la pantalla de cambio de PPP, así como control muestra dinámicamente que se agregan o quitan de la prueba

3. Tener varios monitores con factores de escala diferentes y trasladar la aplicación entre ellos.
    - Este escenario le ayuda a comprobar que la interfaz de usuario está respondiendo a los cambios de PPP de pantalla
    
4. Comunicación remota en un equipo cuando los equipos locales y remotos tienen factores de escala diferentes para el monitor principal.
    - Este escenario le ayuda a comprobar que la interfaz de usuario está respondiendo al cambio de PPP de Windows dinámico

Una buena prueba preliminar de si la interfaz de usuario podría tener problemas es o no el código usa ya sea el *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* o *Microsoft.VisualStudio.PlatformUI.DpiHelper* clases. Estas clases DpiHelper antiguas solo admiten el reconocimiento de PPP del sistema y no siempre funcionará correctamente cuando el proceso PMA.

Uso típico de estos DpiHelpers será similar a:

```cs
Point screenTopRight = logicalBounds.TopRight.LogicalToDeviceUnits();

POINT screenIntTopRight = new POINT
{
    x = (int)screenTopRIght.X,
    y = (int)screenTopRIght.Y
}

IntPtr monitor = NativeMethods.MonitorFromPoint(screenIntTopRight, NativeMethods.Monitor_DEFAULTTONEARST);
```

En el ejemplo anterior, un rectángulo que representa los límites lógicos de una ventana se convierte en unidades de dispositivo para que pueda pasarse al método nativo MonitorFromPoint que espera que las coordenadas de dispositivo con el fin de devolver un puntero de monitor precisa.

### <a name="classes-of-issues"></a>Clases de problemas

Cuando se habilita PMA para Visual Studio, la interfaz de usuario pudo replicar los problemas de varias maneras comunes. Más, si no todos, de estos problemas pueden producirse en cualquiera de los marcos de interfaz de usuario de Visual Studio compatibles. Además, estos problemas pueden ocurrir incluso cuando una parte de la interfaz de usuario se hospeda en escenarios de PPP en modo mixto (consulte el Windows [documentación](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) para obtener más información). 

#### <a name="win32-window-creation"></a>Creación de la ventana de Win32
Al crear windows con CreateWindow() o CreateWindowEx(), un patrón común es crear la ventana en las coordenadas 0,0 (esquina superior izquierda de la pantalla principal), muévala a su posición final. Sin embargo, si lo hace, por lo que puede hacer que la ventana para desencadenar un valor de PPP cambiado mensaje o evento, que puede reactivar otros mensajes de interfaz de usuario o eventos y finalmente llevaría a un comportamiento no deseado o la representación.

#### <a name="wpf-element-placement"></a>Selección de ubicación de elemento WPF
Al mover los elementos WPF con el antiguo Microsoft.VisualStudio.Utilities.Dpi.DpiHelper, las coordenadas de la parte superior izquierda no se podrían calcular correctamente cada vez que los elementos se encuentran en el caso de PPP no principal.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Serialización de tamaños de elemento de interfaz de usuario o posiciones
Cada vez que el tamaño de la interfaz de usuario o la posición se restaura en un contexto de PPP diferente al se almacenó en, se coloca y tamaño de forma incorrecta. Esto sucede porque los límites lógicos de una ventana se convierten en unidades de dispositivo para que pueda pasarse al método Win32 MonitorFromPoint que espera que las coordenadas de dispositivo con el fin de devolver un puntero de monitor precisa.

#### <a name="incorrect-scaling"></a>Escalado incorrecta
Los elementos de interfaz de usuario creados en el valor de PPP principal se escalan correctamente, sin embargo, cuando se mueve a una pantalla con un valor de PPP diferente, no cambia la escala y por lo tanto, su contenido termina siendo demasiado grande o demasiado pequeño.

#### <a name="incorrect-bounding"></a>Rectángulo de selección incorrecta
De forma similar, el problema de escala, los elementos de interfaz de usuario calculará sus límites correctamente en su contexto principal de PPP, sin embargo, cuando se mueve a un valor de PPP no principal, no calcular los nuevos límites correctamente. Por lo tanto, la ventana de contenido termina está demasiado grande o demasiado pequeño en comparación con la interfaz de usuario de hospedaje, lo que resulta en un espacio vacío o el recorte.

#### <a name="drag--drop"></a>Arrastrar y colocar
Cada vez que dentro de los escenarios de PPP de modo mixto (por ejemplo, diferentes elementos de la IU de representación en contexto PPP principal y no principal), arrastre y coloque coordenadas podrían ser errores de cálculo, lo que resulta en la posición final colocar acabar incorrecto.

#### <a name="out-of-process-ui"></a>Interfaz de usuario de fuera de proceso
Alguna interfaz de usuario se crea fuera de proceso y si el proceso externo creación está en un modo de reconocimiento de PPP diferente que Visual Studio, esto puede presentar alguno de los problemas de representación anterior.

#### <a name="windows-forms-controls-images-or-windows-not-displaying"></a>Windows no se están mostrando, imágenes o controles de formularios Windows Forms
Una de las principales causas para este problema es que los desarrolladores que intentan cambiar primario de un control o ventana con un DpiAwarenessContext a otra ventana DpiAwarenessContext. 

Las siguientes imágenes muestran las restricciones de sistema operativo actuales de Windows en windows, puede ser el primario a menos que explícitamente se cambia el subproceso que aloja el comportamiento:

![Captura de pantalla del comportamiento de la relación jerárquica correcta](../../extensibility/ux-guidelines/media/PMA-parenting-behavior.PNG)

Como resultado, si establece la relación de elementos primarios y secundarios entre los modos no admitidos, se producirá un error y el control o la ventana no se puede representar según lo previsto.

### <a name="diagnosing-issues"></a>Diagnóstico de problemas
Hay muchos factores a tener en cuenta al identificar los problemas relacionados con PMA: 

1. No la interfaz de usuario o la API esperadas lógica o los valores del dispositivo.
    - UI de WPF y API normalmente usan los valores lógicos (pero no siempre)
    - Interfaz de usuario de Win32 y API normalmente usan los valores de dispositivo

2. ¿De dónde proceden los valores?
    - Si recibe los valores de otra interfaz de usuario o la API, es pasar dispositivo o los valores lógicos.
    - Si recibe los valores de varios orígenes, ¿todos los use/esperan que los mismos tipos de valores o conversiones necesita mezclar y combinar?

3. ¿Son constantes de la interfaz de usuario en uso y qué formulario están en?

4. ¿Es el subproceso en el contexto correcto para los valores de PPP recibe?
    - Los cambios para habilitar CLMM generalmente deben colocar las rutas de código en el contexto adecuado, sin embargo, podría ejecutar el trabajo realizado fuera del flujo de mensajes principal bucle o un evento en el contexto equivocado de PPP.

5. ¿Los valores entre los límites del contexto PPP?
    - Arrastrar y colocar es una situación común donde coordenadas pueden cruzar los contextos de PPP. Ventana intenta hacer lo correcto, pero en algunos casos, el host de la interfaz de usuario que deba realizar trabajo de conversión para asegurarse de los límites del contexto correspondiente.

### <a name="pma-nugget-package"></a>Paquete de NuGet PMA
Las nuevas bibliotecas DpiAwarness pueden encontrarse en el paquete Microsoft.VisualStudio.DpiAwareness NuGet.

### <a name="recommended-tools"></a>Herramientas recomendadas
Las siguientes herramientas que pueden ayudar a depurar problemas relacionados con PMA en algunas de las diferentes pilas de interfaz de usuario admitidas por Visual Studio.

#### <a name="snoop"></a>Consultar
Snoop es una herramienta de depuración de XAML que tenga alguna funcionalidad adicional que no tiene las herramientas integradas de XAML de Visual Studio. Además, no necesita Snoop activamente depurar Visual Studio para poder ver y ajustar su UI de WPF. Las dos maneras principales Snoop puede ser útil para diagnosticar problemas PMA es para validar las coordenadas de ubicación lógica o los límites de tamaño, y para validar la interfaz de usuario tiene el valor de PPP adecuado.
 
#### <a name="visual-studio-xaml-tools"></a>Herramientas visuales Studio XAML
Al igual que Snoop, las herramientas XAML en Visual Studio pueden ayudar a diagnosticar problemas PMA. Una vez que se encuentra una causa probable, puede establecer puntos de interrupción y usar la ventana de Live Visual Tree, así como las ventanas de depuración para inspeccionar los límites de la interfaz de usuario y una resolución actual.

## <a name="strategies-for-fixing-pma-issues"></a>Estrategias para solucionar problemas PMA

### <a name="replacing-dpihelper-calls"></a>Reemplazando las llamadas DpiHelper
En la mayoría de los casos, corregir problemas de la interfaz de usuario en PMA se reduce a reemplazando las llamadas en el código administrado a la antigua: *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* y *Microsoft.VisualStudio.PlatformUI.DpiHelper* clases, con llamadas a la nueva *Microsoft.VisualStudio.Utilities.DpiAwareness* clase auxiliar. 

Para código nativo, supondrá reemplazando las llamadas a la antigua *VsUI::CDpiHelper* clase con las llamadas a la nueva *VsUI::CDpiAwareness* clase. Las nuevas clases DpiAwareness y CDpiAwareness ofrecen las mismas aplicaciones auxiliares de conversión, como las clases DpiHelper pero que requieren un parámetro de entrada adicional: el elemento de interfaz de usuario para usarla como una referencia de la operación de conversión. 

La clase DpiAwareness administrada ofrece aplicaciones auxiliares para objetos visuales de WPF, los controles de Windows Forms y los HWND Win32 y HMONITORs (tanto en forma de IntPtrs), mientras el nativo CDpiAwareness ofertas HWND y HMONITOR aplicaciones auxiliares de clase.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Los cuadros de diálogo de Windows Forms, windows o controles que se muestran en el DpiAwarenessContext incorrecto
Incluso después de una asociación correcta de windows con DpiAwarenessContext distintos (debido al comportamiento predeterminado de windows), los usuarios todavía pueden ver problemas de escalamiento diferentes ventanas DpiAwarenessContext escalan de forma diferente. Como resultado, los usuarios pueden ver texto alineación/borrosa o problemas de imágenes en la interfaz de usuario.

La solución consiste en establecer el ámbito de DpiAwarenessContext correcto para todas las ventanas y controles en la aplicación.

### <a name="tlmm-dialogs"></a>Cuadros de diálogo TLMM
Al crear ventanas de nivel superior, como cuadros de diálogo modales, es importante para asegurarse de que el subproceso está en el estado correcto antes el HWND que se está creando. El subproceso se puede poner en conocimiento del sistema por utilizando la aplicación auxiliar de CDpiScope en el modo nativo o administrado de la aplicación auxiliar de DpiAwareness.EnterDpiScope en. (TLMM generalmente se debe usar en los cuadros de diálogo del que no son de WPF o windows.)

### <a name="child-level-mixed-mode-clmm"></a>Modo mixto de nivel secundario (CLMM)

De forma predeterminada, ventanas secundarias reciben el mismo modo de reconocimiento de PPP que sus elementos primarios. Sin embargo, puede usar SetThreadDpiHostingBehavior reemplazarlo y ejecutaron ventanas secundarias en un modo de escalado diferente que su elemento primario o host.


#### <a name="clmm-issues"></a>Problemas CLMM
Mayoría del trabajo de cálculo de la interfaz de usuario que se produce como parte de la cadena de bucle o evento mensajería principal ya debe estar ejecutándose en el contexto adecuado de PPP. Sin embargo, si fuera de estos flujos de trabajo principales se realizan de coordenadas y cálculos de tamaño (por ejemplo, durante un tiempo de inactividad, o fuera del subproceso de interfaz de usuario, a continuación, el contexto actual de PPP podría ser incorrecto dan lugar a una mala colocación de la interfaz de usuario o mal problemas de ajuste de tamaño. Colocar el subproceso en el estado correcto para la interfaz de usuario trabajo normalmente corrige el problema.
 
#### <a name="opting-out-of-clmm"></a>Dejar de participar en CLMM
Si se está migrando una ventana de herramientas que no son de WPF para admitir completamente PMA, deberá dejar de participar en CLMM. Para ello, debe implementar una nueva interfaz: IVsDpiAware.

C#:
```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAeware
{
    [ComAliasName("Microsoft.VisualStudio.Shell.Interop.VSDPIMode")]
    uint Mode {get;}
}
```
 
C++:
```cplusplus
IVsDpiAware : public IUnknown
{
    public:
        HRRESULT STDMETHODCALLTYPE get_Mode(__RCP__out VSDPIMODE *dwMode);
};
```
 

Para los lenguajes administrados, el mejor lugar para implementar esta interfaz está en la misma clase que derive de *Microsoft.VisualStudio.Shell.ToolWindowPane*. Para C++, el mejor lugar para implementar esta interfaz se encuentra en la misma clase que implementa *IVsWindowPane* desde vsshell.h.

El valor devuelto por la propiedad Mode en la interfaz es un __VSDPIMODE (y conversión a un tipo uint en administrados):

```cs
enum __VSDPIMODE
    {
        VSDM_Unaware    = 0x01,
        VSDM_System     = 0x02,
        VSDM_PerMonitor = 0x03,
    }
```

- Significa que la ventana de herramientas necesita tratar 96 PPP, Windows controlará de ajuste de escala para todos los demás PPP. Lo que en el contenido que se va a borrosas.
- Medios de sistema de la ventana de herramientas que necesita para controlar el valor de PPP para la réplica principal mostrar PPP. Cualquier presentación con un valor de PPP coincidente tendrá un aspecto nítida, pero si el valor de PPP es diferente o cambia durante la sesión, Windows controlará la escala y será borrosa.
- PerMonitor significa que la ventana de herramientas que necesita administrar todos los PPP en todas las pantallas y cada vez que cambia el valor de PPP.

**NOTA**: Visual Studio solo admite reconocimiento PerMonitorV2, por lo que el valor de enumeración PerMonitor se traduce en el valor de Windows de DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2.

## <a name="known-issues"></a>Problemas conocidos

### <a name="windows-forms"></a>Windows Forms

Para optimizar los nuevos escenarios de modo mixto, Windows Forms puede cambiar cómo crea los controles y windows cada vez que su elemento primario no se estableció explícitamente. Anteriormente, los controles sin una primaria explícita utilizan un interno "estacionamiento ventana" como primario temporal para el control o la ventana que se va a crear. 

La "ventana de estacionamiento" obtiene su DpiAwarenessContext desde el proceso de que la aplicación se ejecuta bajo. El control hereda la misma DpiAwarenessContext como la ventana de estacionamiento y sería duplicando con el elemento primario original o previsto por el desarrollador de aplicaciones.  Esto no funciona cuando el padre deseado para el control no es el mismo DpiAwarenessContext como el control que se está creando.

A partir de .NET 4.8, si el elemento primario no se establece explícitamente en el control o ventana, Windows Forms se para una ventana de estacionamiento que coincida con el DpiAwarenessContext del subproceso en el que se solicita la creación de control o ventana de consulta y usarlo como elemento primario temporal. En otras palabras, tras su creación se crea el control con el DpiAwarenessContext previsto. El control o la ventana se, a continuación, se cambia de elemento primario para el elemento primario esperado por el desarrollador de aplicaciones.
