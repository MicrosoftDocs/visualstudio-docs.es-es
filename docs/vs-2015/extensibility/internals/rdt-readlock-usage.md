---
title: Uso de RDT_ReadLock | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9a6b5f86f0cfbb71f6264bdc74df72ad9209c9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154136"
---
# <a name="rdt_readlock-usage"></a>Uso de RDT_ReadLock
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> es una marca que proporciona lógica para bloquear un documento en la tabla de documentos en ejecución (RDT), que es la lista de todos los documentos que están abiertos actualmente en el IDE de Visual Studio. Esta marca determina cuándo se abren los documentos y si un documento es visible en la interfaz de usuario o se mantiene invisiblemente en la memoria.  
  
 Por lo general, se usaría <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> cuando se cumpla una de las siguientes condiciones:  
  
- Cuando desea abrir un documento de manera invisible y de solo lectura, pero aún no se ha establecido lo que <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> debe ser propietario.  
  
- Cuando quiera que se le solicite al usuario que guarde un documento que se abrió de manera invisible antes de que el usuario lo mostrara en la interfaz de usuario y, a continuación, intentara cerrarlo.  
  
## <a name="how-to-manage-visible-and-invisible-documents"></a>Cómo administrar documentos visibles e invisibles  
 Cuando un usuario abre un documento en la interfaz de usuario, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> se debe establecer un propietario para el documento y <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> se debe establecer una marca. Si no <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> se puede establecer ningún propietario, el documento no se guardará cuando el usuario haga clic en **guardar todo** o cierre el IDE. Esto significa que si un documento está abierto en un lugar invisible en el que se ha modificado en la memoria y se solicita al usuario que guarde el documento al cerrarse o se guarde si se elige **guardar todo** , `RDT_ReadLock` no se puede utilizar. En su lugar, debe utilizar `RDT_EditLock` y registrar un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> cuando una <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> marca.  
  
## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock y modificación del documento  
 La marca anterior mencionada indica que la apertura invisible del documento producirá su `RDT_EditLock` cuando el usuario abra el documento en un **DocumentWindow**visible. Cuando esto ocurre, se muestra al usuario un mensaje de **Guardar** cuando se cierra el **DocumentWindow** visible. Las implementaciones de Microsoft. VisualStudio. Package. Automation. OAProject. CodeModel que usan el <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> servicio funcionan inicialmente cuando solo `RDT_ReadLock` se toma un (es decir, cuando el documento se abre de forma invisible para analizar la información). Más adelante, si se debe modificar el documento, el bloqueo se actualiza a una **RDT_EditLock**débil. Si el usuario abre el documento en un **DocumentWindow**visible, `CodeModel` se libera el débil `RDT_EditLock` .  
  
 Si el usuario cierra el **DocumentWindow** y elige **no** cuando se le pide que guarde el documento abierto, la `CodeModel` implementación desecha toda la información del documento y vuelve a abrir el documento desde el disco de forma invisible la próxima vez que se necesite más información para el documento. El problema de este comportamiento es una instancia en la que el usuario abre el **DocumentWindow** del documento abierto invisible, lo modifica, lo cierra y, a continuación, elige **no** cuando se le pide que guarde el documento. En este caso, si el documento tiene un `RDT_ReadLock` , el documento no se cerrará realmente y el documento modificado permanecerá abierto de manera visible en la memoria, aunque el usuario haya optado por no guardar el documento.  
  
 Si la apertura invisible del documento utiliza un débil `RDT_EditLock` , produce su bloqueo cuando el usuario abre el documento de manera visible y no se mantiene ningún otro bloqueo. Cuando el usuario cierre el **DocumentWindow** y elija **no** cuando se le pida que guarde el documento, el documento se debe cerrar desde la memoria. Esto significa que el cliente invisible debe escuchar los eventos RDT para realizar el seguimiento de esta repetición. La próxima vez que se requiera el documento, se debe volver a abrir el documento.
