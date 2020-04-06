---
title: Tabla de documentos en ejecución (en ejecución de la tabla de documento Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e6aa882921786b1592922372581beae8c4c2443
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705566"
---
# <a name="running-document-table"></a>Tabla de documentos en ejecución
El IDE mantiene la lista de todos los documentos abiertos actualmente en una estructura interna denominada tabla de documentos en ejecución (RDT). Esta lista incluye todos los documentos abiertos en la memoria, independientemente de si estos documentos se están editando actualmente. Un documento es cualquier elemento que se conserva, incluidos los archivos de un proyecto o el archivo de proyecto principal (por ejemplo, un archivo .vcxproj).

## <a name="elements-of-the-running-document-table"></a>Elementos de la tabla de documentos en ejecución
 La tabla de documentos en ejecución contiene las siguientes entradas.

|Elemento|Descripción|
|-------------|-----------------|
|Apodo de documento|Cadena que identifica de forma única el objeto de datos del documento. Esta sería la ruta de acceso de archivo absoluta para un sistema de proyectos que administra archivos (por ejemplo, C:-MiProyecto-MiArchivo). Esta cadena también se utiliza para proyectos guardados en almacenes distintos de los sistemas de archivos, como los procedimientos almacenados en una base de datos. En este caso, el sistema de proyecto puede inventar una cadena única que puede reconocer y posiblemente analizar para determinar cómo almacenar el documento.|
|Propietario de la jerarquía|El objeto de jerarquía que posee el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> documento, representado por una interfaz.|
|ID de artículo|Identificador de elemento para un elemento específico dentro de la jerarquía. Este valor es único entre todos los documentos de la jerarquía que posee este documento, pero no se garantiza que este valor sea único en distintas jerarquías.|
|Objeto de datos de documento|Como mínimo, se trata de un`IUnknown`<br /><br /> objeto. El IDE no requiere ninguna `IUnknown` interfaz en particular más allá de la interfaz para el objeto de datos de documento de un editor personalizado. Sin embargo, para un editor estándar, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> la implementación de la interfaz del editor es necesaria para controlar las llamadas de persistencia de archivos desde el proyecto. Para obtener más información, consulte [Guardar un documento estándar](../../extensibility/internals/saving-a-standard-document.md).|
|Marcas|Los indicadores que controlan si se guarda el documento, si se aplica un bloqueo de lectura o edición, etc., se pueden especificar cuando se agregan entradas al RDT. Para obtener más información, vea la enumeración <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.|
|Editar recuento de bloqueos|Recuento de bloqueos de edición. Un bloqueo de edición indica que algún editor tiene el documento abierto para su edición. Cuando el recuento de bloqueos de edición pasa a cero, se solicita al usuario que guarde el documento, si se ha modificado. Por ejemplo, cada vez que se abre un documento en un editor mediante el comando **Nueva ventana,** se agrega un bloqueo de edición para ese documento en el RDT. Para establecer un bloqueo de edición, el documento debe tener una jerarquía o un identificador de elemento.|
|Leer recuento de bloqueos|Recuento de cerraduras de lectura. Un bloqueo de lectura indica que el documento se está leyendo a través de algún mecanismo, como un asistente. Un bloqueo de lectura mantiene un documento activo en el RDT mientras indica que el documento no se puede editar. Puede establecer un bloqueo de lectura incluso si el documento no tiene una jerarquía o un identificador de elemento. Esta característica le permite abrir un documento en la memoria e introducirlo en el RDT sin que el documento sea propiedad de ninguna jerarquía. Esta característica rara vez se utiliza.|
|Soporte de bloqueo|Instancia de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> una interfaz. El soporte de bloqueo se implementa mediante características como asistentes que abren y editan documentos fuera de un editor. Un soporte de bloqueo permite que la función agregue un bloqueo de edición al documento para evitar que el documento se cierre mientras se está editando. Normalmente, los bloqueos de edición solo se agregan mediante ventanas de documento (es decir, editores).|

 Cada entrada en el RDT tiene una jerarquía única o identificador de elemento asociado, que generalmente corresponde a un nodo del proyecto. Todos los documentos disponibles para su edición suelen ser propiedad de una jerarquía. Las entradas realizadas en el control RDT que proyecto, o, más exactamente, qué jerarquía, posee actualmente el objeto de datos de documento que se está editando. Con la información del RDT, el IDE puede impedir que más de un proyecto abra un documento a la vez.

 La jerarquía también controla la persistencia de los datos y utiliza la información del RDT para actualizar los cuadros de diálogo **Guardar** y **Guardar como.** Cuando los usuarios modifican un documento y, a continuación, eligen el comando **Salir** del menú **Archivo,** el IDE les solicita con el cuadro de diálogo **Guardar cambios** que les muestre todos los proyectos y elementos de proyecto que se modifican actualmente. Esto permite a los usuarios elegir cuál de los documentos guardar. La lista de documentos que se va a guardar (es decir, los documentos que tienen cambios) se genera desde el RDT. Todos los elementos que espera ver en el cuadro de diálogo **Guardar cambios** al salir de la aplicación deben tener registros en el RDT. El RDT coordina qué documentos se guardan y si se solicita al usuario acerca de una operación de salvar utilizando los valores especificados en la entrada Indicadores para cada documento. Para obtener más información sobre los <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> indicadores RDT, vea la enumeración.

## <a name="edit-locks-and-read-locks"></a>Editar bloqueos y leer bloqueos
 Editar bloqueos y bloqueos de lectura residen en el RDT. La ventana del documento incrementa y disminuye el bloqueo de edición. Por lo tanto, cuando un usuario abre una nueva ventana de documento, el recuento de bloqueos de edición aumenta en uno. Cuando el número de bloqueos de edición llega a cero, se indica a la jerarquía que persista o guarde los datos del documento asociado. A continuación, la jerarquía puede conservar los datos de cualquier manera, incluida la persistencia como un archivo o como un elemento en un repositorio. Puede usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> en la interfaz para agregar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> bloqueos de edición y bloqueos de lectura, y el método para quitar estos bloqueos.

 Normalmente, cuando se crea una instancia de la ventana de documento de un editor, el marco de ventana agrega automáticamente un bloqueo de edición para el documento en el RDT. Sin embargo, si crea una vista personalizada de un documento que no utiliza <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> una ventana de documento estándar (es decir, no implementa la interfaz), debe establecer su propio bloqueo de edición. Por ejemplo, en un asistente, un documento se edita sin abrirse en un editor. Para que los bloqueos de documentos se abran los asistentes y entidades similares, estas entidades deben implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaz. Para registrar el titular del <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> bloqueo de documentos, llame al método y pase la implementación. <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Al hacerlo, se añade el soporte de bloqueo de documentos al RDT. Otro escenario para implementar un soporte de bloqueo de documento es si abre un documento a través de una ventana de herramientas especial. En este caso, no puede hacer que la ventana de herramientas cierre el documento. Sin embargo, al registrarse como titular de bloqueo de documentos <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> en el RDT, el IDE puede llamar a la implementación del método para solicitar un cierre del documento.

## <a name="other-uses-of-the-running-document-table"></a>Otros usos de la tabla de documentos en ejecución
 Otras entidades del IDE usan el RDT para obtener información sobre los documentos. Por ejemplo, el administrador de control de código fuente utiliza el RDT para indicar al sistema que vuelva a cargar un documento en el editor, después de obtener la versión más reciente del archivo. Para ello, el administrador de control de código fuente busca los archivos en el RDT para ver si alguno de ellos está abierto. Si lo son, el administrador de control de código fuente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> comprueba primero para ver que la jerarquía implementa el método. Si el proyecto no <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementa el método, el administrador de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> control de código fuente comprueba si hay una implementación del método en el objeto de datos de documento directamente.

 El IDE también usa el RDT para resurgir (llevar al frente) un documento abierto, si un usuario solicita ese documento. Para obtener más información, consulte [Visualización de archivos mediante el comando Abrir archivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Para determinar si un archivo está abierto en el RDT, haga una de las siguientes acciones.

- Consulte el moniker del documento (es decir, la ruta de acceso completa del documento) para averiguar si el elemento está abierto.

- Utilice la jerarquía o el identificador de elemento para solicitar al sistema de proyectos la ruta de acceso completa del documento y, a continuación, busque el elemento en el RDT.

## <a name="see-also"></a>Vea también
- [Uso de RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Persistencia y tabla de documentos en ejecución](../../extensibility/internals/persistence-and-the-running-document-table.md)
