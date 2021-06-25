---
title: Per-Monitor awareness support for Visual Studio extenders
titleSuffix: ''
description: Obtenga información sobre la nueva compatibilidad extensor para el reconocimiento por monitor disponible en Visual Studio 2019.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
author: rub8n
ms.author: rurios
manager: anthc
monikerRange: vs-2019
ms.topic: reference
dev_langs:
- CSharp
- CPP
ms.openlocfilehash: 90ec038e8f27407ba08633bacbb5576bee2a7883
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902051"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Per-Monitor awareness support for Visual Studio extenders

Las versiones anteriores a Visual Studio 2019 tenían su contexto de reconocimiento de PPP establecido en compatible con el sistema, en lugar de reconocimiento de PPP por monitor (PMA). La ejecución en el reconocimiento del sistema dio lugar a una experiencia visual degradada (por ejemplo, fuentes o iconos desenfocados) siempre que Visual Studio tuviera que representarse en monitores con diferentes factores de escala o de forma remota en máquinas con diferentes configuraciones de pantalla (por ejemplo, escalado de Windows diferente).

El contexto de reconocimiento de PPP de Visual Studio 2019 se establece como PMA, cuando el entorno lo admite, lo que permite que Visual Studio se represente según la configuración de la pantalla donde se hospeda en lugar de una única configuración definida por el sistema. En última instancia, se traduce en una interfaz de usuario siempre nítida para las áreas de superficie que admiten el modo PMA.

Consulte la documentación [desarrollo de aplicaciones de](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) escritorio con valores altos de PPP en Windows para obtener más información sobre los términos y el escenario general que se tratan en este documento.

## <a name="quickstart"></a>Inicio rápido

- Asegúrese Visual Studio que se ejecuta en modo DESAO (consulte **Habilitación de PMA)**

- Compruebe que la extensión funciona correctamente en un conjunto de escenarios comunes (consulte Prueba de las extensiones para **problemas de PMA).**

- Si encuentra problemas, puede usar las estrategias y recomendaciones que se deban tratar en este documento para diagnosticar y corregir esos problemas. También deberá agregar el nuevo paquete NuGet [Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) al proyecto para acceder a las API necesarias.

## <a name="enable-pma"></a>Habilitación de PMA

Para habilitar EL VISUAL STUDIO, es necesario cumplir los siguientes requisitos:

- Actualización de abril de 2018 de Windows 10 (v1803, RS4) o posterior
- .NET Framework 4.8 RTM o superior
- Visual Studio 2019 con la opción "Optimizar la representación para pantallas con [densidades de](../../ide/reference/general-environment-options-dialog-box.md) píxeles diferentes" habilitada

Una vez que se cumplen estos requisitos, Visual Studio habilitar automáticamente el modo DESA través del proceso.

> [!NOTE]
> Windows Forms contenido de Visual Studio (por ejemplo, el Explorador de propiedades) solo es compatible con VISUAL STUDIO 2019, versión 16.1 o posterior.

## <a name="test-your-extensions-for-pma-issues"></a>Prueba de las extensiones para problemas de PMA

Visual Studio admite oficialmente los marcos de interfaz de usuario de WPF, Windows Forms, Win32 y HTML/JS. Cuando Visual Studio se pone en modo PMA, cada pila de interfaz de usuario se comporta de forma diferente. Por lo tanto, independientemente del marco de la interfaz de usuario, se recomienda que se realice una prueba para asegurarse de que toda la interfaz de usuario es compatible con el modo DESL.

Se recomienda validar los siguientes escenarios comunes:

- Cambio del factor de escala de un único entorno de supervisión mientras se ejecuta la aplicación.

  Este escenario ayuda a probar que la interfaz de usuario responde al cambio dinámico de PPP de Windows.

- Acoplar o desacoplar un portátil donde un monitor conectado está establecido en el principal y el monitor conectado tiene un factor de escala diferente al portátil mientras se ejecuta la aplicación.

  Este escenario ayuda a probar que la interfaz de usuario responde al cambio de PPP de visualización, así como a controlar las pantallas que se agregan o quitan dinámicamente.

- Tener varios monitores con diferentes factores de escala y mover la aplicación entre ellos.

  Este escenario ayuda a probar que la interfaz de usuario responde al cambio de PPP de visualización.
    
