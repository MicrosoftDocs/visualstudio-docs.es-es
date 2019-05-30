---
title: Ejecución de la tabla de documentos | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd66b245da88b26c75c612ab7e45ccc01b4ab607
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318713"
---
# <a name="running-document-table"></a>Tabla de documentos en ejecución
El IDE mantiene la lista de todos los documentos abiertos actualmente en una estructura interna denominada de la tabla de documentos en ejecución (RDT). Esta lista incluye todos los documentos abiertos en memoria, independientemente de si actualmente se está editando estos documentos. Un documento es cualquier elemento que se conserva, incluidos los archivos en un proyecto o el archivo de proyecto principal (por ejemplo, un archivo .vcxproj).

## <a name="elements-of-the-running-document-table"></a>Elementos de la tabla de documentos en ejecución
 La tabla de documentos en ejecución contiene las siguientes entradas.

|Elemento|Descripción|
|-------------|-----------------|
|Moniker del documento|Cadena que identifica de forma única el objeto de datos. Esto sería la ruta de acceso absoluta del archivo para un sistema de proyectos que administra los archivos (por ejemplo, C:\MyProject\MyFile). Esta cadena se usa también para los proyectos que se guardan en almacenes distintos sistemas de archivos, como procedimientos almacenados en una base de datos. En este caso, el sistema del proyecto puede inventar una cadena única que puedan reconocer y posiblemente analizar para determinar cómo almacenar el documento.|
|Propietario de la jerarquía|El objeto de jerarquía que posee el documento, tal como está representada por un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaz.|
|Id. de elemento|Identificador de elemento de un elemento específico dentro de la jerarquía. Este valor es único entre todos los documentos de la jerarquía que posee este documento, pero este valor no se garantiza que ser único en jerarquías distintas.|
|Objeto de datos de documento|Como mínimo, se trata de un `IUnknown`<br /><br /> objeto. El IDE no requiere ninguna interfaz determinada más allá de la `IUnknown` interfaz para el objeto de datos de un editor personalizado documento. Sin embargo, para un editor estándar, implementación del editor de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaz necesaria para tratar las llamadas de persistencia de archivo del proyecto. Para obtener más información, consulte [guardar un documento estándar](../../extensibility/internals/saving-a-standard-document.md).|
|Marcas|Marcas que controlan si se guarda el documento, si se aplica un bloqueo de lectura o edición y así sucesivamente, se pueden especificar cuando se agregan entradas en el RDT. Para obtener más información, vea la enumeración <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.|
|Editar el número de bloqueos|Recuento de bloqueos de edición. Un bloqueo de edición indica que algunos editor tiene el documento abierto para su edición. Cuando el recuento de bloqueos de edición que se pasa a cero, se solicita al usuario para guardar el documento, si se ha modificado. Por ejemplo, cada vez que abre un documento en un editor mediante el **nueva ventana** comando, se agrega un bloqueo de edición para ese documento en el RDT. Para establecer un bloqueo de edición, el documento debe tener una jerarquía o identificador de elemento|
|Recuento de bloqueos de lectura|Recuento de bloqueos de lectura. Un bloqueo de lectura indica que se está leyendo el documento a través de algún mecanismo como un asistente. Un bloqueo de lectura contiene un documento activo en el RDT mientras que indica que no se puede editar el documento. Puede establecer un bloqueo de lectura incluso si el documento no tiene una jerarquía o identificador de elemento Esta característica permite abrir un documento en memoria y escribirla en el RDT sin el documento de cualquier jerarquía que pertenecen. Esta característica se usa con poca frecuencia.|
|Marcador de bloqueo|Una instancia de un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaz. El marcador de bloqueo se implementa mediante las características, como los asistentes que abrir y edición documentos fuera de un editor. Un marcador de bloqueo permite que la característica Agregar un bloqueo de edición al documento para impedir que se está cerrando mientras todavía se está editando el documento. Normalmente, editar los bloqueos solo se agregan por las ventanas de documento (es decir, los editores).|

 Cada entrada en el RDT tiene una jerarquía único o un identificador de elemento asociado, que suele corresponde a un nodo en el proyecto. Todos los documentos disponibles para su edición normalmente que posee una jerarquía. Las entradas realizadas en el RDT controlan qué proyecto, o, con más precisión, qué jerarquía, actualmente posee el objeto de datos que se está editando. Con la información en el RDT, el IDE puede evitar que un documento que se está abriendo en más de un proyecto a la vez.

 La jerarquía también controla la persistencia de datos y usa la información en el RDT para actualizar el **guardar** y **Guardar como** cuadros de diálogo. Cuando los usuarios modificar un documento y, a continuación, elija el **Exit** comando desde el **archivo** menú, el IDE muestra un mensaje con el **guardar cambios** cuadro de diálogo para mostrar todos los proyectos y elementos de proyecto que actualmente se modifican. Esto permite a los usuarios elegir cuál de los documentos que se va a guardar. La lista de documentos para guardar (es decir, aquellos documentos que tienen cambios) se genera a partir de la RDT. Todos los elementos que se esperan ver en el **guardar cambios** cuadro de diálogo cuando se sale de la aplicación debe tener registros en el RDT. La RDT coordina los documentos que se guardan y si se solicita al usuario sobre una operación de guardar operación utilizando los valores especificados en la entrada de marcas para cada documento. Para obtener más información sobre las marcas RDT, consulte el <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> enumeración.

