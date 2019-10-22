---
title: Compatibilidad de reconocimiento por monitor para extensores de Visual Studio
titleSuffix: ''
description: Obtenga información sobre la nueva compatibilidad con el extensor para el reconocimiento por supervisión disponible en Visual Studio 2019.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
author: rub8n
ms.author: rurios
manager: anthc
monikerRange: vs-2019
ms.topic: conceptual
dev_langs:
- CSharp
- CPP
ms.openlocfilehash: 09ec5d82251fa4598096fca8a59c9a1fd29e3f27
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/19/2019
ms.locfileid: "69585375"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Compatibilidad de reconocimiento por monitor para extensores de Visual Studio

Las versiones anteriores a Visual Studio 2019 tenían su contexto de reconocimiento de PPP establecido en compatible con el sistema, en lugar de con el reconocimiento de PPP por monitor (PMA). La ejecución en el reconocimiento del sistema provocó una experiencia visual degradada (por ejemplo, fuentes borrosas o iconos) siempre que Visual Studio tuviera que representarse en monitores con factores de escala diferentes o en equipos remotos con diferentes configuraciones de pantalla (por ejemplo, diferentes Escalado de Windows).

El contexto de reconocimiento de PPP de Visual Studio 2019 se establece como PMA, cuando el entorno lo admite, lo que permite que Visual Studio se represente según la configuración de la pantalla en la que se hospeda, en lugar de una única configuración definida por el sistema. Trasladar en última instancia a una interfaz de usuario siempre nítida para áreas de superficie que admiten el modo PMA.

Consulte la documentación sobre el [desarrollo de aplicaciones de escritorio de PPP alta en Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) para obtener más información acerca de los términos y el escenario general descritos en este documento.

## <a name="quickstart"></a>Guía de inicio rápido

- Asegúrese de que Visual Studio se está ejecutando en modo PMA (consulte habilitación de **PMA**)

- Validar que la extensión funciona correctamente en un conjunto de escenarios comunes (consulte **comprobación de las extensiones para problemas de PMA**)

- Si encuentra problemas, puede usar las estrategias/recomendaciones descritas en este documento para diagnosticar y corregir dichos problemas. También necesitará agregar el nuevo paquete de NuGet [Microsoft. VisualStudio. DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) al proyecto para tener acceso a las API necesarias.

## <a name="enable-pma"></a>Habilitar PMA

Para habilitar PMA en Visual Studio, deben cumplirse los siguientes requisitos:

- Actualización 2018 de abril de Windows 10 (v1803, RS4) o posterior
- .NET Framework 4,8 RTM o superior
- Visual Studio 2019 con la opción ["optimizar representación para pantallas con densidades de píxeles diferentes"](../../ide/reference/general-environment-options-dialog-box.md) habilitada

Una vez cumplidos estos requisitos, Visual Studio habilita automáticamente el modo PMA en todo el proceso.

> [!NOTE]
> Windows Forms contenido de Visual Studio (por ejemplo, el explorador de propiedades) solo es compatible con PMA si tiene Visual Studio 2019 versión 16,1 o posterior.

## <a name="test-your-extensions-for-pma-issues"></a>Prueba de las extensiones para problemas de PMA

Visual Studio es compatible oficialmente con los marcos de interfaz de usuario de WPF, Windows Forms, Win32 y HTML/JS. Cuando Visual Studio se coloca en el modo PMA, cada pila de la interfaz de usuario se comporta de forma diferente. Por lo tanto, independientemente del marco de interfaz de usuario, se recomienda que se realice un paso de prueba para asegurarse de que toda la interfaz de usuario sea compatible con el modo PMA.

Se recomienda validar los siguientes escenarios comunes:

- Cambiar el factor de escala de un entorno de monitor único mientras la aplicación se está ejecutando.

  Este escenario ayuda a probar que la interfaz de usuario responde al cambio dinámico de PPP de Windows.

- Acoplar y desacoplar un equipo portátil en el que un monitor conectado esté establecido en el servidor principal y el monitor conectado tenga un factor de escala diferente del portátil mientras se ejecuta la aplicación.

  Este escenario ayuda a probar que la interfaz de usuario responde al cambio de PPP de la pantalla, así como al control de las pantallas que se agregan o se quitan dinámicamente.

