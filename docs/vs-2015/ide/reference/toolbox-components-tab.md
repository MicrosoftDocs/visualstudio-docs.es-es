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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661563"
---
# <a name="toolbox-components-tab"></a>Cuadro de herramientas, Componentes (Pestaña)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Muestra los componentes que puede agregar a diseñadores de [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] y [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Además de los componentes de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] que se incluyen con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], como los componentes <xref:System.Messaging.MessageQueue> y <xref:System.Diagnostics.EventLog>, puede agregar sus propios componentes o unos de terceros a esta pestaña. Para obtener más información, consulte [Cómo: Manipular las fichas del cuadro de herramientas](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

 Para mostrar esta pestaña, en el menú **Ver** seleccione **Cuadro de herramientas**. En el **Cuadro de herramientas**, seleccione la pestaña **Componentes**.

 **BackgroundWorker** Crea una instancia del componente `System.ComponentModel.BackgroundWorker` que puede ejecutar una operación en un subproceso independiente y dedicado.

 **DirectoryEntry** Crea una instancia del componente <xref:System.DirectoryServices.DirectoryEntry> que encapsula un nodo u objeto en la jerarquía de Active Directory y se puede usar para interactuar con los proveedores de servicios Active Directory.

 **DirectorySearcher** Crea una instancia del componente <xref:System.DirectoryServices.DirectorySearcher> que se puede utilizar para realizar consultas en el Active Directory.

 **ErrorProvider** Crea una instancia de componente de `System.Windows.Forms.ErrorProvider`, que indica al usuario final que un control de un formulario tiene un error asociado.

 **Registro de eventos** Crea una instancia de componente de <xref:System.Diagnostics.EventLog> que puede usar para interactuar con los registros de eventos del sistema y personalizados, incluida la escritura de eventos en un registro y la lectura de los datos de registro. Para obtener más información, consulte [Introducción al componente EventLog](https://msdn.microsoft.com/a2ba4f28-4b1a-435e-99ef-51b28e21f805).

 **FileSystemWatcher** Crea una instancia de componente de <xref:System.IO.FileSystemWatcher> que puede usar para supervisar los cambios en cualquier directorio o archivo al que tenga acceso. Para obtener más información, consulte [Cómo: Configurar instancias de componentes FileSystemWatcher](https://msdn.microsoft.com/2e628234-4951-4135-8a86-28b924070d50).

 **HelpProvider** Crea una instancia de componente de `System.Windows.Forms.HelpProvider` que proporciona ayuda emergente o en línea para los controles.

 **ImageList** Crea una instancia del componente de `System.Windows.Forms.ImageList` que proporciona métodos para administrar una colección de objetos `System.Drawing.Image`.

 **MessageQueue** Crea una instancia de componente de <xref:System.Messaging.MessageQueue> que se puede utilizar para interactuar con las colas de mensajes, como leer y escribir mensajes en colas, procesar transacciones y realizar tareas de administración de colas. Para obtener más información, consulte [Utilizar componentes de mensajería](https://msdn.microsoft.com/922dbac7-26f0-4e39-b666-ccfc184793d7).

 **PerformanceCounter** Crea una instancia del componente <xref:System.Diagnostics.PerformanceCounter> que se puede usar para interactuar con los contadores de rendimiento de Windows, incluida la creación de nuevas categorías e instancias, la lectura de valores de contadores y la realización de cálculos en los datos de los contadores. Para obtener más información, consulte [Supervisar umbrales de rendimiento](https://msdn.microsoft.com/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91).

 **Proceso** de Crea una instancia de componente de <xref:System.Diagnostics.Process> que puede usar para detener, iniciar y manipular los datos asociados a los procesos del sistema. Para obtener más información, consulte [Supervisar y administrar procesos de Windows](https://msdn.microsoft.com/a86bd4c1-b92c-49a0-8f32-61d67837b45e).

 **SerialPort** Crea una instancia del componente de `System.IO.Ports.SerialPort` que proporciona e/s sincrónica y orientada a eventos, el acceso a los Estados de punto de conexión e interrupción y el acceso a las propiedades del controlador serie.

 **ServiceController** Crea una instancia de componente de <xref:System.ServiceProcess.ServiceController> que puede usar para manipular servicios existentes, como iniciar y detener servicios y enviarles comandos. Para obtener más información, consulte [Supervisar servicios de Windows](https://msdn.microsoft.com/4542ee3f-e052-4cb9-8726-58e9420de222).

 **Temporizador** de Crea una instancia de componente de <xref:System.Windows.Forms.Timer> que puede usar para agregar funcionalidad basada en tiempo a las aplicaciones basadas en Windows. Para obtener más información, consulte [Timer (Componente)](https://msdn.microsoft.com/library/6700e534-6382-43d5-98ed-14205435fff7).

> [!NOTE]
> También hay un componente <xref:System.Timers.Timer> basado en el sistema que se puede agregar al **Cuadro de herramientas**. Este componente <xref:System.Timers.Timer> está optimizado para aplicaciones de servidor, mientras que el componente <xref:System.Windows.Forms.Timer> de Windows Forms es más adecuado para su uso en Windows Forms.

## <a name="see-also"></a>Otras referencias
 [Programar con componentes componentes](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3) [tutoriales de programación](https://msdn.microsoft.com/library/373cacf7-479e-4b05-991c-5cb18824e913) cuadro de [herramientas](../../ide/reference/toolbox.md) elegir elementos del cuadro de [herramientas (Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
