---
title: "Tabla de documentos de ejecuci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "bloqueos de lectura"
  - "tabla document ejecución (RDT), IVsDocumentLockHolder (interfaz)"
  - "tabla de documentos de ejecución (RDT)"
  - "tabla document ejecución (RDT), los bloqueos de edición"
  - "objetos de datos de documentos, ejecutando la tabla document"
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Tabla de documentos de ejecuci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El IDE mantiene la lista de todos los documentos abiertos actualmente en una estructura interna denominada tabla de documento de ejecución \(RDT\). Esta lista incluye todos los documentos abiertos en memoria, independientemente de si estos documentos se esté editando. Un documento es cualquier elemento que se conserva, incluidos los archivos en un proyecto o el archivo de proyecto principal \(por ejemplo, un archivo .vcxproj\).  
  
## Elementos de la tabla Document de ejecución  
 La tabla document ejecución contiene las siguientes entradas.  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|Moniker del documento|Una cadena que identifica de forma única el objeto de datos del documento. Esto sería la ruta de acceso absoluta del archivo para un sistema de proyecto que administra los archivos \(por ejemplo, C:\\MyProject\\MyFile\). Esta cadena también se utiliza para los proyectos que se guardan en almacenes distintos sistemas de archivos, como procedimientos almacenados en una base de datos. En este caso, el sistema de proyectos puede inventar una cadena única que pueda reconocer y posiblemente analizar para determinar cómo almacenar el documento.|  
|Propietario de la jerarquía|El objeto de jerarquía que posee el documento, representado por un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaz.|  
|Id. de elemento|Identificador del elemento de un elemento específico dentro de la jerarquía. Este valor es único entre todos los documentos de la jerarquía que posee este documento, pero este valor no se garantiza que es único en jerarquías distintas.|  
|Objeto de datos de documento|Como mínimo, se trata de una `IUnknown`<br /><br /> objeto. El IDE no requiere ninguna interfaz determinada más allá de la `IUnknown` interfaz para el objeto de datos de documentos de un editor personalizado. Sin embargo, para un editor estándar, implementación del editor de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaz es necesaria para controlar las llamadas de persistencia de archivo del proyecto. Para obtener más información, consulta [Guardar un documento estándar](../../extensibility/internals/saving-a-standard-document.md).|  
|Marcas|Marcas que controlan si se guarda el documento, si se aplica un bloqueo de lectura o modificación y así sucesivamente, pueden especificarse si se agregan entradas a la RDT. Para obtener más información, consulte el <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> \(enumeración\).|  
|Editar el número de bloqueos|Recuento de bloqueos de edición. Un bloqueo de edición indica que algunos editor tiene el documento abierto para su edición. Cuando el recuento de bloqueos de edición realiza una transición a cero, se solicita al usuario para guardar el documento, si se ha modificado. Por ejemplo, cada vez que abra un documento en un editor con el **nueva ventana** comando, se agrega un bloqueo de edición para ese documento en el RDT. Para establecer un bloqueo de edición, el documento debe tener una jerarquía o identificador de elemento|  
|Recuento de bloqueos de lectura|Recuento de bloqueos de lectura. Un bloqueo de lectura indica que se está leyendo el documento a través de algún mecanismo como un asistente. Un bloqueo de lectura contiene un documento activo en el RDT indicando que no se puede editar el documento. Puede establecer un bloqueo de lectura incluso si el documento no tiene una jerarquía o identificador de elemento Esta característica permite abrir un documento en memoria y escríbala en el RDT sin el documento a la propiedad de cualquier jerarquía. Esta característica se utiliza habitualmente.|  
|Titular de bloqueo|Una instancia de un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaz. El titular de bloqueo se implementa mediante características como asistentes que abrir y edición documentos fuera de un editor. Un marcador de bloqueo permite que la característica que se va a agregar un bloqueo de edición al documento para impedir que se está cerrando mientras todavía se está editando el documento. Normalmente, modificar los bloqueos sólo se agregan por las ventanas de documento \(es decir, editores\).|  
  
 Cada entrada en el RDT tiene una única jerarquía o el Id. del elemento asociado, que suele corresponde a un nodo en el proyecto. Todos los documentos disponibles para su edición normalmente pertenecen a una jerarquía. Las entradas hechas en el RDT controlan qué proyecto o, con más precisión, qué jerarquía posee actualmente el objeto de datos de documento que se está editando. Con la información en el RDT, el IDE puede evitar que un documento que se está abriendo en más de un proyecto a la vez.  
  
 La jerarquía también controla la persistencia de los datos y utiliza la información en el RDT para actualizar la **Guardar** y **Guardar como** cuadros de diálogo. Cuando los usuarios modificar un documento y, a continuación, elija la **Exit** comando desde el **archivo** menú, el IDE lo solicite, con el **Guardar cambios** cuadro de diálogo para mostrar todos los proyectos y elementos de proyecto que actualmente se modifican. Esto permite a los usuarios elegir cuál de los documentos que se va a guardar. La lista de documentos para guardar \(es decir, los documentos que tienen cambios\) se genera a partir del RDT. Todos los elementos que se esperan ver en el **Guardar cambios** cuadro de diálogo al salir de la aplicación debe tener registros en el RDT. El RDT coordina los documentos que se guardan y si el usuario se pregunte si desea guardar operación mediante los valores especificados en la entrada de indicadores para cada documento. Para obtener más información sobre las marcas RDT, consulte el <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> \(enumeración\).  
  
