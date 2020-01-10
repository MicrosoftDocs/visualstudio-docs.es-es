---
title: Cuadro de herramientas, Componentes (Pestaña)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.FrameworkComponents
- VS.CHOOSEITEMS.COMComponents
- VS.CHOOSEITEMS.UniversalWindowsComponents
helpviewer_keywords:
- Toolbox, Components tab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5eb8c320a3190121d95395f7b359aa9ed978408
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597313"
---
# <a name="toolbox-components-tab"></a>Cuadro de herramientas, pestaña Componentes

Muestra los componentes que puede agregar a diseñadores de Visual Basic y C# para Windows Forms. Además de los componentes de .NET que se incluyen con Visual Studio, como <xref:System.Messaging.MessageQueue> y <xref:System.Diagnostics.EventLog>, puede agregar sus propios componentes o de terceros a esta pestaña.

Para que se muestre esta pestaña, abra el diseñador de Windows Forms. Seleccione **Vista** > **Cuadro de herramientas**. En el **Cuadro de herramientas**, seleccione la pestaña **Componentes**.

## <a name="components"></a>Componentes

**BackgroundWorker**

Crea una instancia del componente <xref:System.ComponentModel.BackgroundWorker> que puede ejecutar una operación en un subproceso dedicado independiente. Para obtener más información, vea [BackgroundWorker (Componente)](/dotnet/framework/winforms/controls/backgroundworker-component).

**DirectoryEntry**

Crea una instancia del componente <xref:System.DirectoryServices.DirectoryEntry> que encapsula un nodo u objeto en la jerarquía de Active Directory. Se puede usar para interactuar con proveedores de servicios de Active Directory.

**DirectorySearcher**

Crea una instancia del componente <xref:System.DirectoryServices.DirectorySearcher> que se puede usar para realizar consultas en Active Directory.

**ErrorProvider**

Crea una instancia del componente <xref:System.Windows.Forms.ErrorProvider>, que indica al usuario final que un control de un formulario tiene un error asociado. Para obtener más información, vea [ErrorProvider (Componente)](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

**EventLog**

Crea una instancia del componente <xref:System.Diagnostics.EventLog> que puede usar para interactuar con los registros de eventos personalizados y del sistema, como escribir eventos en un registro y leer datos de registro.

**FileSystemWatcher**

Crea una instancia del componente <xref:System.IO.FileSystemWatcher> que se puede usar para supervisar cambios en cualquier directorio o archivo al que se tenga acceso.

**HelpProvider**

Crea una instancia del componente <xref:System.Windows.Forms.HelpProvider> que proporciona ayuda emergente o en pantalla para los controles. Para obtener más información, vea [HelpProvider (Componente)](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms).

**ImageList**

Crea una instancia del componente <xref:System.Windows.Forms.ImageList> que proporciona métodos para administrar una colección de objetos <xref:System.Drawing.Image>. Para obtener más información, vea [ImageList (Componente)](/dotnet/framework/winforms/controls/imagelist-component-windows-forms).

**MessageQueue**

Crea una instancia del componente <xref:System.Messaging.MessageQueue> que se puede usar para interactuar con colas de mensajes, como leer mensajes y escribir mensajes en colas, procesar transacciones y realizar tareas de administración de colas.

**PerformanceCounter**

Crea una instancia del componente <xref:System.Diagnostics.PerformanceCounter> que se puede usar para interactuar con los contadores de rendimiento de Windows, como crear nuevas categorías e instancias, leer valores de contadores y realizar cálculos en datos del contador.

**Process**

Crea una instancia del componente <xref:System.Diagnostics.Process> que se puede usar para detener, iniciar y manipular los datos asociados con procesos del sistema.

**SerialPort**

Crea una instancia del componente <xref:System.IO.Ports.SerialPort> que proporciona E/S sincrónica y orientada a eventos, el acceso a los estados de punto de conexión e interrupción y el acceso a las propiedades del controlador serie.

**ServiceController**

Crea una instancia del componente <xref:System.ServiceProcess.ServiceController> que puede usar para manipular servicios existentes, como iniciar y detener servicios y enviarles comandos.

**Temporizador**

Crea una instancia del componente <xref:System.Windows.Forms.Timer> que se puede usar para agregar funciones basadas en tiempo a las aplicaciones basadas en Windows. Para obtener más información, vea [Timer (Componente)](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> También hay un componente <xref:System.Timers.Timer> basado en el sistema que se puede agregar al **Cuadro de herramientas**. Este componente <xref:System.Timers.Timer> está optimizado para aplicaciones de servidor, mientras que el componente <xref:System.Windows.Forms.Timer> de Windows Forms es más adecuado para su uso en Windows Forms.

## <a name="see-also"></a>Vea también

- [Controles que se utilizan en formularios Windows Forms](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Elegir elementos del Cuadro de herramientas, componentes de WPF](choose-toolbox-items-wpf-components.md)
- [Cuadro de herramientas](../../ide/reference/toolbox.md)
