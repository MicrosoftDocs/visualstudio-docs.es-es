---
title: Ejecuta la tabla Document | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4a49a5267fcccbde60e194e3fc58b0f6b6ea7552
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="running-document-table"></a>Tabla de documentos en ejecución
El IDE mantiene la lista de todos los documentos abiertos actualmente en una estructura interna denominada la tabla document ejecución (RDT). Esta lista incluye todos los documentos abiertos en la memoria, independientemente de si actualmente se está editando estos documentos. Un documento es cualquier elemento que se conserva, incluidos los archivos en un proyecto o el archivo de proyecto principal (por ejemplo, un archivo .vcxproj).  
  
## <a name="elements-of-the-running-document-table"></a>Elementos de la tabla Document de ejecución  
 La tabla document ejecución contiene las siguientes entradas.  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Moniker del documento|Una cadena que identifica de forma única el objeto de datos del documento. Esto sería la ruta de acceso absoluta del archivo para un sistema de proyecto que administra los archivos (por ejemplo, C:\MyProject\MyFile). Esta cadena se usa también para los proyectos que se guardan en almacenes de distintos sistemas de archivos, como procedimientos almacenados en una base de datos. En este caso, el sistema del proyecto puede inventar una cadena única que pueda reconocer y posiblemente analizar para determinar cómo almacenar el documento.|  
|Propietario de la jerarquía|El objeto de jerarquía que posee el documento, tal como está representado por un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaz.|  
|Id. del elemento|Identificador del elemento de un elemento específico de la jerarquía. Este valor es único entre todos los documentos de la jerarquía que posee este documento, pero este valor no se garantiza que es único en jerarquías distintas.|  
|Objeto de datos de documento|Como mínimo, se trata de una `IUnknown`<br /><br /> objeto. El IDE no requiere ninguna interfaz determinado más allá de la `IUnknown` interfaz para el objeto de datos de un editor personalizado documento. Sin embargo, para un editor estándar, implementación del editor de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaz es necesario para controlar las llamadas de persistencia de archivo del proyecto. Para obtener más información, consulte [guardar un documento estándar](../../extensibility/internals/saving-a-standard-document.md).|  
|Marcas|Marcas que controlan si se guarda el documento, si se aplica un bloqueo de lectura o modificación y así sucesivamente, pueden especificarse cuando se agregan entradas a la RDT. Para obtener más información, vea la enumeración <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.|  
|Editar el número de bloqueos|Recuento de bloqueos de edición. Un bloqueo de edición indica que algunos editor tiene el documento abierto para su edición. Cuando el recuento de bloqueos de edición realiza una transición a cero, se pide al guardar el documento, el usuario si se ha modificado. Por ejemplo, cada vez que abre un documento en un editor con el **nueva ventana** comando, se agrega un bloqueo de edición para ese documento en el RDT. En orden a establecerse un bloqueo de edición, el documento debe tener una jerarquía o identificador de elemento|  
|Recuento de bloqueos de lectura|Recuento de bloqueos de lectura. Un bloqueo de lectura indica que se está leyendo el documento a través de algún mecanismo como un asistente. Un bloqueo de lectura contiene un documento activo en el RDT indicando que no se puede editar el documento. Puede establecer un bloqueo de lectura incluso si el documento no tiene una jerarquía o identificador de elemento Esta característica permite abrir un documento en memoria y escribirla en el RDT sin el documento que pertenezca a cualquier jerarquía. Esta característica se usa con poca frecuencia.|  
|Propietario de bloqueo|Una instancia de un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaz. El titular de bloqueo se implementa mediante características como asistentes que abrir y edición documentos fuera de un editor. Un propietario de bloqueo permite que la característica que se va a agregar un bloqueo de edición en el documento para impedir que el documento se está cerrando mientras todavía se está editando. Normalmente, editar bloqueos solo se agregan por las ventanas de documento (es decir, editores).|  
  
 Cada entrada en el RDT tiene una jerarquía única o el Id. del elemento asociado con él, que suele corresponde a un nodo en el proyecto. Todos los documentos disponibles para su edición normalmente pertenecen a una jerarquía. Las entradas hechas en el RDT controlan qué proyecto, o, con más precisión, qué jerarquía posee actualmente el objeto de datos de documento que se está editando. Con la información en el RDT, el IDE puede evitar que un documento que se va a abrir más de un proyecto a la vez.  
  
 La jerarquía también controla la persistencia de los datos y utiliza la información en el RDT para actualizar la **guardar** y **Guardar como** cuadros de diálogo. Cuando los usuarios modificar un documento y, a continuación, elija la **Exit** línea de comandos desde el **archivo** menú, el IDE muestra un mensaje con el **guardar cambios** cuadro de diálogo para mostrar todos los proyectos y elementos de proyecto que actualmente se modifican. Esto permite a los usuarios elegir cuál de los documentos que se va a guardar. La lista de documentos para guardar (es decir, aquellos documentos que han sufrido cambios) se genera a partir del RDT. Todos los elementos que se esperan ver en el **guardar cambios** cuadro de diálogo al salir de la aplicación debe tener registros en el RDT. El RDT coordina los documentos que se guardan y si se solicita al usuario acerca de un proceso de guardar operación con los valores especificados en la entrada de indicadores para cada documento. Para obtener más información sobre las marcas RDT, consulte el <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> enumeración.  
  
