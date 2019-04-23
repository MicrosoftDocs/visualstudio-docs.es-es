---
title: Compatibilidad con reconocimiento de Monitor para que los extensores de Visual Studio
titleSuffix: ''
description: Obtenga información sobre la compatibilidad del nuevo extensor por monitor-reconocimiento disponible en Visual Studio de 2019.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
ms.assetid: ''
author: rub8n
ms.author: rurios
manager: anthc
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- multiple
ms.openlocfilehash: db30c3d74a7742daa3c9cf7225bc2a38062dc6e4
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59660702"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Compatibilidad con reconocimiento de Monitor para que los extensores de Visual Studio
Las versiones anteriores a Visual Studio de 2019 tenían su contexto de reconocimiento de PPP establecido en el sistema tenga en cuenta, en lugar de tener en cuenta DPI (PMA) por monitor. Que se ejecuta en el reconocimiento del sistema dieron lugar a un objeto visual degradado experiencia (p. ej. borrosas fuentes o iconos) cada vez que Visual Studio tenía que procesar en varios monitores con factores de escala diferentes o remota en equipos con configuraciones de pantalla diferentes, por ejemplo, (que son distintas Windows escalado).

El contexto de reconocimiento de PPP de 2019 de Visual Studio se establece como PMA, cuando el entorno lo admite, lo que permite Visual Studio para representar de acuerdo con la configuración de la pantalla donde se hospeda en lugar de una configuración definida solo sistema. En última instancia, traducir en una interfaz de usuario nítida siempre para las áreas de superficie que admiten el modo PMA.

Hacer referencia a la [desarrollo de aplicaciones de escritorio de alto PPP en Windows](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) documentación para obtener más información acerca de los términos y el escenario global se trata en este documento.

## <a name="quickstart"></a>Inicio rápido
- Asegúrese de que Visual Studio se ejecuta en modo PMA (consulte **habilitar PMA**)

- Valide la extensión de funciona correctamente entre un conjunto de escenarios comunes (vea **probar sus extensiones para problemas PMA**)

- Si encuentra problemas, puede usar las estrategias y recomendaciones descritas en este documento para diagnosticar y corregir esos problemas. También deberá agregar el nuevo [Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) paquete NuGet al proyecto para acceder a las API necesarias.

