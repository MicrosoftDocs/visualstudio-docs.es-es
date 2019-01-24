---
title: Uso de RDT_ReadLock | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 96248d799eae5005c996fa1cc192ee3b447571f8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837438"
---
# <a name="rdtreadlock-usage"></a>Uso de RDT_ReadLock

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> es una marca que proporciona la lógica para el bloqueo de un documento en el documento tabla ejecución (RDT), que es la lista de todos los documentos abiertos actualmente en el IDE de Visual Studio. Este indicador determina cuándo se abren documentos, y si el documento es visible en la interfaz de usuario o retenido invisible en la memoria.

Por lo general, se usaría <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> cuando uno de los siguientes es verdadera:

- Cuando desee abrir un documento de manera invisible y de solo lectura, pero todavía no se ha establecido que <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> debe es su propietario.

- Si desea que el usuario que se le solicite guardar un documento que se abrió de manera invisible antes de que el usuario muestra en la interfaz de usuario y, a continuación, intentó cerrarlo.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Cómo administrar documentos Visible e Invisible

Cuando un usuario abre un documento en la interfaz de usuario, un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> se debe establecer el propietario del documento y un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> se debe establecer la marca. Si no hay ningún <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> se puede establecer el propietario y, después, el documento no se guardarán cuando el usuario hace clic en **guardar todo** o cierra el IDE. Esto significa que si un documento está abierto invisible cuando se modifica en la memoria y el usuario se le pide que guarde el documento en el apagado o se guarda si **guardar todo** se elige una `RDT_ReadLock` no se puede usar. En su lugar, debe usar un `RDT_EditLock` y registrar un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> cuando un <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> marca.

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock y modificación del documento

La marca anterior se ha mencionado indica que la apertura del documento invisible produzca su `RDT_EditLock` cuando se abre el documento por el usuario en un visible **DocumentWindow**. Cuando esto ocurre, se presentará al usuario un **guardar** preguntar cuándo visibles **DocumentWindow** está cerrado. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` las implementaciones que usan el <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> servicio funcionan inicialmente cuando solo una `RDT_ReadLock` se toma (es decir, cuando se abre el documento invisible para analizar la información). Más adelante, si se debe modificar el documento, el bloqueo se actualiza a una débil **RDT_EditLock**. Si el usuario, a continuación, abre el documento en un visible **DocumentWindow**, `CodeModel`del débil `RDT_EditLock` se libera.

Si el usuario, a continuación, cierra el **DocumentWindow** y elige **No** cuando se le pida que guarde el documento abierto, el `CodeModel` implementación elimina toda la información en el documento y vuelve a abrir el documento desde el disco de manera invisible la próxima vez que se necesita para el documento más información. El matiz de este comportamiento es una instancia donde el usuario abre el **DocumentWindow** del documento abierto invisible, lo modifica, lo cierra y, a continuación, elige **No** cuando se le pida que guarde el documento. En este caso, si el documento tiene un `RDT_ReadLock`, realmente no se cierra el documento y el documento modificado se mantendrá abierto invisible en la memoria, aunque el usuario eligió no guardar el documento.

Si la apertura del documento invisible usa una débil `RDT_EditLock`, a continuación, produce el bloqueo cuando el usuario abre el documento visiblemente y no hay otros bloqueos. Cuando el usuario cierra el **DocumentWindow** y elige **No** cuando se le pida que guarde el documento, el documento debe cerrarse de la memoria. Esto significa que debe escuchar el cliente sea invisible para que los eventos RDT realizar el seguimiento de este suceso. La próxima vez que el documento es necesario, deberá abrirse el documento.