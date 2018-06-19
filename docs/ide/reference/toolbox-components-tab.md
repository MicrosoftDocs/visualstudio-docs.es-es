---
title: Cuadro de herramientas, Componentes (Pestaña)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a05ea5b06e985a21fbe45882ccfb36bfe194034
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947955"
---
# <a name="toolbox-components-tab"></a>Cuadro de herramientas, Componentes (Pestaña)

Muestra los componentes que puede agregar a diseñadores de Visual Basic y C#. Además de los componentes de .NET Framework que se incluyen con Visual Studio, como los componentes <xref:System.Messaging.MessageQueue> y <xref:System.Diagnostics.EventLog>, puede agregar sus propios componentes o unos de terceros a esta pestaña.

 Para mostrar esta pestaña, en el menú **Ver** seleccione **Cuadro de herramientas**. En el **Cuadro de herramientas**, seleccione la pestaña **Componentes**.

 **BackgroundWorker**

 Crea una instancia del componente `System.ComponentModel.BackgroundWorker` que puede ejecutar una operación en un subproceso dedicado independiente.

 **DirectoryEntry**

 Crea una instancia del componente <xref:System.DirectoryServices.DirectoryEntry> que encapsula un nodo u objeto en la jerarquía de Active Directory. Se puede usar para interactuar con proveedores de servicios de Active Directory.

 **DirectorySearcher**

 Crea una instancia del componente <xref:System.DirectoryServices.DirectorySearcher> que se puede usar para realizar consultas en Active Directory.

 **ErrorProvider**

 Crea una instancia del componente `System.Windows.Forms.ErrorProvider`, que indica al usuario final que un control de un formulario tiene un error asociado.

 **EventLog**

 Crea una instancia del componente <xref:System.Diagnostics.EventLog> que puede usar para interactuar con los registros de eventos personalizados y del sistema, como escribir eventos en un registro y leer datos de registro.

 **FileSystemWatcher**

 Crea una instancia del componente <xref:System.IO.FileSystemWatcher> que se puede usar para supervisar cambios en cualquier directorio o archivo al que se tenga acceso.

 **HelpProvider**

 Crea una instancia del componente `System.Windows.Forms.HelpProvider` que proporciona ayuda emergente o en pantalla para los controles.

 **ImageList**

 Crea una instancia del componente `System.Windows.Forms.ImageList` que proporciona métodos para administrar una colección de objetos `System.Drawing.Image`.

 **MessageQueue**

 Crea una instancia del componente <xref:System.Messaging.MessageQueue> que se puede usar para interactuar con colas de mensajes, como leer mensajes y escribir mensajes en colas, procesar transacciones y realizar tareas de administración de colas.

 **PerformanceCounter**

 Crea una instancia del componente <xref:System.Diagnostics.PerformanceCounter> que se puede usar para interactuar con los contadores de rendimiento de Windows, como crear nuevas categorías e instancias, leer valores de contadores y realizar cálculos en datos del contador.

 **Process**

 Crea una instancia del componente <xref:System.Diagnostics.Process> que se puede usar para detener, iniciar y manipular los datos asociados con procesos del sistema.

 **SerialPort**

 Crea una instancia del componente `System.IO.Ports.SerialPort` que proporciona E/S sincrónica y orientada a eventos, el acceso a los estados de punto de conexión e interrupción y el acceso a las propiedades del controlador serie.

 **ServiceController**

 Crea una instancia del componente <xref:System.ServiceProcess.ServiceController> que puede usar para manipular servicios existentes, como iniciar y detener servicios y enviarles comandos.

 **Temporizador**

 Crea una instancia del componente <xref:System.Windows.Forms.Timer> que se puede usar para agregar funciones basadas en tiempo a las aplicaciones basadas en Windows. Para obtener más información, consulte [Timer (Componente)](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> También hay un componente <xref:System.Timers.Timer> basado en el sistema que se puede agregar al **Cuadro de herramientas**. Este componente <xref:System.Timers.Timer> está optimizado para aplicaciones de servidor, mientras que el componente <xref:System.Windows.Forms.Timer> de Windows Forms es más adecuado para su uso en Windows Forms.


## <a name="see-also"></a>Vea también

- [Programar con componentes](http://msdn.microsoft.com/Library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)
- [Tutoriales sobre la programación de componentes](http://msdn.microsoft.com/Library/373cacf7-479e-4b05-991c-5cb18824e913)
- [Cuadro de herramientas](../../ide/reference/toolbox.md)