- Tener varios monitores con diferentes factores de escala y mover la aplicación entre ellos.

  Este escenario ayuda a probar que la interfaz de usuario responde al cambio de PPP de la pantalla.
    
- Comunicación remota en un equipo cuando los equipos locales y remotos tienen factores de escala diferentes para el monitor principal.

  Este escenario ayuda a probar que la interfaz de usuario responde al cambio dinámico de PPP de Windows.

Una buena prueba preliminar de si la interfaz de usuario puede tener problemas es si el código utiliza las clases *Microsoft. VisualStudio. Utilities. dpi. DpiHelper*, *Microsoft. VisualStudio. PlatformUI. DpiHelper*o *VsUI:: CDpiHelper* . Estas clases DpiHelper antiguas solo admiten el reconocimiento de PPP del sistema y no siempre funcionarán correctamente cuando el proceso sea PMA.

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

En el ejemplo anterior, un rectángulo que representa los límites lógicos de una ventana se convierte en unidades de dispositivo para que se pueda pasar al método nativo MonitorFromPoint que espera las coordenadas del dispositivo para devolver un puntero de monitor preciso.

### <a name="classes-of-issues"></a>Clases de problemas
Cuando el modo PMA está habilitado para Visual Studio, la interfaz de usuario podría replicar problemas de varias maneras comunes. La mayoría de estos problemas, si no todos, pueden producirse en cualquiera de los marcos de interfaz de usuario compatibles con Visual Studio. Además, estos problemas también pueden producirse cuando una parte de la interfaz de usuario se hospeda en escenarios de escala de PPP en modo mixto (consulte la [documentación](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) de Windows para obtener más información). 

#### <a name="win32-window-creation"></a>Creación de ventanas Win32
Al crear ventanas con CreateWindow () o CreateWindowEx (), un patrón común es crear la ventana en coordenadas (0,0) (la esquina superior izquierda de la pantalla principal) y, a continuación, moverla a su posición final. Sin embargo, si lo hace, la ventana desencadenará un evento o mensaje de cambio de PPP, que puede redesencadenar otros eventos o mensajes de la interfaz de usuario y, finalmente, provocar un comportamiento o una representación no deseados.

#### <a name="wpf-element-placement"></a>Colocación de elementos de WPF
Al mover elementos de WPF con las antiguas Microsoft. VisualStudio. Utilities. ppp. DpiHelper, las coordenadas superior izquierda podrían no calcularse correctamente cuando los elementos están en un valor de PPP no primario.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Serialización de los tamaños o posiciones de los elementos de la interfaz de usuario
Cuando el tamaño o la posición de la interfaz de usuario (si se guarda como unidades de dispositivo) se restaura en un contexto de PPP diferente del que se almacenó, se colocará y se dimensionará incorrectamente. Esto sucede porque las unidades de dispositivo tienen una relación PPP inherente.

#### <a name="incorrect-scaling"></a>Escala incorrecta
Los elementos de la interfaz de usuario creados en los PPP primarios se escalan correctamente; sin embargo, cuando se mueven a una pantalla con un valor de PPP diferente, no cambian de escala y su contenido es demasiado grande o demasiado pequeño.

#### <a name="incorrect-bounding"></a>Límite incorrecto
Del mismo modo que el problema de escalado, los elementos de la interfaz de usuario calculan sus límites correctamente en su contexto de PPP primario, sin embargo, cuando se mueven a un valor de PPP no primario, no calcularán correctamente los nuevos límites. Como tal, la ventana de contenido es demasiado pequeña o demasiado grande en comparación con la interfaz de usuario de hospedaje, lo que produce un espacio vacío o un recorte.

#### <a name="drag--drop"></a>Arrastrar & colocar
Siempre que estén dentro de los escenarios de PPP en modo mixto (por ejemplo, distintos elementos de la interfaz de usuario en modos de reconocimiento de PPP diferentes), las coordenadas de arrastrar y colocar podrían ser erróneas, lo que da lugar a que la posición de colocación final sea incorrecta.