## <a name="edit-locks-and-read-locks"></a>Editar bloqueos y bloqueos de lectura  
 Editar bloqueos y bloqueos de lectura residen en el RDT. Los incrementos de la ventana de documento y disminuye la edición de bloqueo. Por lo tanto, cuando un usuario abre una nueva ventana de documento, la edición bloqueo recuento se incrementa en uno. Cuando el número de bloqueos de edición llega a cero, la jerarquía se señala a conservar o guardar los datos para el documento asociado. La jerarquía, a continuación, puede conservar los datos de cualquier manera, incluidos conservar como un archivo o como un elemento en un repositorio. Puede usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> método en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfaz para agregar edición bloqueos y bloqueos, de lectura y la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> método para quitar estos bloqueos.  
  
 Normalmente, cuando se crea una instancia de la ventana de documento para un editor, el marco de ventana agrega automáticamente un bloqueo de edición para el documento en el RDT. Sin embargo, si crea una vista personalizada de un documento que no usa una ventana de documento estándar (es decir, no implementa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaz), a continuación, es necesario establecer su propio bloqueo de edición. Por ejemplo, en un asistente, se modifica un documento sin que se va a abrir en un editor. En orden para los bloqueos de documento para abrirse mediante asistentes y entidades similares, deben implementar estas entidades la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaz. Para registrar el titular de bloqueo de documento, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> método y pase la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implementación. Esta forma, agregará el titular de bloqueo de documento para el RDT. Otro escenario para implementar un titular de bloqueo de documento es si se abre un documento a través de una ventana de herramientas especial. En este caso, no es posible que la ventana de herramientas se cierre el documento. Sin embargo, si se registra como un marcador de bloqueo de documento en el RDT, el IDE puede llamar a la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> método para solicitar un cierre del documento.  
  
## <a name="other-uses-of-the-running-document-table"></a>Otros usos de la tabla Document de ejecución  
 Otras entidades en el IDE utilice el RDT para obtener información acerca de los documentos. Por ejemplo, el Administrador de control de origen usa el RDT para indicar al sistema que volver a cargar un documento en el editor, una vez que obtiene la versión más reciente del archivo. Para ello, el Administrador de control de origen busca los archivos en el RDT para ver si alguno de ellos están abierto. Si son, a continuación, el Administrador de control de código fuente comprueba primero que la jerarquía implementa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> método. Si el proyecto no implementa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> método y, a continuación, el origen de control de revisiones de administrador para una implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> método en el objeto de datos de documento directamente.  
  
 El IDE usa también el RDT reaparece (Traer al frente) un documento abierto, si un usuario solicita ese documento. Para obtener más información, consulte [mostrar archivos mediante el comando archivo abrir](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Para determinar si un archivo está abierto en el RDT, realice una de las siguientes.  
  
-   Consulta para el moniker del documento (es decir, la ruta de acceso completa del documento) averiguar si el elemento está abierto.  
  
-   Use el identificador de jerarquía o elemento para solicitar el sistema del proyecto para la ruta de acceso completa del documento y, a continuación, busque el elemento en el RDT.  
  
## <a name="see-also"></a>Vea también  
 [Uso de RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)   
 [Persistencia y tabla de documentos en ejecución](../../extensibility/internals/persistence-and-the-running-document-table.md)