## <a name="enabling-pma"></a>Habilitar PMA
Para habilitar PMA en Visual Studio, deben cumplirse los siguientes requisitos:
1)  10 de abril de 2018 de Windows Update (v1803, RS4) o posterior
2)  .NET framework 4.8 RTM o posterior
3)  2019 de Visual Studio con el ["Optimizar el procesamiento de las pantallas con densidades de píxeles diferente"](https://docs.microsoft.com/visualstudio/ide/reference/general-environment-options-dialog-box?view=vs-2019) opción habilitada

Una vez que se cumplen estos requisitos, Visual Studio habilitará automáticamente el modo PMA a través del proceso.

> [!NOTE]
> Contenido de Windows Forms en Visual Studio (por ejemplo el Explorador de propiedades) admitirá PMA solo cuando tenga la actualización 1 de Visual Studio de 2019.

## <a name="testing-your-extensions-for-pma-issues"></a>Probar las extensiones para PMA problemas

Visual Studio admite oficialmente los marcos de IU de HTML/JS, Win32, Windows Forms y WPF. Cuando Visual Studio se pone en modo PMA, cada pila de la interfaz de usuario tiene un comportamiento diferente. Por lo tanto, con independencia del marco de interfaz de usuario, se recomienda que se realiza un paso de prueba para asegurarse de que todos los de la interfaz de usuario es compatible con el modo PMA.

Se recomienda que validar los escenarios comunes siguientes:

1. Cambiar el factor de escala de un entorno único monitor mientras la aplicación se está ejecutando *
    - Este escenario le ayuda a comprobar que la interfaz de usuario está respondiendo al cambio de PPP de Windows dinámico

2. Acoplar o desacoplar un equipo portátil donde se establece un monitor que está conectado a la réplica principal y el monitor que está conectado tiene un factor de escala diferente que el equipo portátil mientras se ejecuta la aplicación.
    - Este escenario le ayuda a que la interfaz de usuario responde a la pantalla de cambio de PPP, así como control muestra dinámicamente que se agregan o quitan de la prueba

3. Tener varios monitores con factores de escala diferentes y trasladar la aplicación entre ellos.
    - Este escenario le ayuda a comprobar que la interfaz de usuario está respondiendo a los cambios de PPP de pantalla
    
4. Comunicación remota en un equipo cuando los equipos locales y remotos tienen factores de escala diferentes para el monitor principal.
    - Este escenario le ayuda a comprobar que la interfaz de usuario está respondiendo al cambio de PPP de Windows dinámico

Una buena prueba preliminar de si la interfaz de usuario podría tener problemas es si el código utiliza el *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper*, *Microsoft.VisualStudio.PlatformUI.DpiHelper*, o *VsUI::CDpiHelper* clases. Estas clases DpiHelper antiguas solo admiten el reconocimiento de PPP del sistema y no siempre funcionará correctamente cuando el proceso PMA.

Uso típico de estos DpiHelpers será similar a:

```cs
Point screenTopRight = logicalBounds.TopRight.LogicalToDeviceUnits();

POINT screenIntTopRight = new POINT
{
    x = (int)screenTopRIght.X,
    y = (int)screenTopRIght.Y
}

// Declared via P/Invoke
IntPtr monitor = MonitorFromPoint(screenIntTopRight, MONITOR_DEFAULTTONEARST);
```

En el ejemplo anterior, un rectángulo que representa los límites lógicos de una ventana se convierte en unidades de dispositivo para que pueda pasarse al método nativo MonitorFromPoint que espera que las coordenadas de dispositivo con el fin de devolver un puntero de monitor precisa.

### <a name="classes-of-issues"></a>Clases de problemas
Cuando está habilitado el modo PMA para Visual Studio, la interfaz de usuario pudo replicar los problemas de varias maneras comunes. Más, si no todos, de estos problemas pueden producirse en cualquiera de los marcos de trabajo de la interfaz de usuario admitidos de Visual Studio. Además, estos problemas también pueden ocurrir cuando se hospeda una parte de la interfaz de usuario en escenarios de PPP en modo mixto (consulte el Windows [documentación](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) para obtener más información). 

#### <a name="win32-window-creation"></a>Creación de la ventana de Win32
Al crear windows con CreateWindow() o CreateWindowEx(), un patrón común consiste en crear la ventana en las coordenadas (0,0) (esquina superior izquierda de la pantalla principal), a continuación, muévalo hasta su posición final. Sin embargo, si lo hace, por lo que puede hacer que la ventana para desencadenar un valor de PPP cambiado mensaje o evento, que puede reactivar otros mensajes de interfaz de usuario o eventos y finalmente llevaría a un comportamiento no deseado o la representación.

#### <a name="wpf-element-placement"></a>Selección de ubicación de elemento WPF
Al mover los elementos WPF con el antiguo Microsoft.VisualStudio.Utilities.Dpi.DpiHelper, las coordenadas de la parte superior izquierda no se podrían calcular correctamente cada vez que los elementos que se encuentran en un valor de PPP no principal.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Serialización de tamaños de elemento de interfaz de usuario o posiciones
Cuando se restaura el tamaño de la interfaz de usuario o la posición (si se guardase como unidades de dispositivo) en un contexto de PPP diferente al se almacenó en, se coloca y tamaño de forma incorrecta. Esto sucede porque las unidades de dispositivo tienen una relación de PPP inherente.

#### <a name="incorrect-scaling"></a>Escalado incorrecta
Los elementos de interfaz de usuario creados en el valor de PPP principal se escalan correctamente, sin embargo, cuando se mueve a una pantalla con un valor de PPP diferente, no cambia la escala y por lo tanto, su contenido termina siendo demasiado grande o demasiado pequeño.

#### <a name="incorrect-bounding"></a>Rectángulo de selección incorrecta
De forma similar, el problema de escala, los elementos de interfaz de usuario calculará sus límites correctamente en su contexto principal de PPP, sin embargo, cuando se mueve a un valor de PPP no principal, no calcular los nuevos límites correctamente. Por lo tanto, la ventana de contenido termina está demasiado grande o demasiado pequeño en comparación con la interfaz de usuario de hospedaje, lo que resulta en un espacio vacío o el recorte.

#### <a name="drag--drop"></a>Arrastrar y colocar
Cada vez que dentro de los escenarios de PPP de modo mixto (por ejemplo, distintos elementos de IU de representación en diferentes modos de reconocimiento de PPP), arrastre y coloque coordenadas podrían ser errores de cálculo, lo que resulta en la posición final colocar acabar incorrecto.

#### <a name="out-of-process-ui"></a>Interfaz de usuario de fuera de proceso
Alguna interfaz de usuario se crea fuera de proceso y si el proceso externo creación está en un modo de reconocimiento de PPP diferente que Visual Studio, esto puede presentar alguno de los problemas de representación anterior.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>Controles de formularios Windows Forms, imágenes o diseños representados de forma incorrecta
Todo el contenido de Windows Forms no admite el modo PMA. Como resultado, es posible que vea representación problema con diseños incorrectos o la escala. En este caso es una solución posible representar explícitamente el contenido de Windows Forms en DpiAwarenessContext "Sistema compatible con" (consulte [forzar un control en un DpiAwarenessContext específico](#forcing-a-control-into-a-specific-dpiawarenesscontext)).

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Controles de formularios Windows Forms o windows que no se están mostrando
Una de las principales causas para este problema es que los desarrolladores que intentan cambiar primario de un control o ventana con una DpiAwarenessContext a una ventana con un DpiAwarenessContext diferentes.

Las siguientes imágenes muestran actual **predeterminada** restricciones del sistema operativo Windows en windows puede ser el primario:

![Captura de pantalla del comportamiento de la relación jerárquica correcta](../../extensibility/ux-guidelines/media/PMA-parenting-behavior.PNG)

> [!Note]
> Puede cambiar este comportamiento estableciendo el comportamiento de hospedaje de subprocesos (consulte [DpiHostinBehaviour](https://docs.microsoft.com/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)).

Como resultado, si establece la relación de elementos primarios y secundarios entre los modos no admitidos, se producirá un error y el control o la ventana no se puede representar según lo previsto.

### <a name="diagnosing-issues"></a>Diagnóstico de problemas
Hay muchos factores a tener en cuenta al identificar los problemas relacionados con PMA: 

1. Hace que la interfaz de usuario o la API espera lógica o los valores del dispositivo.
    - UI de WPF y API normalmente usan los valores lógicos (pero no siempre)
    - Interfaz de usuario de Win32 y API normalmente usan los valores de dispositivo

2. ¿De dónde proceden los valores?
    - Si recibe los valores de otra interfaz de usuario o la API, es pasar dispositivo o los valores lógicos.
    - Si recibe los valores de varios orígenes, ¿todos los use/esperan que los mismos tipos de valores o conversiones necesita mezclar y combinar?

3. ¿Son constantes de la interfaz de usuario en uso y qué formulario están en?

4. ¿Es el subproceso en el contexto correcto para los valores de PPP recibe?
    - Los cambios para habilitar el hospedaje de PPP mixto generalmente deben colocar las rutas de código en el contexto adecuado, sin embargo, podría ejecutar el trabajo realizado fuera del flujo de mensajes principal bucle o un evento en el contexto equivocado de PPP.

5. ¿Los valores entre los límites del contexto PPP?
    - Arrastrar y colocar es una situación común donde coordenadas pueden cruzar los contextos de PPP. Ventana intenta hacer lo correcto, pero en algunos casos, el host de la interfaz de usuario que deba realizar trabajo de conversión para asegurarse de los límites del contexto correspondiente.

### <a name="pma-nuget-package"></a>Paquete de NuGet PMA
Las nuevas bibliotecas DpiAwarness pueden encontrarse en el [Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) paquete NuGet.

### <a name="recommended-tools"></a>Herramientas recomendadas
Las siguientes herramientas que pueden ayudar a depurar problemas relacionados con PMA en algunas de las diferentes pilas de interfaz de usuario admitidas por Visual Studio.

#### <a name="snoop"></a>Consultar
Snoop es una herramienta de depuración de XAML que tenga alguna funcionalidad adicional que no tiene las herramientas integradas de XAML de Visual Studio. Además, no necesita Snoop activamente depurar Visual Studio para poder ver y ajustar su UI de WPF. Las dos maneras principales Snoop puede ser útil para diagnosticar problemas PMA es para validar las coordenadas de ubicación lógica o los límites de tamaño, y para validar la interfaz de usuario tiene el valor de PPP adecuado.
 
#### <a name="visual-studio-xaml-tools"></a>Herramientas visuales Studio XAML
Al igual que Snoop, las herramientas XAML en Visual Studio pueden ayudar a diagnosticar problemas PMA. Una vez que se encuentra una causa probable, puede establecer puntos de interrupción y usar la ventana de Live Visual Tree, así como las ventanas de depuración para inspeccionar los límites de la interfaz de usuario y una resolución actual.

## <a name="strategies-for-fixing-pma-issues"></a>Estrategias para solucionar problemas PMA
### <a name="replacing-dpihelper-calls"></a>Reemplazando las llamadas DpiHelper
En la mayoría de los casos, corregir problemas de la interfaz de usuario en modo PMA se reduce a reemplazando las llamadas en el código administrado a la antigua *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* y *Microsoft.VisualStudio.PlatformUI.DpiHelper*clases, con llamadas a la nueva *Microsoft.VisualStudio.Utilities.DpiAwareness* clase auxiliar. 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

Para código nativo, supondrá reemplazando las llamadas a la antigua *VsUI::CDpiHelper* clase con las llamadas a la nueva *VsUI::CDpiAwareness* clase. 

```cpp
// Remove this kind of use:
int cx = VsUI::DpiHelper::LogicalToDeviceUnitsX(m_cxS);
int cy = VsUI::DpiHelper::LogicalToDeviceUnitsY(m_cyS);

// Replace with this use:
int cx = m_cxS;
int cy = m_cyS;
VsUI::CDpiAwareness::LogicalToDeviceUnitsX(m_hwnd, &cx);
VsUI::CDpiAwareness::LogicalToDeviceUnitsY(m_hwnd, &cy);
```

Las nuevas clases DpiAwareness y CDpiAwareness ofrecen la misma unidad de las aplicaciones auxiliares de conversión como las clases DpiHelper pero que requieren un parámetro de entrada adicional: el elemento de interfaz de usuario para usarla como una referencia de la operación de conversión. Es importante tener en cuenta que las aplicaciones auxiliares de escalado de imagen no existen en las nuevas aplicaciones auxiliares de DpiAwareness/CDpiAwareness y si es necesario, el [ImageService](https://docs.microsoft.com/visualstudio/extensibility/image-service-and-catalog?view=vs-2019) debe usarse en su lugar.

La clase DpiAwareness administrada ofrece aplicaciones auxiliares para objetos visuales de WPF, los controles de Windows Forms y los HWND Win32 y HMONITORs (tanto en forma de IntPtrs), mientras el nativo CDpiAwareness ofertas HWND y HMONITOR aplicaciones auxiliares de clase.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Los cuadros de diálogo de Windows Forms, windows o controles que se muestran en el DpiAwarenessContext incorrecto
Incluso después de una asociación correcta de windows con DpiAwarenessContexts distintos (debido al comportamiento predeterminado de Windows), pueden que los usuarios siguen viendo escalado problemas como windows con escala DpiAwarenessContexts diferente de forma diferente. Como resultado, los usuarios pueden ver texto alineación/borrosa o problemas en la interfaz de usuario de la imagen.

La solución consiste en establecer el ámbito de DpiAwarenessContext correcto para todas las ventanas y controles en la aplicación.

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>Cuadros de diálogo de nivel superior de modo mixto (TLMM)
Al crear ventanas de nivel superior, como cuadros de diálogo modales, es importante para asegurarse de que el subproceso en el estado correcto antes de la ventana (y su identificador) se crea. El subproceso se puede poner en conocimiento del sistema por utilizando la aplicación auxiliar de CDpiScope en el modo nativo o administrado de la aplicación auxiliar de DpiAwareness.EnterDpiScope en. (TLMM generalmente se debe usar en los cuadros de diálogo del que no son de WPF o windows.)

### <a name="child-level-mixed-mode-clmm"></a>Modo mixto de nivel secundario (CLMM)
De forma predeterminada, ventanas secundarias reciben lo PPP reconocimiento contexto del subproceso actual si se creó sin un elemento primario o el contexto de reconocimiento de PPP del elemento primario cuando se crean con un elemento primario. Para crear a un elemento secundario con un contexto de reconocimiento de PPP diferente de su elemento primario, se puede poner el subproceso en el contexto de reconocimiento de PPP deseado. A continuación, el elemento secundario se puede crear sin un elemento primario y duplicando manualmente a la ventana primaria.

#### <a name="clmm-issues"></a>Problemas CLMM
Mayoría del trabajo de cálculo de la interfaz de usuario que se produce como parte de la cadena de bucle o evento mensajería principal ya debe estar ejecutándose en el contexto adecuado de reconocimiento de PPP. Sin embargo, si fuera de estos flujos de trabajo principales se realizan de coordenadas y cálculos de tamaño (por ejemplo, durante un tiempo de inactividad, o fuera del subproceso de interfaz de usuario, a continuación, el contexto actual de reconocimiento de PPP podría ser incorrecto dan lugar a una mala colocación de la interfaz de usuario o mal problemas de ajuste de tamaño. Colocar el subproceso en el estado correcto para la interfaz de usuario trabajo normalmente corrige el problema.
 
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
```cpp
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

> [!NOTE]
> Visual Studio solo admite reconocimiento PerMonitorV2, por lo que el valor de enumeración PerMonitor se traduce en el valor de Windows de DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2.

#### <a name="forcing-a-control-into-a-specific-dpiawarenesscontext"></a>Forzar un control en un DpiAwarenessContext específico
Interfaz de usuario heredado que no se está actualizando para admitir el modo PMA, puede seguir necesitando ajustes menores para trabajar mientras se está ejecutando Visual Studio en modo PMA. Una corrección de este tipo implica asegurarse de que se está creando la interfaz de usuario en el derecho DpiAwarenessContext. Para forzar la interfaz de usuario en un determinado DpiAwarenessContext, puede especificar un ámbito de PPP con el código siguiente:

C#:
```cs
using (DpiAwareness.EnterDpiScope(DpiAwarenessContext.SystemAware))
{
    Form form = new MyForm();
    form.ShowDialog();
}
```

C++:
```cpp
void MyClass::ShowDialog()
{
    VsUI::CDpiScope dpiScope(DPI_AWARENESS_CONTEXT_SYSTEM_AWARE);
    HWND hwnd = ::CreateWindow(...);
}
```

> [!NOTE]
> Forzar la DpiAwarenessContext solo funciona en la interfaz de usuario que no son de WPF y de nivel superior cuadros de diálogo WPF. Al crear UI de WPF es hospedar dentro de las ventanas de herramientas o diseñadores, tan pronto como el contenido se inserta en el árbol de la UI de WPF, pasa al proceso actual DpiAwarenessContext.

## <a name="known-issues"></a>Problemas conocidos
### <a name="windows-forms"></a>Windows Forms

Para optimizar los nuevos escenarios de modo mixto, Windows Forms puede cambiar cómo crea los controles y windows cada vez que su elemento primario no se estableció explícitamente. Anteriormente, los controles sin una primaria explícita utilizan un interno "estacionamiento ventana" como primario temporal para el control o la ventana que se va a crear. 

Antes de .NET 4.8, hubo una sola "estacionamiento ventana" que obtiene su DpiAwarenessContext desde el contexto actual de reconocimiento de PPP de subproceso durante la creación de la ventana. Cualquier control anulado como primario hereda la misma DpiAwarenessContext como la ventana de estacionamiento cuando el identificador del control se crea y sería duplicando con el elemento primario y se esperaba el final del desarrollador de aplicaciones. Esto provocaría que errores de tiempo si la "ventana de estacionamiento" tenía un DpiAwarenessContext mayor que la ventana primaria final.

A partir de .NET 4.8, ahora hay una "ventana de estacionamiento" para cada DpiAwarenessContext que se ha encontrado. La principal diferencia es que se almacena en caché el DpiAwarenessContext utilizada para el control cuando se crea el control, no cuando se crea el identificador. Esto significa que el comportamiento de extremo general es el mismo, pero puede desactivar lo que solía ser un problema en función de control de tiempo en un problema de coherencia. También ofrece el programador de aplicaciones más un comportamiento determinista para escribir su código de interfaz de usuario y definir el ámbito correctamente.
