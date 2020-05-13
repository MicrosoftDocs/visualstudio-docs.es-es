---
title: Query Edit Query Save (Control de código fuente VSPackage) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c09ac0cb4f51b8f2484b95d403ff6d0445631479
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705969"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Editar/guardar consulta (VSPackage de control de código fuente)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]los editores pueden transmitir eventos de query Edit Query Save (QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Source Control Stub implementa el servicio QEQS, de modo que sea el destinatario de eventos QEQS. Estos eventos, a continuación, se delegan en el control de código fuente activo actualVSPackage. El control de código fuente <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> activo VSPackage implementa el y sus métodos. Normalmente se `IVsQueryEditQuerySave2` llama a los métodos de la interfaz inmediatamente antes de editar un documento por primera vez e inmediatamente antes de guardar un documento.

## <a name="queryeditquerysave-events"></a>Eventos QueryEditQuerySave
 El control de código fuente VSPackage debe `IVsQueryEditQuerySave2` controlar los eventos QEQS mediante la implementación de la interfaz y los métodos necesarios. A continuación se muestra una breve descripción de los dos métodos que el VSPackage debe implementar como mínimo. La implementación real debe estar de acuerdo con la lógica del modelo de control de código fuente.

### <a name="queryeditfiles-method"></a>Método QueryEditFiles
 Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> llama cuando cualquier proyecto o editor desea modificar un archivo. Idealmente, se llama a este método *antes* de modificar el archivo y cuando se guarda un archivo. Cuando se `IVsQueryEditQuerySave2::QueryEditFiles` invoca, el método comprueba si los archivos especificados están bajo control de código fuente, si es necesario desprotegerlos y si se pueden volver a cargar. Si las circunstancias impiden que `IVsQueryEditQuerySave2::QueryEditFiles` los archivos se puedan editar, el método indica al programa que realiza la llamada que cancele la edición. También es posible que el autor de la llamada especifique un modo de invocación. En el modo "silencioso", este método toma acción solo si no hace que aparezca ninguna interfaz de usuario. Si la interfaz de usuario es inevitable, se debe devolver una marca para indicar el problema.

 El método se comporta de forma transaccional; es decir, si la edición se cancela en un solo archivo, la edición se cancela para todos los archivos. Por el contrario, si se permite la edición, se permite para todos los archivos. Si este método permite editar una vez para un conjunto determinado de archivos, siempre debe permitir la edición en llamadas posteriores para el mismo conjunto de archivos. El bucle allow-edit continúa hasta que los archivos se cierran, se guardan y se vuelven a cargar; hasta que sus atributos (propiedades) cambien; o hasta que se cambie el paquete de control de código fuente. Los casos a `IVsQueryEditQuerySave2::QueryEditFiles` tener en cuenta en la implementación del método incluyen varios archivos, archivos especiales, cancelar desde el usuario y ediciones en memoria.

### <a name="querysavefiles-method"></a>Método QuerySaveFiles
 Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> llama cuando cualquier proyecto o editor necesita guardar un conjunto de archivos. Cuando se `IVsQueryEditQuerySave2::QuerySaveFiles` invoca, el método comprueba si los archivos especificados son de solo lectura y si están bajo control de código fuente. Si es necesario desproteger los archivos, la llamada se delega en el paquete de control de código fuente. Si las circunstancias impiden que `IVsQueryEditQuerySave2::QuerySaveFiles` los archivos se guarden, el método debe indicar al editor que cancele el guardado. Al igual `IVsQueryEditQuerySave2::QueryEditFiles` que con el método, es posible que el autor de la llamada especifique un modo de invocación. En el modo "silencioso", este método toma acción solo si no hace que aparezca ninguna interfaz de usuario. Si la interfaz de usuario es inevitable, se debe devolver una marca para indicar el problema.

 Este método debe comportarse de forma transaccional; es decir, si el guardado se cancela en un solo archivo, el guardado se cancela para todos los archivos. Por el contrario, si se permite guardar, debe permitirse para todos los archivos. Al igual `IVsQueryEditQuerySave2::QueryEditFiles` que con el método, los casos a tener en cuenta en la implementación del `IVsQueryEditQuerySave2::QuerySaveFiles` método incluyen varios archivos, archivos especiales, cancelar desde el usuario y las ediciones en memoria.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
