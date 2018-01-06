---
title: Uso de RDT_ReadLock | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 31c13d9255442459c884379e83b619e1f73a1c2a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="rdtreadlock-usage"></a>Uso de RDT_ReadLock

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>es una marca que proporciona la lógica para bloquear un documento en la ejecución documento tabla (RDT), que es la lista de todos los documentos que están abiertos en el IDE de Visual Studio. Este indicador determina cuando se abren documentos y, si un documento es visible en la interfaz de usuario o tuvo lugar invisible en memoria.

Por lo general, usaría <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> cuando uno de los siguientes es verdadera:

- Cuando desee abrir un documento de manera invisible y de solo lectura, pero aún no se ha establecido que <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> debería es su propietario.

- Si desea que el usuario se le solicite guardar un documento que se abrió invisible antes de que el usuario aparece en la interfaz de usuario y, a continuación, intentó cerrarlo.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Cómo administrar documentos Visible e Invisible

Cuando un usuario abre un documento en la interfaz de usuario, un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> debe establecerse el propietario del documento y un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> se debe establecer la marca. Si no hay ningún <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> propietario puede establecerse, a continuación, el documento no se guardarán cuando el usuario hace clic en **guardar todo** o cierra el IDE. Esto significa que si un documento está abierto invisible donde se han modificado en la memoria y el usuario se pregunte si desea guardar el documento en el apagado o se guarda si **guardar todo** se selecciona, un `RDT_ReadLock` no se puede usar. En su lugar, debe usar un `RDT_EditLock` y registrar un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> cuando un <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> marca.

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock y modificación del documento

La marca anterior se ha mencionado indica que produzca la apertura del documento invisible su `RDT_EditLock` cuando el usuario abre el documento en un visible **DocumentWindow**. Cuando esto ocurre, se presentará al usuario un **guardar** preguntar cuándo visibles **DocumentWindow** está cerrado. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel`las implementaciones que usan el <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> servicio funciona inicialmente cuando sólo un `RDT_ReadLock` procede (es decir, cuando el documento se abre de manera invisible para analizar la información). Más adelante, si se debe modificar el documento, el bloqueo se actualiza a una débil **RDT_EditLock**. Si el usuario, a continuación, abre el documento en un visible **DocumentWindow**, `CodeModel`del débil `RDT_EditLock` se libera.

Si el usuario, a continuación, cierra el **DocumentWindow** y elige **No** cuando se le pida que guarde el documento abierto, la `CodeModel` implementación elimina toda la información en el documento y se vuelve a abrir el documento desde el disco de manera invisible la próxima vez que se necesita para el documento más información. El detalle de este comportamiento es una instancia en el que el usuario abre el **DocumentWindow** del documento abierto invisible, lo modifique, lo cierra y, a continuación, elige **n** cuando se le pida que guarde el documento. En este caso, si el documento tiene un `RDT_ReadLock`, realmente no se cierra el documento y el documento modificado permanecerá abierto invisible en la memoria, aunque el usuario eligió no guardar el documento.

Si la apertura del documento invisible usa una débil `RDT_EditLock`, a continuación, produce el bloqueo cuando el usuario abre el documento visiblemente y no hay otros bloqueos. Cuando el usuario cierra el **DocumentWindow** y elige **n** cuando se le pida que guarde el documento, a continuación, cierra el documento debe ser de la memoria. Esto significa que el cliente sea invisible debe escuchar eventos RDT realizar el seguimiento de esta instancia. La próxima vez que el documento es necesario, el documento deberá abrirse de nuevo.