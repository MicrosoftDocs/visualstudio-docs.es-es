---
title: Cuadro de herramientas, Componentes (Pestaña) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
ms.assetid: 332fafab-a763-4244-b388-15d1b5b5cc04
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce18767d95b3ac539737d78acbd2259dcda0a036
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661563"
---
# <a name="toolbox-components-tab"></a>Cuadro de herramientas, Componentes (Pestaña)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Muestra los componentes que puede agregar a diseñadores de [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] y [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Además de los [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] componentes que se incluyen con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , como los <xref:System.Messaging.MessageQueue> <xref:System.Diagnostics.EventLog> componentes y, puede agregar sus propios componentes de o de terceros a esta pestaña. Para obtener más información, vea [Cómo: manipular pestañas del cuadro de herramientas](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

 Para mostrar esta pestaña, en el menú **Ver** seleccione **Cuadro de herramientas**. En el **Cuadro de herramientas**, seleccione la pestaña **Componentes**.

 **BackgroundWorker** Crea una `System.ComponentModel.BackgroundWorker` instancia del componente que puede ejecutar una operación en un subproceso independiente y dedicado.

 **DirectoryEntry** Crea una <xref:System.DirectoryServices.DirectoryEntry> instancia del componente que encapsula un nodo u objeto en la jerarquía de Active Directory y se puede usar para interactuar con proveedores de servicios de Active Directory.

 **DirectorySearcher** Crea una <xref:System.DirectoryServices.DirectorySearcher> instancia del componente que se puede usar para realizar consultas en el Active Directory.

 **ErrorProvider** Crea una `System.Windows.Forms.ErrorProvider` instancia del componente, que indica al usuario final que un control de un formulario tiene un error asociado.

 **Registro de eventos** Crea una <xref:System.Diagnostics.EventLog> instancia del componente que puede usar para interactuar con los registros de eventos del sistema y personalizados, incluida la escritura de eventos en un registro y la lectura de los datos de registro. Para obtener más información, consulte [Introducción al componente EventLog](https://msdn.microsoft.com/a2ba4f28-4b1a-435e-99ef-51b28e21f805).

 **FileSystemWatcher** Crea una <xref:System.IO.FileSystemWatcher> instancia del componente que puede usar para supervisar los cambios en cualquier directorio o archivo al que tenga acceso. Para obtener más información, consulte [Cómo: Configurar instancias de componentes FileSystemWatcher](https://msdn.microsoft.com/2e628234-4951-4135-8a86-28b924070d50).

 **HelpProvider** Crea una `System.Windows.Forms.HelpProvider` instancia del componente que proporciona ayuda emergente o en línea para los controles.

 **ImageList** Crea una `System.Windows.Forms.ImageList` instancia del componente que proporciona métodos para administrar una colección de `System.Drawing.Image` objetos.

 **MessageQueue** Crea una <xref:System.Messaging.MessageQueue> instancia del componente que puede usar para interactuar con las colas de mensajes, lo que incluye la lectura y la escritura de mensajes en colas, el procesamiento de transacciones y la realización de tareas de administración de colas. Para obtener más información, consulte [Utilizar componentes de mensajería](https://msdn.microsoft.com/922dbac7-26f0-4e39-b666-ccfc184793d7).

 **PerformanceCounter** Crea una <xref:System.Diagnostics.PerformanceCounter> instancia del componente que se puede usar para interactuar con los contadores de rendimiento de Windows, como crear nuevas categorías e instancias, leer valores de contadores y realizar cálculos en los datos de los contadores. Para obtener más información, consulte [Supervisar umbrales de rendimiento](https://msdn.microsoft.com/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91).

 **Proceso** de Crea una <xref:System.Diagnostics.Process> instancia del componente que puede usar para detener, iniciar y manipular los datos asociados a los procesos del sistema. Para obtener más información, consulte [Supervisar y administrar procesos de Windows](https://msdn.microsoft.com/a86bd4c1-b92c-49a0-8f32-61d67837b45e).

 **SerialPort** Crea una `System.IO.Ports.SerialPort` instancia del componente que proporciona e/s sincrónica y orientada a eventos, el acceso a los Estados de punto de conexión e interrupción y el acceso a las propiedades del controlador serie.

 **ServiceController** Crea una <xref:System.ServiceProcess.ServiceController> instancia del componente que puede usar para manipular servicios existentes, como iniciar y detener servicios y enviarles comandos. Para obtener más información, consulte [Supervisar servicios de Windows](https://msdn.microsoft.com/4542ee3f-e052-4cb9-8726-58e9420de222).

 **Temporizador** de Crea una <xref:System.Windows.Forms.Timer> instancia del componente que puede usar para agregar funcionalidad basada en tiempo a las aplicaciones basadas en Windows. Para obtener más información, consulte [Timer (Componente)](https://msdn.microsoft.com/library/6700e534-6382-43d5-98ed-14205435fff7).

> [!NOTE]
> También hay un componente <xref:System.Timers.Timer> basado en el sistema que se puede agregar al **Cuadro de herramientas**. Este componente <xref:System.Timers.Timer> está optimizado para aplicaciones de servidor, mientras que el componente <xref:System.Windows.Forms.Timer> de Windows Forms es más adecuado para su uso en Windows Forms.

## <a name="see-also"></a>Consulte también
 [Programar con componentes componentes](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3) [tutoriales de programación](https://msdn.microsoft.com/library/373cacf7-479e-4b05-991c-5cb18824e913) cuadro de [herramientas](../../ide/reference/toolbox.md) elegir elementos del cuadro de [herramientas (Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
