---
title: "Cuadro de herramientas, Componentes (Pesta&#241;a) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cuadro de herramientas, pestaña Componentes"
ms.assetid: 332fafab-a763-4244-b388-15d1b5b5cc04
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Cuadro de herramientas, Componentes (Pesta&#241;a)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Muestra componentes que puede agregar a los diseñadores de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] y [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].  Además de los componentes de [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] que se incluyen con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], como <xref:System.Messaging.MessageQueue> y <xref:System.Diagnostics.EventLog>, puede agregar sus propios componentes de otros fabricantes a esta ficha.  Para obtener más información, vea [How to: Manipulate Toolbox Tabs](http://msdn.microsoft.com/es-es/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
 Para mostrar esta ficha, dentro del menú **Ver** seleccione **Cuadro de herramientas**.  En el **Cuadro de herramientas**, seleccione la ficha **Componentes**.  
  
 **BackgroundWorker**  
 Crea una instancia de componente `System.ComponentModel.BackgroundWorker` que puede ejecutar una operación en un subproceso independiente dedicado.  
  
 **DirectoryEntry**  
 Crea una instancia del componente <xref:System.DirectoryServices.DirectoryEntry> que encapsula un nodo o un objeto de la jerarquía Active Directory y que se puede utilizar para interactuar con proveedores de servicios de Active Directory.  
  
 **DirectorySearcher**  
 Crea una instancia del componente <xref:System.DirectoryServices.DirectorySearcher> que se puede utilizar para realizar consultas en Active Directory.  
  
 **ErrorProvider**  
 Crea una instancia de componente `System.Windows.Forms.ErrorProvider` que indica al usuario final que un control de un formulario tiene un error asociado.  
  
 **EventLog**  
 Crea una instancia del componente <xref:System.Diagnostics.EventLog> que se puede utilizar para interactuar con registros de eventos tanto de sistema como personalizados, incluida la anotación de eventos en un registro y la lectura de datos de un registro.  Para obtener más información, vea [Introducción al componente EventLog](http://msdn.microsoft.com/es-es/a2ba4f28-4b1a-435e-99ef-51b28e21f805).  
  
 **FileSystemWatcher**  
 Crea una instancia del componente <xref:System.IO.FileSystemWatcher> que se puede utilizar para supervisar cambios en cualquier directorio o archivo al que puede tener acceso.  Para obtener más información, vea [How to: Configure FileSystemWatcher Component Instances](http://msdn.microsoft.com/es-es/2e628234-4951-4135-8a86-28b924070d50).  
  
 **HelpProvider**  
 Crea una instancia de componente `System.Windows.Forms.HelpProvider` que proporciona Ayuda emergente o en pantalla para los controles.  
  
 **ImageList**  
 Crea una instancia de componente `System.Windows.Forms.ImageList` que proporciona métodos para administrar una colección de objetos `System.Drawing.Image`.  
  
 **MessageQueue**  
 Crea una instancia del componente <xref:System.Messaging.MessageQueue> que se puede utilizar para interactuar con colas de mensajes, entre otras cosas permite leer mensajes de colas y escribir mensajes en colas, procesar transacciones y realizar tareas de administración de colas.  Para obtener más información, vea [Using Messaging Components](http://msdn.microsoft.com/es-es/922dbac7-26f0-4e39-b666-ccfc184793d7).  
  
 **PerformanceCounter**  
 Crea una instancia del componente <xref:System.Diagnostics.PerformanceCounter> que se puede utilizar para interactuar con contadores de rendimiento de Windows, así se pueden crear nuevas categorías e instancias, leer valores de contadores y realizar cálculos con datos del contador.  Para obtener más información, vea [Supervisar umbrales de rendimiento](http://msdn.microsoft.com/es-es/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91).  
  
 **Proceso**  
 Crea una instancia del componente <xref:System.Diagnostics.Process> que permite finalizar, iniciar y manipular los datos asociados con procesos del sistema.  Para obtener más información, vea [Supervisar y administrar procesos de Windows](http://msdn.microsoft.com/es-es/a86bd4c1-b92c-49a0-8f32-61d67837b45e).  
  
 **SerialPort**  
 Crea una instancia de componente `System.IO.Ports.SerialPort` que proporciona E\/S sincrónica y orientada a eventos, acceso a estados de punto de conexión e interrupción, y acceso a propiedades del controlador serie.  
  
 **ServiceController**  
 Crea una instancia del componente <xref:System.ServiceProcess.ServiceController> que permite manipular servicios existentes, así se pueden iniciar y detener servicios y enviar comandos a los mismos.  Para obtener más información, vea [Supervisar servicios de Windows](http://msdn.microsoft.com/es-es/4542ee3f-e052-4cb9-8726-58e9420de222).  
  
 **Temporizador**  
 Crea una instancia del componente <xref:System.Windows.Forms.Timer> que permite agregar a las aplicaciones basadas en Windows, una funcionalidad basada en el tiempo.  Para obtener más información, vea [Timer](../Topic/Timer%20Component%20\(Windows%20Forms\).md).  
  
> [!NOTE]
>  Hay también un <xref:System.Timers.Timer> basado en el sistema que puede agregar al **Cuadro de herramientas**. Este <xref:System.Timers.Timer> está optimizado para las aplicaciones de servidor, y <xref:System.Windows.Forms.Timer> de formularios Windows Forms es el más apropiado para su uso en formularios de Windows Forms.  
  
## Vea también  
 [Programming with Components](../Topic/Programming%20with%20Components.md)   
 [Component Programming Walkthroughs](../Topic/Component%20Programming%20Walkthroughs.md)   
 [cuadro de herramientas](../../ide/reference/toolbox.md)   
 [Choose Toolbox Items Dialog Box \(Visual Studio\)](http://msdn.microsoft.com/es-es/bd07835f-18a8-433e-bccc-7141f65263bb)