#### <a name="out-of-process-ui"></a>Interfaz de usuario fuera de proceso
Algunas interfaces de usuario se crean fuera de proceso y, si el proceso externo de creación está en un modo de reconocimiento de PPP diferente que Visual Studio, esto puede presentar cualquiera de los problemas de representación anteriores.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>Windows Forms los controles, las imágenes o los diseños se representan incorrectamente
No todo el contenido de la Windows Forms admite el modo PMA. Como resultado, puede ver el problema de representación con diseños o escalas incorrectos. En este caso, una posible solución consiste en representar explícitamente Windows Forms contenido en "DpiAwarenessContext de sistema" (consulte [forzar un control en un DpiAwarenessContext específico](#force-a-control-into-a-specific-dpiawarenesscontext)).

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Windows Forms controles o ventanas que no se muestran
Una de las principales causas de este problema es que los desarrolladores intentan volver a controlar un control o una ventana con un DpiAwarenessContext en una ventana con un DpiAwarenessContext diferente.

En las siguientes imágenes se muestran las restricciones actuales del sistema operativo Windows en las ventanas parentables:

![Captura de pantalla del comportamiento de la protección correcta](media/PMA-parenting-behavior.PNG)

> [!Note]
> Puede cambiar este comportamiento estableciendo el comportamiento de hospedaje de subprocesos (consulte la [enumeración Dpi_Hosting_Behavior](/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)).

Como resultado, si establece una relación de elementos primarios y secundarios entre los modos no admitidos, se producirá un error y es posible que el control o la ventana no se representen según lo esperado.

### <a name="diagnose-issues"></a>Diagnóstico de problemas

Hay muchos factores que se deben tener en cuenta a la hora de identificar problemas relacionados con PMA: 

- ¿La interfaz de usuario o la API esperan valores lógicos o de dispositivo?
    - La interfaz de usuario y las API de WPF suelen usar valores lógicos (pero no siempre)
    - La interfaz de usuario y las API de Win32 suelen usar valores de dispositivo

- ¿De dónde proceden los valores?
    - Si recibe valores de otra interfaz de usuario o de una API, está pasando valores lógicos o de dispositivo.
    - Si recibe valores de varios orígenes, ¿todos ellos usan/esperan los mismos tipos de valores o se debe mezclar y hacer coincidir las conversiones?

- ¿Se usan constantes de interfaz de usuario y en qué formulario están?

- ¿Es el subproceso en el contexto de PPP correcto para los valores que está recibiendo?

  Los cambios para habilitar el hospedaje de PPP mixto deben poner normalmente las rutas de acceso de código en el contexto derecho; sin embargo, el trabajo realizado fuera del bucle de mensajes principal o el flujo de eventos podría ejecutarse en un contexto de PPP incorrecto.

- ¿Los valores son límites de contexto entre PPP?

  Arrastrar & Drop es una situación común en la que las coordenadas pueden cruzar contextos de PPP. La ventana intenta hacer lo correcto, pero en algunos casos, es posible que la interfaz de usuario del host tenga que realizar el trabajo de conversión para asegurarse de que coincidan los límites del contexto.

### <a name="pma-nuget-package"></a>Paquete NuGet de PMA
Las nuevas bibliotecas de DpiAwarness se pueden encontrar en el paquete NuGet [Microsoft. VisualStudio. DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) .

### <a name="recommended-tools"></a>Herramientas recomendadas
Las herramientas siguientes pueden ayudarle a depurar problemas relacionados con el PMA en algunas de las distintas pilas de interfaz de usuario compatibles con Visual Studio.

#### <a name="snoop"></a>Espionaje
Snoop es una herramienta de depuración de XAML que tiene alguna funcionalidad adicional que las herramientas de XAML de Visual Studio integradas no tienen. Además, Snoop no necesita depurar activamente Visual Studio para poder ver y retocar su interfaz de usuario de WPF. Las dos formas principales de Snoop pueden ser útiles para diagnosticar problemas de PMA es para validar coordenadas de ubicación lógicas o límites de tamaño, y para validar la interfaz de usuario tiene los PPP correctos.
 
#### <a name="visual-studio-xaml-tools"></a>Herramientas XAML de Visual Studio
Como Snoop, las herramientas de XAML en Visual Studio pueden ayudar a diagnosticar problemas de PMA. Una vez que se encuentra un posible culpable, puede establecer puntos de interrupción y usar la ventana del árbol visual activo, así como las ventanas de depuración, para inspeccionar los límites de la interfaz de usuario y los PPP actuales.

## <a name="strategies-for-fixing-pma-issues"></a>Estrategias para corregir problemas de PMA

### <a name="replace-dpihelper-calls"></a>Reemplazar llamadas DpiHelper

En la mayoría de los casos, la corrección de problemas de la interfaz de usuario en el modo PMA reduce el reemplazo de llamadas en código administrado a las clases antiguas *Microsoft. VisualStudio. Utilities. ppp. DpiHelper* y *Microsoft. VisualStudio. PlatformUI. DpiHelper* , con llamadas a la nueva  *Clase auxiliar Microsoft. VisualStudio. Utilities. DpiAwareness* . 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

En el caso de código nativo, se implica el reemplazo de llamadas a la clase antigua *VsUI:: CDpiHelper* con llamadas a la nueva clase *VsUI:: CDpiAwareness* . 

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

Las nuevas clases DpiAwareness y CDpiAwareness ofrecen las mismas aplicaciones auxiliares de conversión de unidades que las clases DpiHelper pero requieren un parámetro de entrada adicional: el elemento de la interfaz de usuario que se va a usar como referencia para la operación de conversión. Es importante tener en cuenta que las aplicaciones auxiliares de escalado de imágenes no existen en las nuevas aplicaciones auxiliares de DpiAwareness/CDpiAwareness y, si es necesario, se debe usar la [ImageService](../image-service-and-catalog.md) en su lugar.

La clase DpiAwareness administrada proporciona aplicaciones auxiliares para objetos visuales de WPF, controles de Windows Forms y HWND de Win32 y HMONITORs (ambos en forma de IntPtrs), mientras que la clase de CDpiAwareness nativa ofrece aplicaciones auxiliares HWND y HMONITOR.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Windows Forms cuadros de diálogo, ventanas o controles que se muestran en el DpiAwarenessContext incorrecto
Incluso después de una protección correcta de Windows con diferentes DpiAwarenessContexts (debido a un comportamiento predeterminado de Windows), los usuarios pueden seguir viendo problemas de escalado como ventanas con diferentes escalas de DpiAwarenessContexts de forma diferente. Como resultado, es posible que los usuarios vean problemas de alineación/texto borroso o imagen en la interfaz de usuario.

La solución consiste en establecer el ámbito de DpiAwarenessContext correcto para todas las ventanas y controles de la aplicación.

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>Cuadros de diálogo de modo mixto de nivel superior (TLMM)
Al crear ventanas de nivel superior como cuadros de diálogo modales, es importante asegurarse de que el subproceso está en el estado correcto antes de que se cree la ventana (y su identificador). El subproceso se puede incluir en el reconocimiento del sistema mediante el uso de la aplicación auxiliar CDpiScope en la aplicación auxiliar nativa o DpiAwareness. EnterDpiScope en Managed. (TLMM generalmente debe usarse en cuadros de diálogo o ventanas que no son de WPF).

### <a name="child-level-mixed-mode-clmm"></a>Modo mixto de nivel secundario (CLMM)
De forma predeterminada, las ventanas secundarias reciben el contexto de reconocimiento de PPP del subproceso actual si se crean sin un elemento primario o el contexto de reconocimiento de PPP del elemento primario cuando se crean con un elemento primario. Para crear un elemento secundario con un contexto de reconocimiento de PPP distinto al de su elemento primario, el subproceso se puede colocar en el contexto de reconocimiento de PPP deseado. Después, el elemento secundario se puede crear sin un elemento primario y cambiar manualmente de primario a la ventana primaria.

#### <a name="clmm-issues"></a>Problemas de CLMM
La mayor parte del trabajo de cálculo de la interfaz de usuario que se produce como parte del bucle de mensajería principal o de la cadena de eventos debe estar ya en ejecución en el contexto de reconocimiento de PPP adecuado. Sin embargo, si los cálculos de coordenadas o de ajuste de tamaño se realizan fuera de estos flujos de trabajo principales (por ejemplo, durante una tarea de tiempo de inactividad o fuera del subproceso de la interfaz de usuario, el contexto de reconocimiento de PPP actual podría ser incorrecto, lo que provocaría un error de la interfaz de usuario o problemas de cambio de tamaño. En general, poner el subproceso en el estado correcto para el trabajo de la interfaz de usuario corrige el problema.
 
#### <a name="opt-out-of-clmm"></a>No participar en CLMM
Si una ventana de herramientas que no es de WPF se está migrando a una compatibilidad total con el PMA, deberá optar por no participar en CLMM. Para ello, es necesario implementar una nueva interfaz: IVsDpiAware.

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

En el caso de los lenguajes administrados, el mejor lugar para implementar esta interfaz está en la misma clase que deriva de *Microsoft. VisualStudio. Shell. ToolWindowPane*. Para C++, el mejor lugar para implementar esta interfaz está en la misma clase que implementa *IVsWindowPane* desde vsshell. h.

El valor devuelto por la propiedad Mode en la interfaz es __VSDPIMODE (y se convierte en un valor uint en Managed):

```cs
enum __VSDPIMODE
{
    VSDM_Unaware    = 0x01,
    VSDM_System     = 0x02,
    VSDM_PerMonitor = 0x03,
}
```

- No compatible significa que la ventana de herramientas debe controlar 96 PPP, Windows controlará el escalado para el resto de PPP. La causa de que el contenido sea ligeramente borroso.
- Sistema significa que la ventana de herramientas debe controlar el PPP del PPP de la pantalla principal. Cualquier presentación con un PPP coincidente tendrá un aspecto nítido, pero si el PPP es diferente o cambia durante la sesión, Windows controlará el escalado y será ligeramente borroso.
- Permonitor significa que la ventana de herramientas debe administrar todos los PPP en todas las pantallas y cada vez que cambie el PPP.

> [!NOTE]
> Visual Studio solo admite el reconocimiento de PerMonitorV2, por lo que el valor de enumeración de permonitor se traduce en el valor de Windows de DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2.

#### <a name="force-a-control-into-a-specific-dpiawarenesscontext"></a>Forzar un control en un DpiAwarenessContext específico

La interfaz de usuario heredada que no se está actualizando para admitir el modo PMA puede seguir necesitando pequeños ajustes para trabajar mientras Visual Studio se ejecuta en modo PMA. Una de estas correcciones implica asegurarse de que la interfaz de usuario se crea en el DpiAwarenessContext derecho. Para forzar la interfaz de usuario en un DpiAwarenessContext determinado, puede especificar un ámbito de PPP con el código siguiente:

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
> Forzar el DpiAwarenessContext solo funciona en los cuadros de diálogo que no son de WPF y de nivel superior. Al crear una interfaz de usuario de WPF que se hospedará dentro de las ventanas de herramientas o los diseñadores, en cuanto el contenido se inserte en el árbol de la interfaz de usuario de WPF, se convertirá en el proceso actual DpiAwarenessContext.

## <a name="known-issues"></a>Problemas conocidos

### <a name="windows-forms"></a>Windows Forms

Para optimizar los nuevos escenarios en modo mixto, Windows Forms ha cambiado la forma en que crea controles y ventanas cuando su elemento primario no se estableció explícitamente. Anteriormente, los controles sin un elemento primario explícito usaban una "ventana de estacionamiento" interna como un elemento primario temporal en el control o la ventana que se va a crear. 

Antes de .NET 4,8, había una única "ventana de estacionamiento" que obtiene su DpiAwarenessContext del contexto de reconocimiento de PPP del subproceso actual en el momento de creación de la ventana. Cualquier control no primario hereda el mismo DpiAwarenessContext que la ventana de estacionamiento cuando se crea el identificador del control y el desarrollador de la aplicación puede cambiar el elemento primario al elemento primario esperado. Esto produciría errores basados en el tiempo si la "ventana de estacionamiento" tenía un DpiAwarenessContext superior al de la ventana primaria final.

A partir de .NET 4,8, ahora hay una "ventana de aparcamiento" para cada DpiAwarenessContext que se ha encontrado. La otra diferencia principal es que el DpiAwarenessContext que se usa para el control se almacena en caché cuando se crea el control, no cuando se crea el identificador. Esto significa que el comportamiento de final general es el mismo, pero puede convertir lo que solía ser un problema basado en el tiempo en un problema coherente. También proporciona al desarrollador de la aplicación un comportamiento más determinista para escribir el código de la interfaz de usuario y el ámbito correcto.