## Bloqueos de edición y lectura  
 Editar bloqueos y bloqueos de lectura residen en el RDT. El documento ventana aumenta y disminuye la edición de bloqueo. Por lo tanto, cuando un usuario abre una nueva ventana de documento, la edición bloqueo recuento se incrementa en uno. Cuando el número de bloqueos de edición llega a cero, la jerarquía se señala a conservar o guardar los datos para el documento asociado. La jerarquía, a continuación, puede conservar los datos de cualquier manera, incluidas conservar como un archivo o como un elemento en un repositorio. Puede usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> método en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfaz Agregar edición bloqueos y bloqueos de lectura y la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> método para quitar estos bloqueos.  
  
 Normalmente, cuando se crea una instancia de la ventana de documento para un editor, el marco de ventana agrega automáticamente un bloqueo de edición para el documento en el RDT. Sin embargo, si crea una vista personalizada de un documento que no utiliza una ventana de documento estándar \(es decir, no implementa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaz\), a continuación, debe configurar su propio bloqueo de edición. Por ejemplo, en un asistente, se modifica un documento sin abrirlo en un editor. Para los bloqueos del documento debe abrirse con asistentes y entidades semejantes, estas entidades deben implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaz. Para registrar el titular del bloqueo de documento, llame el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> método y pase la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implementación. Al hacerlo, el titular del bloqueo de documento agrega al RDT. Otro escenario para implementar un titular de bloqueo de documento es si se abre un documento a través de una ventana de herramientas especiales. En este caso, no es posible tener la ventana de herramientas se cierre el documento. Sin embargo, al registrarse como un marcador de bloqueo de documento en el RDT, el IDE puede llamar a la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> método para solicitar un cierre del documento.  
  
## Otros usos de la tabla Document de ejecución  
 Otras entidades en el IDE utilizan el RDT para obtener información acerca de los documentos. Por ejemplo, el Administrador de control de origen utiliza el RDT debe para indicar al sistema para volver a cargar un documento en el editor, una vez que obtiene la versión más reciente del archivo. Para ello, el Administrador de control de origen busca los archivos en el RDT para ver si alguno de ellos están abierto. Si están, el Administrador de control de código fuente comprueba primero que implementa la jerarquía de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> \(método\). Si el proyecto no implementa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> método y, a continuación, el origen de control de revisiones de administrador para la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> método en el objeto de datos de documento directamente.  
  
 El IDE también usa el RDT reaparece \(Traer al frente\) un documento abierto, si un usuario solicita ese documento. Para obtener más información, consulta [Mostrar archivos mediante el comando Abrir archivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Para determinar si un archivo está abierto en el RDT, realice una de las siguientes.  
  
-   Consultar el moniker del documento \(es decir, la ruta de acceso completa del documento\) averiguar si el elemento está abierto.  
  
-   Utilice el identificador de jerarquía o elemento para pedir la ruta de acceso completa del documento en el sistema del proyecto y, a continuación, busque el elemento en el RDT.  
  
## Vea también  
 [Uso de RDT\_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)   
 [Persistencia y la tabla Document de ejecución](../../extensibility/internals/persistence-and-the-running-document-table.md)