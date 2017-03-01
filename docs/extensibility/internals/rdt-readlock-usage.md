---
title: Uso de RDT_ReadLock | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: e7575b914f0645882f3570bdbe29221f2f8130cc
ms.openlocfilehash: a8ea44ef2dea3b3c4ebd29cf95b1886e2028e2c3
ms.lasthandoff: 02/22/2017

---
# <a name="rdtreadlock-usage"></a>Uso de RDT_ReadLock

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>es un indicador que proporciona la lógica para bloquear un documento en la ejecución documento tabla (RDT), que es la lista de todos los documentos que estén abiertos en el IDE de Visual Studio.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> Este indicador determina cuando se abren los documentos, y si el documento es visible en la interfaz de usuario o retenidos invisible en la memoria.

Por lo general, usaría <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>cuando uno de los siguientes es true:</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>

- Cuando desee abrir un documento de manera invisible y de sólo lectura, pero aún no se ha establecido que <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>debe tuyo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

- Si desea que el usuario que se le solicite que guarde un documento que se abrió de forma imperceptible antes de que el usuario aparece en la interfaz de usuario y, a continuación, intentó cerrar.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Cómo administrar documentos Visible e Invisible

Cuando un usuario abre un documento en la interfaz de usuario, un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>se debe establecer el propietario del documento y un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>se debe establecer la marca.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Si no hay ningún <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>se puede establecer el propietario, a continuación, el documento no se guardará cuando el usuario hace clic en **guardar todo** o cierra el IDE.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Esto significa que si un documento está abierto invisible cuando se modifica en la memoria y se le pide que guarde el documento en el apagado o se guardan si el usuario **guardar todo** elegida, un `RDT_ReadLock` no se puede usar. En su lugar, debe utilizar un `RDT_EditLock` y registrar un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>cuando un <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER>marca.</xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> </xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock y modificación de documento

La marca anterior mencionada indica que brindará la apertura del documento invisible su `RDT_EditLock` cuando se abre el documento por el usuario en un visible **DocumentWindow**. Cuando esto ocurre, se presenta al usuario con un **guardar** preguntar cuándo visibles **DocumentWindow** está cerrado. <xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel>las implementaciones que usan el <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>servicio funciona inicialmente cuando sólo una `RDT_ReadLock` se toma (es decir, cuando se abre el documento invisible para analizar la información).</xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager></xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel> Más adelante, si se debe modificar el documento, el bloqueo se actualiza a una débil **RDT_EditLock**. Si el usuario, a continuación, abre el documento en un visible **DocumentWindow**, `CodeModel`de débil `RDT_EditLock` se libera.

Si el usuario, a continuación, cierra el **DocumentWindow** y elige **No** cuando se le pida que guarde el documento abierto, la `CodeModel` implementación elimina toda la información en el documento y se vuelve a abrir el documento desde el disco invisible la próxima vez que se necesita para el documento más información. El problema de este comportamiento es una instancia donde el usuario abre el **DocumentWindow** del documento abierto invisible, lo modifica, lo cierra y, a continuación, elige **n** cuando se le pida que guarde el documento. En este caso, si el documento tiene un `RDT_ReadLock`, realmente no se cierra el documento y el documento modificado permanecerá abierto invisible en la memoria, aunque el usuario eligió no guardar el documento.

Si la apertura del documento invisible usa una débil `RDT_EditLock`, a continuación, genera su bloqueo cuando el usuario abre el documento de forma visible y no hay otros bloqueos. Cuando el usuario cierra la **DocumentWindow** y elige **n** cuando se le pida que guarde el documento, el documento deberá cerrarse de la memoria. Esto significa que el cliente invisible debe escuchar eventos RDT realizar el seguimiento de esta instancia. La próxima vez que el documento es necesario, debe abrirse el documento.