## <a name="edit-locks-and-read-locks"></a>Bloqueos de edición y bloqueos de lectura
 Editar los bloqueos y bloqueos de lectura residen en el RDT. El documento ventana aumenta y disminuye la edición de bloqueo. Por lo tanto, cuando un usuario abre una nueva ventana de documento, el bloqueo de edición recuento aumenta en uno. Cuando el número de bloqueos de edición llega a cero, la jerarquía se señala para conservar o guardar los datos para el documento asociado. La jerarquía, a continuación, puede conservar los datos de cualquier forma, como conservar como un archivo o como un elemento en un repositorio. Puede usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> método en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfaz para agregar bloqueos de edición y bloqueos, de lectura y la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> método para quitar estos bloqueos.

 Normalmente, cuando se crea una instancia de la ventana de documento para un editor, el marco de ventana agrega automáticamente un bloqueo de edición para el documento en el RDT. Sin embargo, si crea una vista personalizada de un documento que no utiliza una ventana de documento estándar (es decir, no implementa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaz), a continuación, deberá establecer su propio bloqueo de edición. Por ejemplo, en un asistente, se modifica un documento sin que se abre en un editor. Para los bloqueos de documento debe abrirse con los asistentes y entidades semejantes, estas entidades deben implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaz. Para registrar el marcador de bloqueo del documento, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> método y pase la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implementación. Si lo hace, agrega el marcador de bloqueo del documento en el RDT. Otro escenario para la implementación de un marcador de bloqueo del documento es si abre un documento a través de una ventana de herramientas especiales. En este caso, no es posible que la ventana de herramientas se cierre el documento. Sin embargo, al registrarse como un marcador de bloqueo del documento en el RDT, el IDE puede llamar a la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> método para solicitar un cierre del documento.

## <a name="other-uses-of-the-running-document-table"></a>Otros usos de la tabla de documentos en ejecución
 Otras entidades en el IDE usan la RDT para obtener información acerca de los documentos. Por ejemplo, el Administrador de control de origen usa la RDT para indicar al sistema para volver a cargar un documento en el editor, una vez que obtiene la versión más reciente del archivo. Para ello, el Administrador de control de origen busca los archivos en el RDT para ver si alguno de ellos están abierto. Si son, a continuación, el Administrador de control de código fuente en primer lugar comprueba que la jerarquía implementa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> método. Si el proyecto no implementa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> manager busca una implementación de controlar el método y, a continuación, el origen de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> método en el objeto de datos de documento directamente.

 El IDE usa también la RDT reaparece (Traer al frente) un documento abierto, si un usuario solicita ese documento. Para obtener más información, consulte [mostrar archivos mediante el uso del comando archivo abrir](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Para determinar si un archivo está abierto en el RDT, realice una de las siguientes.

- Consulta para el moniker del documento (es decir, la ruta de acceso completa del documento) averiguar si el elemento está abierto.

- Use el identificador de jerarquía o el elemento para formular el sistema del proyecto para la ruta de acceso completa del documento y, a continuación, busque el elemento en el RDT.

## <a name="see-also"></a>Vea también
- [Uso de RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Persistencia y tabla de documentos en ejecución](../../extensibility/internals/persistence-and-the-running-document-table.md)