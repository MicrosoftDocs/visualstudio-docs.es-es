---
title: Ejecución de la tabla de documentos | Microsoft Docs
description: Obtenga información sobre cómo Visual Studio IDE mantiene la tabla de documentos en ejecución, que incluye todos los documentos abiertos en memoria.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d260534d58853afc6b84ba484eb3a806250e2aa6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900413"
---
# <a name="running-document-table"></a>Tabla de documentos en ejecución
El IDE mantiene la lista de todos los documentos abiertos actualmente en una estructura interna denominada tabla de documentos en ejecución (RDT). Esta lista incluye todos los documentos abiertos en memoria, independientemente de si estos documentos se están editando actualmente. Un documento es cualquier elemento que se conserva, incluidos los archivos de un proyecto o el archivo de proyecto principal (por ejemplo, un archivo .vcxproj).

## <a name="elements-of-the-running-document-table"></a>Elementos de la tabla de documentos en ejecución
 La tabla de documentos en ejecución contiene las siguientes entradas.

|Elemento|Descripción|
|-------------|-----------------|
|Moniker de documento|Cadena que identifica de forma única el objeto de datos del documento. Esta sería la ruta de acceso de archivo absoluta para un sistema de proyecto que administra archivos (por ejemplo, C:\MyProject\MyFile). Esta cadena también se usa para proyectos guardados en almacenes que no son sistemas de archivos, como procedimientos almacenados en una base de datos. En este caso, el sistema del proyecto puede inventar una cadena única que pueda reconocer y, posiblemente, analizar para determinar cómo almacenar el documento.|
|Propietario de la jerarquía|Objeto de jerarquía que posee el documento, representado por una <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaz.|
|Id. de elemento|Identificador de elemento para un elemento específico dentro de la jerarquía. Este valor es único entre todos los documentos de la jerarquía propietaria de este documento, pero no se garantiza que este valor sea único en distintas jerarquías.|
|Objeto de datos de documento|Como mínimo, se trata de un `IUnknown`<br /><br /> objeto. El IDE no requiere ninguna interfaz concreta más allá de la interfaz para el objeto de datos de documento de un `IUnknown` editor personalizado. Sin embargo, para un editor estándar, la implementación del editor de la interfaz es necesaria para controlar las llamadas de persistencia <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> de archivos desde el proyecto. Para obtener más información, vea [Guardar un documento estándar.](../../extensibility/internals/saving-a-standard-document.md)|
|Marcas|Las marcas que controlan si se guarda el documento, si se aplica un bloqueo de lectura o edición, y así sucesivamente, se pueden especificar cuando se agregan entradas al RDT. Para obtener más información, vea la enumeración <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.|
|Editar recuento de bloqueos|Recuento de bloqueos de edición. Un bloqueo de edición indica que algún editor tiene el documento abierto para su edición. Cuando el recuento de bloqueos de edición pasa a cero, se solicita al usuario que guarde el documento, si se ha modificado. Por ejemplo, cada vez que se abre un documento en un editor mediante el comando **Nueva** ventana, se agrega un bloqueo de edición para ese documento en el RDT. Para que se establezca un bloqueo de edición, el documento debe tener un identificador de jerarquía o elemento.|
|Recuento de bloqueos de lectura|Recuento de bloqueos de lectura. Un bloqueo de lectura indica que el documento se está leyendo a través de algún mecanismo, como un asistente. Un bloqueo de lectura contiene un documento activo en el RDT, al tiempo que indica que no se puede editar el documento. Puede establecer un bloqueo de lectura incluso si el documento no tiene una jerarquía o un identificador de elemento. Esta característica permite abrir un documento en memoria y escribirlo en el RDT sin que el documento sea propiedad de ninguna jerarquía. Esta característica rara vez se usa.|
|Soporte de bloqueo|Instancia de una <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaz. El titular del bloqueo se implementa mediante características como asistentes que abren y editan documentos fuera de un editor. Un titular de bloqueo permite que la característica agregue un bloqueo de edición al documento para evitar que el documento se cierre mientras se sigue editando. Normalmente, los bloqueos de edición solo se agregan mediante ventanas de documento (es decir, editores).|

 Cada entrada del RDT tiene asociada una jerarquía única o un identificador de elemento, que normalmente corresponde a un nodo del proyecto. Todos los documentos disponibles para su edición suelen pertenecer a una jerarquía. Las entradas realizadas en el RDT controlan qué proyecto o, con más precisión, qué jerarquía posee actualmente el objeto de datos de documento que se está editando. Con la información del RDT, el IDE puede impedir que más de un proyecto abra un documento a la vez.

 La jerarquía también controla la persistencia de los datos y  usa la información del RDT para actualizar los cuadros de diálogo Guardar **y** Guardar como. Cuando los usuarios modifican un documento  y, a continuación, eligen  el comando Salir en el menú Archivo, el IDE les solicita el cuadro de diálogo Guardar cambios para mostrar todos los proyectos y elementos de proyecto que se han modificado actualmente.  Esto permite a los usuarios elegir cuál de los documentos guardar. La lista de documentos que se guardarán (es decir, los documentos que tienen cambios) se genera a partir del RDT. Los elementos que espera ver en el cuadro de **diálogo Guardar** cambios al salir de la aplicación deben tener registros en el RDT. El RDT coordina qué documentos se guardan y si se solicita al usuario una operación de guardado con los valores especificados en la entrada Marcas de cada documento. Para obtener más información sobre las marcas RDT, vea la <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> enumeración .

