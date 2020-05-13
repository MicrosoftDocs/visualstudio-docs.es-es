---
title: Uso de RDT_ReadLock de la banda de la página de la Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb897fab61e1e14b52863b5853748c685200d5ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705929"
---
# <a name="rdt_readlock-usage"></a>Uso de RDT_ReadLock

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) es una marca que proporciona lógica para bloquear un documento en la tabla de documentos en ejecución (RDT), que es la lista de todos los documentos que están abiertos actualmente en el IDE de Visual Studio. Esta marca determina cuándo se abren los documentos y si un documento es visible en la interfaz de usuario o se mantiene invisiblemente en la memoria.

Por lo general, [usas _VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) cuando se cumple una de las siguientes condiciones:

- Desea abrir un documento de forma invisible y de solo lectura, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> pero aún no se ha establecido el que debe poseerse.

- Desea que se pida al usuario que guarde un documento que se abrió de forma invisible antes de que el usuario lo mostrara en la interfaz de usuario y, a continuación, intentara cerrarlo.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Cómo administrar documentos visibles e invisibles

Cuando un usuario abre un documento <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> en la interfaz de usuario, se debe establecer un propietario para el documento y un [_VSRDTFLAGS. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) marca debe establecerse. Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> no se puede establecer ningún propietario, el documento no se guardará cuando el usuario haga clic en **Guardar todo** o cierre el IDE. Esto significa que si un documento está abierto de forma invisible donde se modifica en la memoria y se pide al `RDT_ReadLock` usuario que guarde el documento al apagarlo o guardarlo si se elige **Guardar todo,** no se puede utilizar un archivo. En su lugar, `RDT_EditLock` debe <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> usar un y registrar un [__VSREGDOCLOCKHOLDER. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) bandera.

## <a name="rdt_editlock-and-document-modification"></a>modificación de RDT_EditLock y documentos

La marca anterior mencionada indica que la apertura `RDT_EditLock` invisible del documento dará su cuando el documento sea abierto por el usuario en un **DocumentWindow**visible. Cuando esto ocurre, se presenta al usuario un símbolo del sistema **Save** cuando se cierra la **DocumentWindow** visible. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel`las implementaciones <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> que utilizan el servicio `RDT_ReadLock` funcionan inicialmente cuando solo se toma un (es decir, cuando el documento se abre de forma invisible para analizar información). Más adelante, si el documento se debe modificar, el bloqueo se actualiza a un **RDT_EditLock**débil. Si el usuario abre el documento en `CodeModel`una **DocumentWindow**visible , `RDT_EditLock` se libera el débil 's.

Si el usuario cierra el **DocumentWindow** y elige **No** cuando se le `CodeModel` pide que guarde el documento abierto, la implementación elimina toda la información en el documento y vuelve a abrir el documento desde el disco de forma invisible la próxima vez que se requiere más información para el documento. La sutileza de este comportamiento es una instancia donde el usuario abre el **DocumentWindow** del documento abierto invisible, lo modifica, lo cierra y, a continuación, elige **No** cuando se le pide que guarde el documento. En este caso, si `RDT_ReadLock`el documento tiene un , entonces el documento no se cerrará realmente y el documento modificado permanecerá abierto invisiblemente en la memoria, aunque el usuario haya elegido no guardar el documento.

Si la apertura invisible del `RDT_EditLock`documento utiliza un débil , entonces produce su bloqueo cuando el usuario abre el documento visiblemente y no se mantienen otros bloqueos. Cuando el usuario cierra **DocumentWindow** y elige **No** cuando se le pide que guarde el documento, el documento debe cerrarse de memoria. Esto significa que el cliente invisible debe escuchar los eventos RDT para realizar un seguimiento de esta ocurrencia. La próxima vez que se requiera el documento, el documento debe volver a abrirse.
