---
title: Consultar editar consulta guardar (VSPackage de control de código fuente) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be12297bdaeb112d7421b02da1153ed62d6d14f8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724769"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Editar/guardar consulta (VSPackage de control de código fuente)
los editores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pueden difundir eventos de modificación de consultas de edición de consulta (QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] código auxiliar de control de código fuente implementa el servicio QEQS, de modo que es el destinatario de los eventos QEQS. A continuación, estos eventos se delegan en el VSPackage de control de código fuente activo actualmente. El VSPackage de control de código fuente activo implementa los <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> y sus métodos. Normalmente, se llama a los métodos de la interfaz `IVsQueryEditQuerySave2` inmediatamente antes de que se edite un documento por primera vez y inmediatamente antes de que se guarde un documento.

## <a name="queryeditquerysave-events"></a>Eventos QueryEditQuerySave
 El VSPackage de control de código fuente debe controlar los eventos QEQS implementando la interfaz de `IVsQueryEditQuerySave2` y los métodos necesarios. A continuación se muestra una breve descripción de los dos métodos que el VSPackage debe implementar como mínimo. La implementación real debe estar de acuerdo con la lógica del modelo de control de código fuente.

### <a name="queryeditfiles-method"></a>Método QueryEditFiles
 Se llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> cuando cualquier proyecto o editor desea modificar un archivo. Idealmente, se llama a este método *antes* de que se modifique el archivo y cuando se guarda un archivo. Cuando se invoca, el método `IVsQueryEditQuerySave2::QueryEditFiles` comprueba si los archivos especificados están bajo control de código fuente, si es necesario desprotegerlos y si se pueden volver a cargar. Si las circunstancias impiden que los archivos sean editables, el método `IVsQueryEditQuerySave2::QueryEditFiles` indica al programa que realiza la llamada que cancele la edición. También es posible que el llamador especifique un modo de invocación. En el modo "silencioso", este método solo realiza una acción si no hace que aparezca ninguna interfaz de usuario. Si la interfaz de usuario es inevitable, se debe devolver una marca para indicar el problema.

 El método se comporta de manera transaccional; es decir, si se cancela la edición en un solo archivo, la edición se cancela para todos los archivos. Por el contrario, si se permite la edición, se permite para todos los archivos. Si este método permite la edición una vez para un conjunto determinado de archivos, siempre debe permitir la edición en llamadas posteriores para el mismo conjunto de archivos. El bucle allow-Edit continúa hasta que se cierran, guardan y recargan los archivos. hasta que cambien sus atributos (propiedades); o hasta que se cambie el paquete de control de código fuente. Entre los casos que se deben tener en cuenta al implementar el método `IVsQueryEditQuerySave2::QueryEditFiles` se incluyen varios archivos, archivos especiales, cancelación del usuario y ediciones en memoria.

### <a name="querysavefiles-method"></a>Método QuerySaveFiles
 Se llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> cuando cualquier proyecto o editor necesita guardar un conjunto de archivos. Cuando se invoca, el método `IVsQueryEditQuerySave2::QuerySaveFiles` comprueba si los archivos especificados son de solo lectura y si están bajo control de código fuente. Si los archivos deben desprotegerse, la llamada se delega en el paquete de control de código fuente. Si las circunstancias impiden que los archivos se guarden, el método `IVsQueryEditQuerySave2::QuerySaveFiles` debe indicar al editor que cancele la guardado. Al igual que con el método `IVsQueryEditQuerySave2::QueryEditFiles`, es posible que el llamador especifique un modo de invocación. En el modo "silencioso", este método solo realiza una acción si no hace que aparezca ninguna interfaz de usuario. Si la interfaz de usuario es inevitable, se debe devolver una marca para indicar el problema.

 Este método debe comportarse de manera transaccional; es decir, si se cancela la guardado en un único archivo, se cancela la guardado de todos los archivos. Por el contrario, si se permite el guardado, debe permitirse para todos los archivos. Al igual que con el método `IVsQueryEditQuerySave2::QueryEditFiles`, los casos que se deben tener en cuenta al implementar el método `IVsQueryEditQuerySave2::QuerySaveFiles` incluyen varios archivos, archivos especiales, cancelación del usuario y ediciones en memoria.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>