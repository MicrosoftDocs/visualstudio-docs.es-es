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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0ebbf8a0492537ee40062fb17bb338d46c228a9a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59652870"
---
# <a name="toolbox-components-tab"></a>Cuadro de herramientas, Componentes (Pestaña)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Muestra los componentes que puede agregar a diseñadores de [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] y [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Además de los componentes de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] que se incluyen con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], como los componentes <xref:System.Messaging.MessageQueue> y <xref:System.Diagnostics.EventLog>, puede agregar sus propios componentes o unos de terceros a esta pestaña. Para obtener más información, consulte [Cómo: Manipular las fichas del cuadro de herramientas](http://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
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
 Crea una instancia del componente <xref:System.Diagnostics.EventLog> que puede usar para interactuar con los registros de eventos personalizados y del sistema, como escribir eventos en un registro y leer datos de registro. Para obtener más información, consulte [Introducción al componente EventLog](http://msdn.microsoft.com/a2ba4f28-4b1a-435e-99ef-51b28e21f805).  
  
 **FileSystemWatcher**  
 Crea una instancia del componente <xref:System.IO.FileSystemWatcher> que se puede usar para supervisar cambios en cualquier directorio o archivo al que se tenga acceso. Para obtener más información, consulte [Cómo: Configurar instancias de componentes FileSystemWatcher](http://msdn.microsoft.com/2e628234-4951-4135-8a86-28b924070d50).  
  
 **HelpProvider**  
 Crea una instancia del componente `System.Windows.Forms.HelpProvider` que proporciona ayuda emergente o en pantalla para los controles.  
  
 **ImageList**  
 Crea una instancia del componente `System.Windows.Forms.ImageList` que proporciona métodos para administrar una colección de objetos `System.Drawing.Image`.  
  
 **MessageQueue**  
 Crea una instancia del componente <xref:System.Messaging.MessageQueue> que se puede usar para interactuar con colas de mensajes, como leer mensajes y escribir mensajes en colas, procesar transacciones y realizar tareas de administración de colas. Para obtener más información, consulte [Utilizar componentes de mensajería](http://msdn.microsoft.com/922dbac7-26f0-4e39-b666-ccfc184793d7).  
  
 **PerformanceCounter**  
 Crea una instancia del componente <xref:System.Diagnostics.PerformanceCounter> que se puede usar para interactuar con los contadores de rendimiento de Windows, como crear nuevas categorías e instancias, leer valores de contadores y realizar cálculos en datos del contador. Para obtener más información, consulte [Supervisar umbrales de rendimiento](http://msdn.microsoft.com/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91).  
  
 **Process**  
 Crea una instancia del componente <xref:System.Diagnostics.Process> que se puede usar para detener, iniciar y manipular los datos asociados con procesos del sistema. Para obtener más información, consulte [Supervisar y administrar procesos de Windows](http://msdn.microsoft.com/a86bd4c1-b92c-49a0-8f32-61d67837b45e).  
  
 **SerialPort**  
 Crea una instancia del componente `System.IO.Ports.SerialPort` que proporciona E/S sincrónica y orientada a eventos, el acceso a los estados de punto de conexión e interrupción y el acceso a las propiedades del controlador serie.  
  
 **ServiceController**  
 Crea una instancia del componente <xref:System.ServiceProcess.ServiceController> que puede usar para manipular servicios existentes, como iniciar y detener servicios y enviarles comandos. Para obtener más información, consulte [Supervisar servicios de Windows](http://msdn.microsoft.com/4542ee3f-e052-4cb9-8726-58e9420de222).  
  
 **Temporizador**  
 Crea una instancia del componente <xref:System.Windows.Forms.Timer> que se puede usar para agregar funciones basadas en tiempo a las aplicaciones basadas en Windows. Para obtener más información, consulte [Timer (Componente)](http://msdn.microsoft.com/library/6700e534-6382-43d5-98ed-14205435fff7).  
  
> [!NOTE]
>  También hay un componente <xref:System.Timers.Timer> basado en el sistema que se puede agregar al **Cuadro de herramientas**. Este componente <xref:System.Timers.Timer> está optimizado para aplicaciones de servidor, mientras que el componente <xref:System.Windows.Forms.Timer> de Windows Forms es más adecuado para su uso en Windows Forms.  
  
## <a name="see-also"></a>Vea también  
 [Programar con componentes](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)   
 [Tutoriales sobre la programación de componentes](http://msdn.microsoft.com/library/373cacf7-479e-4b05-991c-5cb18824e913)   
 [Cuadro de herramientas](../../ide/reference/toolbox.md)   
 [Elegir elementos del cuadro de herramientas (Cuadro de diálogo): Visual Studio](http://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