- Comunicación remota en una máquina cuando las máquinas locales y remotas tienen factores de escala diferentes para el monitor principal.

  Este escenario ayuda a probar que la interfaz de usuario responde al cambio dinámico de PPP de Windows.

Una buena prueba preliminar de si la interfaz de usuario puede tener problemas es si el código utiliza las clases *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper*, *Microsoft.VisualStudio.PlatformUI.DpiHelper* o *VsUI::CDpiHelper.* Estas clases de DpiHelper antiguas solo admiten el reconocimiento de PPP del sistema y no siempre funcionarán correctamente cuando el proceso es DESAse.

El uso típico de estos DpiHelpers tendrá el siguiente aspecto:

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

En el ejemplo anterior, un rectángulo que representa los límites lógicos de una ventana se convierte en unidades de dispositivo para que se pueda pasar al método nativo MonitorFromPoint que espera coordenadas de dispositivo para devolver un puntero de monitor preciso.

### <a name="classes-of-issues"></a>Clases de problemas
Cuando el modo DES++ está habilitado Visual Studio, la interfaz de usuario podría replicar los problemas de varias maneras comunes. La mayoría de estos problemas, si no todos, pueden producirse en cualquiera de los Visual Studio de interfaz de usuario compatibles. Además, estos problemas también pueden producirse cuando un elemento de la interfaz de usuario se hospeda en escenarios de escalado de PPP en modo mixto (consulte la documentación de [Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) para obtener más información). 

#### <a name="win32-window-creation"></a>Creación de ventanas de Win32
Al crear ventanas con CreateWindow() o CreateWindowEx(), un patrón común es crear la ventana en coordenadas (0,0) (la esquina superior e izquierda de la pantalla principal) y moverla a su posición final. Sin embargo, esto puede hacer que la ventana desencadene un mensaje o evento con cambios de PPP, lo que puede volver a procesar otros mensajes o eventos de la interfaz de usuario y, finalmente, provocar un comportamiento o una representación no deseados.

#### <a name="wpf-element-placement"></a>Colocación de elementos WPF
Al mover elementos wpf mediante el antiguo Microsoft.VisualStudio.Utilities.Dpi.DpiHelper, es posible que las coordenadas superior izquierda no se calcule correctamente siempre que los elementos estén en un PPP no principal.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Serialización de posiciones o tamaños de elementos de interfaz de usuario
Cuando el tamaño o la posición de la interfaz de usuario (si se guardan como unidades de dispositivo) se restauran en un contexto de PPP diferente al que se almacenaba, se colocará y se dimensionará incorrectamente. Esto sucede porque las unidades de dispositivo tienen una relación de PPP inherente.

#### <a name="incorrect-scaling"></a>Escalado incorrecto
Los elementos de la interfaz de usuario creados en el PPP principal se escalarán correctamente; sin embargo, cuando se mueven a una pantalla con un PPP diferente, no se escalan de nuevo y su contenido es demasiado grande o demasiado pequeño.

#### <a name="incorrect-bounding"></a>Límite incorrecto
De forma similar al problema de escalado, los elementos de la interfaz de usuario calculan sus límites correctamente en su contexto de PPP principal; sin embargo, cuando se mueven a un PPP no principal, no calculan los nuevos límites correctamente. Por lo tanto, la ventana de contenido es demasiado pequeña o demasiado grande en comparación con la interfaz de usuario de hospedaje, lo que da como resultado un espacio vacío o un recorte.

#### <a name="drag--drop"></a>Arrastrar & colocar
Siempre que dentro de escenarios de PPP en modo mixto (por ejemplo, distintos elementos de la interfaz de usuario que se representa en distintos modos de reconocimiento de PPP), las coordenadas de arrastrar y colocar podrían estar malcalculadas, lo que provocaría que la posición final de colocación terminara incorrecta.