## <a name="edit-locks-and-read-locks"></a>Editar bloqueos y bloqueos de lectura
 Los bloqueos de edición y los bloqueos de lectura residen en el RDT. La ventana del documento incrementa y disminuye el bloqueo de edición. Por lo tanto, cuando un usuario abre una nueva ventana de documento, el recuento de bloqueos de edición se incrementa en una. Cuando el número de bloqueos de edición alcanza cero, se indica a la jerarquía que conserve o guarde los datos del documento asociado. A continuación, la jerarquía puede conservar los datos de cualquier manera, incluida la conservación como un archivo o como un elemento en un repositorio. Puede usar el método en la interfaz para agregar bloqueos de edición y bloqueos de lectura, y el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> para quitar estos <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> bloqueos.

 Normalmente, cuando se crea una instancia de la ventana de documento de un editor, el marco de ventana agrega automáticamente un bloqueo de edición para el documento en el RDT. Sin embargo, si crea una vista personalizada de un documento que no usa una ventana de documento estándar (es decir, no implementa la interfaz), debe establecer su propio bloqueo <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> de edición. Por ejemplo, en un asistente, se edita un documento sin abrirse en un editor. Para que los asistentes y entidades similares abran bloqueos de documentos, estas entidades deben implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaz . Para registrar el titular del bloqueo del documento, llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> método y pase la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implementación. Al hacerlo, se agrega el titular del bloqueo de documento al RDT. Otro escenario para implementar un titular de bloqueo de documento es si abre un documento a través de una ventana de herramientas especial. En este caso, no puede hacer que la ventana de herramientas cierre el documento. Sin embargo, al registrarse como un titular de bloqueo de documento en el RDT, el IDE puede llamar a la implementación del método para solicitar el cierre <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> del documento.

## <a name="other-uses-of-the-running-document-table"></a>Otros usos de la tabla de documentos en ejecución
 Otras entidades del IDE usan el RDT para obtener información sobre los documentos. Por ejemplo, el administrador de control de código fuente usa el RDT para decir al sistema que vuelva a cargar un documento en el editor, después de obtener la versión más reciente del archivo. Para ello, el administrador de control de código fuente busca los archivos del RDT para ver si alguno de ellos está abierto. Si lo están, el administrador de control de código fuente comprueba primero que la jerarquía implementa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> método . Si el proyecto no implementa el método , el administrador de control de código fuente comprueba directamente si hay una implementación del método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> en el objeto de datos del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> documento.

 El IDE también usa el RDT para volver a mostrar (llevar al frente) un documento abierto, si un usuario solicita ese documento. Para obtener más información, vea [Mostrar archivos mediante el comando Abrir archivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Para determinar si un archivo está abierto en rdT, realice una de las acciones siguientes.

- Consulte el moniker del documento (es decir, la ruta de acceso completa del documento) para averiguar si el elemento está abierto.

- Use la jerarquía o el identificador de elemento para solicitar al sistema del proyecto la ruta de acceso completa del documento y, a continuación, busque el elemento en el RDT.

## <a name="see-also"></a>Consulta también
- [Uso de RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Persistencia y tabla de documentos en ejecución](../../extensibility/internals/persistence-and-the-running-document-table.md)