#### <a name="out-of-process-ui"></a>Interfaz de usuario fuera de proceso
Parte de la interfaz de usuario se crea fuera de proceso y, si el proceso externo de creación está en un modo de reconocimiento de PPP diferente al de Visual Studio, esto puede presentar cualquiera de los problemas de representación anteriores.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>Windows Forms, imágenes o diseños representados incorrectamente
No todos los contenidos Windows Forms admiten el modo PMA. Como resultado, es posible que vea un problema de representación con diseños o escalado incorrectos. Una posible solución en este caso es representar explícitamente contenido Windows Forms en PppAwarenessContext "compatible con el sistema" (consulte Forzar un control en un [DpiAwarenessContext específico).](#force-a-control-into-a-specific-dpiawarenesscontext)

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Windows Forms controles o ventanas que no se muestran
Una de las principales causas de este problema es que los desarrolladores intentan volver a tener un control o una ventana con un Objeto DpiAwarenessContext en una ventana con un DpiAwarenessContext diferente.

En las imágenes siguientes se muestran las **restricciones del** sistema operativo Windows predeterminadas actuales en las ventanas primarias:

![Captura de pantalla del comportamiento de parentesco correcto](media/PMA-parenting-behavior.PNG)

> [!Note]
> Puede cambiar este comportamiento estableciendo el comportamiento de hospedaje de subprocesos (consulte Dpi_Hosting_Behavior [enumeración](/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)).

Como resultado, si establece la relación de elementos primarios y secundarios entre modos no admitidos, se producirá un error y es posible que el control o la ventana no se representen según lo previsto.

### <a name="diagnose-issues"></a>Diagnosticar problemas

Hay muchos factores que se deben tener en cuenta al identificar problemas relacionados con ELÉC: 

- ¿La interfaz de usuario o la API esperan valores lógicos o de dispositivo?
    - Las API y la interfaz de usuario de WPF suelen usar valores lógicos (pero no siempre)
    - La interfaz de usuario y las API de Win32 suelen usar valores de dispositivo

- ¿De dónde vienen los valores?
    - Si recibe valores de otra interfaz de usuario o API, es pasar valores lógicos o de dispositivo.
    - Si recibe valores de varios orígenes, ¿todos usan o esperan los mismos tipos de valores o las conversiones deben combinarse y combinarse?

- ¿Están en uso las constantes de interfaz de usuario y en qué formulario se encuentran?

- ¿Está el subproceso en el contexto de PPP correcto para los valores que recibe?

  Los cambios para habilitar el hospedaje de PPP mixto suelen colocar las rutas de acceso de código en el contexto correcto; sin embargo, el trabajo realizado fuera del bucle de mensajes principal o el flujo de eventos podría ejecutarse en el contexto de PPP incorrecto.

- ¿Los valores cruzan los límites de contexto de PPP?

  Arrastrar & colocar es una situación común en la que las coordenadas pueden atravesar contextos de PPP. Window intenta hacer lo correcto, pero en algunos casos, es posible que la interfaz de usuario del host tenga que realizar el trabajo de conversión para garantizar la coincidencia de los límites de contexto.

### <a name="pma-nuget-package"></a>Paquete NuGet DE PMA
Las nuevas bibliotecas dpiAwarness se pueden encontrar en el [paquete NuGet Microsoft.VisualStudio.DpiAwareness.](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/)

### <a name="recommended-tools"></a>Herramientas recomendadas
Las siguientes herramientas pueden ayudar a depurar problemas relacionados con EL MUNDO en algunas de las distintas pilas de interfaz de usuario admitidas por Visual Studio.

#### <a name="snoop"></a>Snoop
La herramienta de depuración Xaml es una herramienta de depuración XAML que tiene alguna funcionalidad adicional que las herramientas integradas Visual Studio XAML no tienen. Además, No es necesario depurar de forma activa Visual Studio para poder ver y ajustar su interfaz de usuario de WPF. Las dos maneras principales en las que El usuario puede resultar útil para diagnosticar problemas de PMA es para validar coordenadas de colocación lógicas o límites de tamaño, y para validar que la interfaz de usuario tiene el PPP correcto.
 
#### <a name="visual-studio-xaml-tools"></a>Visual Studio XAML
Al igual que La mente, las herramientas XAML de Visual Studio pueden ayudar a diagnosticar problemas de PMA. Una vez que se encuentra un probable responsable, puede establecer puntos de interrupción y usar la ventana Árbol visual en directo, así como las ventanas de depuración, para inspeccionar los límites de la interfaz de usuario y el PPP actual.

## <a name="strategies-for-fixing-pma-issues"></a>Estrategias para corregir problemas de PMA

### <a name="replace-dpihelper-calls"></a>Reemplazo de llamadas de DpiHelper

En la mayoría de los casos, la corrección de problemas de la interfaz de usuario en modo PMA se reduce a reemplazar las llamadas en código administrado a las clases anteriores *Microsoft.VisualStudio.Utilities.DpiHelper* y *Microsoft.VisualStudio.PlatformUI.DpiHelper,* por llamadas a la nueva clase auxiliar *Microsoft.VisualStudio.Utilities.DpiAwareness.* 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

Para el código nativo, implicará reemplazar las llamadas a la clase *VsUI::CDpiHelper* anterior por llamadas a la nueva clase *VsUI::CDpiAwareness.* 

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

Las nuevas clases DpiAwareness y CDpiAwareness ofrecen los mismos asistentes de conversión de unidades que las clases DpiHelper, pero requieren un parámetro de entrada adicional: el elemento de interfaz de usuario que se usará como referencia para la operación de conversión. Es importante tener en cuenta que los asistentes de escalado de imágenes no existen en los nuevos asistentes dpiAwareness/CDpiAwareness y, si es necesario, se debe usar [ImageService](../image-service-and-catalog.md) en su lugar.

La clase PppAwareness administrada ofrece asistentes para objetos visuales de WPF, controles Windows Forms y HWND de Win32 y HMONITORs (ambos en forma de IntPtrs), mientras que la clase CDpiAwareness nativa ofrece asistentes HWND y HMONITOR.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Windows Forms diálogos, ventanas o controles mostrados en el dpiAwarenessContext incorrecto
Incluso después de un paréntesis correcto de ventanas con diferentes DpiAwarenessContexts (debido al comportamiento predeterminado de Windows), los usuarios pueden ver problemas de escalado a medida que las ventanas con diferentes DpiAwarenessContexts escalan de forma diferente. Como resultado, los usuarios pueden ver problemas de alineación o texto o imagen desenfocado en la interfaz de usuario.

La solución es establecer el ámbito de DpiAwarenessContext correcto para todas las ventanas y controles de la aplicación.

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>Cuadros de diálogo de modo mixto de nivel superior (TLMM)
Al crear ventanas de nivel superior, como los diálogos modales, es importante asegurarse de que el subproceso está en el estado correcto antes de crear la ventana (y su identificador). El subproceso se puede poner en conocimiento del sistema mediante el asistente CDpiScope en nativo o el asistente DpiAwareness.EnterDpiScope en administrado. (TLMM debe usarse generalmente en ventanas o cuadros de diálogo que no son de WPF).

### <a name="child-level-mixed-mode-clmm"></a>Modo mixto de nivel secundario (CLMM)
De forma predeterminada, las ventanas secundarias reciben el contexto de reconocimiento de PPP del subproceso actual si se crea sin un elemento primario o el contexto de reconocimiento de PPP del elemento primario cuando se crea con un elemento primario. Para crear un elemento secundario con un contexto de reconocimiento de PPP diferente al primario, el subproceso se puede colocar en el contexto de reconocimiento de PPP deseado. A continuación, el elemento secundario se puede crear sin un elemento primario y volver a ser primario manualmente en la ventana primaria.

#### <a name="clmm-issues"></a>Problemas de CLMM
La mayor parte del trabajo de cálculo de la interfaz de usuario que se produce como parte del bucle de mensajería principal o la cadena de eventos ya debe ejecutarse en el contexto de reconocimiento de PPP correcto. Sin embargo, si los cálculos de coordenada o ajuste de tamaño se realizan fuera de estos flujos de trabajo principales (por ejemplo, durante una tarea de tiempo de inactividad o fuera del subproceso de la interfaz de usuario), el contexto de reconocimiento de PPP actual podría ser incorrecto, lo que podría dar lugar a errores de colocación de la interfaz de usuario o problemas de tamaño incorrecto. Poner el subproceso en el estado correcto para el trabajo de la interfaz de usuario suele corregir el problema.
 
#### <a name="opt-out-of-clmm"></a>No participar en CLMM
Si se está migrando una ventana de herramientas que no es de WPF para admitir totalmente ELWS, tendrá que dejar de participar en CLMM. Para ello, es necesario implementar una nueva interfaz: IVsDpiAware.

```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAware
{
    [ComAliasName("Microsoft.VisualStudio.Shell.Interop.VSDPIMode")]
    uint Mode {get;}
}
```

```cpp
IVsDpiAware : public IUnknown
{
    public:
        HRRESULT STDMETHODCALLTYPE get_Mode(__RCP__out VSDPIMODE *dwMode);
};
```

Para los lenguajes administrados, el mejor lugar para implementar esta interfaz es en la misma clase que deriva de *Microsoft.VisualStudio.Shell.ToolWindowPane*. Para C++, el mejor lugar para implementar esta interfaz es en la misma clase que implementa *IVsWindowPane* desde vsshell.h.

El valor devuelto por la propiedad Mode en la interfaz es un __VSDPIMODE (y se convierte en un uint en administrado):

```cs
enum __VSDPIMODE
{
    VSDM_Unaware    = 0x01,
    VSDM_System     = 0x02,
    VSDM_PerMonitor = 0x03,
}
```

- Desconocido significa que la ventana de herramientas debe controlar 96 PPP, Windows controlará el escalado de todas las demás DPI. Como resultado, el contenido está ligeramente desenfocado.
- El sistema significa que la ventana de herramientas debe controlar el valor de PPP del valor de PPP de la pantalla principal. Cualquier pantalla con un PPP correspondiente tendrá un aspecto nítido, pero si el valor de PPP es diferente o cambia durante la sesión, Windows controlará el escalado y estará ligeramente desenfocado.
- PerMonitor significa que la ventana de herramientas debe controlar todos los DPI en todas las pantallas y cada vez que cambia el valor de PPP.

> [!NOTE]
> Visual Studio solo admite el reconocimiento de PerMonitorV2, por lo que el valor de enumeración PerMonitor se traduce en el valor de Windows de DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2.

#### <a name="force-a-control-into-a-specific-dpiawarenesscontext"></a>Forzar un control en un objeto DpiAwarenessContext específico

La interfaz de usuario heredada que no se está actualizando para admitir el modo PMA, puede seguir necesitando pequeños ajustes para funcionar mientras Visual Studio se ejecuta en el modo PMA. Una de estas corrección implica asegurarse de que la interfaz de usuario se crea en el dpiAwarenessContext correcto. Para forzar la interfaz de usuario a un Determinado DpiAwarenessContext, puede escribir un ámbito de PPP con el código siguiente:

```cs
using (DpiAwareness.EnterDpiScope(DpiAwarenessContext.SystemAware))
{
    Form form = new MyForm();
    form.ShowDialog();
}
```

```cpp
void MyClass::ShowDialog()
{
    VsUI::CDpiScope dpiScope(DPI_AWARENESS_CONTEXT_SYSTEM_AWARE);
    HWND hwnd = ::CreateWindow(...);
}
```

> [!NOTE]
> Forzar DpiAwarenessContext solo funciona en cuadros de diálogo de WPF y de interfaz de usuario que no son de WPF. Al crear la interfaz de usuario de WPF que se va a hospedar en ventanas de herramientas o diseñadores, en cuanto el contenido se inserta en el árbol de interfaz de usuario de WPF, se convierte al proceso actual DpiAwarenessContext.

## <a name="known-issues"></a>Problemas conocidos

### <a name="windows-forms"></a>Windows Forms

Para optimizar para los nuevos escenarios de modo mixto, Windows Forms cómo crea controles y ventanas siempre que su elemento primario no se haya establecido explícitamente. Anteriormente, los controles sin un elemento primario explícito usaban una "ventana de aparcamiento" interna como elemento primario temporal para el control o la ventana que se está creando. 

Antes de .NET 4.8, había una única "ventana de aparcamiento" que obtiene su DpiAwarenessContext del contexto de reconocimiento de PPP del subproceso actual en el momento de creación de la ventana. Cualquier control no primario hereda el mismo DpiAwarenessContext que la ventana de aparcamiento cuando se crea el identificador del control y el desarrollador de la aplicación lo reparentaría con el elemento primario final o esperado. Esto provocaría errores basados en el tiempo si la "ventana de aparcamiento" tuviera un valor de PppAwarenessContext superior al de la ventana primaria final.

A partir de .NET 4.8, ahora hay una "ventana de aparcamiento" para cada DpiAwarenessContext que se encuentre. La otra diferencia principal es que El Objeto DpiAwarenessContext usado para el control se almacena en caché cuando se crea el control, no cuando se crea el identificador. Esto significa que el comportamiento final general es el mismo, pero puede convertir lo que solía ser un problema basado en el tiempo en un problema coherente. También proporciona al desarrollador de aplicaciones un comportamiento más determinista para escribir su código de interfaz de usuario y determinar su ámbito correctamente.
